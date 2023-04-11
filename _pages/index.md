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
    <h1>this is talyssa's <a class="internal-link" href="/what-is-digital-gardening">digital garden</a></h1>
    <p>recent edits</p>
<ul>
{% assign sorted_pages = site.pages | where: "path", "_notes" | sort: "last_modified_at"}
{% for i in (sorted_pages | size | minus:20)..(sorted_pages | size) %}
  {% assign page = sorted_pages[i] %}
  <li><a href="{{ page.url }}">{{ page.title }}</a> ({{ page.last_modified_at | date: "%Y-%m-%d" }})</li>
{% endfor %}
</ul>
<script>
    var colours = ["#32AE4D", "#F2CF7D", "#0A2463", "#E46A3A", "#A30000", "#1672AB", "#FFD20A"],
        idx;
    $(document).ready(function(){
        var body = $('body'); 
        var chars = body.text().split('');
        body.html('');     
        for(var i=0; i<chars.length; i++) {
            idx = Math.floor(Math.random() * colours.length);
            var span = $('<span>' + chars[i] + '</span>').css("color", colours[idx])
            body.append(span);
        }
    });
</script>
                              
</body>
</html>

<p>recent edits</p>
{% assign sorted_pages = site.pages | sort: "last_modified_at" %}
{% for page in sorted_pages limit:20 %}
  <li><a href="{{ page.url }}">{{ page.title }}</a> ({{ page.last_modified_at | date: "%Y-%m-%d" }})</li>
{% endfor %}


<style>
  .wrapper {
    max-width: 46em;
  }
</style>
