### workspace.userlandSamples.fasterTextBuilding
<pre>
on fasterTextBuilding ()
   //Changes
      //8/27/11; 9:55:36 AM by DW
         //We discovered a faster way to build blocks of text, something web applications do a lot. Two methods below, one is faster, as you'll see by running this script.
   local (ctloops = 25000)
   on fastmethod ()
      local (htmltext = "", indentlevel = 0, i)
      on add (s)
         htmltext = htmltext + (string.filledstring ("\t", indentlevel) + s + "\r");
      indentlevel = 1
      for i = 1 to ctloops
         add (string.filledstring ("123456789 ", random (1, 10)))
      return (htmltext)
   on slowmethod ()
      local (htmltext = "", indentlevel = 0, i, tc = clock.ticks ())
      on add (s)
         htmltext = htmltext + string.filledstring ("\t", indentlevel) + s + "\r";
      indentlevel = 1
      for i = 1 to ctloops
         add (string.filledstring ("123456789 ", random (1, 10)))
      return (htmltext)
   local (tc = clock.ticks ())
   fastmethod ()
   fastticks = clock.ticks () - tc; tc = clock.ticks ()
   slowmethod ()
   slowticks = clock.ticks () - tc
   dialog.alert ("fast = " + fastticks + " ticks. slow = " + slowticks + ".")
bundle //test code
   fasterTextBuilding ()

</pre>