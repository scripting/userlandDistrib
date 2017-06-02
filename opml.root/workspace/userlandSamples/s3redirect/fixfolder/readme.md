### workspace.userlandSamples.s3redirect.fixfolder
<pre>
on fixfolder ()
   //Changes
      //7/24/12; 8:32:27 PM by DW
         //A utility script that adds HTML-level redirects to a folder on S3, redirecting from files without extensions to the .html equivalent. Manila sites that are converted to S3 need this kind of redirecting, because Manila didn't require extensions. Turns out S3 doesn't either, but my conversion script adds them. :-(
   local (bucket = "/bloggercon.scripting.com/", foldertable, path)
   s3.getbucket (bucket, @foldertable)
   for adrfile in @foldertable
      path = bucket + nameof (adrfile^)
      if path endswith ".html"
         local (t)
         new (tabletype, @t)
         t.url = string.lastfield (nameof (adrfile^), "/")
         path = string.delete (path, sizeof (path) - 4, 5)
         s = string.multiplereplaceall (string (workspace.userlandsamples.s3redirect.template), @t, false, "&lt;%", "%>")
         s3.newobject (path, s, type:"text/html")
bundle //test code
   fixfolder ()

</pre>