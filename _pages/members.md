---
layout: page
permalink: /members/
title: Members
description: Researchers and students of the PAMI Lab.
nav: true
nav_order: 4
---

## Principal Investigator

<div class="table-responsive">
<table class="table table-sm"><thead><tr><th>Name</th><th>Personal Page</th></tr></thead><tbody>
{% for member in site.data.members.pi %}<tr><td>{{ member.name }}</td><td>{% if member.personal_page %}<a href="{{ member.personal_page }}">Profile</a>{% endif %}</td></tr>{% endfor %}
</tbody></table></div>

## Current Students
{% assign undergraduate_groups = site.data.members.current_students.undergraduate %}
{% for group in undergraduate_groups %}
### {{ group[0] | capitalize }}
<div class="table-responsive"><table class="table table-sm"><thead><tr><th>Name</th><th>Personal Page</th></tr></thead><tbody>
{% for member in group[1] %}<tr><td>{{ member.name }}</td><td>{% if member.personal_page %}<a href="{{ member.personal_page }}">Profile</a>{% endif %}</td></tr>{% endfor %}
</tbody></table></div>
{% endfor %}

{% for level in site.data.members.current_students %}
  {% unless level[0] == 'undergraduate' %}
    {% if level[1].size > 0 %}
### {{ level[0] | capitalize }} Students
<div class="table-responsive"><table class="table table-sm"><thead><tr><th>Name</th><th>Personal Page</th></tr></thead><tbody>
{% for member in level[1] %}<tr><td>{{ member.name }}</td><td>{% if member.personal_page %}<a href="{{ member.personal_page }}">Profile</a>{% endif %}</td></tr>{% endfor %}
</tbody></table></div>
    {% endif %}
  {% endunless %}
{% endfor %}

## Alumni
{% for group in site.data.members.alumni %}
### {{ group[0] | capitalize }} Alumni
<div class="table-responsive"><table class="table table-sm"><thead><tr><th>Name</th><th>Thesis Title</th><th>Graduation Year</th><th>Study Program</th></tr></thead><tbody>
{% for member in group[1] %}<tr><td>{{ member.name }}</td><td>{{ member.thesis_title }}</td><td>{{ member.graduation_year }}</td><td>{{ member.study_program }}</td></tr>{% endfor %}
</tbody></table></div>
{% endfor %}
