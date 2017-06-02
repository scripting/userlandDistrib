### workspace.userlandSamples.outlineDomains
<pre>
on outlineDomains (adrtable)
   //Changes
      //2/14/12; 11:54:26 AM by DW
         //Using our Amazon Route53 interface, create an outline with your domains at the top level, and underneath them, the records in each domain. I needed this to help me locate all the cnames that point to a domain that I need to move. How sweet to finally have a programmable DNS.
   local (zones, adrzone, adrrecord)
   s3.route53.listHostedZones (@zones)
   //scratchpad.zones = zones
   new (tabletype, adrtable)
   for adrzone in @zones
      local (adrsub = @adrtable^.[adrzone^.name])
      new (tabletype, adrsub)
      s3.route53.listRecords (nameof (adrzone^), @records)
      //scratchpad.records = records
      for adrrecord in @records
         local (adrsubsub = @adrsub^.[nameof (adrrecord^)])
         if adrrecord^.type == "CNAME"
            adrsubsub^ = adrrecord^.value
         else
            adrsubsub^ = adrrecord^
bundle //test code
   local (opmltext)
   outlineDomains (@scratchpad.tableOutline)
   opmltext = xml.opml.getOpmlText (@scratchpad.tableOutline, "My Domains and CNAMEs", valueName:"cname")
   op.newoutlineobject (opmltext, @scratchpad.myDomains)

</pre>