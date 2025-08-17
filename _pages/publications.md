---
layout: single
title: Publications
permalink: /publications/
---

<style>
  /* Keep your label styles (Bootstrap-like) */
  .label{display:inline;padding:.2em .6em .3em;font-size:75%;font-weight:700;line-height:1;color:#fff;text-align:center;white-space:nowrap;vertical-align:baseline;border-radius:.25em}
  a.label:hover,a.label:focus{color:#fff;text-decoration:none;cursor:pointer}
  .label-success{background:#5cb85c}.label-primary{background:#337ab7}
  .label-warning{background:#f0ad4e}.label-danger{background:#d9534f}
  .label-info{background:#5bc0de}.label-default{background:#777}
  /* Small polish */
  .pubs{list-style:none;padding-left:0}
  .pub{margin:0 0 1.1rem}
  .pub-title{font-weight:600;font-size:1rem}
  .pub-authors,.pub-venue{color:#555}
  .chips a{margin-right:.35rem}
</style>

<div id="main">
  {% assign posts_by_year = site.posts | group_by_exp: "p", "p.date | date: '%Y'" %}

  {% for year_group in posts_by_year %}
    <h3 id="{{ year_group.name }}-ref">{{ year_group.name }}</h3>
    <ul class="pubs">
      {% for post in year_group.items %}
        <li class="pub">
          <div class="pub-title">
            {% if post.pdf and post.pdf != 'NONE' %}
              <a href="/assets/papers/{{ post.base }}/{{ post.pdf }}" target="_blank">{{ post.title }}</a>
            {% elsif post['pdf-ext'] and post['pdf-ext'] != 'NONE' %}
              <a href="{{ post['pdf-ext'] }}" target="_blank">{{ post.title }}</a>
            {% else %}
              {{ post.title }}
            {% endif %}
          </div>

          {% if post.authors %}
            <div class="pub-authors"><em>{{ post.authors }}</em></div>
          {% endif %}

          {% if post.venue %}
            <div class="pub-venue">{{ post.venue }}</div>
          {% endif %}

          <div class="chips" style="margin-top:.3rem">
            {% if post.pdf and post.pdf != 'NONE' %}
              <a class="label label-success" href="/assets/papers/{{ post.base }}/{{ post.pdf }}" target="_blank">PDF</a>
            {% endif %}
            {% if post['pdf-ext'] and post['pdf-ext'] != 'NONE' %}
              <a class="label label-success" href="{{ post['pdf-ext'] }}" target="_blank">PDF</a>
            {% endif %}
            {% if post.data %}
              <a class="label label-success" href="{{ post.data }}" target="_blank">{{ post['data-name'] | default: 'DATA' }}</a>
            {% endif %}
            {% if post.code and post.code != 'NONE' %}
              <a class="label label-primary" href="{{ post.code }}" target="_blank">CODE</a>
            {% endif %}
            {% if post.talk and post.talk != 'NONE' %}
              <a class="label label-warning" href="{{ post.talk }}" target="_blank">TALK</a>
            {% endif %}
            {% if post.slides and post.slides != 'NONE' %}
              <a class="label label-danger" href="/assets/papers/{{ post.base }}/{{ post.slides }}" target="_blank">SLIDES</a>
            {% endif %}
            {% if post.website and post.website != 'NONE' %}
              <a class="label label-danger" href="{{ post.website }}" target="_blank">WEBSITE</a>
            {% endif %}
            {% if post.poster and post.poster != 'NONE' %}
              <a class="label label-info" href="/assets/papers/{{ post.base }}/{{ post.poster }}" target="_blank">POSTER</a>
            {% endif %}
            {% if post.bib and post.bib != 'NONE' %}
              <a class="label label-default" href="/assets/papers/{{ post.base }}/{{ post.bib }}" target="_blank">BIB</a>
            {% endif %}
            {% if post['bib-ext'] and post['bib-ext'] != 'NONE' %}
              <a class="label label-default" href="{{ post['bib-ext'] }}" target="_blank">BIB</a>
            {% endif %}
          </div>
        </li>
      {% endfor %}
    </ul>
  {% endfor %}
</div>
