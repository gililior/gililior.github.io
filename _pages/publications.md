---
layout: single
title: Publications
permalink: /publications/
---

<style>
  /* ===== Card layout & typography ===== */
  .pubs{list-style:none;padding-left:0;margin:0}
  .pub{
    background:#fafafa;
    padding:.9rem 1.05rem;
    margin:0 0 1.1rem;
    border-radius:8px;
    box-shadow:0 1px 3px rgba(0,0,0,.08);
  }
  .pub-title a{
    font-size:1.08rem;
    font-weight:600;
    color:#222;
    text-decoration:none;
  }
  .pub-title a:hover{color:#007acc;text-decoration:underline}
  .pub-authors{font-size:.92rem;color:#666;margin-top:.2rem}
  .pub-venue{font-size:.9rem;color:#444;font-style:italic;margin-top:.15rem}

  /* Year headers */
  .pub-year{
    margin:2rem 0 .6rem;
    font-size:1.3rem;
    border-bottom:2px solid #eee;
    padding-bottom:.25rem;
  }

  /* ===== Chip (label) styling ===== */
  .chips{margin-top:.35rem}
  .chips a{
    display:inline-block;
    margin:.25rem .35rem 0 0;
    border-radius:12px;
    font-size:.75rem;
    padding:.28rem .6rem;
    color:#fff !important;
    text-decoration:none;
  }

  /* Base label palette */
  .label-success{background:#5cb85c}
  .label-primary{background:#337ab7}
  .label-warning{background:#f0ad4e}
  .label-danger{background:#d9534f}
  .label-info{background:#5bc0de}
  .label-default{background:#777}

  /* Custom colors */
  .label-data{background:#9b59b6}      /* DATA: purple */
  .label-website{background:#3f51b5}   /* WEBSITE: indigo */
  .label-poster{background:#009688}    /* POSTER: teal */

  /* Hover states */
  .label-success:hover{background:#449d44}
  .label-primary:hover{background:#286090}
  .label-warning:hover{background:#ec971f}
  .label-danger:hover{background:#c9302c}
  .label-info:hover{background:#31b0d5}
  .label-default:hover{background:#5e5e5e}
  .label-data:hover{background:#8e44ad}
  .label-website:hover{background:#3646a0}
  .label-poster:hover{background:#007d73}

  /* Mobile niceties */
  @media (max-width: 600px){
    .pub{padding:.85rem .9rem}
    .pub-title a{font-size:1.02rem}
    .pub-authors,.pub-venue,.chips{display:block}
  }
</style>

<div id="main">
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
