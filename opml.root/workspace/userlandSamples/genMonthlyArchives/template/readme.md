### workspace.userlandSamples.genMonthlyArchives.template
<pre>
&lt;!DOCTYPE html>
&lt;html>
   &lt;head>
      &lt;title>&lt;%title%>&lt;/title>
      &lt;meta http-equiv="Content-Type" content="text/html; charset=UTF-8"/> 
      &lt;link rel="alternate" type="application/rss+xml" title="RSS" href="http://scripting.com/rss.xml" />
      &lt;link rel="alternate" type="application/rss+xml" title="RSS/link-blog" href="http://links.scripting.com/rss.xml" />
      &lt;meta name="generator" content="&lt;%generatorProgramName%>">
      &lt;meta name="description" content="&lt;%metaDescription%>">
      
      &lt;link href="http://static.scripting.com/github/bootstrap2/css/bootstrap.css" rel="stylesheet">
      &lt;script src="http://static.smallpicture.com/bootstrap/js/jquery-1.9.1.min.js">&lt;/script>
      &lt;script src="http://static.smallpicture.com/bootstrap/js/bootstrap.min.js">&lt;/script>
      &lt;link rel="stylesheet" href="http://static.smallpicture.com/concord-assets/fontawesome/3.2.1/css/font-awesome.min.css">
      
      &lt;script src="http://static.opml.org/scripts.js">&lt;/script>
      &lt;link href="http://static.opml.org/styles.css" rel="stylesheet">
      
      &lt;style>
         body {
            background-image: url ('http://static.scripting.com/images/lisa.jpg');
            }
         .divThreadSuitePage {
            width: 80%;
            margin-left: 75px;
            margin-top: 50px;
            }
         .divThreadSuitePage span {
            color: black;
            margin-left: 0;
            }
         .divLogo {
            margin-top: 50px;
            }
         .divLinksTable a:link {
            color: black;
            }
         .divLinksTable a:visited {
            color: black;
            }
         .divTabTitles {
            font-family: Arial;
            font-size: 15px;
            font-weight: bold;
            }
         .divLinksTable .linkWhat {
            font-family: Georgia;
            font-size: 16px;
            line-height: 140%;
            vertical-align: top;
            }
         .divLinksTable .linkWhen {
            font-family: Georgia;
            font-size: 16px;
            line-height: 140%;
            vertical-align: top;
            text-align: right;
            }
         .divLinksTable td {
            border: none;
            }
         .divAbout {
            text-align: left;
            }
         .spanWhenStory {
            font-family: Arial;
            font-size: 14px;
            float: none;
            }
         .modal {
            width: 770px;
            left: 40%;
            }
         a, a:link, a:visited {
            color: #0069D6;
            }
         .aStoryTitle {
            color: black;
            }
         .aStoryTitle:visited {
            color: black;
            }
         .aStoryTitle:link {
            color: black;
            }
         &lt;/style>
      &lt;/head>
   &lt;body>
      &lt;style>
         .aStoryTitle {
            color: black;
            }
         .aStoryTitle:visited {
            color: black;
            }
         .aStoryTitle:link {
            color: black;
            }
         .divStoriesOutline {
            margin-top: 10px;
            }
         h1 {
            font-family: "Georgia";
            font-size: 32px;
            margin-bottom: 30px;
            margin-top: 30px;
            }
         h4 {
            font-family: "Arial";
            margin-bottom: 20px;
            margin-top: 10px;
            }
         .whenPosted {
            font-family: "Arial";
            font-size: .9em;
            color: silver;
            }
         &lt;/style>
      &lt;div class="divThreadSuitePage">
         &lt;div class="row-fluid">
            &lt;div class="span2">
               &amp;nbsp;
               &lt;/div>
            &lt;div class="span8">
               &lt;h4>&lt;a href="http://scripting.com/">Home&lt;/a>&lt;/h4>
               &lt;h1>&lt;%headline%>&lt;/h1>
               &lt;div class="divStoriesOutline">
                  &lt;%outlinetext%>
                  &lt;/div>
               &lt;/div>
            &lt;div class="span2">
               &amp;nbsp;
               &lt;/div>
            &lt;/div>
         &lt;div class="scriptingFooter">
            &lt;br>&lt;hr size=1 noshade>&amp;copy; Copyright 1997-&lt;%year%> &lt;%ownerName%>. Last build: &lt;%now%>. "It's even worse than it appears." &lt;br />&lt;br />
            Built by &lt;%this%> on server "&lt;%machineName%>."&lt;br />&lt;br />
            &lt;a href="&lt;%urlRSS%>">&lt;img src="http://www.scripting.com/images/xml.gif" width="36" height="14" border="0" alt="RSS feed for &lt;%weblogName%>">&lt;/a>
            &lt;br>&lt;script language="JavaScript" type="text/javascript">&lt;!--
               var imageUrl = "http://counters.scripting.com/counters/count.gif";
               var imageTag = "&lt;img src=\"" + imageUrl + "?group=&lt;%countergroup%>&amp;referer=" + escape (document.referrer) + "\" height=\"1\" width=\"1\">";
               document.write (imageTag);
               -->&lt;/script>
            &lt;/div>
         &lt;/div>
      &lt;/body>
   &lt;/html>

</pre>