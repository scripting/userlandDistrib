### workspace.userlandSamples.infiniteLoop
<pre>
//Changes
   //2/27/12; 5:47:26 PM by DW
      //This is an example of an infinite loop. 
      //Click the Run button and watch the numbers go up in the About window.
      //Click the Kill button when you get the idea. :-)
local (ct = 0)
window.about () //open the About window
loop
   msg (ct++) //display the counter, and add one to it

</pre>