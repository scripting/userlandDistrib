### workspace.userlandSamples.mailOutlineItem
<pre>
on mailOutlineItem (recipient)
   //Changes
      //10/3/01; 1:49:52 PM by DW
         //Made general -- the bar cursor headline is routed to the mail address specified by the parameter
      //9/13/01; 8:20:45 AM by DW
         //Created. Grab the bar cursor headline, format it and send it to the scriptingNewsWorldTradeCenter mail list.
         //I added this to my Custom menu with Control-= as the single keystroke.
   
   local (adroutline = address (window.frontmost ()))
   if typeof (adroutline^) != outlinetype
      scriptError ("This command only works with outline windows.")
   if dialog.ask ("Enter subject:", @scratchpad.lastBulletinSubject)
      local (s = string.htmlToEmail (op.getlinetext ()) + string.filledstring ("\r\n ", 3))
      tcp.sendmail (recipient, scratchpad.lastBulletinSubject, s)

</pre>