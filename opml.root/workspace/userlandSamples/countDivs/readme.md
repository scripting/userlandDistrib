### workspace.userlandSamples.countDivs
<pre>
on countDivs ()
   //Changes
      //4/15/12; 3:57:28 PM by DW
         //I was staring at a bit of HTML wondering if there were the same number of opening and closing divs. So I wrote a script to find out. 
            //To run the script, open it. Then bring the window you want to check to the front, put the cursor on the bit of code you want to check, bring the script back to the front and click Run. Two dialogs will appear that tell you what you want to know. 
            //Obviously it's easily modified to look for other stuff. 
   local (texttosearch = op.getsuboutline ())
   wp.newtextobject (texttosearch, @scratchpad.texttosearch)
   on count (searchfor)
      local (s = texttosearch, ct = 0)
      loop
         ix = string.patternmatch (searchfor, s)
         if ix == 0
            return (ct)
         ct++
         s = string.delete (s, 1, ix)
   dialog.alert (count ("<div"))
   dialog.alert (count ("</div"))
bundle //test code
   countDivs ()

</pre>