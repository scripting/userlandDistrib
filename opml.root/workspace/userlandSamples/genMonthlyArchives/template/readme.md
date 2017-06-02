### workspace.userlandSamples.genMonthlyArchives.template
<pre>
&lt;!DOCTYPE html>
&lt;html>
   &lt;head>
      &lt;title>&lt;%title%>&lt;/title>
      &lt;meta http-equiv="Content-Type" content="text/html; charset=UTF-8"/> 
      &lt;link rel="alternate" type="application/rss+xml" title="RSS" href="http://scripting.com/rss.xml" />
      &lt;link rel="alternate" type="application/rss+xml" title="RSS/link-blog" href="http://links.scripting.com/rss.xml" />
      &lt;meta name="generator" content="<%generatorProgramName%>">
      &lt;meta name="description" content="<%metaDescription%>">
      
      &lt;link href="http://static.scripting.com/github/bootstrap2/css/bootstrap.css" rel="stylesheet">
      &lt;script src="http://static.smallpicture.com/bootstrap/js/jquery-1.9.1.min.js">&lt;/script>
      &lt;script src="http://static.smallpicture.com/bootstrap/js/bootstrap.min.js">&lt;/script>
      &lt;link rel="stylesheet" href="http://static.smallpicture.com/concord-assets/fontawesome/3.2.1/css/font-awesome.min.css">
      
      &lt;script src="http://static.opml.org/scripts.js">&lt;/script>
      &lt;link href="http://static.opml.org/styles.css" rel="stylesheet">
      
      &lt;style>
         body &#123;
            background-image: url ('http://static.scripting.com/images/lisa.jpg');
            }
         .divThreadSuitePage &#123;
            width: 80%;
            margin-left: 75px;
            margin-top: 50px;
            }
         .divThreadSuitePage span &#123;
            color: black;
            margin-left: 0;
            }
         .divLogo &#123;
            margin-top: 50px;
            }
         .divLinksTable a:link &#123;
            color: black;
            }
         .divLinksTable a:visited &#123;
            color: black;
            }
         .divTabTitles &#123;
            font-family: Arial;
            font-size: 15px;
            font-weight: bold;
            }
         .divLinksTable .linkWhat &#123;
            font-family: Georgia;
            font-size: 16px;
            line-height: 140%;
            vertical-align: top;
            }
         .divLinksTable .linkWhen &#123;
            font-family: Georgia;
            font-size: 16px;
            line-height: 140%;
            vertical-align: top;
            text-align: right;
            }
         .divLinksTable td &#123;
            border: none;
            }
         .divAbout &#123;
            text-align: left;
            }
         .spanWhenStory &#123;
            font-family: Arial;
            font-size: 14px;
            float: none;
            }
         .modal &#123;
            width: 770px;
            left: 40%;
            }
         a, a:link, a:visited &#123;
            color: #0069D6;
            }
         .aStoryTitle &#123;
            color: black;
            }
         .aStoryTitle:visited &#123;
            color: black;
            }
         .aStoryTitle:link &#123;
            color: black;
            }
         &lt;/style>
      &lt;/head>
   &lt;body>
      &lt;style>
         .aStoryTitle &#123;
            color: black;
            }
         .aStoryTitle:visited &#123;
            color: black;
            }
         .aStoryTitle:link &#123;
            color: black;
            }
         .divStoriesOutline &#123;
            margin-top: 10px;
            }
         h1 &#123;
            font-family: "Georgia";
            font-size: 32px;
            margin-bottom: 30px;
            margin-top: 30px;
            }
         h4 &#123;
            font-family: "Arial";
            margin-bottom: 20px;
            margin-top: 10px;
            }
         .whenPosted &#123;
            font-family: "Arial";
            font-size: .9em;
            color: silver;
            }
         &lt;/style>
      &lt;div class="divThreadSuitePage">
         &lt;div class="row-fluid">
            &lt;div class="span2">
               &nbsp;
               &lt;/div>
            &lt;div class="span8">
               &lt;h4>&lt;a href="http://scripting.com/">Home&lt;/a>&lt;/h4>
               &lt;h1>&lt;%headline%>&lt;/h1>
               &lt;div class="divStoriesOutline">
                  &lt;%outlinetext%>
                  &lt;/div>
               &lt;/div>
            &lt;div class="span2">
               &nbsp;
               &lt;/div>
            &lt;/div>
         &lt;div class="scriptingFooter">
            &lt;br>&lt;hr size=1 noshade>&copy; Copyright 1997-&lt;%year%> &lt;%ownerName%>. Last build: &lt;%now%>. "It's even worse than it appears." &lt;br />&lt;br />
            Built by &lt;%this%> on server "&lt;%machineName%>."&lt;br />&lt;br />
            &lt;a href="<%urlRSS%>">&lt;img src="http://www.scripting.com/images/xml.gif" width="36" height="14" border="0" alt="RSS feed for <%weblogName%>">&lt;/a>
            &lt;br>&lt;script language="JavaScript" type="text/javascript">&lt;!--
               var imageUrl = "http://counters.scripting.com/counters/count.gif";
               var imageTag = "<img src=\"" + imageUrl + "?group=<%countergroup%>&referer=" + escape (document.referrer) + "\" height=\"1\" width=\"1\">";
               document.write (imageTag);
               -->&lt;/script>
            &lt;/div>
         &lt;/div>
      &lt;/body>
   &lt;/html>

</pre>