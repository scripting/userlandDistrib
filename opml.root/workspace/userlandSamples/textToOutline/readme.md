### workspace.userlandSamples.textToOutline
<pre>
on textToOutline ()
   //Changes
      //2/25/15; 12:05:19 PM by DW
         //Take a string of text separated by \n chars and break it up into an outline.
   local (s = string (scratchpad.exampletext), adroutline = @scratchpad.exampleoutline)
   new (outlinetype, adroutline)
   target.set (adroutline)
   loop
      line = string.nthfield (s, "\n", 1)
      op.insert (line, down)
      s = string.delete (s, 1, sizeof (line) + 1)
      if sizeof (s) == 0
         break
bundle //test code
   textToOutline ()

</pre>