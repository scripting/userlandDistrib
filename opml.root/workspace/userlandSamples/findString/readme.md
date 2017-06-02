### workspace.userlandSamples.findString
<pre>
//1/13/01; 9:13:34 AM by DW
   //Visit all objects in all open databases looking for objects that contain a string you enter in a dialog. Create a list in scratchpad.objectsThatContainString.
   //Changes:
      //2/22/01; 3:07:24 PM by PBS
         //Do a case-inensitive search.
if dialog.ask ("What string would you like to search for?", @scratchpad.lastsearchstring)
   local (lowerSearchString = string.lower (scratchpad.lastsearchstring)) //PBS 02/22/01: case-insensitive
   local (ct = 0)
   local (adroutline = @scratchpad.objectsThatContainString, insertdir = right)
   bundle //set up the outline
      new (outlinetype, adroutline); edit (adroutline)
      target.set (adroutline)
      op.firstsummit ()
      op.setlinetext ("Objects that contain \"" + scratchpad.lastsearchstring + "\" on " + clock.now () + ":")
   window.about ()
   on dotable (adrtable)
      on addadr (adr)
         if adr == @scratchpad.lastsearchstring
            return
         local (s = string (adr))
         local (pattern = "\"].")
         local (ix = string.patternmatch (pattern, s))
         if ix > 0
            s = string.delete (s, 1, ix + sizeof (pattern) - 1)
         op.insert (s + " (" + sizeof (adr^) + ")", insertdir); insertdir = down
      local (adr)
      for adr in adrtable
         case typeof (adr^)
            tabletype
               dotable (adr)
         else
            try
               if string.lower (string (adr^)) contains lowerSearchString //PBS 02/22/01: case-inensitive
                  addadr (adr)
         if (++ct % 1000) == 0
            msg (ct)
            filemenu.save ()
      return (true)
   dotable (@root)
   op.firstsummit ()
   edit (adroutline)
   msg ("")

</pre>