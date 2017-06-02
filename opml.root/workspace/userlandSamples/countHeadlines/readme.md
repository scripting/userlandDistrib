### workspace.userlandSamples.countHeadlines
<pre>
//Changes
   //2/9/11; 3:47:12 PM by DW
      //Count the number of top-level headlines in the front outline window.
local (ct = 0)
op.firstsummit ()
loop
   ct++
   if not op.go (down, 1)
      break
dialog.alert (ct)

</pre>