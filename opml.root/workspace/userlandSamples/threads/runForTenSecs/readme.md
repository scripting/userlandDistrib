### workspace.userlandSamples.threads.runForTenSecs
<pre>
on runForTenSecs ()
   //Changes
      //5/17/13; 11:05:12 AM by DW
         //Created.
   adrmsg = @scratchpad.idscripts.[thread.getCurrentId ()]
   for i = 1 to 10
      clock.waitseconds (1)
      adrmsg^ = i
   adrmsg^ = ""
bundle //test code
   runForTenSecs ()

</pre>