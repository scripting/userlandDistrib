### workspace.userlandSamples.rpcInteropTests.clientScripts.echoString
<pre>
on echoString (server, port, protocol)
   local (n = random (1, 50))
   local (aString = states.nthState (n))
   
   local (result, params = {"inputString":aString})
   result = xml.rpc (server, port, "interopEchoTests.echoString", @params, protocol:protocol, soapAction:"/interopEchoTests")
   
   if result != aString
      scriptError ("The call failed because the response was different from the request. We sent " + aString + " and the server returned " + result + ".")
   
   return (true) //success

</pre>