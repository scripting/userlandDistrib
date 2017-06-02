### workspace.userlandSamples.webserverThreadWatcher
<pre>
on webserverThreadWatcher (pta)
   //Changes
      //2/24/12; 4:42:36 PM by DW
         //A sample script that runs when ever a hit comes into your server. It keeps a table at system.temp.threadtable, which it opens when it creates it, that has one entry for each active thread. If a thread hangs around for a long time that could be a sign of a problem.
            //http://worknotes.scripting.com/february2012/22412ByDw/threadwatcherSampleScript/
   local (adrtable = @system.temp.threadtable)
   //scratchpad.threadwatcherparams = pta^ //debugging
   bundle //add the thread to the table
      local (url = pta^.host + pta^.uri, adrsub, flnew = false)
      if not defined (adrtable^)
         new (tabletype, adrtable)
         flnew = true
      adrsub = @adrtable^.[thread.getCurrentID ()]
      adrsub^ = url
      if flnew
         edit (adrtable)
   bundle //delete items if the thread it represents is gone
      local (i, adrsub, id)
      for i = sizeof (adrtable^) downto 1
         adrsub = @adrtable^ [i]
         id = nameof (adrsub^)
         if not thread.exists (id)
            delete (adrsub)
bundle //test code
   user.webserver.preFilters.threadWatcher = this

</pre>