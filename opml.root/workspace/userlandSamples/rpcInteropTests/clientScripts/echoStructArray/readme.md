### workspace.userlandSamples.rpcInteropTests.clientScripts.echoStructArray
<pre>
on echoStructArray (server, port, protocol)
   local (aStructArray = &#123;})
   bundle //generate the array
      local (i)
      for i = 1 to 3
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
         
         aStructArray[0] = aStruct
   
   local (result, params = &#123;"inputStructArray":aStructArray})
   case protocol
      "xml-rpc"
         result = xml.rpc (server, port, "interopEchoTests.echoStructArray", @params, protocol:protocol, soapAction:"/interopEchoTests")
      "soap"
         result = soap.rpc.client ("/interopEchoTests", "echoStructArray", @params, server, port, customStructType:"SOAPStruct", customNamespace:"urn", customNamespaceURI:"url", flDebug:true)
   
   bundle //test return value
      if typeOf (result) != listType and typeOf (result) != tableType
         scriptError ("The call failed because the response was not an array.")
      local (i, ct = sizeOf (result))
      if ct != sizeOf (aStructArray)
         scriptError ("The call failed because the size of the request array is different from the size of the response array.")
      for i = 1 to ct
         local (aRequestStruct = aStructArray[i])
         local (aResultStruct = result[i])
         if typeOf (aResultStruct) != tableType
            scriptError ("The call failed because the response was not a struct.")
         if not workspace.userlandSamples.rpcInteropTests.floatNearlyEqual (aResultStruct.varFloat, aRequestStruct.varFloat)
            scriptError ("The call failed because the response struct's float was different from the request. We sent " + aRequestStruct.varFloat + " and the server returned " + aResultStruct.varFloat + ".")
         if aResultStruct.varInt != aRequestStruct.varInt
            scriptError ("The call failed because the response struct's integer was different from the request. We sent " + aRequestStruct.varInt + " and the server returned " + aResultStruct.varInt + ".")
         if aResultStruct.varString != aRequestStruct.varString
            scriptError ("The call failed because the response struct's string was different from the request. We sent " + aRequestStruct.varString + " and the server returned " + aResultStruct.varString + ".")
   
   return (true) //success

</pre>