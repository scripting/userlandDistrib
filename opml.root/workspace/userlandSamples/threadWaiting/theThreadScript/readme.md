### workspace.userlandSamples.threadWaiting.theThreadScript
<pre>
//Changes
   //12/7/10; 7:27:05 PM by DW
      //Created. 
local (startticks = clock.ticks ())
thread.sleepfor (15)
local (waketicks = clock.ticks ())
local (secs = string.formatdouble (double (waketicks - startticks) / 60))
dialog.alert ("We were asleep for " + secs + " seconds.")

</pre>