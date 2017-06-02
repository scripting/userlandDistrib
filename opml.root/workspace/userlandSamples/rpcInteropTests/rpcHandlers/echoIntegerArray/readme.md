### workspace.userlandSamples.rpcInteropTests.rpcHandlers.echoIntegerArray
<pre>
on echoIntegerArray (inputIntegerArray)
   if typeOf (inputIntegerArray) != listType
      scriptError ("Can't process the request because the input parameter is not an array of integers.")
   for i = 1 to sizeOf (inputIntegerArray)
      if typeOf (inputIntegerArray[i]) != longType
         scriptError ("Can't process the request because element " + i + " (1-based) is not an integer.")
   return (inputIntegerArray)

</pre>