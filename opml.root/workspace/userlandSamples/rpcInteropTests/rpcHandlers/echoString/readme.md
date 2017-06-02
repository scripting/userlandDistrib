### workspace.userlandSamples.rpcInteropTests.rpcHandlers.echoString
<pre>
on echoString (inputString)
   if typeOf (inputString) == stringType
      return (inputString)
   ScriptError ("Can't process the request because the input parameter is not a string.")

</pre>