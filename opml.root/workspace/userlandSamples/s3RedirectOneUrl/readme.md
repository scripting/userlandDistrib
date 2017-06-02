### workspace.userlandSamples.s3RedirectOneUrl
<pre>
on s3RedirectOneUrl (url, urlredirectto) 
   //Changes
      //8/17/15; 3:40:45 PM by DW
         //The first URL is one that points to a page that doesn't exist. The second URL is the one it should redirect to. We set it up so that it does.
   local (filepath = string.delete (url, 1, 6), metadata)
   new (tabletype, @metadata)
   metadata.["website-redirect-location"] = urlredirectto
   s3.newobject (filepath, " ")
   s3.setObjectMetadata (filepath, @metadata)
bundle //test code
   s3RedirectOneUrl ("http://scripting.com/davenet/96/02/ipromisedmygrandfather.html", "http://scripting.com/davenet/1996/02/09/ipromisedmygrandfather.html")

</pre>