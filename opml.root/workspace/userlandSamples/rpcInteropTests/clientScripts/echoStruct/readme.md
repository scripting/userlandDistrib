### workspace.userlandSamples.rpcInteropTests.clientScripts.echoStruct
<pre>
on echoStruct (server, port, protocol)
   local (numerator = random (-5000, 5000))
   local (denominator = random (1, 1000))
   local (aFloat = double (numerator) / denominator)
   
   local (anInteger = random (-5000, 5000))
   
   local (n = random (1, 50))
   local (aString = states.nthState (n))
   
   local (aStruct); new (tableType, @aStruct)
   aStruct.varFloat = aFloat
   aStruct.varInt = anInteger
   aStruct.varString = aString
   
   local (result, params = &#123;"inputStruct":aStruct})
   result = xml.rpc (server, port, "interopEchoTests.echoStruct", @params, protocol:protocol, soapAction:"/interopEchoTests")
   
   bundle //test return value
      if typeOf (result) != tableType
         scriptError ("The call failed because the response was not a struct.")
      if not workspace.userlandSamples.rpcInteropTests.floatNearlyEqual (result.varFloat, aFloat)
         scriptError ("The call failed because the response struct's float was different from the request. We sent " + aFloat + " and the server returned " + result.varFloat + ".")
      if result.varInt != anInteger
         scriptError ("The call failed because the response struct's integer was different from the request. We sent " + anInteger + " and the server returned " + result.varInt + ".")
      if result.varString != aString
         scriptError ("The call failed because the response struct's string was different from the request. We sent " + aString + " and the server returned " + result.varString + ".")
   
   return (true) //success

</pre>