### workspace.userlandSamples.fickrPoolDownloader
<pre>
//Changes
   //8/12/10; 4:45:02 AM by DW
      //Sample script that shows how to download a pool to a folder on your local disk.
         //It may not immediately be obvious what the id of the group is. If you get the group displayed in your web browser, then locate the RSS feed, you'll see the id in the URL for the feed.
         //For example here's the URL for the feed of the landing around the world pool.
         //http://api.flickr.com/services/feeds/groups_pool.gne?id=726229@N24&amp;lang=en-us&amp;format=rss_200
         //The id should be pretty obvious! :-)
local (pc = file.getpathchar ())
local (folder = frontier.pathstring + "Flickr" + pc + "Let's Put Gruber To Work" + pc)
flickr.savePool ("1121198@N20", folder)

</pre>