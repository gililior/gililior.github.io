---
layout: home
title: "Home"
permalink: /
author_profile: true

quicklinks:
  - title: "Publications"
    url: "/publications/"
    btn_label: "Browse"
    btn_class: "btn--primary"
    excerpt: "Papers and preprints on evaluating and improving large language models."
  - title: "Teaching"
    url: "/teaching/"
    btn_label: "Course materials"
    btn_class: "btn"
    excerpt: "Lectures, exercises, and resources for ML and NLP students."
---

<section class="hero">
  <div class="hero-inner">
    <span class="hero-kicker">Gili Lior · NLP & LLMs</span>
    <h1>Ph.D. Candidate at The Hebrew University of Jerusalem</h1>
    <p class="subtitle">
      Cognitive perspectives on <strong>evaluating</strong> — and <strong>improving</strong> — large language models.
    </p>
    <div class="cta">
      <a class="btn-pretty btn-primary" href="{{ '/publications/' | relative_url }}">See publications</a>
      <a class="btn-pretty" href="{{ '/assets/cv.pdf' | relative_url }}">Download CV</a>
      <a class="btn-pretty" href="{{ '/#contact' | relative_url }}">Contact</a>
    </div>
    <div class="hero-note">
      Currently researching reliable evaluation of LLMs and cognitively inspired methods to mitigate skill gaps.
    </div>
  </div>
</section>

{% include feature_row id="quicklinks" type="center" %}
