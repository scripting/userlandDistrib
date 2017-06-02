### workspace.userlandSamples.buildReplacetables.buildTheTables
<pre>
on buildTheTables ()
   //Changes
      //8/13/12; 7:43:26 AM by DW
         //Created.
   local (adrtable = @workspace.userlandSamples.buildReplacetables.replaceTable)
   bundle //create table, add characters 128 through 255
      local (i)
      new (tabletype, adrtable)
      for i = 128 to 255
         adrtable^.[char (i)] = "&#" + i + ";"
   //bundle //add entities for symbols and Greek letters
      //http://htmlhelp.com/reference/html40/entities/symbols.html
      //local (s = string (workspace.buildnewreplacetable.w3ctext), xstruct)
      //xml.compile (s, @xstruct)
      //workspace.userlandSamples.buildReplacetables.w3cstruct = xstruct
      //
      //local (adrtbody = xml.getaddress (@xstruct, "tbody"), adr, val, name, num)
      //for adr in adrtbody
         //val = adr^ [2]
         //name = adr^ [3]
         //bundle //do the bit twiddling
            //name = string.delete (name, 1, 2)
            //name = string.mid (name, 1, sizeof (name) - 1)
            //num = number (name)
            //name = char (bit.logicaland (num, 255)) + char (bit.shiftright (num, 8))
         //adrtable^.[name] = val
   bundle //build the inverted table
      local (adrinvertedtable1 = @workspace.userlandSamples.buildReplacetables.replaceTableInverted1, adr)
      local (adrinvertedtable2 = @workspace.userlandSamples.buildReplacetables.replaceTableInverted2)
      new (tabletype, adrinvertedtable1)
      new (tabletype, adrinvertedtable2)
      for adr in adrtable
         if defined (adrinvertedtable1^.[adr^])
            adrinvertedtable2^.[adr^] = nameof (adr^)
         else
            adrinvertedtable1^.[adr^] = nameof (adr^)
bundle //test code
   buildTheTables ()

</pre>