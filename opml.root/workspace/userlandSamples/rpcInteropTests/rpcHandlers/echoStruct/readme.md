### workspace.userlandSamples.rpcInteropTests.rpcHandlers.echoStruct
<pre>
on echoStruct (inputStruct)
   if typeOf (inputStruct) != tableType
      scriptError ("Can't process the request because the input parameter is not a struct.")
   return (inputStruct)

</pre>