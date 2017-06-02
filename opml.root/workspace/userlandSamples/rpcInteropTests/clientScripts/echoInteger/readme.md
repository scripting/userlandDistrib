### workspace.userlandSamples.rpcInteropTests.clientScripts.echoInteger
<pre>
on echoInteger (server, port, protocol)
   local (anInteger = random (-5000, 5000))
   
   local (result, params = &#123;"inputInteger":anInteger})
   result = xml.rpc (server, port, "interopEchoTests.echoInteger", @params, protocol:protocol, soapAction:"/interopEchoTests")
   
   if result != anInteger
      scriptError ("The call failed because the response was different from the request. We sent " + anInteger + " and the server returned " + result + ".")
   
   return (true) //success

</pre>