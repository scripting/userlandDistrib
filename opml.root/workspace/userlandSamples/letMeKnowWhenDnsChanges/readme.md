### workspace.userlandSamples.letMeKnowWhenDnsChanges
<pre>
//Changes
   //5/22/10; 7:24:38 AM by DW
      //Copy the message into the object db location scratchpad.letmeknowmsg. That way you can open the window and watch the value change. It can be hard to read the message in the About window.
   //1/21/10; 6:43:12 AM by DW
      //If you put in a change for a domain and want to know when the change is visible where you are, run this script. Note that it can't call tcp.dns.getdottedid because it caches the value, so it won't change as long as the app is running.
local (domain = "scripting.com")
on getdottedid (name)
   return (tcp.addressDecode (tcp.nameToAddress (domain)))
local (id = getdottedid (domain), ct = 0)
while getdottedid (domain) == id
   scratchpad.letmeknowmsg = domain + " = " + id + ". (" + ct + " loops)"
   msg (scratchpad.letmeknowmsg)
   thread.sleepfor (5)
   ct++
dialog.alert (getdottedid (domain))

</pre>