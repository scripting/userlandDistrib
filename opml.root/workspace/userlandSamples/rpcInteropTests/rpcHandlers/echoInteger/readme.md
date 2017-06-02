### workspace.userlandSamples.rpcInteropTests.rpcHandlers.echoInteger
<pre>
on echoInteger (inputInteger)
   if typeOf (inputInteger) == longType
      return (inputInteger)
   scriptError ("Can't process the request because the input parameter is not an integer.")

</pre>