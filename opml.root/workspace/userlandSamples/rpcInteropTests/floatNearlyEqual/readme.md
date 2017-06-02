### workspace.userlandSamples.rpcInteropTests.floatNearlyEqual
<pre>
on floatNearlyEqual (a, b)
   //4/16/01; 2:18:29 PM by JES
      //Tests whether two floating point numbers are close enough to be considered equal.
      //This is necessary because binary representations of floating point numbers do not map exactly to decimal representations, so converstions may introduce small, but acceptible errors.
   if a == b
      return (true)
   local (epsilon = 0.0000001)
   local (nearlyEqual = abs (a - b) &lt;= (abs (a) * epsilon))
   return (nearlyEqual)

</pre>