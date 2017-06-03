### workspace.userlandSamples.readChangesXml
<pre>
//10/2/01; 9:47:17 AM by DW
   //Sample script, reads the changes.xml file managed by Weblogs.Com.
   //It creates a table at scratchpad.weblogUpdates, each sub-table represents one weblog that changed.
   //See http://newhome.weblogs.com/ for more information.

local (adrtable = @scratchpad.weblogUpdates)
local (s = tcp.httpReadUrl ("http://static.userland.com/weblogs/changes.xml"))
xml.compile (s, @xstruct)
local (adrroot = xml.getaddress (@xstruct, "weblogUpdates"))
local (whenxmlfilechanged = date (xml.getattribute (adrroot, "updated")^))
local (loglist = xml.getaddresslist (adrroot, "weblog"), adrxlog)
on untaint (s)
   s = string.replaceAll (s, "{", "&amp;#123;")
   s = html.neuterJavaScript (s)
   return (s)
new (tabletype, adrtable)
for adrxlog in loglist
   local (url = untaint (xml.getattribute (adrxlog, "url")^))
   local (name = untaint (xml.getattribute (adrxlog, "name")^))
   local (when = number (xml.getattribute (adrxlog, "when")^))
   local (whenthisweblogchanged = whenxmlfilechanged - when)
   if whenthisweblogchanged > clock.now ()
      whenthisweblogchanged = clock.now ()
   
   local (day, month, year, hour, minute, second)
   date.get (whenthisweblogchanged, @day, @month, @year, @hour, @minute, @second)
   nameitem = year + "." + string.padwithzeros (month, 2) + "." + string.padwithzeros (day, 2) + "." + string.padwithzeros (hour, 2) + "." + string.padwithzeros (minute, 2) + "." + string.padwithzeros (second, 2)
   
   local (adrsubtable = @adrtable^.[nameitem])
   new (tabletype, adrsubtable)
   adrsubtable^.sitename = xml.entitydecode (name, true)
   adrsubtable^.siteurl = xml.entitydecode (url, true)
   adrsubtable^.timeupdate = whenthisweblogchanged

</pre>