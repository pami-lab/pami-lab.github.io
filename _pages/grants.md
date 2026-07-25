---
layout: page
permalink: /grants/
title: Grants
description: Research funding supporting the PAMI Lab.
nav: true
nav_order: 5
---

<div class="table-responsive">
<table class="table table-sm"><thead><tr><th>Project</th><th>Funder</th><th>Period</th><th>Role</th><th>Status</th></tr></thead><tbody>
{% for grant in site.data.grants %}<tr><td>{{ grant.title }}</td><td>{{ grant.funder }}</td><td>{{ grant.period }}</td><td>{{ grant.role }}</td><td>{{ grant.status }}</td></tr>{% endfor %}
</tbody></table></div>
