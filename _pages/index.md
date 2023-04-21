---
layout: page
title: home
id: home
permalink: /
---
<html>
<head>
  <meta charset="UTF-8">
  <title>Talyssa's Digital Garden</title>
  <style>
    /* Define the layout of the two columns */
    .container {
      display: flex;
      flex-direction: row;
      max-width: 1000px;
      margin: 0 auto;
    }
    .left-column {
      width: 70%;
      padding: 10px;
      box-sizing: border-box;
    }
    .right-column {
      width: 30%;
      padding: 10px;
      box-sizing: border-box;
      font-size: 16px;
    }
    /* Style the recent edits list */
    ul {
      list-style-type: none;
      padding: 0;
    }
    li {
      margin-bottom: 10px;
    }
  </style>
</head>
<body>
  <div class="container">
    <div class="left-column">
      <h1>this is talyssa's <a class="internal-link" href="/what-is-digital-gardening">digital garden</a></h1>
      <p>you can think of it as a sprawling collection of digital references, miscellaneous artifacts, and fragmented thoughts. everything that exists in the garden can be visualized in a web, which you can find <a class="internal-link" href="/web">here</a> <img src="/assets/mini-graphics/sprout.gif" style="padding: 0px 0px 0px 0px;"><br><i>thanks for stopping by! please leave a note <a class="external-link" href="https://www.yourworldoftext.com/~talyssa.txt/">in my guestbook</a> if you wish</i></p>
    </div>
    <div class="right-column">
      <p><h3>like a real garden,</h3>this space is always changing. here's a log of my <b>recently edited notes</b> to see what i've tended to lately:</p>
      <ul>
        {% assign sorted_notes = site.notes | sort: "last_modified_at" | reverse %}
        {% for i in (0..4) %}
          {% assign page = sorted_notes[i] %}
          <li><a href="{{ page.url }}">{{ page.title }}</a> ({{ page.last_modified_at | date: "%d %B %Y" }})</li>
        {% endfor %}
      </ul>
      <hr>
      <p> dont mind me... trying to figure out why things aren't actually sorting in chronological order!</p>
     <ul>
       {% assign recent_notes = site.notes | sort: "last_modified_at_timestamp" | reverse %}
       {% for note in recent_notes limit: 5 %}
         <li>
           {{ note.last_modified_at | date: "%Y-%m-%d" }} — <a class="internal-link" href="{{ note.url }}">{{ note.title }}</a>
          </li>
       {% endfor %}
      </ul>
      {% assign sorted_notes = site.notes | sort: "last_modified_at" | reverse %}
      <ul>
       {% for note in sorted_notes %}
          <li><a href="{{ note.url }}">{{ note.title }}</a> ({{ note.last_modified_at | date: "%-m-%-d-%y" }})</li>
        {% endfor %}
      </ul>
    



    </div>
  </div>
</body>
</html>


<style>
  .wrapper {
    max-width: 46em;
  }
</style>

