### workspace.userlandSamples.pullMacrosFromOutline
<pre>
on pullMacrosFromOutline (s)
   //Changes
      //4/26/12; 12:19:51 PM by DW
         //Use this script to get a list of macros that appear in an outline. To use, open the outline containing the macros, then open this script and click the Run button. A list of macros will open. 
   local (adroutline = @scratchpad.macros, macros, oldtarget)
   new (tabletype, @macros)
   loop
      local (ix = string.patternmatch ("<%", s), macro)
      if ix == 0
         break
      s = string.delete (s, 1, ix-1)
      ix = string.patternmatch ("%>", s)
      if ix == 0
         break
      macros.[string. mid (s, 1, ix+1)] = true
      s = string.delete (s, 1, ix+1)
   
   new (outlinetype, adroutline)
   oldtarget = target.set (adroutline)
   for adrmacro in @macros
      op.insert (nameof (adrmacro^), down)
   op.firstsummit ()
   op.deleteline ()
   edit (adroutline)
   target.set (oldtarget)
bundle //test code
   local (adrfrontwindow = address (window.frontmost ()))
   pullMacrosFromOutline (string (adrfrontwindow^))

</pre>