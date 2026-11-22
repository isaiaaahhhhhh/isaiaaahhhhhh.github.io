---
layout: default
title: Home
---

<style>
  .section { margin: 0 0 3em; }
  .section h2 { border-bottom: 1px solid #333; padding-bottom: .3em; }
  .section .intro { opacity: .75; margin-top: -.4em; }

  .projects {
    display: grid;
    grid-template-columns: repeat(auto-fill, minmax(240px, 1fr));
    gap: 1.25em;
    margin-top: 1.25em;
  }
  .project {
    background: #1a1a1a;
    border: 1px solid #333;
    border-radius: 8px;
    padding: 1.1em 1.2em;
    display: flex;
    flex-direction: column;
  }
  .project img, .project video, .project .yt { width: 100%; border-radius: 4px; margin-bottom: .8em; }
  .project .yt { aspect-ratio: 16 / 9; height: auto; border: 0; }
  .project h3 { margin: 0 0 .4em; }
  .project p { margin: 0 0 .8em; flex: 1; }
  .project p.team { flex: 0; margin: -.2em 0 .6em; font-size: .85em; opacity: .7; }
  .kind { align-self: flex-start; font-size: .7em; text-transform: uppercase; letter-spacing: .08em; padding: .15em .6em; border: 1px solid #555; border-radius: 999px; margin-bottom: .6em; }
  .tags { list-style: none; padding: 0; margin: 0 0 .8em; display: flex; flex-wrap: wrap; gap: .4em; }
  .tags li { font-size: .75em; padding: .15em .6em; border: 1px solid #555; border-radius: 999px; margin: 0; }
  .tags li:before { content: none; }
  .project-links a { margin-right: 1em; }
  .project-links a.primary { font-weight: bold; }

  .other { list-style: none; padding: 0; margin: 1em 0 0; }
  .other li { padding: .7em 0; border-bottom: 1px solid #2a2a2a; margin: 0; }
  .other li:before { content: none; }
  .other .other-desc { display: block; opacity: .75; font-size: .9em; margin: .2em 0; }
  .other .project-links { font-size: .9em; }
</style>

<section id="about" class="section" markdown="1">

## About Me

Hi, I'm Isaiah! Write a few sentences here about who you are — what you're studying
or working on, what kinds of things you like to build, and what you're looking for
(internships, jobs, collaborators, etc.).

**Skills:** Language, Framework, Tool, Another Tool

**Find me:** [GitHub](https://github.com/isaiaaahhhhhh) · [Email](mailto:you@example.com)

</section>

{% assign featured = site.data.projects | where_exp: "p", "p.case_study" %}
{% assign others = site.data.projects | where_exp: "p", "p.case_study == nil" %}

<section id="case-studies" class="section">
  <h2>Case Studies</h2>
  <p class="intro">Three projects in depth: the problem, the constraints, what failed, and what I changed.</p>
  <div class="projects">
    {% for project in featured %}
    <article class="project">
      {% if project.kind %}<span class="kind">{{ project.kind }}</span>{% endif %}
      {% include project-media.html p=project %}
      <h3><a href="{{ project.case_study | relative_url }}">{{ project.title }}</a></h3>
      {% if project.team %}<p class="team">{{ project.team }}</p>{% endif %}
      <p>{{ project.description }}</p>
      {% if project.tags %}
      <ul class="tags">
        {% for tag in project.tags %}<li>{{ tag }}</li>{% endfor %}
      </ul>
      {% endif %}
      <div class="project-links">
        <a class="primary" href="{{ project.case_study | relative_url }}">Read case study →</a>
        {% if project.link %}<a href="{{ project.link }}">Live →</a>{% endif %}
        {% if project.repo %}<a href="{{ project.repo }}">Code →</a>{% endif %}
      </div>
    </article>
    {% endfor %}
  </div>
</section>

{% if others.size > 0 %}
<section id="other-work" class="section">
  <h2>Other Work</h2>
  <ul class="other">
    {% for project in others %}
    <li>
      <strong>{{ project.title }}</strong>{% if project.team %} · <span style="opacity:.7">{{ project.team }}</span>{% endif %}
      <span class="other-desc">{{ project.description }}</span>
      <span class="project-links">
        {% if project.link %}<a href="{{ project.link }}">Live →</a>{% endif %}
        {% if project.repo %}<a href="{{ project.repo }}">Code →</a>{% endif %}
        {% for l in project.links %}<a href="{{ l.url | relative_url }}">{{ l.label }} →</a>{% endfor %}
      </span>
    </li>
    {% endfor %}
  </ul>
</section>
{% endif %}
