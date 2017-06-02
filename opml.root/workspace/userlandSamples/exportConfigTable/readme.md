### workspace.userlandSamples.exportConfigTable
<pre>
on exportConfigTables ()
   //Changes
      //12/14/13; 7:45:33 AM by DW
         //Exports all of the sub-tables of config.root to your export folder, user.opmlEditor.prefs.exportFolder, which you should be sure to set before running this script. Very useful to have this kind of backup when re-installing the OPML Editor freshly.
   local (adr, folder, pc = file.getpathchar ())
   bundle //set folder
      if defined (user.opmlEditor.prefs.exportFolder)
         folder = user.opmlEditor.prefs.exportFolder
      else
         if not file.getfolderdialog ("Choose a folder to export to:", @folder)
            return
         user.opmlEditor.prefs.exportFolder = folder
   for adr in @config
      local (suffix = Frontier.getFileSuffix (typeOf (adr^), true), fname, adrparent)
      fname = nameof (adr^)
      adrparent = parentOf (adr^)
      if adrparent != nil
         if (not table.inguestdatabase (adr)) or (adrparent != table.getrootaddress (adr))
            local (dottedname = nameOf (adrParent^) + '.' + fname)
            if (sizeof (dottedname) + sizeof (suffix) + 1) &lt; 32
               fname = dottedname
      local (f = folder + "config" + pc + fname + "." + suffix)
      file.surefilepath (f)
      msg (f)
      export.sendobject (adr, f)
bundle //test code
   exportConfigTables ()

</pre>