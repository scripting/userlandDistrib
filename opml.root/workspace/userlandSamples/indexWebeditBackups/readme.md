### workspace.userlandSamples.indexWebeditBackups
<pre>
on indexWebeditBackups (folder, cutoffdate)
   //Changes
      //6/8/12; 3:14:57 PM by DW
         //Run this when you want to create a list of updated parts from a Webedit Backups folder.
   local (cutoffday, cutoffmonth, cutoffyear, hour, minute, second, day, month, year)
   local (pc = file.getpathchar (), adroutline = @scratchpad.indexoutline)
   on popfile (s)
      local (pattern = "\"].", ix = string.patternmatch (pattern, s))
      if ix > 0
         s = string.delete (s, 1, ix + sizeof (pattern) - 1)
      return (s)
   bundle //set up outline
      if defined (adroutline^)
         target.set (adroutline)
         op.wipe ()
      else
         new (outlinetype, adroutline)
         target.set (adroutline)
   date.get (cutoffdate, @cutoffday, @cutoffmonth, @cutoffyear, @hour, @minute, @second)
   for year = cutoffyear downto date.year ()
      for month = 12 downto 1
         for day = 31 downto 1
            local (subfolder = folder + year + pc + string.padwithzeros (month, 2) + pc + string.padwithzeros (day, 2) + pc)
            if file.exists (subfolder)
               local (thedate = date.set (day, month, year, 0, 0, 0))
               if thedate > cutoffdate
                  local (f, dir, changedtoday)
                  new (tabletype, @changedtoday)
                  op.insert (date.shortstring (thedate), down); dir = right
                  fileloop (f in subfolder)
                     local (bits = string (file.readwholefile (f)), atts)
                     if fatPages.getPageAtts (@bits, @atts)
                        local (name = popfile (atts.adrPageData))
                        if not defined (changedtoday.[name])
                           op.insert (name, dir); dir = down
                           changedtoday.[name] = true
                  if dir == down
                     op.sort ()
                     op.go (left, 1)
   op.firstsummit (); op.deleteline ()
bundle //test code
   local (folder = user.prefs.dropboxfolder + "OPML Editor Stuff:Webedit Backups:pensacola:")
   local (cutoffdate = date ("May 29, 2012"))
   indexWebeditBackups (folder, cutoffdate)

</pre>