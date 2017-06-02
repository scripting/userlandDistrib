### workspace.userlandSamples.rpcInteropTests.clientScripts.echoFloat
<pre>
on echoFloat (server, port, protocol)
   local (numerator = random (-5000, 5000))
   local (denominator = random (1, 1000))
   local (aFloat = double (numerator) / denominator)
   
   local (result, params = &#123;"inputFloat":aFloat})
   result = xml.rpc (server, port, "interopEchoTests.echoFloat", @params, protocol:protocol, soapAction:"/interopEchoTests")
   
   if not workspace.userlandSamples.rpcInteropTests.floatNearlyEqual (result, aFloat)
      scriptError ("The call failed because the response was different from the request. We sent " + aFloat + " and the server returned " + result + ".")
   
   return (true) //success

</pre>