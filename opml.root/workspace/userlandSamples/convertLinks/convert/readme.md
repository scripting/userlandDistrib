### workspace.userlandSamples.convertLinks.convert
<pre>
on convert ()
   //Changes
      //8/8/13; 11:54:42 AM by DW
         //Created.
   local (adrinput = @workspace.userlandSamples.convertLinks.inputOutline, linkbegin = "&lt;a href=\"", ix, url)
   local (adroutput = @workspace.userlandSamples.convertLinks.outputOutline)
   adroutput^ = adrinput^
   target.set (adroutput)
   op.firstsummit ()
   edit (adroutput)
   loop
      op.expand (1)
      s = op.getlinetext ()
      if s beginswith linkbegin
         local (atts)
         new (tabletype, @atts)
         s = string.delete (s, 1, sizeof (linkbegin))
         ix = string.patternmatch ("\"", s)
         url = string.mid (s, 1, ix - 1)
         atts.type = "link"
         atts.url = url
         op.attributes.addgroup (@atts)
         op.setlinetext (searchengine.stripmarkup (op.getlinetext ()))
      if not op.go (flatdown, 1)
         break
bundle //test code
   convert ()

</pre>