### workspace.userlandSamples.getGoogleMovies
<pre>
on getGoogleMovies (zip, adrmoviestable)
   //Changes
      //11/19/12; 1:07:35 PM by DW
         //A sample script that tells you what movies are playing nearby now. Unfortunately the API doesn't tell you where they're playing. Oh well.
            //http://worknotes.scripting.com/november2012/111912ByDw/googleMoviesApi
   local (xmltext, xstruct, i = 0, adrreply, adrmovies, adrmovie, fldone = false, url)
   new (tabletype, adrmoviestable)
   while not fldone
      url = "http://www.google.com/ig/api?movies=" + zip + "&start=" + 3 * i++
      xmltext = tcp.httpreadurl (url, 3, false)
      msg (url)
      xml.compile (xmltext, @xstruct)
      adrreply = xml.getaddress (@xstruct, "xml_api_reply")
      adrmovies = xml.getaddress (adrreply, "movies")
      for adrmovie in adrmovies
         if nameof (adrmovie^) endswith "movie"
            local (adrsub, title)
            on getvalue (name)
               try
                  local (adrval)
                  adrval = xml.getaddress (adrmovie, name)
                  return (adrval^.["/atts"].data)
               else
                  return ("")
            title = getvalue ("title")
            if sizeof (title) == 0
               fldone = true
               break
            adrsub = @adrmoviestable^.[title]
            new (tabletype, adrsub)
            adrsub^.movieId = getvalue ("movie_id")
            adrsub^.length = getvalue ("length")
            adrsub^.genre = getvalue ("genre")
            adrsub^.mpaaRating = getvalue ("mpaarating")
            adrsub^.numreviews = getvalue ("num_reviews")
            adrsub^.reviewsUrl = getvalue ("reviews_url")
            adrsub^.imgdbUrl = getvalue ("imgdb_url")
            adrsub^.landingpageUrl = getvalue ("landingpage_url")
            adrsub^.reviewsRatingPercent = getvalue ("reviews_rating_percent")
bundle //test code
   getGoogleMovies ("10003", @scratchpad.mygooglemovies)
   edit (@scratchpad.mygooglemovies)

</pre>