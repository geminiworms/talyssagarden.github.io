---
title: to do list
---
### stuff I'm building
I'm new to css/html and so if you ran into a 404, it's probably because I haven't quite figured it out yet.
I'll keep this list as updated as possible just as a reference and also as an invitation for feedback.
Here's [my repo](https://github.com/geminiworms/geminiworms.github.io) for reference.

### index:
1. [[on celebration]] page is lacking the grid map! Maybe it has to do with the instagram post embeds? since that's probably the only unique thing i've added on that note in comparsion to others 
2. I am trying to use jquery to make my index (homepage) more interesting
3. stylistic updates to the home page
4. date created in notes (i have last modified, but how to display the initial file commit date???)
5. redoing my entire [[about]] page

#### 2. using jquery on my homepage
basically, i want to add some more interesting dynamics to the front page of the site... and js (rather [jquery](https://releases.jquery.com/)) seems like the most attainable way to go about this... to start, i'm trying to use jquery to randomize the colors of letters in a title text string. I'm following [this](https://stackoverflow.com/questions/20228961/how-to-make-each-letter-in-text-a-different-random-color-in-javascript) right now... and i was using this [youtube tutorial](https://www.youtube.com/watch?v=EwUOsRlDTLQ) to figure stuff out on a basic level. my code looks like this right now:
```js
<html>
<head>
    <script src="https://code.jquery.com/jquery-3.6.0.min.js" integrity="sha256-/xUj+3OJU5yExlq6GSYGSHk7tPXikynS7ogEvDej/m4=" crossorigin="anonymous"></script>
</head>
<body>
        <h2><div id="arch">i guess i have to make sure this works first</div></h2>
    <script>
            var colours = ["#32AE4D", "#F2CF7D", "#0A2463", "#E46A3A", "#A30000", "#1672AB", "#FFD20A"], 
            idx;
        $(document).ready(function(){
    var div = $('#arch'); 
    var chars = div.text().split('');
    div.html('');     
    for(var i=0; i<chars.length; i++) {
        idx = Math.floor(Math.random() * colours.length);
        var span = $('<span>' + chars[i] + '</span>').css("color", colours[idx])
        div.append(span);
    }
}

</script>                                

</body>
</html>
```
and clearly it's not really working out... but we'll see what happens. For reference (when I go and reopen all these tabs), I'm also skimming through [this resource](https://www.w3schools.com/js/js_htmldom.asp) for jquery x html/css background. 

#### 3. troubleshooting the list on my homepage for most recently updated notes
I cant get things to sort in chronological order!! [this issue](https://github.com/gjtorikian/jekyll-last-modified-at/issues/70) is the same one i'm having but of course there's no posted solution...


### finished!
1. I used this code for a [responsive photo grid](https://www.w3schools.com/howto/howto_css_image_grid_responsive.asp) to create a image gallery inspired by [alisa.wtf's photo galleries](https://alisa.wtf/plants). Some code I also considered using was [this guide](https://dmnfarrell.github.io/software/jekyll-galleries) for a photo gallery `_includes` situation... Ideally, it would've been a generative loop the read photo files out of a directory, but it seems like for now, I'm just working with it as a local grid.
2. I added a site thumbnail using `<meta property="og:image" content="path" />` in my `head.html` file
3. I made updates to my home page by creating columns, and then included a better flow into the concept of a digital garden. I also made a few aesthetic changes.
