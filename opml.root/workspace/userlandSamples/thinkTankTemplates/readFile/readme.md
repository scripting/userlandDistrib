### workspace.userlandSamples.thinkTankTemplates.readFile
<pre>
on readFile (f, adroutline)
   //Changes
      //9/28/12; 6:57:17 PM by DW
         //Extracted this script from a fatpage. It's useful for converting .head files, the format used by ThinkTank, Ready and MORE, to exchange outlines. MORE switched to a binary format at some point. 
            //http://worknotes.scripting.com/september2012/92812ByDw/newNodetypePresentation
   local (firstline = true, level, lastlevel)
   new (outlineType, adroutline)
   target.set (adroutline)
   edit (adroutline)
   file.open (f)
   while not file.endOfFile (f)
      s = file.readLine (f) - char (10)
      if s beginsWith char (26) Çend of file
         break
      if string.lower (s) beginswith ".head"
         s = string.delete (s, 1, 6) Çpop off the .HEAD
         level = ""
         while string.isNumeric (s [1])
            level = level + string (s [1])
            s = string.delete (s, 1, 1)
         level = number (level)
         s = string.delete (s, 1, 3)
      else
         level = lastlevel
      msg (level + ":" + s)
      if firstline
         op.setLineText (s)
         lastlevel = 0
         firstline = false
      else
         if level > lastlevel
            op.insert (s, right)
         else
            op.go (left, lastlevel - level)
            op.insert (s, down)
      lastlevel = level
   file.close (f)
   op.firstSummit ()
   window.zoom (adroutline)
   window.close (adroutline)
bundle Çtest code
   //local (f = "Ohio:tmp.txt")
   //local (s = tcp.httpreadurl ("https://dl.dropbox.com/u/36518280/misc/MORE%201.1c/Read%20Me"))
   //file.writewholefile (f, s)
   //readFile (f, @scratchpad.myoutline)
   //return
   
   local (folder = "Macintosh HD:Users:davewiner:Downloads:ThinkTank Templates:", f)
   local (adrtable = @workspace.userlandSamples.thinkTankTemplates.templates)
   new (tabletype, adrtable)
   edit (adrtable)
   fileloop (f in folder)
      readfile (f, @adrtable^.[file.fileFromPath (f) - ".TXT"])
      window.zoom (adrtable)

</pre>