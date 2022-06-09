---
layout: page
title: Home
id: home
permalink: /
---
<html>
<head>
<script>
var colours = ["#32AE4D", "#F2CF7D", "#0A2463", "#E46A3A", "#A30000", "#1672AB", "#FFD20A"], 
    idx;

$(function() {
    var div = $('#arch'); 
    var chars = div.text().split('');
    div.html('');     
    for(var i=0; i<chars.length; i++) {
        idx = Math.floor(Math.random() * colours.length);
        var span = $('<span>' + chars[i] + '</span>').css("color", colours[idx]);
        div.append(span);
    }
});
</script>
</head>
<body>
<h2><div id="arch">i guess i have to make sure this works first</div></h2>

</body>
</html>

{% include notes_graph.html %}


<style>
  .wrapper {
    max-width: 46em;
  }
</style>
