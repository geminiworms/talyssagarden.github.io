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
      max-width: 100%;
      margin: 0 auto;
    }
    .left-column {
      flex: 70%;
      padding: 10px;
      box-sizing: border-box;
    }
    .right-column {
      flex: 30%;
      padding: 10px;
      box-sizing: border-box;
      font-size: 16px;
    }
    /* Style the link list */
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

      <!-- LEFT COLUMN -->
    <div class="left-column">
      <h2>this is Talyssa's <a class="internal-link" href="/what-is-digital-gardening">digital garden</a></h2>
      <p>you can think of it as a sprawling collection of digital references, miscellaneous artifacts, and fragmented thoughts. it's a personalized wiki, and it works similarly to a scrap journal or a commonplace book (see: <a class="external-link" href="https://youtu.be/aaHEgPk0tNM">this</a>, <a class="external-link" href="https://youtu.be/XFUQJtOcras">this</a>, and <a class="external-link" href="https://youtu.be/T_S7Uiy03pw?t=731">this</a>) except that it's completely online and very easy to keep in tangent to my analog systems. i started this garden in 2022 out of curiousity and its relevance in my life waxes and wanes depending on what i'm interested in and working on. <br> if you want to see everything that exists in my garden, you can visualize it in this <a class="internal-link" href="/web">web</a></p><br>
      <h2>thanks for stopping by</h2>
      <p><i> feel free to drop a note <a class="external-link" href="https://www.yourworldoftext.com/~talyssa.txt/">in my guestbook</a></i><br>
      i also maintain a project website that explores intimate internet spaces, visit it here: <a class="external-link" href="https://smallweb.site">smallweb.site</a>
      </p>
    </div>
  

 <!-- RIGHT COLUMN -->
    <div class="right-column">
      <p><h3>like a real garden,</h3>this space is always growing and evolving. here are my <b>indexes</b> that can help you move around in this space:</p><br>
      <a class="internal-link" href="/site-meta">site meta</a>
      <a class="internal-link" href="/self">self</a>
      <a class="internal-link" href="/science">science</a>
      <a class="internal-link" href="/audio">audio</a>
      <a class="internal-link" href="/tech">tech</a>
      <a class="internal-link" href="/reads">reads</a>
      <p><h3>& a few random notes:</h3></p>
      {% assign notes_pages = site.notes %}
      {% assign random_pages = notes_pages | sample: 3 %}
      <ul>
        {% for page in random_pages %}
          <li><a href="{{ page.url }}">{{ page.title }}</a> ({{ page.last_modified_at | date: "%B %-d, %Y" }})</li>
        {% endfor %}
      </ul>
       <pre>
                    .-.
                          \ \
                           \ \
                            | |
                            | |
          /\---/\   _,---._ | |
         /^   ^  \,'       `. ;
        ( O   O   )           ;
         `.=o=__,'            \
           /         _,--.__   \
          /  _ )   ,'   `-. `-. \
         / ,' /  ,'        \ \ \ \
        / /  / ,'          (,_)(,_)
       (,;  (,,)      
                            
        </pre>
    </div>
  </div>
</body>
</html>

<style>
  .wrapper {
    max-width: 46em;
  }
</style>
