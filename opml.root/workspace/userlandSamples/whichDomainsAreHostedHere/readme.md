### workspace.userlandSamples.whichDomainsAreHostedHere
<pre>
//Changes
   //12/2/10; 10:49:43 AM by DW
      //Sometimes I move around domains and content and lose track of which domains are still hosted on the server I'm looking at. This script tells me for sure.
local (adroutline = @workspace.userlandsamples.domains, adrdomain)
local (myAddress = tcp.dns.getdottedid ("ec2.scripting.com"), dir = right)
new (outlinetype, adroutline)
target.set (adroutline)
edit (adroutline)
op.setlinetext ("Good domains")
on addlinkatt (url)
   local (atts)
   new (tabletype, @atts)
   atts.type = "link"
   atts.url = "http://" + domain + "/"
   op.attributes.addgroup (@atts)
for adrdomain in @config.mainresponder.domains
   local (domain = nameof (adrdomain^))
   try
      if tcp.dns.getdottedid (domain) == myAddress
         op.insert (domain, dir); dir = down
         addlinkatt ("http://" + domain + "/")
op.go (left, 1); op.insert ("Bad domains", down); dir = right
for adrdomain in @config.mainresponder.domains
   local (domain = nameof (adrdomain^), flgood = true, ip = "")
   try
      ip = tcp.dns.getdottedid (domain)
      if ip != myAddress
         flgood = false
   else
      flgood = false
   if not flgood
      if ip == ""
         op.insert (domain, dir)
      else
         op.insert (domain + " = " + ip, dir) 
         addlinkatt ("http://" + domain + "/")
      dir = down

</pre>