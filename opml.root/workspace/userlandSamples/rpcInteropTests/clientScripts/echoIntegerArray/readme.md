### workspace.userlandSamples.rpcInteropTests.clientScripts.echoIntegerArray
<pre>
on echoIntegerArray (server, port, protocol)
   local (anIntegerArray = {})
   bundle //generate the array
      local (i)
      for i = 1 to 3
         local (anInteger = random (-5000, 5000))
         anIntegerArray = anIntegerArray + anInteger
   
   local (result, params = {"inputIntegerArray":anIntegerArray})
   result = xml.rpc (server, port, "interopEchoTests.echoIntegerArray", @params, protocol:protocol, soapAction:"/interopEchoTests")
   
   if typeOf (result) != listType
      scriptError ("The call failed because the response was not an array.")
   local (i, ct = sizeOf (result))
   if ct != sizeOf (anIntegerArray)
      scriptError ("The call failed because the size of the request array is different from the size of the response array.")
   for i = 1 to ct
      if result[i] != anIntegerArray[i]
         scriptError ("The call failed because the response was different from the request. We sent " + anIntegerArray[i] + " for element " + i + ", and the server returned " + result[i] + ".")
   
   return (true) //success

</pre>