### workspace.userlandSamples.threadWaiting.readMe
<pre>
Shows how the realtime verbs work.
   To run the experiment, press Cmd-/ on the line below:
      workspace.userlandSamples.threadWaiting.launchThreadScript ()
   Wait a few seconds, then press Cmd-/ on this line:
      workspace.userlandSamples.threadWaiting.stopThreadScript ()
         //true
   You should see a dialog saying how long the script was running.
Then Cmd-/ the first script, but not the second:
   workspace.userlandSamples.threadWaiting.launchThreadScript ()
      //"The script has been launched!"
It should say the script was running for 15 seconds.

</pre>