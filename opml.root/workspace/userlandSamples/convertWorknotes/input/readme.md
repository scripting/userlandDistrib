### workspace.userlandSamples.convertWorknotes.input
<pre>
Small Picture worknotes
   July 2013
      Fargo 0.98
         <rules (blogSectionsRules)>
         Shift-click on Eye icon
            If you want to get the URL of a page without having to go to the page, shift-click on the Eye icon in the left margin. A dialog will appear that contains the URL. You can copy it to the clipboard there. Saves a couple of steps. ;-)
         New img attribute
            You could, before 0.98, <a href="http://dave.smallpict.com/2013/07/25/howToAddAnImageToAPost">include</a> an image in a Fargo blog post by adding HTML to the text of the post. 
            Now it's a bit simpler. 
               1. Get the URL of your image on the clipboard. If you don't have one handy, use <a href="http://static.scripting.com/larryKing/images/2013/07/25/phone.gif">this</a> one. 
               2. In Fargo, put the bar cursor on the headline that you want to attach the image to. The image will appear in the right margin of the post at the start of this headline. 
                  <i>Note: The img attribute must appear on a line within the post, not on the title headline of the post.</i>
               3. Click on the suitcase icon in the left margin. 
               4. Add a new attribute by clicking the + button. It's name is <i>img,</i> the value is the URL you have on the clipboard.
               5. Click OK.
            When you view the outline in a web page, the image will appear in the right margin. It will also appear in the RSS feed. 
         New settings, RSS features
            There are a couple of new entries on the <a href="http://static.scripting.com/larryKing/images/2013/07/29/newTwitterFacebookSettings.gif">You panel</a> in the Fargo Settings dialog, for your Twitter and Facebook usernames. 
            If you enter values for these entries, we will generate new elements in your RSS feeds that contain this information. 
            This is an <a href="http://reboot.reallysimplesyndication.com/2013/07/28/implementingSomeNewRssIdeasInFargo">experiment</a>. We're adding these features in the hope that other developers will use the information to add features to their products. Then we'll add some more stuff, and others will too, and hopefully RSS will improve and become more useful. It's been quite a while since people worked together on improving RSS. 
         Viewing commented pages
            When you click the eye icon to view a page, we now check to see if it's commented. If it is, instead of taking you to the page, which will show up 404 not found, we ask if you'd like to uncomment it. Then you can click the eye icon again, after waiting a few seconds for the outline to save, and for the CMS to notice the change. 
         Creating commented headlines with + icon
            In previous versions the headlines would be commented, but they weren't visibly commented. Now they are. 
         Perspective
            As we're getting close to 1.0, I wanted to offer a few <a href="http://dave.smallpict.com/2013/07/29/moreMondayMorningFargoFeatures">observations</a> on where we're at and how it's going. ;-)
      Fargo 0.97
         <rules (blogSectionsRules)>
         Home icon in left sidebar
            Suppose you're editing a named outline and you want to quickly view the home page of the site. There's actually no UI for in prior to 0.97. You have to type the URL in the browser's address bar. This won't do! :-)
            Now the Home icon shows up in the left sidebar whenever the eye icon does. 
            Click on it to view the home page of the side in a new tab/window.
         New command in Outliner menu
            A new Outliner menu command toggles between Render and Non-render mode. The single keystroke is Cmd-`.
            In render mode HTML entities are seen as they would be seen in a web page rendering of the content. This is possible because Fargo runs in the browser, which of course, naturally renders things as HTML. 
            In non-render mode, the entities appear unrendered. So in image would show up in non-render mode as an &lt;img> tag. 
            This command worked in earlier versions of Fargo and Little Outliner, but it wasn't present in a menu, so was harder to discover. 
            A <a href="http://static.scripting.com/larryKing/images/2013/07/28/renderMode.gif">screen shot</a> of an outline in render mode, and a <a href="http://static.scripting.com/larryKing/images/2013/07/28/nonRenderMode.gif">screen shot</a> of the same outline in non-render mode.
         File menu changes
            Removed two commands from the File menu, View in Reader and Save as Markdown. 
            Added these back as new scripting verbs, file.viewCurrentFileInReader () and file.saveCurrentFileAsMarkdown ().
            If you were depending on these commands, you can add them back menubar.opml.
            The reason for removing them is that there are now better ways to read content created in Fargo, using the web content management system. Having these commands in the menus were confusing for some users.
            See: <a href="http://scripting.smallpict.com/2013/07/24/introToFargoScripting">Intro to Fargo Scripting</a>.
      Fargo 0.94
         In previous versions, if you had a page with <i>type</i> or <i>method</i> equal to markdown, it would render fine on the website, but its markdown nature would be ignored by the feed generator. That's now fixed.
         <a href="http://dave.smallpict.com/2013/07/22/fargo094MarkdownInFeeds">This post</a>, as an example, has a <i>method</i> attribute of markdown, and it should appear with proper markup in the <a href="http://dave.smallpict.com/rss.xml">feed</a>.
      Fargo 0.93
         Before this release, the + icon required that the calendar be at the top level of the outline. Now, the calendar can be anywhere in the outline.
         Not a whole lot more to say about it. ;-)
      Fargo 0.92
         One small feature, a nice thing to have, not crucial.
         If you put an <i>insertedNodeType</i> attribute on your calendar, then when you click the + in Fargo, that type will override the type you set in the Insert settings panel.
         You could also put the attribute on a month or a day. But it probably makes the most sense to put it on the year. You will have to remember to copy it to 2014 at the beginning of the next year. 
         This allows you to maintain several blogs which may not want to use the same type for posts.
         <a href="http://static.scripting.com/larryKing/images/2013/07/14/insertedNodeType.gif">Screen shot</a>.
      Fargo 0.91
         Rearranged the right sidebar.
         Removed links to docs that were already in the Docs menu.
         Moved the Save button up, and the Message of the Day down.
         Fargo will work better on shorter screens as a result.
      Fargo 0.90
         <rules (blogSectionsRules)>
         The equivalent of draft mode
            New setting in the Insert panel, allows you to tell Fargo to create new items with the + icon as comments. Comments will not be rendered by Trex, and will not appear in your RSS feed. This is useful if you're creating posts and don't want them to be viewed until they're finished. 
            The workflow:
               1. Click + to create a new post.
               2. Edit your post until you're happy with it.
               3. Put the cursor on the top head in the post.
               4. Choose <i>Toggle Comment </i>in the Outline menu.
               When the outline is next saved the new item will then appear on the site, and will be included in the RSS feed. 
            <a href="http://static.scripting.com/larryKing/images/2013/07/12/newSetting.gif">Screen shot</a>.
         Redundant setting
            Removed the Autosave pref from the Advanced panel in Settings. There is a panel just for Autosave, so the setting was redundant. 
      Fargo 0.89 -- Podcasting
         Our feeds now support enclosures, and thus enable podcasting with Fargo. 
         Here's how you do it.
         1. Record your podcast as an MP3, Quicktime movie, whatever you like.
         2. Upload it to the normal place. Copy the URL to the clipboard.
         3. Create a <a href="http://dave.smallpict.com/2013/06/29/howToWriteABlogPostWithFargo">new post</a>.
         4. Put the cursor on the top headline, click the suitcase icon in the left margin.
         5. Add a new attribute called <i>enclosure,</i> its value is the URL on the clipboard.
         6. Click Save.
         If the URL points to something that Fargo is able to access, it will add enclosureLength and enclosureType attributes to the headline, automatically, and will generate an enclosure element on the RSS feed item. All of this will happen without you having to do anything.
         Here's a <a href="http://static.scripting.com/larryKing/images/2013/07/02/atts.gif">screen shot</a> of the attributes on my test podcast <a href="http://dave.smallpict.com/2013/07/02/howPodcastsWorkInFargo">post</a>. 
      Fargo 0.87
         Switched from <a href="http://fortawesome.github.io/Font-Awesome/icons/">Font Awesome</a> 3.1 to 3.2.
         I took <a href="http://dave.smallpict.com/2013/07/01/testingTheNewIconChooser">notes</a> on the work on my Fargo blog.
   June 2013
      Fargo 0.86
         <rules (blogSectionsRules)>
         New entries in the Docs menu
            You can get to the Presentation and Blog post howtos from the Docs menu.
         The eye icon is a little smarter
            Suppose you're editing in a named outline, inside a presentation or a blog post. The cursor is on one of the subs, not on the top headline. 
            Previously, if you clicked on the eye icon, it would erroneously take you to a rendering of the headline you are on. 
            Now it shows you the post or presentation. 
            Saves you from having to move the cursor just to view the document. 
         Fixed a bug in encoding RSS descriptions
            The text of the description element in each item was double-encoded, so when you viewed it in a feed reader, you'd see the markup instead of the effects of the markup. 
         Excessive saving bug
            In certain circumstances Fargo would save an outline on each change as many as 20 times. You would experience this as a sluggishness in the Save button in the right margin. Dropbox would experience an excessive amount of traffic for each save. 
            The problem was that we were setting the &lt;link> element in the OPML &lt;head> section every time we saved the RSS. This would mark the outline as changed, which would force another save, marking the outline dirty, and around the loop we go. Since the saving happens asynchronously, eventually there would be a moment when the outline was not changed and it would stop the cascade. Now that it's fixed you get one save per change, and one build of the RSS feed. Whew! :-)
         The contents of the right sidebar is fixed
            It doesn't scroll as you navigate down through the outline. 
            This is as it always should have been. 
      Fargo 0.85
         We've transitioned from running a community feed, to <a href="http://worknotes.smallpicture.com/june2013/fargo081">using RSS</a> and hooking into the wealth of new RSS-consuming applications. 
         We learned a lot from the experience with the community feed, but now it's time to complete the transition, so we removed the icon for the community feed in this release, and updated the Fargo docs accordingly.
         Also, there's a <a href="http://dave.smallpict.com/2013/06/28/howToCreateAPresentationInFargo">new howto</a> that shows how to create a presentation with Fargo.
      Fargo 0.84
         The <i>name</i> attribute gives us a canonical way to refer to a headline that doesn't vary with its text. Prior to version 0.84 Fargo wasn't generating them, now it is.
         When you click on the Eye icon in the left margin, we take the text of the headline, remove blanks and some special characters and innerCase the text to form the name attribute.
         Net-net: Links won't break if you change the text of a headline. 
      Fargo 0.82 loves RSS more
         Jeffrey Kishner <a href="https://groups.google.com/d/msg/smallpicture-web/Qg8ondVA60g/dyv07_v-xgoJ">points</a> out that &lt;rules> were being included in the RSS description element of Fargo's new feeds. That's not cool! Rules are meant to guide the rendering on Trex, but won't mean anything to a RSS aggregator. So in this release we take the rules out as we send the text out to RSS. 
         The hits keep coming! :-)
      Fargo 0.81 loves RSS
         You can now use <a href="http://fargo.io/">Fargo</a> to post items to an RSS feed.
         Every outline has a feed, but the feed is only public for <a href="http://dave.smallpict.com/2013/06/18/howToCreateANamedOutline">named</a> outlines.
         The feeds are created in a new sub-folder of the Fargo folder called <i>rss.</i>
         You can access the feed through the named outline at /rss.xml. 
         For example, my feed is at <a href="http://dave.smallpict.com/rss.xml">http://dave.smallpict.com/rss.xml</a>. 
         To add an item to the feed, <a href="http://static.scripting.com/larryKing/images/2013/06/20/plusIcon.gif">click</a> the + icon in the left margin. The main headline is the title of the item. The subtext forms the RSS item description. 
         If you don't want the + icon to create feed items, you can turn this feature off in the <i>Insert</i> panel of Settings. <a href="http://static.scripting.com/larryKing/images/2013/06/20/insertPanelFargo.gif">Screen shot</a>.
         You can cause any headline to be part of the feed by adding an <i>isFeedItem</i> attribute with the value true.
         PS: My feed is <a href="http://feedvalidator.org/check.cgi?url=http%3A%2F%2Fdave.smallpict.com%2Frss.xml">valid</a>. :-)
      Fix for missing eye icon
         Some people report named outlines for which the eye icon does not appear. We have a fix that works in some situations.
         <rules (blogSectionsRules)>
         The fix
            1. Open the outline in Fargo.
            2. Make it the current tab.
            3. Choose <i>Name outline</i> in the File menu. 
            4. Enter the name of the outline. Ignore the message that says the name is taken.
            5. Click OK.
         What should happen
            1. You should get a confirmation dialog saying the name has been assigned.
            2. When you edit the outline you should see the eye icon.
      Fargo 0.80
         With this release Fargo is coupled with a new content management system called Trex, which was also developed at Small Picture. This means that you can publish documents and presentations from Fargo. And it's easy! :-)
         <rules (blogSectionsRules)>
         How to publish
            1. Open a <a href="http://smallpicture.com/fargoDocs.html#names">named</a> outline. 
            2. Create a new headline in that outline, something like <i>My first story.</i>
            3. Write a paragraph or two indented beneath the headline. 
            4. Put the bar cursor on the top headline, and click the suitcase icon in the left margin to edit attributes.
            5. Add a <i>type</i> attribute, with the value <i>outline.</i> Click OK.
            6. Click the eye icon in the left margin. 
            You should see a simple lovely page with your words on it!
         Viewing an outline
            If you enter paragraphs under a headline you get something that looks like a story, but if you enter indented headlines, you get something that looks like an outline. 
            Here's an <a href="http://helloworld.smallpict.com/example8">example</a> that looks like an outline.
            And <a href="http://helloworld.smallpict.com/essays/june2013/theQuietWarInTech">here's one</a> that looks like an essay.
         Make a presentation
            1. Open a <a href="http://smallpicture.com/fargoDocs.html#names">named</a> outline. 
            2. Enter a main headline, something like My first presentation.
            3. Enter a series of slide titles underneath, Slide 1, Slide 2, etc. (Or be creative!)
            4. Under each slide title, add a few bullet points.
            5. Put the cursor on the main headline, and click the suitcase icon to edit attributes.
            6. Add a type attribute, with the value presentation. Click OK.
            7. Click the eye icon in the left margin. 
            Here's an example <a href="http://helloworld.smallpict.com/example10">presentation</a>. This is what it <a href="http://static.scripting.com/larryKing/images/2013/06/08/slideOutline.gif">looks like</a> as it's being edited in Fargo, and the <a href="http://helloworld.smallpict.com/example10?format=opml">OPML</a> for the presentation.
         Profile change
            The special headline with the text <i>profile</i> is still displayed when we display the top level of your website, but instead of using Reader to display the outline, we use the content management system.
            For example, here's my <a href="http://dave.smallpict.com/">profile</a> outline. 
            Because the headline must be exactly <i>profile</i> in order for it to be recognized, you'll need a way to specify the text that's displayed in place of the headline text when the page is rendered. You can do this with a #text directive just below the headline. 
            Here's a <a href="http://static.scripting.com/larryKing/images/2013/06/18/textDirective.gif">screen shot</a> that illustrates.
         Where we go from here
            We want to make a great environment where writers, designers and programmers work together. 
            There's a lot more that Trex can do. We plan to provide simple Fargo-based interfaces for much of it. But we're going to show the features slowly, one step at a time.
         Lifting the hood
            If you're a web developer or designer, you may want to dive right into Trex, if so here are <a href="http://trexdocs.smallpicture.com/">the docs</a>. But we want to emphasize that if you're a writer and non-technical, you don't need to understand what's in the engine. It's our job to make this simple for you, a job that we take very seriously! ;-)
         Participate
            When you write something new feel free to post a link in a comment here. :-)
            We want to see how you're using the new stuff. 
            Questions and comments are most welcome. 
      Fargo 0.78
         A few touch-ups for the + icon.
         1. When we generate the top level headline for the year, instead of setting the <i>type</i> to calendar, we set the <i>icon</i> to calendar.
         2. If there's already a type of calendar on the year headline, we remove it. Any other type, we leave alone. 
         3. When creating a headline, the type goes on the headline we create, not on its parent. This way when we generate a web index for a calendar structure, the document boundary will be where users expect it. 
      Fargo 0.77
         <rules (blogSectionsRules)>
         More improvements to the + icon
            A new Settings panel, Insert, lets you change the level of insertion and determines the type of headline it creates.
            <a href="http://static.scripting.com/larryKing/images/2013/06/06/newSettingsPanel.gif">Screen shot</a> of the new panel.
            If you choose to create one note per day, then when you click on the + icon, Fargo will navigate to the headline for today, creating it if it doesn't exist. It creates a new empty headline just below, enters text mode, so you can start typing.
            If you don't choose one note per day, we create a new entry with the current time every time you click the + icon. This is the way it worked before version 0.77. 
            We added this option because we felt that for some people one note per day was enough. 
            You can also enter the name of a type that will be automatically assigned to each new item it creates. If you're in one-note-per-day mode, the type will be put on each day. Otherwise the type will be attatched to each time entry. 
            The default value of this setting is <i>outline.</i> If you don't have a strong reason to change it, we recommend that you don't. 
            This feature is here to connect with the new server software we're working on. :-)
      Fargo 0.75
         This release improves the big + icon at the top of the left sidebar.
         Recall that it adds a new headline to a calendar-structured outline. At the top level is the year, below that the month, then the day, then a time stamp, and then a place to add your notes. Here's a <a href="http://static.scripting.com/larryKing/images/2013/06/03/calendar.gif">screen shot</a>.
         If you use the + icon to add to your outline you'll get a neat structure organized in reverse chronologic order, much like a weblog.
         <rules (blogSectionsRules)>
         What's new
            1. You can now place the calendar anywhere at the top level of your outline. It no longer has to be the first item, but it must be at the top level.
            2. The first time you add an item to the calendar with 0.75, we'll add a type attribute to the year with the value <i>calendar,</i> but only if it doesn't already have a type. 
            3. The icon for the calendar type is, of course, a calendar. ;-)
         How to try it out
            To try it out, if you have a calendar in one of your outlines, move it, and try adding an item. It should find the calendar in its new location.
      Fargo 0.74
         First a little story...
         <rules (blogSectionsRules)>
         I was watching the game last night
            <img src="http://static.scripting.com/larryKing/images/2013/06/02/clyde.gif" width="161" height="258" border="0" style="float: right; padding-left: 25px; padding-bottom: 10px; padding-top: 10px; padding-right: 15px;" alt="A picture named clyde.gif">There was an incredible <a href="http://www.nytimes.com/2013/06/02/sports/basketball/heat-falter-fume-and-fall.html?pagewanted=all">basketball game</a> on last night. As you may know from reading Scripting News, I have been enthusiastically following  basketball all season, and now we're in the semi-finals, and the Indiana-Miami series has been incredible. Last night's game was probably the best game all season. 
            At the same time, the community feed is going through what I think of as growing pains. I've been developing community software for a long time, going back to the early 80s, and I've started lots of these things. Some of them grow up to be huge, like blogging and podcasting, and some don't. I learn a lot either way. But I don't need to learn things three or four times. Or more! One would hope. :-)
            The community feed, as it was set up, is exactly the same as an unmoderated mail list or discussion group. The fact that we're all using an outliner to write for it doesn't matter. It goes in a predictable direction. There's a sense that this is the center of everything, the place where decisions are made, the authority of everything. It isn't that. But it <i>feels</i> that way. 
            Over time that tends to push away the people we want to hear from most, the people who use our product but for their own work. They're not trying to do our work, which is to develop and enhance an outliner product, Fargo. But over time that's where these things tend to go. This community is growing very quickly, so the focus has shifted a lot sooner than I thought it would. I think to some extent, btw, that I am responsible for this rapid shift. My presence there serves as a lightning rod for people to give me feedback, and I even ask for it. I shouldn't, and I wll try not to in the future. I want to participate less, and get out of the way and let the users speak.
            Anyway, during the game, a couple of well-intentioned outlines were posted that said "Pay attention to me now or else!" But I didn't want to do that, because I was watching a game, and I needed some time to think about what to do next, and I honestly I had had a few beers by then, and the last thing I wanted to do is get involved in the community feed. So, this is what I did:
               1. I set the <i>enabled</i> flag for the group to false.
               2. I went back to watching the game.
               3. I thought some more about where I want to go with this.
         The Community Feed is now moderated
            That means that someone from Small Picture will read everything that's posted to the feed. If it's primarily feature suggestions about one of our products, we'll read it and it will influence our product decisions. Can't say we'll do everything people ask us to do, we can't (sometimes the requests are contradictory), but we are listening. 
            If it's a personal comment, we'll listen to that too, but hopefully it won't influence us very much. (That was a joke.)
            If it's an ad for a product, esp from a competitor, we will read it, be influenced by it too. However none of these will be posted. 
            You are of course free to post these items anywhere else you like. 
            It's possible that moderation on this feed will help boot up an active widespread community of outliners publishing to the web. That's our hope! We're working on tools to make that easy and fun and powerful. It's certainly not unprecedented that lots of good can come from distributing the flow of ideas wide and far. That's what blogging is, after all. 
            Other than these items, unless people come up with other ideas, everything else will go through. 
         Feature changes in 0.74
            There's not very much new in the product itself. 
            A few changes needed to be made to support moderation. 
            And I still have more work to do on the back-end, so you can post items to the feed now, but they won't appear until the moderation feature is finished, server-side.
            Thanks for your help in this, it really has been and continues to be a great learning experience for us! :-)
   May 2013
      Fargo 0.75
      Fargo 0.74
      Fargo 0.72
         We did some work today on the community feed server.
         If you want to post to the feed, you need to reload Fargo. 
         Be sure you're running 0.72.
      Tech feature -- startup code
         In Fargo 0.71 there's a new Settings panel called Code, with a place to enter JavaScript that runs when Fargo starts up. <a href="http://static.scripting.com/larryKing/images/2013/05/29/codePanel.gif">Screen shot</a>.
         Note of caution: If you're a programmer, be careful. If you're not a programmer, be much more careful. This is potentially a very powerful feature which means it is also potentially a very <i>dangerous</i> feature. 
         Be sure you know what the code you're entering does, and that you trust the person who gave it to you. When in doubt, don't. 
         With that caveat... we look forward to seeing what people do with this feature. ;-)
      Fargo 0.71
         Lots of little chotchkas in this release.
         <rules (blogSectionsRules)>
         Heart menu
            We use a lot of toolkits provided by some very generous developers and designers. The heart menu is where we thank them for their generosity. <a href="http://static.scripting.com/larryKing/images/2013/05/29/heartMenu.gif">Screen shot</a>.
            It's divided into three sections:
               1. Tools that we use in the workstation software, Fargo and Little Outliner,
               2. Tools that we use in our server software,
               3. Technologies we use everywhere. 
         Suitcase icon
            There's a new icon in the left sidebar, the suitcase. <a href="http://static.scripting.com/larryKing/images/2013/05/29/suitcase.gif">Screen shot</a>.
            When you click it, the Edit Attributes dialog opens.
            By popular demand, from the best users in the universe! :-)
         Save button hidden
            The Save button which was new in <a href="http://worknotes.smallpicture.com/may2013/fargo065">Fargo 0.65</a> would be visible even when viewing read-only outlines. 
            Now it is only visible on outlines that you can edit.
         Fix in <i>Set Name</i> command
            If you try to set the name of a new outline that did not have a title, before we assign the name, we set the title to the name you chose.
            A few users set the name of the first outline they created in their first use of Fargo. When the outline got a title, we automatically change the name of the file from untitled.opml to title.opml. This would break their named outline.
      Tech feature -- cssTextClass
         In 0.69, we added support for a new attribute, cssTextClass. If present, when we render the headline in Fargo, we add the class to the text. So this allows you to control the styling of text in Fargo on a per-headline basis. 
         <rules (blogSectionsRules)>
         An example
            Using the CSS setting, I <a href="http://static.scripting.com/larryKing/images/2013/05/23/cssSettings.gif">added</a> this class:
               .greenText {
                  color: green !important;
                  }
            Then I set a <a href="http://static.scripting.com/larryKing/images/2013/05/23/greentextatt.gif">cssTextClass attribute</a> on a headline to greenText. 
            As you might imagine, the text is now displayed in green when I view it in Fargo.
            BTW, it didn't work until I added the !important bit to the declaration. If at first you try a style and it doesn't seem to take, try adding this bit. I don't really <a href="http://stackoverflow.com/questions/9245353/what-does-important-in-css-mean">understand</a> what it does, but it seems to help. ;-)
         Why separate worknote?
            I'm trying out a new idea, writing up a technical feature in a separate worknote. I don't want all users to feel they need to understand this. We added the feature for more technical users, to give them a way to try some ideas out with Fargo.
      Fargo 0.70 -- Strikethrough
         There's a new strikethrough icon in the left margin. <a href="http://static.scripting.com/larryKing/images/2013/05/23/strikethroughFargo.gif">Screen shot</a>.
         It marks the selected text with a <del>strikethrough</del>. 
         If you're in structure mode when you click the icon, the whole headline is changed.
         Doing it again "unstrikes" the text (if that's a word). 
      Fargo 0.69
         <rules (blogSectionsRules)>
         Phone-friendly
            Previous versions of Fargo did not work at all on phone-size screens. This version works a lot better. As with the tablet-size version of Fargo, we're going to iterate over this, so it will work better over time. If you have suggestions, please post comments here. 
         Comments in WordPress blog posts
            You can now add comments to your blog posts, and they will not appear in the post on the WordPress server.
         Custom icons are now grayed
            Fargo now grays custom icons the same way it grays wedges. 
            If an item is collapsed and has subs the icon is displayed in black. 
            Otherwise it's gray.
         Fargo docs updated
            We added the big features from the Worknotes site to the <a href="http://smallpicture.com/fargoDocs.html">Fargo docs</a>. 
      Fargo 0.67
         You can now use the cursor keys in watched outlines in read-only mode.
      Fargo 0.66 -- Bookmarks
         <rules (blogSectionsRules)>
         Watched outlines
            A bit of terminology.
            There are two kinds of outlines in Fargo.
               1. Editable outlines.
               2. Watched outlines.
            Editable outlines live in the Fargo sub-folder of your Dropbox Apps folder. Open them with the File/Open command. 
            Watched outlines live elsewhere. You can open them in read-only mode via the Open By URL command, also in the File menu. When they update, your view of them updates. Until now you had to keep the URLs of these outlines somewhere else, or leave the tabs open all the time. 
         Bookmarks menu
            The Bookmarks menu is for watched outlines.
            It behaves more or less like the Bookmarks menu in a web browser. When you have opened an outline that you want to remember, choose Add Bookmark from the Bookmarks menu. A dialog appears asking what you want to call the bookmark. We suggest the title of the outline (or the long title if it has one).
            When you choose Edit Bookmarks, a new tab opens with the contents of the menu in an outline. You can edit the bookmarks there. The menu  contains link nodes. You can change the text, or the URLs associated with the items, and reorganize the menu in any way you like. 
            Only the top level headlines are included in the Bookmarks menu.
         Changes in the Icon Chooser
            The OK button changes to Close, to more accurately indicate what it does. 
            We added a link to the wonderful <a href="http://fortawesome.github.io/Font-Awesome/">Font Awesome</a> github repo in the dialog.
            We <a href="http://threads2.scripting.com/2013/may/iconChooserDialog">open sourced</a> our dialog, so other people may include the Icon Chooser in their apps. It's licensed under the GPL.
      Fargo 0.65 -- Icon Chooser + Save Button
         <rules (blogSectionsRules)>
         Icon Chooser dialog
            There's a new <i>Choose Icon</i> command in the Outliner menu. It brings up a dialog with several tabs. In each tab are 35 awesome icons. <a href="http://static.scripting.com/larryKing/images/2013/05/20/chooseIconDialogScreen.gif">Screen shot</a>.
            Click on one of the icons to set the icon of the bar cursor headline. 
            Click Close to dismiss the dialog without setting an icon. 
         Save Button
            There's a new Save button in the right sidebar.
            It has two states:
               1. The outline in the active tab has changes. In this case the button says SAVE and is enabled.
               2. The outline has not been changed, then the button says SAVED and is disabled.
            This way you can see at a glance if your outline needs to be saved, whether or not you have AutoSave turned on. 
            We hope, with this change, to prevent some data loss for users.
      Fargo 0.64
         <rules (blogSectionsRules)>
         New commands
            There are two new commands in <a href="http://fargo.io/">Fargo's</a> Outliner menu. 
               <b>Add Include</b> prompts for a URL and turns the bar cursor headline into an <i>include</i> node. The URL must point to an OPML file, though the command does not verify this. 
               <b>Add Feed</b> turns the bar cursor headline into a node of type <i>rss.</i> A collection of these nodes forms a standard OPML <a href="http://dev.opml.org/spec2.html#subscriptionLists">subscription list</a>. The URL should point to a feed, in RSS or Atom formats. Again, no attempt is made by Fargo to verify the format of the file being pointed to.
         Clipboard
            The internal clipboard now remembers outline attributes. So when you copy within an outline, or between two outlines in different tabs, the attributes are now preserved.
         Troubleshooting link
            Added a <a href="http://smallpicture.com/fargoDocs.html#tips">Troubleshooting</a> link in the right sidebar and in the Docs menu.
      Fargo 0.63 -- New icons
         This release adds <a href="http://fortawesome.github.io/Font-Awesome/icons/">54 new icons</a> from Font Awesome 3.1.1 to Fargo.
         Icons can be added to any headline by going to Outliner > Edit Attributes and adding a new attribute named "icon" with the value being the name of the icon you'd like to use.  The name of the icon should be the name listed on the Font Awesome website without the "icon-" prefix.  So if you wanted to use the new fire extinguisher icon you would just enter in "fire-extinguisher" as the name.
         Kyle
      Fargo 0.62 -- Open by URL
         One new command in this release, <i>Open by URL,</i> in the File menu in Fargo.
         It prompts for the address of an OPML file. The file opens in a new read-only tab. If the file changes, the tab display updates to reflect the change. It's like having a Reader tab inside Fargo. With this you can cook your own group of "Instant Outline" collaborators.
         You could, for example, watch the updates to the Small Picture users' directory, which is an <a href="http://smallpicture.com/userDirectory.opml">OPML file</a>, using this command. 
         It's a deceptively small feature. It opens up a pretty large new set of applications for Fargo. :-)
         BTW, here's a <a href="http://bhc3.com/2009/01/16/before-there-was-twitter-there-was-dave-winers-instant-outliner/">great piece</a> about Instant Outlining, written by Hutch Carpenter in 2009. That's what the Open by URL command enables. This has been an elusive goal for many years. We had I/O running at UserLand in 2001 when we were developing Radio. That's why we were able to get such an ambitious project done with a team that was spread out geographically. With Fargo, it seems we may have I/O in a package that can be used by a lot more people. 
      Fargo 0.61 -- Identity
         In this release we connect identity and outlines. This is someting we've been working towards from the day we started Small Picture. Actually quite a bit before that, if you've been following my writing on Scripting News.
         The idea is simple. Every outline can have a name. The name is much shorter and easier to remember than the URL assigned to it by Dropbox. 
         For example: <a href="http://dave.smallpict.com/">dave.smallpict.com</a>. And when you want to view this outline in Fargo, you can leave off the domain and just ask it to open dave. When you do that you'll be viewing the public embodiment of me, the whole thing. 
         This is the stuff I want to show you. The private stuff doesn't get named. 
         You can think of it as the outline equivalent of a website. But it's bigger than a website, because it can <i>contain</i> websites. That's part of a future step we're going to take, which is already pretty far along (in its third generation, btw).
         Those are the high-level ideas. I'll be writing more about that on my blog. Now to the practical.
         <rules (blogSectionsRules)>
         Naming an outline
            You can name any outline anything you want, as long as:
               1. It hasn't already been named.
               2. The name you want to use is available.
               3. The name is 4 characters or more.
               4. It contains only alphabetic and numeric characters, or hyphens.
            To give an outline a name, click on its tab and choose <i>Name outline</i> in the File menu. A dialog appears. <a href="http://static.scripting.com/larryKing/images/2013/05/14/choosePublicName.gif">Screen shot</a>.
            Enter a name. As you're typing, you're given an indication whether the name is available. 
            When you're ready click OK. Be sure this is the name you want to use because it can't be changed or deleted. 
         Be kind
            Right now there is no charge to create a name because these are early days, and you're helping us debug a new feature.
            So just name one or two outlines. If people abuse the feature, we'll delete the names and put a price on each. 
         Making a name equal to you
            You can name any outline, but only one outline is you. 
            To say which one that is, choose Settings from the system menu (upper-right corner of the window). In the first panel, named You, there's a new place to enter your Profile URL. <a href="http://static.scripting.com/larryKing/images/2013/05/14/youPanel.gif">Screen shot</a>. This should be the address of your outline. If the name you chose is "mitch" then your profile URL is: http://mitch.smallpict.com/.
            Note: If you want to use another system for your profile you can point to that page from this spot. But other features may depend on it being hosted by us, or fully compatible with our implementation. 
         Editing your profile
            You will notice that if you go to your profile page now, it's blank. 
            If you edit your outline and add a top-level section called profile -- the contents of that page will display when you go there. 
            <a href="http://static.scripting.com/larryKing/images/2013/05/14/profileSetup.gif">Screen shot</a>.
         Using the URL
            Your profile is automatically pointed to in the Community Feed when you post something new there. 
            That way people who want to know who you are when reading something you wrote will be able to do that easily, by clicking on the eye icon that appears in the left margin when the highlight your name with the bar cursor.
            You can also include your outline within other outlines, or other people's outlines. 
         Opening a named outline
            You may have noticed that the Community Feed is a special kind of outline in Fargo. When it's open in a tab it's called a "watched" outline. That means that whenever it updates the icon in front of its name changes to a lightning bolt, and when you click on it, you'll see the changed text. 
            Named outlines work the same way. If you choose Open By Name in the file menu, and enter the name of someone else's outline, you will be able to watch changes in that outline. This works extremely well if you're collaborating with other people and want to keep up to date. We call this Instant Outlining. 
      Fargo 0.60 -- Long titles
         There are places where you need a long title for an outline, and places where you need a short one. A short title is good for a tab. But in the Reader app, you want a longer more descriptive title. This really showed up when we were viewing the Community Feed in Reader. The title at the top of the page said "Feed." That looked like a bug to me, even though the software was fully functional.
         So, primarily to make Reader work better, we changed the Set Title command in the File menu. It now gives you a way of setting two titles, one short and one long. You can set a description for the outline. 
         Here's a <a href="http://static.scripting.com/larryKing/images/2013/05/10/settitles.gif">screen shot</a> of the new dialog.
         There's a new version of Reader to go with these changes, version 0.11.
         Here's an <a href="http://reader.smallpicture.com/?opmlurl=http://smallpicture.com/feed.opml">example </a>, Reader displaying the Community Feed, which now has a long title and a description.
      Fargo 0.59 -- Community Feed
         The Community Feed is an outline that any user of Fargo can post to when there's an idea they want to share with people who are listening. 
         Who is listening? What does it mean? How will we use it? 
         These are, at this time, unknowns. :-)
         <rules (blogSectionsRules)>
         Posting to the feed
            When you have an item you want to share with the community, put the cursor on it, and click in the new Feed icon in the icon chain. 
            A confirmation dialog appears, making sure you want to add the item to the community feed. 
            When it's done, you'll hear a beep sound. 
         Editing an item
            If you edit your item and want to update it in the feed, put the cursor on the top headline and click the Feed icon again. It automatically updates the Community Feed with your changes. No confirmation this time. When it's done, it beeps. 
         Watching the feed
            There's a new command in the Docs menu, probably just a temporary home, called Community Feed. 
            When you choose it a new tab opens displaying the contents of the Community Feed. 
            When it updates its icon will change to a lightning bolt. When you select the tab, the icon changes to what it was before. That's how you can tell that it updated.
         Video demo
            Here's the video on YouTube. 
            <a href="http://youtu.be/g85e5lB6pqw">http://youtu.be/g85e5lB6pqw</a>
         Where's the feed?
            It's just an OPML file, of course.
            <a href="http://smallpicture.com/feed.opml">http://smallpicture.com/feed.opml</a>
      Fargo 0.58
         Chris Wolverton wrote a <a href="http://www.gravitropic.net/2013/05/a-week-with-the-fargo-outliner/">blog post</a> today listing some things we want to fix in <a href="http://fargo.io/">Fargo</a>. The one that was bugging me was the inconsistent implementation of Return in our dialogs. In some places it dismissed the dialog, but in most dialogs, it did nothing. I fixed most if not all of the dialogs in Fargo, they all handle Return properly. If I missed any please post a comment here, with steps to reproduce. 
         Dave
      Fargo 0.57
         There's a new checkbox setting for WordPress blog posts, that allows you to pass the text of each post through Markdown before it's sent to WordPress. 
         <a href="http://static.scripting.com/larryKing/images/2013/05/04/markdownWordPressPref.gif">Screen shot</a>.
      Fargo 0.55, 0.56 -- Markdown
         <a href="http://fargo.io/">Fargo</a> now has a built-in <a href="http://daringfireball.net/projects/markdown/">Markdown</a> processor. 
         We're using the open source <a href="https://code.google.com/p/pagedown/">Pagedown</a> library. 
         The Fargo docs have been updated to include a new <a href="http://smallpicture.com/fargoDocs.html#markdown">section</a> on Markdown. 
         Here's an <a href="http://static.smallpicture.com/dave/markdown/example1.opml">example</a> of an outline, and the Markdown-rendered <a href="http://static.smallpicture.com/dave/markdown/example1.html">version</a> of the outline. 
         We generate the text from the outline and pass it through Pagedown, and save what it returns to the #markdown sub-folder of the Fargo folder. 
         <rules (blogSectionsRules)>
         Two returns for every headline (0.56)
            Based on feedback from Jason Gilman, I changed the way we generate text before passing it to Markdown. Previously we added a single newline character at the end of each line. Now we generate two carriage return characters. That way each headline generates a new paragraph in Markdown. 
            This kind of feedback, especially early in the process, is very important. We can change things now because there is no installed base of documents that use Markdown. Later it will be harder to make a change because of potential breakage. 
            This was the only change in 0.56.
         Consider it experimental
            We've tested the processor and it seems to work, but neither Kyle or myself are experts on Markdown. 
            Markdown support was a much listed feature request, so we know that there are plenty of Fargo users who will know what to do with this. However the conventions on how to use outline structure are not at well-understood. It's all very new as far as we know. 
            If there are problems, please report them in a comment here. Also if you feel we should be generating the text differently, post a comment. It's just the beginning of outliners and Markdown, so we may have to make changes in how this works. 
            We're also planning on implementing Markdown in Trex, the server-side CMS we're building to work with Fargo.
      Fargo 0.54 -- WordPress
         Fargo-WordPress connection ships. 
         You can create new posts, edit them, organize collections of posts in the outliner, and use the outliner to author WordPress blog posts.
         <a href="http://smallpicture.com/fargoDocs.html#wordpress">A new section</a> of Fargo Docs that walks you through the setup and creating and editing a post.
         <a href="http://static.scripting.com/larryKing/images/2013/05/01/blogSettings.gif">Screen shot</a> of the Blog settings panel.
         A homemade <a href="http://www.youtube.com/watch?v=zCV9HJpeWWs&feature=youtu.be">video demo</a> showing how to write WordPress blog posts with the new version of Fargo. 
         <a href="http://fargo.io/blogUpdates.opml">An OPML file</a> with the most recent 100 new posts. The same data in a <a href="http://recentposts.smallpicture.com/">web page</a>.
         Dave
      Fargo 0.53
         <rules (blogSectionsRules)>
         Control over how often autosave happens
            It's possible if you're typing for a long time to cause more updates more frequently than Dropbox allows.
            There is a workaround -- if you pause for a minute without typing, the condition clears. 
            We added a new pair of settings, in the Auto-save panel, that gives you control over how frequently Fargo saves. 
            1. A new checkbox allows you to turn off auto-save. If it's off you must remember to save using the Save command in the File menu.
            2. A new setting determines the minimum number of seconds between saves. If you're saving too often for Dropbox, try increasing this number to 15 or 20. That should cut down the number of saves. No matter how often you pause it will never save more often than this number of seconds.
            <a href="http://static.scripting.com/larryKing/images/2013/04/30/autoSavePrefs.gif">Screen shot</a>.
         New Docs menu
            The iPad version doesn't have the right sidebar, so there were no links to docs for users.
            I also added links to the Worknotes site, the mail list, and a page showing all the Font-awesome icons. 
         Eye icon fix
            When you save a WordPress post the first time, the eye icon wouldn't display. Now it does. 
            Note: the WordPress feature is in testing. We expect to release it publicly in 0.54 or 0.55.
         Fixed cribsheet
            There was a change at the top level of Fargo that set the margin-top of <i>.bs-docs-grid .row-fluid</i> to 50px. 
            This added a 50px margin to the cribsheet too. 
            I fixed it so that the change only applied to the top level grid, and the cribsheet looks good again. 
            Also verified that the tablet version works as well.
   April 2013
      Fargo 0.52 -- Tablet UI
         We've known, since starting work on <a href="http://fargo.io/" target="_blank">Fargo</a> last year, that the outliner had to work great on all devices. When we hooked it up to Dropbox the need became even more apparent. The same outlines that we work on on our Macs and PCs had to work well on iPads and Androids. 
         <rules (blogSectionsRules)>
         A bit at a time
            So this is how we're approaching it. A little bit at a time. We solve a few problems, make it work a little better, come back later, and make it work a better. Eventually we figure it out. 
            The reason this is the best approach is that while we had excellent prior art for desktop outliners dating back almost 30 years, there isn't any good prior art for mobile device outliners. So we want to go slowly so we make better design choices. 
            Today, with Fargo 0.52, we're shipping the first iteration of mobile support. In this release we smooth out the interface on tablets. Following is a list of changes. 
         General note
            The changes below only apply when Fargo is running on a tablet device. 
            The functionality in other environments is unchanged. 
         Double-clicking
            When you double-click, the event was intercepted by the system, and it would cause the text to zoom in. 
            Now, when you double-click, it expands the headline the bar cursor is pointing to.
         Landscape and portrait
            When you switch from landscape to portrait or the other way around, Fargo correctly adjusts the outline display.
         Tapping wedges
            Tapping on headline wedges has been made easier.  The tappable area is larger for the iPad.
         Single-tap on a wedge
            You can tap once on a wedge to expand, tap again to collapse. 
         Reorganizing
            Use the Outliner menu to reorg the outline. No change.
            Dave
      Fargo 0.51
         We've gotten a lot of feedback on the initial user experience for Fargo, and decided to take another look. 
         The result is a <a href="http://www.flickr.com/photos/scriptingnews/8674885729/in/photostream/lightbox/">new intro dialog</a>. 
         This is what the <a href="http://static.scripting.com/larryKing/images/2013/04/23/oldDropboxDialog.gif">previous dialog</a> used to look like.
         I wrote a <a href="http://threads2.scripting.com/2013/april/newFargoIntroDialog">blog post</a> about this feature.
         Dave
      Fargo 0.50
         <rules (blogSectionsRules)>
         Navbar
            The Fargo navbar is now fixed when vertically scrolling.
            Kyle
      Fargo 0.49
         <rules (blogSectionsRules)>
         Icon chain
            The icon chain to the left of the outliner is now fixed when vertically scrolling.
         Tabs
            If there is an error loading an outline into a tab an error box will now display at the top of the outline describing the problem and offer the option to try again or close the tab.
            If you ever run into a situation where no tabs are present, navigate to the <i>#prefs</i> folder within the Fargo folder on Dropbox and remove the file <i>tabs.json</i>.
         International characters
            When we save files to Dropbox, Dropbox attempts to detect the encoding (ASCII, Latin1, UTF-8) of the file.  Sometimes their encoding detection is incorrect.  This caused international characters to occasionally be encoded incorrectly when reading an outline back into Fargo.<br>
            This release has a change in it to avoid that encoding problem.  Files are now read from Dropbox in a (binary) way that prevents the auto-detected encoding from being applied.  International characters should no longer be encoded incorrectly.
            Kyle
      Fargo 0.48 -- View in Reader
         The big change in 0.48 is the introduction of <i>Small Picture Reader.</i> 
         It's a separate app, in a web page, as with all our apps, that is used to read outlines, the same way Readability is used to read web pages. 
         <rules (blogSectionsRules)>
         To use it 
            1. Prepare an outline in Fargo that you want to share.
            2. When you're ready, choose <i>View in Reader</i> in the File menu. 
            3. Reader should open, with your outline displayed.
            4. You can then send the URL of that page to friends or colleagues, or use the Tweet icon in the left margin to send it to your Twitter followers.
         Tips for readers
            Reader is always checking to see if your outline has updated, and when it does, it automatically displays the updated outline. This can be disturbing if you're reading an outline, you can lose your place. 
            If this bothers you, click the lock icon in the left margin. Reader will hold on to any updates, and only show them when you unlock it. When there are changes the lock icon will change from gray to green. 
         Demo
            Here's an <a href="http://reader.smallpicture.com/?opmlurl=https://dl.dropboxusercontent.com/u/36518280/outlines/fargoAboutText.opml" target="_blank">example</a> of an outline from Fargo being viewed in Reader.
      Fargo 0.47
         <rules (blogSectionsRules)>
         Restoring tab state
            There was an issue with refreshing Fargo when the last active tab was renamed or removed from the Dropbox folder.
         Dropbox error reporting
            An error box will show above an outline if there are any issues with saving an outline to Dropbox.
            Dropbox error box<a href="http://static.smallpicture.com/images/dropboxError1.png"> screenshot</a>.
            Kyle
      Tip: Reload often
         A general note...
         We have heard reports of people losing work in <a href="http://fargo.io/">Fargo</a>.
         We're looking into them, and working on fixes, and will report when we have them.
         In the meantime -- at least some of the problems can be worked around by reloading Fargo.
         <rules (blogSectionsRules)>
         Tips
            1. Reload at least once a day to be sure your connection with Dropbox is active.
            2. If you make changes to the Fargo folder, reload Fargo after making the change.
            3. You can back up all your work by making a copy of the Fargo folder.
            More coming soon.
            Dave
      Fargo 0.46
         For this release be sure to hold down the Shift key and hit the Refresh button to be sure you have the latest version.
         <rules (blogSectionsRules)>
         Untitled document
            Changing the title of an Untitled document will save a new OPML file based on the new title and remove the untitled.opml file. 
         Charset encoding
            If a file is read from Dropbox and the character set specified within the Content-Type header is ISO-8859-1 the contents of the file will be decoded from UTF-8 to avoid character encoding problems.
      Fargo 0.34
         On Windows instead of the "Cmd" symbol for menu items, it should now say Ctrl+.
         The Preferences command moves to the System menu, and its name changed to Settings.
      Fargo 0.14
         <a href="https://workflowy.com/">Workflowy</a> is a browser-based outliner that a number of Little Outliner users like, and naturally they want to move ideas into and out of both products. It would be easier if they supported OPML import and export, like our outliners do, but they don't at this time.
         So we added a feature in the Small Picture outliner that handles Workflowy's export format. So you should be able to paste outlines that you export from Workflowy into Fargo and (later today) Little Outliner.
         <rules (blogSectionsRules)>
         Howto
            1. In Workflowy, get the section of the outline that you want to export on screen. 
            2. Hover with the mouse just to the left of the main headline and nudge the mouse down to reveal the full menu, and click on the Export command. (<a href="http://static.scripting.com/larryKing/images/2013/04/11/workflowy1.gif">Screen shot</a>.)
            3. A dialog appears containing the exported text. Be sure to click on the Plain text option. (<a href="http://static.scripting.com/larryKing/images/2013/04/11/exportDialog.gif">Screen shot</a>.)
            4. Copy all the text, then go to Fargo (or Little Outliner, later today). Position the cursor where you want to paste the text, and Paste. (<a href="http://static.scripting.com/larryKing/images/2013/04/11/fargoText.gif">Screen shot</a>.)
      Fargo 0.12
         The main visible change in 0.12 is the display of attribute values in the right sidebar. 
         How to turn this on:
            1. Choose Preferences from the File menu.
            2. Click on the Advanced tab.
            3. Check the box to display attributes in the right sidebar. (<a href="http://static.scripting.com/larryKing/images/2013/04/11/checkbox.gif">Screen shot</a>.)
            4. Click OK.
         Now as you move the cursor through the outline, you will see the attributes of any headline that has them.
         Note: Since every headline has a "created" attribute, we don't display it. And any attribute that's longer than 10 characters is truncated to 10 (just for display of course). URLs can be very long, and there's limited space in the right sidebar.
         If you want an outline to look at that has headlines with lots of attributes, here's my <a href="https://dl.dropboxusercontent.com/u/36518280/readingLists/movies.opml">Movies subscription list</a>. Download it, and copy it into your smallPicture sub-folder on Dropbox and open it in Fargo.
      Little Outliner 0.40
         <rules (blogSectionsRules)>
         First-time, in text mode
            When the outliner boots up for the first time, for the first-time user, it is in text mode not structure mode.
            That means that insead of showing the bar cursor, we show a blinking caret cursor.
            This is more accurate. It's the first thing a first-time user should do. The software should invite the user to type. That's what the blinking caret says. 
         Moved the clock
            In the right sidebar, the clock moves below the version number. Looks a little more balanced, imho.
      Redirect
   March 2013
      Plug-in Demo
         <a href="http://littleoutliner.com/">In Little Outliner</a> 0.39 we will start to explore the idea of web-based outliner plug-ins. Right now, it's just a demo, an illustration of how the idea may work when developers can add functionality to the outliner through web services. 
         <rules (blogSectionsRules)>
         How to demo
            1. To enable the demo, choose Preferences from the Outliner menu, and click on the Demo tab.
            2. You'll see a checkbox that enables the plug-in demo. Check it and click submit. 
            3. Choose Import OPML from the Outliner menu. Enter this URL into the dialog.
            https://dl.dropbox.com/u/36518280/outlines/hazelnut.opml
            4. Now place the cursor on the top-level headline, <i>My presentation,</i> and click the new icon (<a href="http://static.scripting.com/larryKing/images/2013/03/31/screen1.gif">screen shot</a>). 
            5. In a few seconds a preview of a presentation should appear. Step through it by clicking on the <a href="http://static.scripting.com/larryKing/images/2013/03/31/screen2.gif">arrows</a> in the lower right corner of the window. 
         Editing
            You can edit my slides or create your own. 
            The top level headline is the title of the show. Its subheads are the titles of slides. And the text under each slide are the bullet points. 
         Publishing
            You can create a finished presentation that you can send to others by clicking the Publish button in the lower left corner of the Preview dialog. 
            <i>Note that since this is just a demo, all published presentations will be automatically deleted one month after they are published. So if you want to keep a copy you should download it before the month is over.</i>
         The idea
            This part is for developers.
            When the user clicks the icon, a dialog opens, and calls a web service. It returns HTML code that is displayed in the dialog.
            There is a single parameter to the service, the OPML text of the outline pointed to by the bar cursor.
            The plug-in then processes the OPML in some way, and returns HTML which is then displayed in the preview dialog.
            The HTML text could simply be a message saying that the process worked. Or it could be, as in the case of our demo, a rendering of the outline.
         Why this is useful
            Outliners are a good way to compose content for rendering. 
         Is this open?
            Yes. OPML is a simple format that anyone can process. Nothing hidden there.
            And the idea of an AJAX web service also is very open. We use jQuery to make the call. As long as you can receive a call from jQuery you should be fine.
            The presentations are displayed by <a href="http://lab.hakim.se/reveal-js/#/">reveal.js</a>. 
         This is just a demo
            Right now we don't have a way for users to add items to the plug-in list, that's why it's just a demo. But it's not very far from being a for-real feature. :-)
         Update
            Here's a <a href="http://threads2.scripting.com/2013/april/outlinerPlugins">blog post</a> about plug-ins.
      Little Outliner 0.38
         Fixed issues in the cribsheet.
         Keystrokes no longer flow through to the outline while the cribsheet is displayed. 
         Any keystroke causes the cribsheet to be closed.
      Little Outliner 0.37
         New cribsheet shows keyboard commands, and important mouse gestures. 
         Not meant to replace the Outliner Howto, so please do read that. Use it when you quickly need to remember a keystroke. 
         To access the cribsheet, either press Cmd-? or click the Cribsheet link in the right margin.
         <a href="http://static.scripting.com/larryKing/images/2013/03/27/cribsheet.gif">Screen shot</a>.
      Little Outliner 0.35
         Fixed a problem that caused the title not to display when <a href="http://littleoutliner.com/">Little Outliner</a> starts. 
         <rules (blogSectionsRules)>
         Download OPML 
            New experimental command.
            It should work in all browsers, <i>except IE9 and IE10. </i>
            Thanks to Dan MacTough for this excellent hack.
         Don't save if it's been one or more seconds since the last keystroke
            The user has to let up a little before we save.
            Saw a <a href="http://threads2.scripting.com/2013/march/usersGuideToLocalStorage#comment-843356505">comment</a> from Alec Perkins saying that he had problems if he saved on every keystroke. We're basically doing that now. Better to be a little more conservative. 
         Smaller font in the Outliner menu
            And a little less space between the commands. 
            Trying to make a little more room for people with shorter screens.
      Little Outliner 0.34
         Fix problem with URL params encoded <a href="http://littleoutliner.blorkmark.com/?reader=https%3A%2F%2Fdl.dropbox.com%2Fu%2F36518280%2Fmisc%2FdemoForGuy.opml">like this</a>. The JavaScript built-in function doesn't deal with them correctly.
         Add a link on the home page to the <a href="http://threads2.scripting.com/2013/march/usersGuideToLocalStorage">local storage FAQ</a> that I wrote this morning. 
      Little Outliner 0.33
         Fixed bugs in "reader" mode.
         <a href="http://littleoutliner.com/?reader=http://smallpicture.com/states.opml">http://littleoutliner.com/?reader=http://smallpicture.com/states.opml</a>
         The title should be the title of the outline you're viewing.
         Editing commands in the menu are not present. The preferences command is still there, but the prefs that would impact the outline being displayed don't do anything.
      Little Outliner 0.32
         Yes, it was lame to ship a product with Mac cmd-key labels on Windows and other operating systems.
         That should be fixed now. On Windows, cmd-keys are prefixed with Ctrl+.
         I'm assuming it's the same on Linux? 
      Little Outliner 0.31
         New "Title" prefs panel. Allows you to set the title and say whether or not you want the title to display above the outline.
         The Set Title menu command was removed. 
         When the bar cursor points to a headline with an xmlUrl attribute, allow the user to double-click to open the feed in another browser tab. 

</pre>