### workspace.userlandSamples.soapValidatorScripts.soapValidatorHandlers.simpleStructReturnTest
<pre>
on simpleStructReturnTest (myNumber)
   local (struct)
   new (tabletype, @struct)
   struct.times10 = myNumber * 10
   struct.times100 = myNumber * 100
   struct.times1000 = myNumber * 1000
   return (struct)

</pre>