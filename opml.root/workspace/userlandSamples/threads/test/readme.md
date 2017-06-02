### workspace.userlandSamples.threads.test
<pre>
on test ()
   //Changes
      //5/17/13; 11:03:49 AM by DW
         //Created.
   local (adrtable = @scratchpad.idscripts)
   new (tabletype, adrtable)
   for i = 1 to 10
      adrtable^.[thread.callscript (@workspace.userlandSamples.threads.runForTenSecs, &#123;})] = 0
   edit (adrtable)
   window.zoom (adrtable)
bundle //test code
   test ()

</pre>