### workspace.userlandSamples.checkS3Archive
<pre>
on checkS3Archive ()
   //Changes
      //6/21/12; 9:08:30 AM by DW
         //Compare a folder on the hard disk with a folder on S3. Report any files that are missing in S3.
   local (folder = user.prefs.dropboxfolder + "Public:", s3path = "/dropbox.goodfood.com/bullman/")
   local (adroutline = @scratchpad.missingFiles, dir = right)
   bundle //set up outline
      if not defined (adroutline^)
         new (outlinetype, adroutline)
      target.set (adroutline)
      edit (adroutline)
      op.firstsummit ()
      op.insert ("Files missing in \"" + s3path + "\" on " + clock.now () + ".", up)
   fileloop (f in folder, infinity)
      local (path = s3path + string.replaceall (string.delete (f, 1, sizeof (folder)), ":", "/"))
      if file.filefrompath (f) == ".DS_Store"
         continue
      if not s3.objectexists (path)
         op.insert (path, dir); dir = down
bundle //test code
   checkS3Archive ()

</pre>