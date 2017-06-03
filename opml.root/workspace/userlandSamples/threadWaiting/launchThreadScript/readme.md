### workspace.userlandSamples.threadWaiting.launchThreadScript
<pre>
//Changes
   //12/7/10; 7:27:58 PM by DW
      //Created. 
local (id = thread.callscript (@workspace.userlandSamples.threadWaiting.theThreadScript, {}))
workspace.userlandSamples.threadWaiting.idThread = id
return ("The script has been launched!")

</pre>