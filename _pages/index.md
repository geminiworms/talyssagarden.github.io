---
layout: page
title: home
id: home
permalink: /
---
<html>
<head>
    <script src="https://code.jquery.com/jquery-3.6.0.min.js" integrity="sha256-/xUj+3OJU5yExlq6GSYGSHk7tPXikynS7ogEvDej/m4=" crossorigin="anonymous"></script>
</head>
<body>
    <h1><div id="arch">this is talyssa's <a class="internal-link" href="/what-is-digital-gardening">digital garden</a></div></h1>
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
        });
    </script>                                
</body>
</html>

<ul>
<h3><div id="arch">recent edits</div></h3>
{% assign sorted_pages = site.pages | sort: "last_modified_at" | reverse %}
{% for page in sorted_pages limit:10 %}
  <li><a href="{{ page.url }}">{{ page.title }}</a> ({{ page.last_modified_at | date: "%Y-%m-%d" }})</li>
{% endfor %}
</ul>

<style>
  .wrapper {
    max-width: 46em;
  }
</style>
