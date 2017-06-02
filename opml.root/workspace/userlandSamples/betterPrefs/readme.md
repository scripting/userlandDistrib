### workspace.userlandSamples.betterPrefs
<pre>
on betterPrefs ()
   //Changes
      //9/16/10; 11:24:59 AM by DW
         //Add some bits that make it so that mainresponder.respond handles all the requests that used to go through the websiteframework responder.
      //9/10/10; 9:09:28 PM by DW
         //Script that sets more reasonable defaults for today's machines, with an eye toward including this code in userland.cleanroot.
   user.prefs.commonStyles.medium.size = 14
   user.prefs.flBookmarkMenu = true
   user.prefs.flCustomMenu = true
   user.prefs.flGenerateOpml2 = true
   user.prefs.flMainResponderHandlesErrors = false
   user.prefs.fonts.outlineFontSize = 14
   user.prefs.fonts.scriptFontSize = 14
   user.prefs.fonts.wptextFontSize = 14
   user.prefs.fonts.menuBarFontSize = 14
   user.prefs.fonts.tableFontSize = 14
   menus.buildMenuBar ()
   bundle //9/16/10 by DW
      table.rename (@user.webserver.responders.websiteFramework.condition, "conditionOld")
      user.webserver.responders.websiteFramework.condition = false
      config.mainresponder.domains.default = @user.webserver.responders.websiteFramework.data.doctree
bundle //test code
   betterPrefs ()

</pre>