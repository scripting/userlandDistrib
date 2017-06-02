### workspace.userlandSamples.deleteBTSyncExtras
<pre>
on deleteBTSyncExtras ()
   //Changes
      //1/9/14; 9:16:46 AM by DW
         //I use BitTorrent Sync to manage scripting.com on S3. Sometimes it leaves around these old files, and they annoy me. This script deletes them. ;-)
   local (f, ctdeleted = 0)
   fileloop (f in "C:\\scriptings3\\", infinity)
      if file.filefrompath (f) endswith ".SyncOld"
         file.delete (f)
         ctdeleted++
   dialog.alert (ctdeleted)
bundle //test code
   deleteBTSyncExtras ()

</pre>