### workspace.userlandSamples.checkS3Folder
<pre>
on checkS3Folder ()
   //Changes
      //1/2/13; 8:58:39 AM by DW
         //I just uploaded all of the static files on scripting.com to a bucket on S3. This script verifies that they're all there, and reports any that are missing. Important -- work with a copy of the folder you're checking. Once we've verified thatva file exists on S3, we delete it in the local folder. This means the search can be restarted without having to check files that we've already verified are there. 
   local (folder = "Macintosh HD:Users:davewiner:Downloads:work area:scripting.com:", s3path = "/scripting.com/", relpath)
   local (adroutline = @scratchpad.missingS3files)
   bundle //set up outline
      new (outlinetype, adroutline)
      target.set (adroutline)
      edit (adroutline)
   fileloop (f in folder, infinity)
      relpath = s3path + string.replaceall (string.delete (f, 1, sizeof (folder)), ":", "/")
      if relpath contains ".DS_Store"
         continue
      msg (relpath)
      if s3.objectExists (relpath)
         file.delete (f)
      else
         op.insert (relpath, up)
      scratchpad.lastfilechecked = relpath
bundle //test code
   checkS3Folder ()

</pre>