### workspace.userlandSamples.soapValidatorScripts.soapValidatorHandlers.arrayOfStructsTest
<pre>
on arrayOfStructsTest (myArray)
   local (i, ct = 0, struct)
   for i = 1 to sizeof (myArray)
      struct = myArray [i]
      ct = ct + struct.curly
   return (ct)

</pre>