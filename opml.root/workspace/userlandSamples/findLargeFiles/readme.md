### workspace.userlandSamples.findLargeFiles
<pre>
on findLargeFiles (folder, maxbytes=1024*1024*100)
   //Changes
      //6/6/09; 9:48:24 AM by DW
         //Created. Find large files in the indicated folder. Default size is 100MB
   local (f, adroutline = @scratchpad.largeFiles)
   new (outlinetype, adroutline)
   target.set (adroutline)
   edit (adroutline)
   fileloop (f in folder, infinity)
      if file.size (f) > maxbytes
         op.insert (f, down)
   op.firstsummit (); op.deleteline ()
bundle //test code
   findLargeFiles ("Ohio:")

</pre>