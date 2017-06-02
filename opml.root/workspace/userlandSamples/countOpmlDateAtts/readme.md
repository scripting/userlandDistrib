### workspace.userlandSamples.countOpmlDateAtts
<pre>
on countOpmlDateAtts (url)
   //Changes
      //9/6/13; 9:34:22 AM by DW
         //This script loops over an outline and gathers the date attributes into a table, allowing you to quickly see if there are duplicates. I needed to find out if this was happening because I had built the Find command on the assumption that the created att made a good node identifier. In the example I was looking at, this was clearly not true! :-)
   local (adrtable = @scratchpad.datesFromOutline, xstruct)
   xml.compile (tcp.httpreadurl (url), @xstruct)
   //scratchpad.xstruct = xstruct
   new (tabletype, adrtable)
   on dolevel (adrlevel)
      local (adr)
      for adr in adrlevel
         if nameof (adr^) endswith "outline"
            local (adrcreated = @adr^.["/atts"].created)
            if defined (adrcreated^)
               local (adrdate = @adrtable^.[adrcreated^])
               if defined (adrdate^)
                  adrdate^++
               else
                  adrdate^ = 1
            dolevel (adr)
   dolevel (xml.opml.getbodyaddress (@xstruct))
   edit (adrtable)
   table.sortby ("Value")
bundle //test code
   countOpmlDateAtts ("http://ronchester.smallpict.com/?format=opml")

</pre>