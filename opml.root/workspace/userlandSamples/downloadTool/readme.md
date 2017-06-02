### workspace.userlandSamples.downloadTool
<pre>
on downloadTool (toolname)
   //Changes
      //10/28/10; 10:44:45 AM by DW
         //Downloads a tool via HTTP and installs it.
   local (url = "http://codecasting.org/" + toolname + "/" + toolname + ".root")
   local (filetext = tcp.httpreadurl (url))
   local (f = frontier.getsubfolder ("apps") + "Tools" + file.getpathchar () + toolname + ".root")
   file.surefilepath (f)
   file.writewholefile (f, filetext)
   frontier.tools.install (f)
bundle //test code
   downloadTool ("ec2Support")

</pre>