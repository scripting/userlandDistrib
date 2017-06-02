### workspace.userlandSamples.rpcInteropTests.rpcHandlers.echoFloat
<pre>
on echoFloat (inputFloat)
   if typeOf (inputFloat) == doubleType
      return (inputFloat)
   if defined (soap.constants.floatINF)
      case inputFloat
         soap.constants.floatINF
         soap.constants.floatNegativeINF
         soap.constants.floatNaN
            return (inputFloat)
   scriptError ("Can't process the request because the input parameter was not a float.")

</pre>