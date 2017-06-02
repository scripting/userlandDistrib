### workspace.userlandSamples.findObjectInFolder
<pre>
on findObjectInFolder (adrobject, folder)
   //Changes
      //1/17/12; 10:06:24 AM by DW
         //Loop over the files in a folder, looking for a file that's a backup of a given odb object. Useful for scanning the rootbackups folder for an old version of some object, if you're not sure when it changed. 
   local (f, s, atts, adroutline = @scratchpad.foundObjects)
   new (outlinetype, adroutline)
   target.set (adroutline)
   edit (adroutline)
   fileloop (f in folder, infinity)
      msg (f)
      s = string (file.readwholefile (f))
      if fatPages.dataIsFat (@s)
         fatPages.getPageAtts (@s, @atts)
         try
            if address (atts.adrpagedata) == adrobject
               op.insert (f - folder, up)
            //scratchpad.atts = atts
   op.go (down, infinity); op.deleteline (); op.firstsummit ()
bundle //test code
   local (folder = frontier.getsubfolder ("/ops/rootUpdateBackups/"))
   findObjectInFolder (@opmlEditor.data.outlines.prefs, folder)

</pre>