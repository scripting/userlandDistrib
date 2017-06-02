### workspace.userlandSamples.findLargeDatabases
<pre>
//Changes
   //4/20/08; 2:26:40 PM by DW
      //Created. One of the things that slows down a Frontier installation are files at or near their maxium size. This script shows all the databases in the Guest Databases folder that are larger than 500MB.
local (maxsize = 500 * 1024 * 1024)
//msg (string.megabytestring (maxsize))
local (folder = frontier.pathstring + "Guest Databases" + file.getpathchar ())
new (outlinetype, @scratchpad.largedatabases)
target.set (@scratchpad.largedatabases)
edit (@scratchpad.largedatabases)
fileloop (f in folder, infinity)
   msg (f)
   if string.lower (file.filefrompath (f)) endswith ".root"
      if file.size (f) > maxsize
         op.insert (file.filefrompath (f) + " = " + string.gigabytestring (file.size (f)), down)
op.firstsummit ()
op.deleteline ()
msg ("")

</pre>