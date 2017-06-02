### workspace.userlandSamples.parseFontAwesomeIcons.readme
<pre>
//8/1/14; 1:12:53 PM by DW
   //When a new version of Font Awesome comes out, we need to rebuild the JSON that Fargo uses to create the Choose Icon dialog. The parser routine here does that.
   //1. Get the latest Font Awesome, open font-awesome.css.
   //2. Find fa-glass:before, select all the declarations from that point, to the end of the file. Copy.
   //3. Paste into the text object in this table.
   //4. Run parser.
   //5. Copy the JSON text and paste it into the Fargo code.

</pre>