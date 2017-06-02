### workspace.userlandSamples.exportChildren
<pre>
on exportChildren ()
   //Changes
      //1/6/13; 8:42:52 PM by DW
         //A tool that's useful for feeling your way through a database to find out which branches are using up most of the space. You can put the cursor on a table and each sub is exported to its own file. Look in the folder to see how big each one is. It helped me find the fat part of river2data.root in about five minutes. Wish I had this a long time ago! :-)
   local (adrtable = table.getcursoraddress ())
   if dialog.confirm ("Export the children of \"" + nameof (adrtable^) + "?\"")
      local (folder = frontier.pathstring + "exports:", adrsub, f)
      for adrsub in adrtable
         local (fname = nameof (adrsub^))
         local (suffix = Frontier.getFileSuffix (typeOf (adrsub^), true))
         fname = string.replaceall (fname, ":", "")
         fname = string.replaceall (fname, "/", "")
         fname = fname  + "." + suffix
         f = folder + fname
         msg (f)
         file.surefilepath (f)
         export.sendobject (adrsub, f)
bundle //test code
   exportChildren ()

</pre>