### workspace.userlandSamples.flickrFolderUploader
<pre>
//Changes
   //11/1/10; 9:48:01 AM by DW
      //Uploads a folder of images to your Flickr account, newest first, so when you view them in Flickr they appear in chronologic order. The picture taken first appears first, the most recent picture appears last.
      //I know that Flickr has an organizer to compensate for this, but that adds another layer of complexity for my mom, who needs as few layers as possible to get the job done. :-)
      //Her photos are here:
         //http://www.flickr.com/photos/55412882@N08/
local (folder = "Ohio:Israel trip pics:", f, array, fname)
bundle //if you've never used Flickr from scripts before this gets us permission to upload
   if not defined (user.flickr.prefs.token)
      flickr.authpage ()
bundle //fill array, sort it by date, so oldest pic is first
   new (tabletype, @array)
   fileloop (f in folder)
      fname = file.filefrompath (f)
      if string.lower (fname) endswith ".jpg"
         array.[fname] = file.created (f)
   local (oldtarget = target.set (@array))
   table.sortby ("Value")
   target.set (oldtarget)
   //scratchpad.array = array
bundle //upload the pictures, oldest first
   local (i, adr, f)
   for i = sizeof (array) downto 1
      adr = @array [i]
      f = folder + nameof (adr^)
      //scratchpad.flickrMessage = "Uploading " + f
      flickr.uploadPhoto (f)

</pre>