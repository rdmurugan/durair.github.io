---
layout: default
title: "Tags"
permalink: /tags/
---

<section class="section">
  <div class="container">
    <h1 class="section-title">Browse by Tag</h1>

    {% assign all_tags = "" | split: "" %}
    {% for post in site.posts %}
      {% for t in post.tags %}
        {% assign all_tags = all_tags | push: t %}
      {% endfor %}
    {% endfor %}
    {% assign uniq = all_tags | uniq | sort %}

    <div class="tags-cloud">
      {% for t in uniq %}
        <a class="tag" href="#{{ t | replace: ' ', '-' }}">{{ t }}</a>
      {% endfor %}
    </div>

    <div class="tags-groups">
      {% for t in uniq %}
        <h2 id="{{ t | replace: ' ', '-' }}" class="tag-head">{{ t }}</h2>
        <ul class="tag-list">
          {% for post in site.posts %}
            {% if post.tags contains t %}
              <li>
                <a href="{{ post.url | relative_url }}">{{ post.title }}</a>
                <span class="tag-date">{{ post.date | date: "%b %d, %Y" }}</span>
              </li>
            {% endif %}
          {% endfor %}
        </ul>
      {% endfor %}
    </div>
  </div>
</section>
