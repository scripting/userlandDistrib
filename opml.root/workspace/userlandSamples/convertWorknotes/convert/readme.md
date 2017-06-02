### workspace.userlandSamples.convertWorknotes.convert
<pre>
on convert ()
   //Changes
      //7/30/13; 2:44:32 PM by DW
         //Created.
   local (adrinput = @workspace.userlandSamples.convertWorknotes.input, xstructIn)
   xml.compile (op.outlinetoxml (adrinput), @xstructIn)
   //workspace.userlandSamples.convertWorknotes.xstructIn = xstructIn
   
   local (adroutput = @workspace.userlandSamples.convertWorknotes.xstructOut)
   adroutput^ = workspace.userlandSamples.convertWorknotes.xstructTemplate
   //new (tabletype, adroutput)
   
   on findnode (adrparent, namenode, nameatt)
      local (adr)
      for adr in adrparent
         if nameof (adr^) endswith "outline"
            if adr^.["/atts"].text == namenode
               return (adr)
      local (adrsub = xml.addtable (adrparent, "outline"))
      local (adratts = @adrsub^.["/atts"])
      new (tabletype, adratts)
      adratts^.text = namenode
      adratts^.name = nameatt
      return (adrsub)
   on savepost (adrpost)
      local (adratts = @adrpost^.["/atts"])
      //scratchpad.myatts = adratts^; edit (@scratchpad.myatts)
      local (when = date (adratts^.created))
      local (day, month, year, hour, minute, second)
      date.get (when, @day, @month, @year, @hour, @minute, @second)
      //scratchpad.mypost = adrpost^; edit (@scratchpad.mypost)
      
      local (nomad = xml.opml.getbodyaddress (adroutput))
      nomad = findnode (nomad, year, year)
      nomad = findnode (nomad, date.monthtostring (month) + " " + year, string.padwithzeros (month, 2))
      nomad = findnode (nomad, date.monthtostring (month) + " " + day, string.padwithzeros (day, 2))
      
      adrpost^.["/atts"].type = "outline"
      nomad^.[nameof (adrpost^)] = adrpost^
   on visitlevel (adrlevel) 
      local (adr)
      for adr in adrlevel
         if nameof (adr^) endswith "outline"
            local (adratts = @adr^.["/atts"])
            if defined (adratts^) and defined (adratts^.type) and (adratts^.type != "index")
               savepost (adr)
            else
               visitlevel (adr)
   visitlevel (xml.opml.getbodyaddress (@xstructIn))
   
   local (xmltext = xml.decompile (adroutput))
   op.xmltooutline (xmltext, @workspace.userlandSamples.convertWorknotes.output)
   file.writewholefile (user.prefs.dropboxfolder + "apps:fargo:worknotesConverted.opml", xmltext)
bundle //test code
   convert ()

</pre>