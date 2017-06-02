### workspace.userlandSamples.threadAnalyzer
<pre>
//Changes
   //1/16/10; 9:47:49 AM by DW
      //Lots of changes. 
         //If there's an error in locating a thread, put the cursor on the element that caused it so you can delete it.
         //Look in the hourly and overnight tables.
         //Look in scheduler2 tables.
   //5/24/06; 7:37:51 AM by DW
      //Created. 
      //Ever wonder what the OPML Editor (or Radio or Frontier) is doing in the background? This script gives you a list of things you should look at. You might find some surprises, I did. 
      //It looks in two tables, user.scheduler.threads and user.scheduler.everyMinute. 
      //In the first case, it lists all threads that are enabled. Ones that aren't don't run and can't use any resources. In the second case, it looks at the script, if it's in its initial state, with just a single line that's a comment, it doesn't list it. 
      //On my system, most threads were not enabled, and the everyMinute scripts were mostly defaults, so finding the culprit that was making my machine slow was a bit of a needle in a haystack thing. Not any more. ;->
      //http://geeks.opml.org/2006/05/24#a877
local (adroutline = @scratchpad.threadanalysis)
new (outlinetype, adroutline)
target.set (adroutline)
edit (adroutline)

bundle //threads
   local (dir, adr)
   op.setlinetext ("Threads that are enabled"); dir = right
   for adr in @user.scheduler.threads
      local (origadr = adr)
      try
         while typeof (adr^) == addresstype
            adr = adr^
         if adr^.enabled
            op.insert (string.popFileFromAddress (adr), dir)
            dir = down
      else
         edit (origadr)
         scripterror (tryerror)
bundle //background scripts
   on dotable (adrtable)
      op.go (left, 1)
      op.insert ("Scripts in \"" + adrtable + "\" that might do something", down); dir = right
      for adr in adrtable
         local (origadr = adr, flNotTrivial = false)
         try
            while typeof (adr^) == addresstype
               adr = adr^
            if sizeof (adr^) > 1
               flNotTrivial = true
            else
               if typeof (adr^) == scripttype //it's a one-line script
                  local (oldtarget = target.set (adr))
                  if not script.iscomment ()
                     flNotTrivial = true
                  target.set (oldtarget)
            if flNotTrivial
               op.insert (string.popFileFromAddress (adr), dir)
               dir = down
         else
            edit (origadr)
            scripterror (tryerror)
   dotable (@user.scheduler.everyMinute)
   dotable (@user.scheduler.hourly)
   dotable (@user.scheduler.overnight)
   dotable (@user.scheduler2.everyMinute)
   dotable (@user.scheduler2.hourly)
   dotable (@user.scheduler2.overnight)

op.firstsummit (); op.fullcollapse ()

</pre>