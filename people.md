---
title: People
description: Lab members, trainees, alumni, and collaborators.
permalink: /people/
hide_title: true
---

<div class="container content-page">

{% assign current_people = site.people | where: "status", "current" | sort: "order" %}
{% assign past_people = site.people | where: "status", "past" | sort: "order" %}

<h2>Wang Lab Members</h2>
<div class="people-list">
{% for person in current_people %}
  <article class="person-card person-row" id="{{ person.name | slugify }}">
    <div class="person-sidebar">
      {% assign photo_filename = person.photo | default: person.photo_filename %}
      {% if photo_filename %}
        <img class="person-photo" src="{{ '/assets/img/people/' | append: photo_filename | relative_url }}" alt="{{ person.name }}">
      {% else %}
        <div class="person-avatar">{{ person.initials }}</div>
      {% endif %}
      <div class="person-meta">
        <strong>{{ person.name }}</strong><br>
        {{ person.role }}<br>
        {% if person.dates %}{{ person.dates }}<br>{% endif %}
        {% if person.email_display %}<em>{{ person.email_display }}</em><br>{% endif %}
        {% if person.ucsf_profile %}<a class="person-link" href="{{ person.ucsf_profile }}"><img class="mem-icon" src="{{ '/assets/img/logo/ucsf_logo_black.svg' | relative_url }}" alt="" aria-hidden="true">UCSF Profile</a><br>{% endif %}
        {% if person.orcid_url %}<a class="person-link" href="{{ person.orcid_url }}"><img class="mem-icon" src="{{ '/assets/img/logo/orcid_logo.svg' | relative_url }}" alt="" aria-hidden="true">{{ person.orcid_id | default: "ORCID" }}</a><br>{% elsif person.orcid_id %}<span class="person-link"><img class="mem-icon" src="{{ '/assets/img/logo/orcid_logo.svg' | relative_url }}" alt="" aria-hidden="true">ORCID: {{ person.orcid_id }}</span><br>{% endif %}
        {% if person.google_scholar %}<a class="person-link" href="{{ person.google_scholar }}"><img class="mem-icon" src="{{ '/assets/img/logo/gscholar_logo.svg' | relative_url }}" alt="" aria-hidden="true">Scholar Citations</a><br>{% endif %}
        {% if person.twitter %}<a class="person-link" href="{{ person.twitter }}"><img class="mem-icon" src="{{ '/assets/img/logo/twitter_logo.svg' | relative_url }}" alt="" aria-hidden="true">Twitter</a><br>{% endif %}
        {% if person.github %}<a class="person-link" href="{{ person.github }}"><img class="mem-icon" src="{{ '/assets/img/logo/github_logo.svg' | relative_url }}" alt="" aria-hidden="true">{{ person.github_label | default: "GitHub" }}</a><br>{% endif %}
        {% if person.linkedin %}<a class="person-link" href="{{ person.linkedin }}"><img class="mem-icon" src="{{ '/assets/img/logo/linkedin_logo.svg' | relative_url }}" alt="" aria-hidden="true">LinkedIn</a><br>{% endif %}
        {% if person.website %}<a class="person-link" href="{{ person.website }}">{{ person.website_label | default: "Website" }}</a><br>{% endif %}
      </div>
    </div>
    <div class="person-main">
      {% assign bio = person.content | strip %}
      {% if bio != "" %}
        <div class="person-bio">{{ person.content | markdownify }}</div>
      {% endif %}
    </div>
  </article>
{% endfor %}
</div>

<hr>

<h2>Wang Lab Alumni</h2>
<div class="people-list alumni-list">
{% for person in past_people %}
  <article class="person-card alumni-row" id="{{ person.name | slugify }}">
    {% assign photo_filename = person.photo | default: person.photo_filename %}
    {% if photo_filename %}
      <img class="person-photo" src="{{ '/assets/img/people/' | append: photo_filename | relative_url }}" alt="{{ person.name }}">
    {% else %}
      <div class="person-avatar">{{ person.initials }}</div>
    {% endif %}
    <div class="person-main">
      <div class="person-meta">
        <strong>{{ person.name }}</strong><br>
        {{ person.role }}<br>
        {% if person.dates %}{{ person.dates }}<br>{% endif %}
      </div>
      {% assign bio = person.content | strip %}
      {% if bio != "" %}
        <div class="person-bio">{{ person.content | markdownify }}</div>
      {% else %}
        <div class="person-bio"><p>Subsequently: [position to add].</p></div>
      {% endif %}
    </div>
  </article>
{% endfor %}
</div>

{% comment %}
Member timeline preserved for future use in _includes/member-timeline.html
and _data/member_timeline.yml.
{% endcomment %}

</div>
