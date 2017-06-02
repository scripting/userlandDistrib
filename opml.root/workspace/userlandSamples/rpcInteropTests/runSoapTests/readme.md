### workspace.userlandSamples.rpcInteropTests.runSoapTests
<pre>
on runSoapTests (server, port, adrResultsCallback = nil)
   local (adrClientScripts = @workspace.userlandSamples.rpcInteropTests.clientScripts)
   
   local (adrClientScript)
   for adrClientScript in adrClientScripts
      local (name = nameOf (adrClientScript^))
      try
         adrClientScript^ (server, port, "soap")
         if adrResultsCallback != nil
            adrResultsCallback^ (name + ": Passed")
      else
         if adrResultsCallback != nil
            adrResultsCallback^ (name + ": Failed: " + tryError)
         else
            scriptError ("Error calling " + name + ": " + tryError)
   
   return (true) //success

</pre>