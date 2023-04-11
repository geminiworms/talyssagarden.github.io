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
      font-size: 14px;
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
      <p>you can think of it as a sprawling collection of digital references, miscellaneous artifacts, and fragmented thoughts<br>everything that exists in the garden can be found <a class="internal-link" href="/web">here</a></p>
    </div>
    <div class="right-column">
      <p><h4>like a real garden,</h4><br>this space is always changing.<br>here's a log of my<b>recently edited notes</b>to see what i've tended to lately</p>
      <ul>
        {% assign sorted_pages = site.notes | sort: "last_modified_at" %}
        {% for i in (0..9) %}
          {% assign page = sorted_pages[i] %}
          <li><a href="{{ page.url }}">{{ page.title }}</a> ({{ page.last_modified_at | date: "%Y-%m-%d" }})</li>
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

