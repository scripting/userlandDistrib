### workspace.userlandSamples.parseFontAwesomeIcons.parser
<pre>
on parser ()
   //Changes
      //7/1/13; 2:36:49 PM by DW
         //Created.
   local (s = string (workspace.userlandSamples.parseFontAwesomeIcons.text), num, name)
   local (adricons = @workspace.userlandSamples.parseFontAwesomeIcons.icons)
   new (tabletype, adricons)
   on popuntil (chlookfor)
      local (returnstring = "")
      loop
         if sizeof (s) == 0
            return (returnstring)
         ch = s [1]
         s = string.delete (s, 1, 1)
         returnstring = returnstring + ch
         if ch == chlookfor
            return (returnstring)
   loop
      popuntil (".")
      name = popuntil (":") - ":"
      if sizeof (name) == 0
         break
      popuntil ("\"")
      num = popuntil ("\r") - "\\" - "\"" - "\r"
      num = "&amp;#x" + num
      adrsub = xml.addtable (adricons, "icon")
      xml.addvalue (adrsub, "num", num)
      xml.addvalue (adrsub, "name", name)
   //local (adroutline = @workspace.userlandSamples.parseFontAwesomeIcons.outline, s, name, value, adrsub)
   //target.set (adroutline)
   //op.firstsummit ()
   //loop
      //s = op.getlinetext ()
      //if sizeof (s) == 0
         //break
      //name = string.delete (string.nthfield (s, ":", 1), 1, 1)
      //op.go (right, 1)
      //value = string.nthfield (op.getlinetext (), ":", 2)
      //value = value - "\\" - " "
      //value = string.replaceall (value, '"', "")
      //value = "&amp;#x" + value
      //op.go (left, 1)
      //adrsub = xml.addtable (adricons, "icon")
      //xml.addvalue (adrsub, "num", value)
      //xml.addvalue (adrsub, "name", name)
      //if not op.go (down, 2)
         //break
   local (jsontext = json.decompile (adricons))
   jsontext = string.replaceall (jsontext, "}\r\t\t,", "},")
   wp.newtextobject (jsontext, @workspace.userlandSamples.parseFontAwesomeIcons.json)
bundle //test code
   parser ()

</pre>