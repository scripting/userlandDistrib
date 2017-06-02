### workspace.userlandSamples.rpcInteropTests.rpcHandlers.echoStringArray
<pre>
on echoStringArray (inputStringArray)
   if typeOf (inputStringArray) != listType
      scriptError ("Can't process the request because the input parameter was not an array of strings.")
   for i = 1 to sizeOf (inputStringArray)
      if typeOf (inputStringArray[i]) != stringType
         scriptError ("Can't process the request because element " + i + " (1-based) is not a string.")
   return (inputStringArray)

</pre>