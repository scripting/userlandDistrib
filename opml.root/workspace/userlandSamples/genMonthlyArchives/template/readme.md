### workspace.userlandSamples.genMonthlyArchives.template
<pre>
<!DOCTYPE html>
<html>
   <head>
      <title><%title%></title>
      <meta http-equiv="Content-Type" content="text/html; charset=UTF-8"/> 
      <link rel="alternate" type="application/rss+xml" title="RSS" href="http://scripting.com/rss.xml" />
      <link rel="alternate" type="application/rss+xml" title="RSS/link-blog" href="http://links.scripting.com/rss.xml" />
      <meta name="generator" content="<%generatorProgramName%>">
      <meta name="description" content="<%metaDescription%>">
      
      <link href="http://static.scripting.com/github/bootstrap2/css/bootstrap.css" rel="stylesheet">
      <script src="http://static.smallpicture.com/bootstrap/js/jquery-1.9.1.min.js"></script>
      <script src="http://static.smallpicture.com/bootstrap/js/bootstrap.min.js"></script>
      <link rel="stylesheet" href="http://static.smallpicture.com/concord-assets/fontawesome/3.2.1/css/font-awesome.min.css">
      
      <script src="http://static.opml.org/scripts.js"></script>
      <link href="http://static.opml.org/styles.css" rel="stylesheet">
      
      <style>
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
         </style>
      </head>
   <body>
      <style>
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
         </style>
      <div class="divThreadSuitePage">
         <div class="row-fluid">
            <div class="span2">
               &nbsp;
               </div>
            <div class="span8">
               <h4><a href="http://scripting.com/">Home</a></h4>
               <h1><%headline%></h1>
               <div class="divStoriesOutline">
                  <%outlinetext%>
                  </div>
               </div>
            <div class="span2">
               &nbsp;
               </div>
            </div>
         <div class="scriptingFooter">
            <br><hr size=1 noshade>&copy; Copyright 1997-<%year%> <%ownerName%>. Last build: <%now%>. "It's even worse than it appears." <br /><br />
            Built by <%this%> on server "<%machineName%>."<br /><br />
            <a href="<%urlRSS%>"><img src="http://www.scripting.com/images/xml.gif" width="36" height="14" border="0" alt="RSS feed for <%weblogName%>"></a>
            <br><script language="JavaScript" type="text/javascript"><!--
               var imageUrl = "http://counters.scripting.com/counters/count.gif";
               var imageTag = "<img src=\"" + imageUrl + "?group=<%countergroup%>&referer=" + escape (document.referrer) + "\" height=\"1\" width=\"1\">";
               document.write (imageTag);
               --></script>
            </div>
         </div>
      </body>
   </html>

</pre>