### workspace.userlandSamples.exportListToFolder
<pre>
on exportListToFolder ()
   //Changes
      //9/6/11; 7:58:18 AM by DW
         //Create an outline with a list of parts, bring it to the front and run this script. We'll create a folder containing those parts.
   local (pc = file.getpathchar (), folder = frontier.pathstring + "Saved Parts" + pc, now = clock.now ())
   on saveobject (adr, folder)
      local (suffix = Frontier.getFileSuffix (typeOf (adr^), true))
      if suffix != ""
         suffix = "." + suffix
      s = nameof (adr^)
      adrParent = parentOf (adr^)
      if adrParent != nil
         if (not table.inguestdatabase (adr)) or (adrparent != table.getrootaddress (adr))
            local (dottedname = nameOf (adrParent^) + '.' + s)
            if (sizeof (dottedname) + sizeof (suffix) + 1) < 32
               s = dottedname
      local (f = folder + s + suffix)
      file.surefilepath (f)
      export.sendobject (adr, f)
      if timemodified (adr) == date (0)
         file.setmodified (f, now)
         file.setcreated (f, now)
      else
         file.setmodified (f, timemodified (adr))
         file.setcreated (f, timecreated (adr))
   loop
      local (adr = address (op.getlinetext ()))
      saveobject (adr, folder)
      if not op.go (down, 1)
         file.openfolder (folder)
         break
bundle //test code
   exportListToFolder ()

</pre>