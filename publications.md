---
title: Publications
permalink: /publications/
hide_title: true
---

<div class="container content-page">
<h1 class="plain-page-title">Publications</h1>

<div class="publication-filters" aria-label="Publication filters">
  <button class="publication-filter is-active" type="button" data-filter="all">All Publications</button>
  <button class="publication-filter" type="button" data-filter="key">Key Publications</button>
  <button class="publication-filter" type="button" data-filter="preprint">Preprints</button>
</div>

<p class="publication-note">bold = Wang lab; * = co-first or equal contribution; # = co-last or co-senior</p>

<div class="publication-list">
  {% for publication in site.data.publications %}
    <article class="publication-item" data-key="{{ publication.key }}" data-preprint="{{ publication.preprint }}">
      <div class="publication-layout">
        <div class="publication-figure">
          {% if publication.image_filename %}
            <img src="{{ '/assets/img/publications/' | append: publication.image_filename | relative_url }}" alt="{{ publication.image_alt_text | default: publication.title }}">
          {% else %}
            <div class="publication-image-placeholder" aria-label="Publication image placeholder"></div>
          {% endif %}
        </div>
        <div class="publication-body">
          <h2>{{ publication.title }}</h2>
          <p class="publication-authors">{{ publication.authors_html }}</p>
          <p class="publication-meta"><em>{{ publication.journal }}</em>, {{ publication.year }}</p>

          {% if publication.access.size > 0 or publication.deposited_data.size > 0 %}
            <h3>Access the paper</h3>
            {% if publication.access.size > 0 %}
              <ul class="publication-links">
                {% for link in publication.access %}
                  <li>{% if link.prefix %}{{ link.prefix }}{% endif %}{% if link.url %}<a href="{{ link.url }}">{{ link.label }}</a>{% else %}{{ link.label }}{% endif %}{% if link.links %}{% for child_link in link.links %} <a href="{{ child_link.url }}">{{ child_link.label }}</a>{% endfor %}{% endif %}</li>
                {% endfor %}
              </ul>
            {% endif %}
            {% if publication.deposited_data.size > 0 %}
              <h4>Deposited data</h4>
              <ul class="publication-links">
                {% for link in publication.deposited_data %}
                  <li>{% if link.prefix %}{{ link.prefix }}{% endif %}<a href="{{ link.url }}">{{ link.label }}</a></li>
                {% endfor %}
              </ul>
            {% endif %}
          {% endif %}

          {% if publication.additional_links.size > 0 %}
            <h3>Additional links</h3>
            <ul class="publication-links">
              {% for link in publication.additional_links %}
                <li><a href="{{ link.url }}">{{ link.label }}</a></li>
              {% endfor %}
            </ul>
          {% endif %}
        </div>
      </div>
    </article>
  {% endfor %}
</div>
</div>

<script>
  document.querySelectorAll(".publication-filter").forEach((button) => {
    button.addEventListener("click", () => {
      const filter = button.dataset.filter;

      document.querySelectorAll(".publication-filter").forEach((item) => {
        item.classList.toggle("is-active", item === button);
      });

      document.querySelectorAll(".publication-item").forEach((item) => {
        item.hidden =
          (filter === "key" && item.dataset.key !== "true") ||
          (filter === "preprint" && item.dataset.preprint !== "true");
      });
    });
  });
</script>
