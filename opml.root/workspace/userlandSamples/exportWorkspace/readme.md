### workspace.userlandSamples.exportWorkspace
<pre>
//Changes
   //12/22/10; 10:01:47 AM by DW
      //This script is a step on the path to making it easy to start with a fresh OPML installation. It exports all the parts of your workspace table. Bonus -- it also exports the sub-tables of your user table.
local (pc = file.getpathchar (), folder = frontier.pathstring + "Workspace backup" + pc)
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
   file.setmodified (f, timemodified (adr))
   file.setcreated (f, timecreated (adr))
on savetable (adrtable, folder)
   local (adr)
   for adr in adrtable
      saveobject (adr, folder + nameof (adrtable^) + pc)
savetable (@workspace, folder)
savetable (@user, folder)

</pre>