### workspace.userlandSamples.rpcInteropTests.rpcHandlers.echoFloatArray
<pre>
on echoFloatArray (inputFloatArray)
   if typeOf (inputFloatArray) != listType
      scriptError ("Can't process the request because the input parameter is not an array of floats.")
   for i = 1 to sizeOf (inputFloatArray)
      if typeOf (inputFloatArray[i]) != doubleType
         scriptError ("Can't process the request because element " + i + " (1-based) is not a float.")
   return (inputFloatArray)

</pre>