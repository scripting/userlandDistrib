### workspace.userlandSamples.setupWebeditServer
<pre>
on setupWebeditServer (name, password, email)
   //Changes
      //11/2/2010; 6:55:18 PM by DW
         //Run this script to set up WebEdit server so you can check out and check in objects in the main root and in guest databases. 
   user.betty.rpcHandlers.webEdit = @webEditServer.rpcHandlers.webEdit
   people.newuser (name, password, email)
   people.attachServiceToUser (name, "Custody")
   people.attachServiceToUser (name, "WebEdit")
//bundle //test code
   //setupWebeditServer ("Bull Mancuso", string.getrandompassword (10), "bull@mancuso.net")

</pre>