### workspace.userlandSamples.jsonTesting.scripts.runAllTests
<pre>
//Changes
   //10/23/10; 5:22:10 AM by DW
      //Also test xml.tableToJson. 
   //10/22/10; 11:18:27 AM by DW
      //Created. 
local (adrsource, adrdest)
new (tabletype, @system.temp.jsonSource)
for adrsource in @workspace.userlandSamples.jsonTesting.source
   adrdest = @workspace.userlandSamples.jsonTesting.tables.[nameof (adrsource^)]
   xml.jsonToTable (string (adrsource^), adrdest)
   wp.newtextobject (xml.tableToJson (adrdest), @system.temp.jsonSource.[nameof (adrsource^)])

</pre>