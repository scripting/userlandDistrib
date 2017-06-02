### workspace.userlandSamples.blogger.newPost
<pre>
on newPost (username, password, blogId, text, flPublish=true, adrdata=@workspace.userlandSamples.blogger.data)
   //8/9/01; 12:28:47 PM by JES
      //This sample script shows how to create a new post on a Blogger site, using XML-RPC.
      //http://samples.userland.com/stories/storyReader$204
      //To use it, you must first be a registered Blogger user, and have a site.
      //The parameters are as follows:
         //username -- Your Blogger username.
         //password -- Your Blogger password.
         //blogId -- The ID of your Blogger site (a.k.a. Blog). You can get the ID of your Blog from the URL you use to edit it in the browser. It's the number after blogid= in the URL.
         //text -- The text that you want to post to your site.
         //flPublish -- A boolean which specifies whether the Blog will be published when creating the post. The default is true.
         //adrdata -- The address of a data table, which contains information needed to communicate with the Blogger server. The default is @workspace.userlandSamples.blogger.data, which is pre-configured.
      //This script returns the post ID, as returned by the server.
      //More info:
         //The Blogger API documentation from Evan Williams:
            //http://plant.blogger.com/api/
         //The bloggerDev mailing list:
            //http://groups.yahoo.com/group/bloggerDev
   
   with adrdata^
      local (params = &#123;appkey, string (blogId), username, password, text, flPublish})
      return (xml.rpc (server, port, "blogger.newPost", @params, rpcPath:rpcPath, protocol:protocol))

bundle //testing
   local (username = "bmancuso")
   local (password = "ForgetIt!")
   local (blogId = 3106645)
   local (text = "It worked!")
   local (postId = newPost (username, password, blogId, text))
   webBrowser.openUrl ("http://www.blogger.com/blog.pyra?blogid=" + blogId)
   webBrowser.bringToFront ()

</pre>