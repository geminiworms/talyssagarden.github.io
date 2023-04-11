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
      padding: 20px;
      box-sizing: border-box;
    }
    .right-column {
      width: 30%;
      padding: 20px;
      box-sizing: border-box;
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
      <h1>This is Talyssa's <a class="internal-link" href="/what-is-digital-gardening">Digital Garden</a></h1>
      <p>Welcome to my digital garden! Here, you'll find my thoughts, ideas, and notes on various topics. I hope you find something interesting!</p>
    </div>
    <div class="right-column">
      <p>recent edits:</p>
      <ul>
        {% assign sorted_pages = site.pages | where: "path", "contains", "_notes" | sort: "last_modified_at" %}
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

