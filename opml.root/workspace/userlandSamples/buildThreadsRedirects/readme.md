### workspace.userlandSamples.buildThreadsRedirects
<pre>
on buildThreadsRedirects (adroutline)
   //Changes
      //9/3/12; 12:00:16 PM by DW
         //Builds redirects from the new threads site to posts on the original one.
            //http://worknotes.scripting.com/september2012/9312ByDw/workingOnThreads
   local (adrcal = @scratchpad.calendar)
   bundle //build the calendar from the outline
      new (tabletype, adrcal)
      target.set (adroutline)
      op.firstsummit ()
      op.collapse ()
      op.expand (2) 
      op.go (right, 1)
      loop
         local (parentname = string.innerCaseName (string.replaceall (op.getlinetext (), "/", "")))
         if op.go (right, 1)
            loop
               //msg (op.getlinetext ())
               
               local (atts)
               op.attributes.getall (@atts)
               local (adrday = mainresponder.calendar.getdayaddress (adrcal, date (atts.created)))
               local (adritem = @adrday^.[atts.name])
               atts.parentname = parentname
               atts.text = op.getlinetext ()
               adritem^ = atts
               
               if not op.go (down, 1)
                  break
            op.go (left, 1)
         if not op.go (down, 1)
            break
   bundle //build an outline with redirects
      adroutline = @scratchpad.newthreadsoutline
      new (outlinetype, adroutline)
      target.set (adroutline)
      for adryear in adrcal
         op.insert (nameof (adryear^), up)
         for adrmonth in adryear
            local (dir = right)
            op.insert (date.monthToString (number (nameof (adrmonth^))), right)
            for adrday in adrmonth
               for adrpost in adrday
                  local (atts)
                  new (tabletype, @atts)
                  atts.type = "redirect"
                  //http://threads.scripting.com/61712ByDw/newOrleansBlogs
                  atts.url = "http://threads.scripting.com/" + adrpost^.parentname + "/" + adrpost^.name
                  atts.created = adrpost^.created
                  atts.pgfnum = adrpost^.pgfnum
                  op.insert (adrpost^.text, dir); dir = up
                  op.attributes.addgroup (@atts)
            op.go (left, 2)
         op.go (left, 1)
      edit (adroutline)
bundle //test code
   local (adroutline = @system.temp.op.netOutlines.["http://static.reallysimple.org/worldoutline/dave/2012/06/09/archive109.opml"].outline)
   buildThreadsRedirects (adroutline)

</pre>