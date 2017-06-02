### workspace.userlandSamples.readScriptingJson
<pre>
on readScriptingJson ()
   //Changes
      //6/1/17; 10:25:47 AM by DW
         //We now open the scratchpad table after compiling the JSON. 
      //6/1/17; 9:24:13 AM by DW
         //Read the Scripting News JSON feed, compile it and store the result in scratchpad.
   local (url = "http://scripting.com/rss.json")
   local (jsontext = tcp.httpReadUrl (url, 3, false)) //redirect up to 3 times, no msgs
   json.compile (jsontext, @scratchpad.scriptingStruct)
   edit (@scratchpad.scriptingStruct)
bundle //test code
   readScriptingJson ()

</pre>