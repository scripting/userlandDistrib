### workspace.userlandSamples.manilaToBlog
<pre>
//Changes
   //1/3/02; 4:58:45 PM by DW
      //Change "playlist" to "radio".
   //02/01/01; 10:15:31 AM by JES
      //Convert homepages of a downloaded Manila website into items in a Weblog.
      //How to use this script:
         //1) First, open a downloaded Manila site's guest database. The site will be in a top-level table in the guest database.
         //2) Change the value of adrManilaSite in the local declaration below to the address of your downloaded Manila site -- the address of the top-level table in the guest database.
         //3) Run the script. (Warning: This step will erase everything in your current Weblog. Proceed with caution.)
         //After a few seconds, your Weblog will open in the browser.

local (adrManilaSite = @myManilaSite) //put the address of your Manila site here.
local (flSplitMessages = true) //flag for whether messages are split into individual items
local (flConvertToMacText = system.environment.isMac)
local (adrBlog = @myUserLandData.blogs.default)

on getMessageText (msgNum)
   local (adrMessages = @adrManilaSite^.["#discussionGroup"].messages)
   local (adrMessage = @adrMessages^.[string.padWithZeros (msgNum, 7)])
   if defined (adrMessage^.bodyType) //the message might be an outline or opml
      case string.lower (adrMessage^.bodyType)
         "text/x-opml"
            local (theOutline)
            if flConvertToMacText
               op.xmlToOutline (string.latinToMac (string (adrMessage^.opml)), @theOutline)
            else
               op.xmlToOutline (string (adrMessage^.opml), @theOutline)
            return (theOutline)
         "text/x-outline-tabbed"
            if typeOf (adrMessage^.outline) == outlineType
               return (adrMessage^.outline)
            local (theOutline)
            if flConvertToMacText
               op.newOutlineObject (string.latinToMac (string (adrMessage^.outline)), @theOutline)
            else
               op.newOutlineObject (string (adrMessage^.outline), @theOutline)
            return (theOutline)
   if flConvertToMacText
      return (string.latinToMac (string (adrMessage^.body)))
   else
      return (string (adrMessage^.body))

bundle //initialize the weblog
   new (tableType, adrBlog)
   myUserLandSuite.blog.init (adrBlog)
bundle //convert homepages to weblog items
   on post (s, d)
      if s contains "Leander"
         msg (s)
      s = string.replaceAll (s, "\\\"", "\"") //we don't have to worry about escaping quotes -- we're not in the wsf
      s = string.replaceAll (s, "\r\n", "\r")
      s = string.replaceAll (s, "\r\r", "&lt;br>&lt;br>")
      myUserLandSuite.blog.post (s, adrBlog, d)
   on getMessageDate (msgNum)
      local (adrMessages = @adrManilaSite^.["#discussionGroup"].messages)
      local (adrMessage = @adrMessages^.[string.padWithZeros (msgNum, 7)])
      return (adrMessage^.postTime)
   on getDayAddress (year, month, day, adrCalendar)
      return (@adrCalendar^.[year].[string.padWithZeros (month, 2)].[string.padWithZeros (day, 2)])
   on convertNewsItemsDay (year, month, day)
      local (adrDgDay = getDayAddress (year, month, day, @adrManilaSite^.["#discussionGroup"].calendar))
      if defined (adrDgDay^)
         local (adrItem)
         for adrItem in adrDgDay
            local (s, d)
            local (adrMsg = @adrManilaSite^.["#discussionGroup"].messages.[nameOf (adrItem^)])
            local (flDeleted = false)
            if defined (adrMsg^.flDeleted)
               flDeleted = adrMsg^.flDeleted
            if flDeleted
               continue
            if defined (adrMsg^.newsItem)
               if adrMsg^.newsItem.flPosted
                  s = adrMsg^.newsItem.description
                  d = adrMsg^.newsItem.postTime
                  post (s, d)
         return (true)
      return (false)
   on stringToStories (s, d)
      //Cribbed from manilaSuite.xml.getRssXml
      s = string.replaceAll (s, "\r\n", "\r")
      local (ix, lineString)
      while sizeOf (s) > 0
         local (sizePattern)
         on tryPattern (pattern) //PBS 03/27/00: routine for looking for a pattern
            sizePattern = sizeOf (pattern)
            ix = string.patternMatch (pattern, s)
            return (ix > 0)
         //if not (tryPattern ("&lt;li>"))
         if not (tryPattern ("\r\r"))
            //if not tryPattern ("\r")
            tryPattern ("&lt;br>&lt;br>\r")
         if ix == 0
            lineString = s
            s = ""
         if ix > 0
            lineString = string.mid (s, 1, ix - 1)
            s = string.delete (s, 1, ix + (sizePattern - 1))
            lineString = string.trimWhiteSpace (lineString)
            //case string.lower (lineString) //skip lines with only common markup
               //""
               //"&lt;br>"
               //"&lt;p>"
               //"&lt;/p>"
               //"&lt;ul>"
               //"&lt;/ul>"
               //"&lt;li>"
               //"&lt;/li>"
               //"&lt;blockquote>"
               //"&lt;/blockquote>"
                  //continue
         post (lineString, d)
   on convertOutline (theOutline, d)
      if flSplitMessages
         stringToStories (string (theOutline), d)
      else //post the outline as a single story rendered with the pikeRenderer
         local (s)
         local (pageTable, oldPta); new (tableType, @pageTable)
         try &#123;oldPta = html.getPageTableAddress ()}
         html.setPageTableAddress (@pageTable)
         s = pikeRenderer (@theOutline)
         html.deletePageTableAddress ()
         post (s, d)
   on convertString (s, d)
      if flSplitMessages
         stringToStories (s, d)
      else //post the message as a single story
         post (s, d)
   on convertDay (year, month, day)
      local (s, d)
      local (adrDay = getDayAddress (year, month, day, adrManilaSite))
      if defined (adrDay^.flNewsItems) and adrDay^.flNewsItems
         convertNewsItemsDay (year, month, day)
      else //convert a message to blog items
         s = getMessageText (adrDay^.msgNum)
         d = getMessageDate (adrDay^.msgNum)
         if typeOf (s) == outlineType
            convertOutline (s, d)
         else
            convertString (s, d)
   on walkCalendar ()
      local (year, startYear = 1999, endYear = date.year ())
      for year = startYear to endYear
         local (month)
         if defined (adrManilaSite^.[year])
            for month = 1 to 12
               local (day, monthString = string.padWithZeros (month, 2))
               if defined (adrManilaSite^.[year].[monthString])
                  for day = 1 to 31
                     local (dayString = string.padWithZeros (day, 2))
                     if defined (adrManilaSite^.[year].[monthString].[dayString])
                        msg ("Creating " + date.shortString (date.set (day, month, year, 0, 0, 0)) + "...")
                        convertDay (year, month, day)
   walkCalendar ()
   msg ("")
bundle //publish the weblog, and open in the browser
   myUserLandSuite.blog.publish (@myUserLandData.blogs.[blogName])
   local (pc = file.getPathChar ())
   local (blogPath = myUserLandData.blogs.default.prefs.homePageFilePath)
   blogPath = string.replaceAll (blogPath, "/", pc)
   blogPath = user.radio.prefs.wwwFolder + blogPath
   webBrowser.openDocument (blogPath)
   webBrowser.bringToFront ()

</pre>