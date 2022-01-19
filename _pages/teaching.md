---
layout: page
title: Teaching
permalink: /teaching/
description: A list of courses that I have either facilitated or assisted with.
nav: true
---

<!--pages/teaching.md -->
<div class="teaching">
    {%- assign teaching_entries = site.teaching | sort: "start_date" | reverse %}
    {%- for entry in teaching_entries %}
        {% include teaching_entry.html content=entry%}
    {% endfor %}
</div>