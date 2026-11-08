---
layout: default
title: Home
---

<style>
  .section { margin: 0 0 3em; }
  .section h2 { border-bottom: 1px solid #333; padding-bottom: .3em; }

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
  .project img, .project video { width: 100%; border-radius: 4px; margin-bottom: .8em; }
  .project h3 { margin: 0 0 .4em; }
  .project p { margin: 0 0 .8em; flex: 1; }
  .tags { list-style: none; padding: 0; margin: 0 0 .8em; display: flex; flex-wrap: wrap; gap: .4em; }
  .tags li { font-size: .75em; padding: .15em .6em; border: 1px solid #555; border-radius: 999px; margin: 0; }
  .tags li:before { content: none; }
  .project-links a { margin-right: 1em; }
</style>

<section id="about" class="section" markdown="1">

## About Me

Hi, I'm Isaiah! Write a few sentences here about who you are — what you're studying
or working on, what kinds of things you like to build, and what you're looking for
(internships, jobs, collaborators, etc.).

**Skills:** Language, Framework, Tool, Another Tool

**Find me:** [GitHub](https://github.com/isaiaaahhhhhh) · [Email](mailto:you@example.com)

</section>

<section id="projects" class="section">
  <h2>Projects</h2>
  <div class="projects">
    {% for project in site.data.projects %}
    <article class="project">
      {% if project.video %}
      <video src="{{ project.video | relative_url }}" {% if project.image %}poster="{{ project.image | relative_url }}"{% endif %} autoplay muted loop playsinline controls preload="metadata"></video>
      {% elsif project.image %}<img src="{{ project.image | relative_url }}" alt="{{ project.title }} screenshot">{% endif %}
      <h3>{{ project.title }}</h3>
      <p>{{ project.description }}</p>
      {% if project.tags %}
      <ul class="tags">
        {% for tag in project.tags %}<li>{{ tag }}</li>{% endfor %}
      </ul>
      {% endif %}
      <div class="project-links">
        {% if project.link %}<a href="{{ project.link }}">Live →</a>{% endif %}
        {% if project.repo %}<a href="{{ project.repo }}">Code →</a>{% endif %}
      </div>
    </article>
    {% endfor %}
  </div>
</section>
