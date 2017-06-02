### workspace.userlandSamples.savePagesFilter.savePages
<pre>
on savePages (pta)
   //Changes
      //2/3/10; 11:36:10 AM by DW
         //Install this script in user.webserver.postFilters. It will create a folder in the ops sub-folder of your Guest Databases folder that contains images of each of the pages or objects that are requested of the built-in web server. It also creates a table of data in user.savePagesFilter that makes it possible to create redirects to those pages. 
         //The purpose is to help "static-ize" a dynamic Manila site or some other app running in Frontier or the OPML Editor.
   local (adrdata = @user.savePagesFilter, pc = file.getpathchar (), now = clock.now ())
   bundle //init
      if not defined (adrdata^)
         new (tabletype, adrdata)
      if not defined (adrdata^.prefs)
         new (tabletype, @adrdata^.prefs)
      if not defined (adrdata^.prefs.folder)
         adrdata^.prefs.folder = frontier.getsubfolder ("ops") + "saved pages" + pc
      if not defined (adrdata^.prefs.enabled)
         adrdata^.prefs.enabled = true
      if not defined (adrdata^.redirects)
         new (tabletype, @adrdata^.redirects)
      if not defined (adrdata^.savedParams)
         new (tabletype, @adrdata^.savedParams)
      if not defined (adrdata^.stats)
         new (tabletype, @adrdata^.stats)
      if not defined (adrdata^.stats.cthits)
         adrdata^.stats.cthits = 0
      if not defined (user.webserver.prefs.MIME2ext) //running in Frontier or Radio
         user.webserver.prefs.MIME2ext = workspace.userlandSamples.savePagesFilter.data.MIME2ext
   if adrdata^.prefs.enabled
      if (pta^.code == 200) and (string.upper (pta^.method) == "GET")
         local (url = string.nthfield (pta^.firstline, " ", 2))
         url = string.nthfield (url, "?", 1)
         url = string.replaceall (url, "/$", "/") //we keep getting requests with this weird string in it
         local (sourceurl = url, desturl = url, host = "")
         //adrdata^.params = pta^ //debugging
         bundle //set the file extension
            try
               if not (desturl contains ".")
                  local (type = pta^.responseHeaders.["Content-Type"])
                  if (desturl endswith "/") or (desturl == "")
                     desturl = desturl + "index." + user.webserver.prefs.MIME2ext.[type]
                  else
                     desturl = desturl + "." + user.webserver.prefs.MIME2ext.[type]
         //if defined (pta^.host)
            //if sizeof (pta^.host) > 0
               //host = pta^.host + pc
         local (f = adrdata^.prefs.folder + pta^.host + string.replaceall (desturl, "/", pc))
         if not file.exists (f)
            file.surefilepath (f)
            file.writewholefile (f, pta^.responsebody)
         bundle //save info about redirect
            local (adrtable = @adrdata^.redirects.[pta^.host])
            if not defined (adrtable^)
               new (tabletype, adrtable)
            adrtable = @adrtable^.[sourceurl]
            if not defined (adrtable^)
               new (tabletype, adrtable)
               adrtable^.ct = 0
            adrtable^.f = f
            adrtable^.ct++
            adrtable^.when = now
            //
            //adrdata^.redirects.["http://" + string.replaceall (host, pc, "/") + sourceuri] = f
         adrdata^.stats.cthits++
         adrdata^.stats.whenLastHit = now
bundle //test code
   savepages (@user.savePagesFilter.savedParams.["00028"])

</pre>