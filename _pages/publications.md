---
layout: single
title: Publications
permalink: /publications/
---

<div class="pub-list">
  {% assign posts_sorted = site.posts | sort: "date" | reverse %}
  {% assign posts_by_year = posts_sorted | group_by_exp: "p", "p.date | date: '%Y'" %}

  {% for year_group in posts_by_year %}
    <h3 class="pub-year" id="{{ year_group.name }}-ref">{{ year_group.name }}</h3>
    <ul class="pubs">
      {% for post in year_group.items %}
        <li class="pub">
          <div class="pub-title">
            {% if post.pdf and post.pdf != 'NONE' %}
              <a href="/assets/papers/{{ post.base }}/{{ post.pdf }}" target="_blank" rel="noopener">{{ post.title }}</a>
            {% elsif post['pdf-ext'] and post['pdf-ext'] != 'NONE' %}
              <a href="{{ post['pdf-ext'] }}" target="_blank" rel="noopener">{{ post.title }}</a>
            {% else %}
              {{ post.title }}
            {% endif %}
          </div>

          {% if post.authors and post.authors != 'NONE' %}
            <div class="pub-authors"><em>{{ post.authors }}</em></div>
          {% endif %}

          {% if post.venue and post.venue != 'NONE' %}
            <div class="pub-venue">{{ post.venue }}</div>
          {% endif %}

          <div class="chips">
            {% comment %} PDF(s) {% endcomment %}
            {% if post.pdf and post.pdf != 'NONE' %}
              <a class="label-success" href="/assets/papers/{{ post.base }}/{{ post.pdf }}" target="_blank" rel="noopener">PDF</a>
            {% endif %}
            {% if post['pdf-ext'] and post['pdf-ext'] != 'NONE' %}
              <a class="label-success" href="{{ post['pdf-ext'] }}" target="_blank" rel="noopener">PDF</a>
            {% endif %}

            {% comment %} DATA (distinct color) {% endcomment %}
            {% if post.data and post.data != 'NONE' %}
              <a class="label-data" href="{{ post.data }}" target="_blank" rel="noopener">{{ post['data-name'] | default: 'DATA' }}</a>
            {% endif %}

            {% comment %} CODE / TALK / SLIDES / WEBSITE / POSTER / BIB {% endcomment %}
            {% if post.code and post.code != 'NONE' %}
              <a class="label-primary" href="{{ post.code }}" target="_blank" rel="noopener">CODE</a>
            {% endif %}
            {% if post.talk and post.talk != 'NONE' %}
              <a class="label-warning" href="{{ post.talk }}" target="_blank" rel="noopener">TALK</a>
            {% endif %}
            {% if post.slides and post.slides != 'NONE' %}
              <a class="label-danger" href="/assets/papers/{{ post.base }}/{{ post.slides }}" target="_blank" rel="noopener">SLIDES</a>
            {% endif %}
            {% if post.website and post.website != 'NONE' %}
              <a class="label-website" href="{{ post.website }}" target="_blank" rel="noopener">WEBSITE</a>
            {% endif %}
            {% if post.poster and post.poster != 'NONE' %}
              <a class="label-poster" href="/assets/papers/{{ post.base }}/{{ post.poster }}" target="_blank" rel="noopener">POSTER</a>
            {% endif %}
            {% if post.bib and post.bib != 'NONE' %}
              <a class="label-default" href="/assets/papers/{{ post.base }}/{{ post.bib }}" target="_blank" rel="noopener">BIB</a>
            {% endif %}
            {% if post['bib-ext'] and post['bib-ext'] != 'NONE' %}
              <a class="label-default" href="{{ post['bib-ext'] }}" target="_blank" rel="noopener">BIB</a>
            {% endif %}
          </div>
        </li>
      {% endfor %}
    </ul>
  {% endfor %}
</div>
