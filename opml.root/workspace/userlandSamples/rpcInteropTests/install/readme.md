### workspace.userlandSamples.rpcInteropTests.install
<pre>
//4/15/01; 12:59:42 AM by JES
   //This script installs the interop test SOAP and XML-RPC handlers.
bundle //set up the xml-rpc responder and install rpc handlers
   user.webserver.responders.RPC2.enabled = true
   user.betty.rpcHandlers.interopEchoTests = @workspace.userlandSamples.rpcInteropTests.rpcHandlers
bundle //set up the soap responder and install rpc handlers
   user.webserver.responders.soap.enabled = true
   user.soap.rpcHandlers.interopEchoTests = @workspace.userlandSamples.rpcInteropTests.rpcHandlers

</pre>