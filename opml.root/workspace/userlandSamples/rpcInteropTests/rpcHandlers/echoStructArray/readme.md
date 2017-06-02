### workspace.userlandSamples.rpcInteropTests.rpcHandlers.echoStructArray
<pre>
on echoStructArray (inputStructArray)
   if defined (adrRequest) //set some directives if we're processing a SOAP request
      if defined (adrRequest^)
         adrRequest^.customStructType = "SOAPStruct"
         adrRequest^.customNamespace = "urn"
         adrRequest^.customNamespaceURI = "http://www.xmethods.com/service"
   if typeOf (inputStructArray) != listType and typeOf (inputStructArray) != tableType
      scriptError ("Can't process the request because the input parameter was not an array of structs.")
   local (returnArray = &#123;})
   for i = 1 to sizeOf (inputStructArray)
      if typeOf (inputStructArray[i]) != tableType
         scriptError ("Can't process the request because element " + i + " (1-based) is not a struct.")
      returnArray[i] = inputStructArray[i]
   return (returnArray)

</pre>