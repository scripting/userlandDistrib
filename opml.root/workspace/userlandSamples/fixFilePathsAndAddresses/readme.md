### workspace.userlandSamples.fixFilePathsAndAddresses
<pre>
//Changes:
   //1/3/02; 4:57:07 PM by DW
      //Change "playlist" to "radio".
   //3/4/01; 5:37:46 PM by JES
      //Fixed an error if user.backups or user.batchExporter aren't defined.
   //1/21/01; 4:02:08 AM by JES
      //Fix preferences, addresses and filespecs in Radio.root, MyUserLand.root and Weblog.root, after having renamed or moved the Radio UserLand application folder.
      //How to use this script:
         //Make sure that Radio.root is up-to-date using the Update Radio.root command in the file menu.
         //Quit Radio UserLand, and move or rename the application folder as needed, taking note of the old path to the application folder.
         //Launch Radio UserLand and run this script. A dialog will appear, asking for the old Radio UserLand application folder path. The default should be correct, but if it isn't, then enter the correct path.
         //If all goes well, a few seconds after clicking the OK button, a dialog will appear telling you that your data has been successfully updated.

local (oldAppFolder = string.mid (user.radio.prefs.wwwFolder, 1, sizeOf (user.radio.prefs.wwwFolder) - 4))
local (lowerOldAppFolder = string.lower (oldAppFolder))
local (currentAppFolder = system.verbs.builtins.Frontier.pathstring)

if dialog.ask ("Enter the old Radio UserLand application folder path:", @oldAppFolder)
   
   on fixAddress (adrAddress)
      //try
      if string.lower (adrAddress^) beginsWith "[\"" + lowerOldAppFolder
         local (s = string (adrAddress^))
         local (ix = string.patternMatch ("\"].", s))
         if ix > 0
            s = string.delete (s, 1, ix + 2)
         adrAddress^ = address (s)
   on fixString (adrString)
      //try
      if string.lower (adrString^) beginsWith lowerOldAppFolder
         adrString^ = currentAppFolder + string.delete (adrString^, 1, sizeOf (oldAppFolder))
   on fixFilespec (adrFilespec)
      //try
      if string.lower (adrFilespec^) beginsWith lowerOldAppFolder
         adrFilespec^ = filespec (currentAppFolder + string.delete (adrFilespec^, 1, sizeOf (oldAppFolder)))
   on fixObject (adrObject)
      case typeOf (adrObject^)
         addressType
            return (fixAddress (adrObject))
         stringType
            return (fixString (adrObject))
         filespecType
            return (fixFilespec (adrObject))
   
   local (adrItem, pc = file.getPathChar ())
   
   bundle //fix items in MyUserLandData.root
      if defined (myUserLandData)
         myUserLandData.prefs.enclosureFolder = currentAppFolder + "Downloaded enclosures" + pc
         myUserLandData.stats.imagesFolder = currentAppFolder + "www" + pc + "images" + pc
         local (ct = 0)
         for adrItem in @myUserLandData.stories //fix enclosures
            if (++ct % 1000) == 0
               msg ("Fixing channel enclosure paths: " + ct)
               fileMenu.saveMyRoot (@myUserLandData)
            if defined (adrItem^.enclosure)
               if defined (adrItem^.enclosure.f)
                  fixObject (@adrItem^.enclosure.f)
         msg ("Saving...")
         fileMenu.saveMyRoot (@myUserLandData)
   bundle //fix folder paths in Weblog sites' #ftpSite tables
      if defined (weblogData.sites)
         msg ("Fixing Weblog folders...")
         for adrItem in @weblogData.sites
            if defined (adrItem^.website.["#ftpSite"])
               if defined (adrItem^.website.["#ftpSite"].folder)
                  fixObject (@adrItem^.website.["#ftpSite"].folder)
         fileMenu.saveMyRoot (@weblogData)
   bundle //fix items in the user table
      msg ("Fixing the user table...")
      if defined (user.backups)
         fixObject (@user.backups.folder)
      if defined (user.batchExporter)
         fixObject (@user.batchExporter.folder)
      for adrItem in @user.betty.rpcHandlers
         fixObject (adrItem)
      for adrItem in @user.callbacks
         local (adrCallback)
         for adrCallback in adrItem
            fixObject (adrCallback)
      if defined (user.html.callbacks.fileWriters.ftp.write)
         for adrItem in @user.html.callbacks.fileWriters.ftp.write
            fixObject (adrItem)
      if defined (user.html.prefs.lastImportedFolder)
         fixObject (@user.html.prefs.lastImportedFolder)
      if defined (user.log)
         if defined (user.log.prefs)
            user.log.prefs.folder = currentAppFolder + "Logs" + pc
      for adrItem in @user.pike.commandCallbacks
         local (adrCallback)
         for adrCallback in adrItem
            fixObject (adrCallback)
      //if defined (user.playlist.data.upstream.magicFolders)
         //for adrItem in @user.playlist.data.upstream.magicFolders
            //fixObject (adrItem)
      if defined (user.webserver.responders.websiteFramework)
         for adrItem in @user.webserver.responders.websiteFramework.data.docTree
            fixObject (adrItem)
      
      //do this last, since this is how we tell if the app folder has changed
      user.radio.prefs.wwwFolder = currentAppFolder + "www" + pc
      
      fileMenu.saveMyRoot (@user)
   msg ("")
   
   dialog.alert ("Your data has been successfully updated for the new application folder.")

</pre>