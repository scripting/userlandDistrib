### workspace.userlandSamples.findChangedParts
<pre>
on findChangedParts (adrtable, marktime, adroutline)
   //Changes
      //1/6/12; 8:25:07 AM by DW
         //Added string.popfilefromaddress call, so that we can use this to find changes in a tool. Also it checks if tables have been modified. This helps catch changes to scalars -- they don't have their own moddates, only "large" objects have them. 
      //9/1/11; 11:27:42 AM by DW
         //New sample script. Look in the indicated table for parts that changed since marktime. We only look at scripts and outlines.
   on dotable (adrtable)
      local (adr)
      on checkobject (adr)
         if timemodified (adr) >= marktime
            local (s = string.popfilefromaddress (adr))
            s = s - "system.verbs.builtins."
            op.insert (s, down)
      for adr in adrtable
         case typeof (adr^)
            scripttype
            outlinetype
               checkobject (adr)
            tabletype
               checkobject (adr)
               dotable (adr)
   new (outlinetype, adroutline)
   edit (adroutline)
   target.set (adroutline)
   dotable (adrtable)
   op.firstsummit ()
   op.deleteline ()
bundle //test code
   local (marktime = date ("December 15, 2011; 5:00PM"))
   findChangedParts (@worldOutlineWebsite, marktime, @scratchpad.changedParts)

</pre>