### workspace.userlandSamples.s3RedirectOneFile
<pre>
on s3RedirectOneFile (url, urlredirectto) 
   //Changes
      //8/17/15; 3:40:45 PM by DW
         //The first URL is one that points to a page that doesn't exist. The second URL is the one it should redirect to. We set it up so that it does.
   local (filepath = string.delete (url, 1, 6), metadata)
   new (tabletype, @metadata)
   metadata.["website-redirect-location"] = urlredirectto
   s3.newobject (filepath, " ")
   s3.setObjectMetadata (filepath, @metadata)
bundle //test code
   //s3RedirectOneFile ("http://xmlrpc.scripting.com/directory/1568", "http://directory.xmlrpc.com")
   //s3RedirectOneFile ("http://xmlrpc.scripting.com/directory/1568/implementations", "http://directory.xmlrpc.com/implementations/")
   //s3RedirectOneFile ("http://xmlrpc.scripting.com/directory/1568/services", "http://directory.xmlrpc.com/services/")
   //s3RedirectOneFile ("http://xmlrpc.scripting.com/directory/1568/communities", "http://directory.xmlrpc.com/communities/")
   //s3RedirectOneFile ("http://xmlrpc.scripting.com/directory/1568/tutorialspress", "http://directory.xmlrpc.com/tutorialspress/")
   //s3RedirectOneFile ("http://dev.opml.org/spec2", "http://dev.opml.org/spec2.html")
   s3RedirectOneFile ("http://xmlrpc.scripting.com/spec", "http://xmlrpc.scripting.com/spec.html")

</pre>