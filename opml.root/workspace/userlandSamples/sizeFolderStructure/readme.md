### workspace.userlandSamples.sizeFolderStructure
<pre>
on sizeFolderStructure (folder, adroutline)
   //Changes
      //11/27/10; 5:59:50 PM by DW
         //I always wondered where all the files were in a huge folder, like the one that stores all the static files for scripting.com. This script walks the folder structure recursively, and on each folder tells you how many files it contains, at all levels, and how much space they occupy. That way you can quickly zoom in on where the big stuff is. 
   bundle //set up outline
      new (outlinetype, adroutline)
      target.set (adroutline)
      op.setlinetext (file.filefrompath (folder))
      edit (adroutline)
   on dofolder (folder, adrdata=nil)
      local (f, dir = right)
      if adrdata != nil
         new (tabletype, adrdata)
         adrdata^.ctfiles = 0
         adrdata^.size = 0
      fileloop (f in folder)
         if file.isfolder (f)
            local (data, fname = file.filefrompath (f))
            op.insert (fname, dir); dir = down
            dofolder (f, @data)
            op.setlinetext (fname + " (" + string.gigabytestring (data.size) + " -- " + string.addcommas (data.ctfiles) + ")")
            if adrdata != nil
               adrdata^.ctfiles = adrdata^.ctfiles + data.ctfiles
               adrdata^.size = adrdata^.size + data.size
         else
            if adrdata != nil
               adrdata^.ctfiles++
               adrdata^.size = adrdata^.size + file.size (f)
      if dir == down
         op.go (left, 1)
         op.collapse ()
   dofolder (folder)
bundle //test code
   sizeFolderStructure ("Ohio:Server Backups:static sites:scripting.com:", @scratchpad.folderstructure)

</pre>