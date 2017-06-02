### workspace.userlandSamples.doSomeUpstreaming
<pre>
//Changes
   //1/3/02; 4:54:25 PM by DW
      //Change "playlist" to "radio".
   //2/12/01; 1:49:33 PM by DW
      //Test upstreaming by sprinkling a few files in a nice new test folder.

on writetestfile (f, size)
   file.surefilepath (f)
   file.writewholefile (f, string.filledstring ("x", size))

local (folder = user.radio.prefs.wwwfolder + "test\\largefiles\\")
for ch = 'a' to 'z'
   writetestfile (folder + ch + ".html", random (1000, 16000))

</pre>