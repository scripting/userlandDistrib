### workspace.userlandSamples.rpcInteropTests.runTests
<pre>
//4/16/01; 2:21:35 PM by JES
   //This script runs all the client-side test scripts in the workspace.userlandSamples.rpcInteropTests.clientScripts table.
   //Tests are run once for SOAP, and once for XML-RPC. Results are displayed in an outline.
   //To change the server, edit values in workspace.userlandSamples.rpcInteropTests.endpoint.

local (adrEndpoint = @workspace.userlandSamples.rpcInteropTests.endpoint)
local (adrlog = @scratchpad.rpcTestResults)

new (outlineType, adrlog)

local (dir = right)
bundle //set up results outline
   edit (adrlog)
   local (oldTarget = target.set (adrlog))
   op.setLineText ("RPC Client echo-test run at " + clock.now ())
   target.set (oldTarget)
on addToResults (s)
   local (oldTarget = target.set (adrlog))
   op.insert (s, dir)
   target.set (oldTarget)
   dir = down

with adrEndpoint^
   
   bundle //XML-RPC heading
      dir = right
      addToResults ("Testing XML-RPC:")
      dir = right
   workspace.userlandSamples.rpcInteropTests.runXmlRpcTests (server, port, @addToResults)
   
   bundle //SOAP heading
      dir = left
      addToResults ("Testing SOAP:")
      dir = right
   workspace.userlandSamples.rpcInteropTests.runSoapTests (server, port, @addToResults)

</pre>