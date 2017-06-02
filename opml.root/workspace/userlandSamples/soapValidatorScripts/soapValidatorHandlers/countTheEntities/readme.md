### workspace.userlandSamples.soapValidatorScripts.soapValidatorHandlers.countTheEntities
<pre>
on countTheEntities (s)
   local (struct, i)
   new (tabletype, @struct)
   struct.ctLeftAngleBrackets = 0
   struct.ctRightAngleBrackets = 0
   struct.ctAmpersands = 0
   struct.ctApostrophes = 0
   struct.ctQuotes = 0
   for i = 1 to sizeof (s)
      case s [i]
         '<'
            struct.ctLeftAngleBrackets++
         '>'
            struct.ctRightAngleBrackets++
         '&'
            struct.ctAmpersands++
         '\''
            struct.ctApostrophes++
         '"'
            struct.ctQuotes++
   return (struct)
bundle //test code
   local (s)
   bundle //build the string
      local (i)
      for i = 1 to random (100, 255)
         s = s + char (random ('a', 'z'))
      on addentity (ch)
         local (ct = random (2, 10))
         for i = 1 to ct
            s [random (1, sizeof (s))] = ch
      addentity ('<')
      addentity ('>')
      addentity ('&')
      addentity ('\'')
      addentity ("'")
   scratchpad.entities = countTheEntities (s)

</pre>