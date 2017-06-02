### workspace.userlandSamples.getListDottedIds
<pre>
//Changes
   //11/27/10; 3:23:40 AM by DW
      //Create an outline with a list of domain names, put the cursor on one of the names, and run this script. It will fill in the IP addresses as sub-heads. 
         //http://scripting.com/images/2010/11/27/list.gif
local (domain, ip)
op.go (up, infinity)
loop
   domain = op.getlinetext ()
   try &#123;delete (@system.temp.reverseIpCache.[domain])}
   ip = tcp.dns.getdottedid (domain)
   if op.countsubs (1) == 1
      op.expand (1)
      op.go (right, 1)
      op.setlinetext (ip)
   else
      op.insert (ip, right)
   op.go (left, 1)
   if not op.go (down, 1)
      op.go (up, infinity)
      break

</pre>