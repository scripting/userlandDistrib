### workspace.userlandSamples.downloadLinkblogArchive
<pre>
on downloadLinkblogArchive (urlFeed, folder)
   //Changes
      //10/13/12; 12:38:32 PM by DW
         //Download a linkblog that has an archive element at the top leve. 
            //http://threads2.scripting.com/2012/october/myLinkblogHasAnArchive
   local (xmltext = tcp.httpreadurl (urlfeed, 3, false))
   xml.compile (xmltext, @xstruct)
   //scratchpad.xstruct = xstruct
   local (adrrss = xml.getaddress (@xstruct, "rss"))
   local (adrchannel  = xml.getaddress (adrrss, "channel"))
   local (adrarchive  = xml.getaddress (adrchannel, "archive"))
   local (urlarchive = xml.getvalue (adrarchive, "url"))
   local (fname = xml.getvalue (adrarchive, "filename"))
   on getdate (name)
      local (s = xml.getvalue (adrarchive, name))
      return (date.set (string.nthfield (s, "-", 3), string.nthfield (s, "-", 2), string.nthfield (s, "-", 1), 0, 0, 0))
   local (theday = getdate ("startDay"), endday = getdate ("endDay"))
   loop
      local (urlday = urlarchive + file.getdatepath ("/", theday) + fname)
      local (fday = folder + file.getdatepath (file.getpathchar (), theday, false) + ".xml")
      try
         local (xmltext = tcp.httpreadurl (urlday, 3, false))
         file.surefilepath (fday) //make sure all folders in path exist
         file.writewholefile (fday, xmltext)
         bundle //set mod and creation dates
            local (xstruct, adrrss, adrchannel)
            xml.compile (xmltext, @xstruct)
            adrrss = xml.getaddress (@xstruct, "rss")
            adrchannel  = xml.getaddress (adrrss, "channel")
            file.setcreated (fday, date (xml.getvalue (adrchannel, "pubDate")))
            file.setmodified (fday, date (xml.getvalue (adrchannel, "lastBuildDate")))
         msg (fday)
      theday = date.tomorrow (theday)
      if theday > endday
         break
bundle //test code
   downloadLinkblogArchive ("http://links.scripting.com/rss.xml", "Ohio:mylinkblog:")

</pre>