### workspace.userlandSamples.genMonthlyArchives.genOneMonthArchive
<pre>
on genOneMonthArchive (adrmonth)
   //Changes
      //8/8/13; 1:03:53 PM by DW
         //Created.
   local (rulestext = string (workspace.userlandSamples.genMonthlyArchives.rules), htmltext = "", indentlevel = 0, maxstories = 25, xshell, adrshellbody)
   local (outlinetext, adr, t)
   new (tabletype, @t)
   xml.compile (op.outlinetoxml (adrmonth), @xshell)
   adrshellbody = xml.opml.getbodyaddress (@xshell)
   for adr in adrshellbody
      delete (@adr^.["/atts"].type)
      try
         created = date (adr^.["/atts"].created)
         adrsub = xml.addtable (adr, "outline")
         xml.addattribute (adrsub, "text", "<span class=\"whenPosted\">Posted: " + string (created) + ".</span>")
   workspace.userlandSamples.genMonthlyArchives.struct = xshell
   t.outlinetext = op.render.viewoutline ("", adrparent:adrshellbody, adrInitialRulesText: @rulestext)
   t.systemStyles = webApp.viewHeadIncludes (flBootstrap2:true)
   t.year = date.year ()
   t.now = clock.now ()
   t.generatorProgramName = frontier.getprogramname () + "/" + string.popfilefromaddress (this)
   t.machineName = config.myServerFarm.prefs.myName
   t.pleaseWaitMessage = opmleditor.viewslogan ()
   t.generatorProgramName = this
   t.metaDescription = "Scripting News, the weblog started in 1997 that bootstrapped the blogging revolution."
   
   t.menutext = ""
   t.this = this
   t.ownername = "Scripting News, Inc"
   t.headline = "Scripting News archive for " + nameof (adrmonth^)
   t.title = t.headline
   htmltext = string.tablereplace (string.replaceall (string (workspace.userlandSamples.genMonthlyArchives.template), "\r", "\r\n"), @t)
   s3.newobject ("/scripting.com/threads/" + string.innercasename (nameof (adrmonth^)) + ".html", htmltext)
   //webbrowser.displaytext (htmltext)
bundle //test code
   local (adr)
   for adr in @workspace.userlandSamples.genMonthlyArchives.months
      workspace.userlandSamples.genMonthlyArchives.genOneMonthArchive (adr)
   export.sendobject (@workspace.userlandSamples.genMonthlyArchives, "ohio:getMonthlyArchives.fttb")
   s3.newobject ("/scripting.com/threads/getMonthlyArchives.fttb", file.readwholefile ("ohio:getMonthlyArchives.fttb"))
   

</pre>