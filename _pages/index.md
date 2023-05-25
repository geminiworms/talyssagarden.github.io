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
      <h1>this is Talyssa's <a class="internal-link" href="/what-is-digital-gardening">digital garden</a></h1>
      <p>you can think of it as a sprawling collection of digital references, miscellaneous artifacts, and fragmented thoughts. it's a personalized wiki, and it works similarly to a scrap journal or a commonplace book (see: <a class="external-link" href="https://youtu.be/aaHEgPk0tNM">this</a>, <a class="external-link" href="https://youtu.be/XFUQJtOcras">this</a>, and <a class="external-link" href="https://youtu.be/T_S7Uiy03pw?t=731">this</a>) except that it's completely online and very easy to keep in tangent to my analog systems. i started this garden in 2022 out of curiousity and its relevance in my life waxes and wanes depending on what i'm interested in and working on. <br>everything that exists in the garden can be visualized in a web, which you can find <a class="internal-link" href="/web">here</a> <img src="/assets/mini-graphics/sprout.gif" style="padding: 0px 0px 0px 0px;"><br><i>thanks for stopping by! please leave a note <a class="external-link" href="https://www.yourworldoftext.com/~talyssa.txt/">in my guestbook</a> if you wish</i></p>
    </div>
    <div class="right-column">
      <p><h3>like a real garden,</h3>this space is always growing and evolving. Here are my <b>indexes</b> that can help you move through this space:</p><br>
      <a class="internal-link" href="/site-meta">site meta</a><br>
      <a class="internal-link" href="/self">self</a><br>
      <a class="internal-link" href="/science">science</a><br>
      <a class="internal-link" href="/audio">audio</a><br>
      <a class="internal-link" href="/tech">tech</a><br>
      <a class="internal-link" href="/reads">reads</a><br>
      <p><h3>a few random notes:</h3></p>
      {% assign notes_pages = site.notes %}
      {% assign random_pages = notes_pages | sample: 5 %}
      <ul>
        {% for page in random_pages %}
          <li><a href="{{ page.url }}">{{ page.title }}</a> ({{ page.last_modified_at | date: "%B %-d, %Y" }})</li>
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
