---
layout: page
title: Achievements
permalink: /achievements/
description: Highlights of some of my achievements thus far.
nav: true
---

<!--pages/achievements.md -->
<div class="achievements">
    {%- assign achievement_entries = site.achievements | sort: "importance" | reverse %}
    {%- for entry in achievement_entries %}
        {% include achievement_entry.html content=entry%}
    {% endfor %}
</div>