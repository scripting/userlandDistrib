### workspace.userlandSamples.smallPictRedirect
<pre>
on smallPictRedirect (pta)
   //Changes
      //1/28/14; 12:34:12 PM by DW
         //Added stats.
      //1/28/14; 12:07:01 PM by DW
         //A redirector that works for smallpict.com with the new way our "database" works.
            //Every named outline is represented by a JSON file in a folder in an S3 bucket.
            //If it contains a urlRedirect entry, we redirect through it.
            //Here's an example of a file:
               //http://beta.fargo.io/data/names/hellodere.json
         //As with all sample code, it may have some techniques you find useful.
            //It also serves to document the new technique in case anyone is interested.
         //To install it, cmd-/ on the line below:
            //config.mainresponder.callbacks.hostNotFound.smallPict = @workspace.userlandSamples.smallPictRedirect
               //@workspace.userlandSamples.smallPictRedirect
   local (lowerhost = string.lower (pta^.host), startticks = clock.ticks ())
   if lowerhost endswith "smallpict.com"
      local (name = string.nthfield (lowerhost, ".", 1))
      local (s3url = "http://beta.fargo.io/data/names/" + name + ".json")
      local (jsontext = tcp.httpreadurl (s3url, 3, false))
      json.compile (jsontext, @xstruct)
      //scratchpad.xstruct = xstruct
      local (urlRedirect = xml.getvalue (@xstruct, "urlRedirect"))
      urlRedirect = string.replace (urlRedirect, "tmp.fargo.io", "beta.fargo.io") //1/28/14 by DW
      
      local (path = pta^.path)
      if path beginswith "/"
         path = string.delete (path, 1, 1)
      webserver.redirect (pta, urlRedirect + path)
      
      bundle //stats
         local (adrstats = @scratchpad.smallPictRedirectStats)
         if not defined (adrstats^)
            new (tabletype, adrstats)
         if not defined (adrstats^.ctRedirects)
            adrstats^.ctRedirects = 0
         adrstats^.ctRedirects++
         adrstats^.lastSource = "http://" + pta^.host + "/" + path
         adrstats^.lastDest = urlRedirect + path
         adrstats^.whenLastRedirect = clock.now ()
         adrstats^.ctSecs = double (clock.ticks () - startticks) / 60
      
//bundle //test code
   //local (pagetable)
   //new (tabletype, @pagetable)
   //pagetable.host = "hellodere.smallpict.com"
   //pagetable.path = "/rss.xml"
   //smallPictRedirect (@pagetable)

</pre>