### workspace.userlandSamples.genMonthlyArchives.utilityGenLinks
<pre>
on genLinks ()
   //Changes
      //8/8/13; 2:11:29 PM by DW
         //Created.
   local (adroutline = @workspace.userlandSamples.genMonthlyArchives.links, name, atts)
   new (outlinetype, adroutline)
   target.set (adroutline)
   for adrmonth in @workspace.userlandSamples.genMonthlyArchives.months
      name = nameof (adrmonth^)
      op.insert (name, down)
      new (tabletype, @atts)
      atts.type = "link"
      atts.url = "http://scripting.com/threads/" + string.innercasename (name) + ".html"
      op.attributes.addgroup (@atts)
bundle //test code
   genLinks ()

</pre>