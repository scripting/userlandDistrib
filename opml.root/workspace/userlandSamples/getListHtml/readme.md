### workspace.userlandSamples.getListHtml
<pre>
//Changes
   //11/27/10; 3:39:52 AM by DW
      //Take an outline with a list of domain names, put the cursor on one of the names, and run this script. It will create a list in the web browser of links you can click on to verify that the sites are accessible.
         //http://scripting.com/images/2010/11/27/list.gif
local (htmltext = "", indentlevel = 0, domain)
on add (s)
   htmltext = htmltext + string.filledstring ("\t", indentlevel) + s + "\r"
op.go (up, infinity)
add ("&lt;ol>"); indentlevel++
loop
   domain = op.getlinetext ()
   add ("&lt;li>&lt;a href=\"http://" + domain + "/\">" + domain + "&lt;/a>&lt;/li>&lt;br>")
   if not op.go (down, 1)
      op.go (up, infinity)
      break
add ("&lt;/ol>"); indentlevel--
webbrowser.displaytext (htmltext)

</pre>