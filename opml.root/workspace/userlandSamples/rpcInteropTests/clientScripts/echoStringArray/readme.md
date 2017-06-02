### workspace.userlandSamples.rpcInteropTests.clientScripts.echoStringArray
<pre>
on echoStringArray (server, port, protocol)
   local (aStringArray = &#123;})
   bundle //generate the array
      local (i)
      for i = 1 to 3
         local (n = random (1, 50))
         local (aString = states.nthState (n))
         aStringArray = aStringArray + aString
   
   local (result, params = &#123;"inputStringArray":aStringArray})
   result = xml.rpc (server, port, "interopEchoTests.echoStringArray", @params, protocol:protocol, soapAction:"/interopEchoTests")
   
   if typeOf (result) != listType
      scriptError ("The call failed because the response was not an array.")
   local (i, ct = sizeOf (result))
   if ct != sizeOf (aStringArray)
      scriptError ("The call failed because the size of the request array is different from the size of the response array.")
   for i = 1 to ct
      if result[i] != aStringArray[i]
         scriptError ("The call failed because the response was different from the request. We sent " + aStringArray[i] + " for element " + i + ", and the server returned " + result[i] + ".")
   
   return (true) //success

</pre>