### workspace.userlandSamples.manilaHtaccessGen
<pre>
//Changes
   //1/20/10; 6:08:09 AM by DW
      //Generate an .htaccess file for a statically rendered Manila site.
      //To use the script, change the folder to one on your disk and the URL to the base URL of the folder on the web.
local (folder = "E:\\www\\wwwScriptingCom\\manila\\theTwoWayWeb\\", pc = file.getpathchar ())
local (baseurl = "http://thetwowayweb.com/", f, suffix = ".html", httext = "", indentlevel = 0)
on add (s)
   httext = httext + string.filledstring ("\t", indentlevel) + s + "\r\n"
fileloop (f in folder, infinity)
   if not file.isfolder (f)
      if f endswith ".html"
         local (relpath = string.replaceall (string.delete (f, 1, sizeof (folder)), pc, "/"))
         add ("Redirect /" + string.delete (relpath, sizeof (relpath) - sizeof (suffix) + 1, sizeof (suffix)) + " " + baseurl + relpath)
file.writewholefile (folder + ".htaccess", httext)

</pre>