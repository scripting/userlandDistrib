### workspace.userlandSamples.findBigThings
<pre>
on findBigThingsInTable (adrroottable = @root)
   //Changes
      //6/9/09; 9:11:53 AM by DW
         //Getting errors on table.inguestdatabase call. Since it's only for displaying progress messages, I put it inside a try so it wouldn't halt the scan.
      //4/26/09; 10:20:45 AM by DW
         //I wasted the better part of a week trying to figure out why one of my servers was flatlining. It turns out a random table in opmlCommunityServerData.root was expanded. This script was only looking in the user sub-table of opml.root. So this time (it's happened before) -- I'm going to invest a couple of hours into making this script look in all open database files. 
      //1/26/08; 8:54:28 AM by DW
         //Add a paramenter, the root of the table you're going to look in. Makes it possible to be selective where you search.
      //1/10/01; 7:57:47 AM by DW
         //Visit all objects in all open databases looking for tables and outlines that have more than 1000 elements. Big outlines really slow things down. You might want to know where your big tables are.
   on dotable (adrtable)
      on addadr (adr)
         local (s = string (adr))
         local (pattern = "\"].")
         local (ix = string.patternmatch (pattern, s))
         if ix > 0
            s = string.delete (s, 1, ix + sizeof (pattern) - 1)
         op.insert (s + " (" + sizeof (adr^) + ")", insertdir); insertdir = down
      local (adr)
      for adr in adrtable
         case typeof (adr^)
            tabletype
               if sizeof (adr^) > marksize
                  addadr (adr)
               if (++ct % 1000) == 0
                  try //6/9/09 by DW
                     local (s = string (adr))
                     if table.inguestdatabase (adr)
                        if s contains "]"
                           local (ix = string.patternmatch ("]", s))
                           s = string.delete (s, 1, ix+1)
                     msg (ct + ": " + s)
               dotable (adr)
            outlinetype
               if sizeof (adr^) > marksize
                  addadr (adr)
      return (true)
   dotable (adrroottable)
   op.firstsummit ()
   edit (adroutline)
   msg ("")
bundle //body
   local (marksize = 1000, ct = 0)
   local (adroutline = @scratchpad.bigOutlines, adrfile, insertdir)
   bundle //set up the outline
      new (outlinetype, adroutline); 
      edit (adroutline)
      window.setsize (adroutline, 700, 500)
      window.setposition (adroutline, 250, 250)
      target.set (adroutline)
      op.firstsummit ()
      op.setlinetext ("Big tables and outlines on " + clock.now () + ":")
   for adrfile in @system.compiler.files
      local (f = nameof (adrfile^), adrtable = @[f])
      op.firstsummit ()
      op.insert (f - frontier.pathstring, right); insertdir = right
      findBigThingsInTable (adrtable)
      op.go (left, 1)
   op.insert ("user", right); insertdir = right
   findBigThingsInTable (@user)

</pre>