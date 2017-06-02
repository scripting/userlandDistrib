### workspace.userlandSamples.webserverCallback
<pre>
on webserverCallback (pta)
   //Changes
      //2/14/12; 10:57:33 AM by DW
         //A sample script that runs when ever a hit comes into your server. All the information about the request is in pta. In the first line, we copy it into a global so you can have a look. Rename the table to get another example to scratch your head over. :-)
            //http://worknotes.scripting.com/february2012/21412ByDw/sampleWebserverCallbackScript
   if not defined (scratchpad.debugParams)
      scratchpad.debugParams = pta^ //copy it to a place where you can look at it
   log2.scroller ("http://" + pta^.host + pta^.uri)
   return (true)
bundle //code that installs this script
   user.webserver.preFilters.testFilter = this

</pre>