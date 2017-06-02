### workspace.userlandSamples.readSimmonsJson
<pre>
on readSimmonsJson ()
   //Changes
      //6/1/17; 10:16:59 AM by DW
         //Read the inessential.com JSON feed, compile it and store the result in scratchpad.
   local (url = "http://inessential.com/feed.json")
   local (jsontext = tcp.httpReadUrl (url, 3, false)) //redirect up to 3 times, no msgs
   json.compile (jsontext, @scratchpad.simmonsStruct)
   edit (@scratchpad.simmonsStruct)
bundle //test code
   readSimmonsJson ()

</pre>