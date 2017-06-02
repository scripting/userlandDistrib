### workspace.userlandSamples.rpcInteropTests.clientScripts.echoFloatArray
<pre>
on echoFloatArray (server, port, protocol)
   local (aFloatArray = {})
   bundle //generate the array
      local (i)
      for i = 1 to 3
         local (numerator = random (-5000, 5000))
         local (denominator = random (1, 1000))
         local (aFloat = double (numerator) / denominator)
         aFloatArray = aFloatArray + aFloat
   
   local (result, params = {"inputFloatArray":aFloatArray})
   result = xml.rpc (server, port, "interopEchoTests.echoFloatArray", @params, protocol:protocol, soapAction:"/interopEchoTests")
   
   if typeOf (result) != listType
      scriptError ("The call failed because the response was not an array.")
   local (i, ct = sizeOf (result))
   if ct != sizeOf (aFloatArray)
      scriptError ("The call failed because the size of the request array is different from the size of the response array.")
   for i = 1 to ct
      if not workspace.userlandSamples.rpcInteropTests.floatNearlyEqual (result[i], aFloatArray[i])
         scriptError ("The call failed because the response was different from the request. We sent " + aFloatArray[i] + " for element " + i + ", and the server returned " + result[i] + ".")
   
   return (true) //success

</pre>