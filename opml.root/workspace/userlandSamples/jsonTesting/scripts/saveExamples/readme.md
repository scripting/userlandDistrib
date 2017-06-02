### workspace.userlandSamples.jsonTesting.scripts.saveExamples
<pre>
//Changes
   //10/24/10; 8:23:30 PM by DW
      //A utility script I need to save the examples to a location that json.scripting.com can get at them.
local (adrsource, path)
for adrsource in @workspace.userlandSamples.jsonTesting.source
   path = "/static.opml.org/jsonExamples/" + nameof (adrsource^) + ".json"
   msg (path)
   s3.newobject (path, string (adrsource^))

</pre>