### workspace.userlandSamples.soapValidatorScripts.soapValidatorHandlers.nestedStructTest
<pre>
on nestedStructTest (myStruct)
   local (adrmoelarrycurly = @myStruct.["year2000"].["month04"].["day01"])
   return (adrmoelarrycurly^.moe + adrmoelarrycurly^.larry + adrmoelarrycurly^.curly)

</pre>