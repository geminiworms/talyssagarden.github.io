---
title: to do list
---
### stuff I'm building
I'm new to css/html and so if you ran into a 404, it's probably because I haven't quite figured it out yet.
I'll keep this list as updated as possible just as a reference and also as an invitation for feedback.

###1. creating a photogallery layout 
I'm inspired by [alisa.wtf's photo galleries](https://alisa.wtf/plants) and am hoping to translate her [code](https://github.com/alisasgithub/alisa-digital-garden/blob/main/_layouts/photoessay.html) to work in my own site. So far, this is what the bulk of the code looks like:
`---
layout: default
class: photoessay
---
<article>
  <div>
    <h1>{{ page.title }}</h1>
    <time datetime="{{ page.last_modified_at | date_to_xmlschema }}">{% if page.type != 'pages' %}
      Last updated on {{ page.last_modified_at | date: "%B %-d, %Y" }}
      {% endif %}
    </time>
  </div>
    <div id="notes-entry-container">
    <content>
        {{ content }}
    </content> 
    <div id="gallery">
        <ul>
        {% for image in site.static_files %}
        {% if image.path contains page.url %}
            <li>
                <img class="photoessay" src="{{ site.baseurl }}{{ image.path }}" alt="image" />
            </li>
            {% endif %}
            {% endfor %}
        </ul>  
    </div>

</div>`
and I'll have to play with it more to make sure my paths line up right to my repo.

####2. gotta get to that about page...
