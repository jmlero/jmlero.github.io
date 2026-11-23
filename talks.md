---
title: Talks
label: Talks
heading: Talks on running AI agents in production.
subtitle: Available for conferences, meetups and company events, in English or Spanish. Sessions can be tailored for engineering or business audiences.
permalink: /talks/
description: Talks by Jose Molero on Agent Platform Engineering, agent evaluation and agent context.
---

<div class="talk-list talk-list-full">
{% for t in site.data.talks %}
<article class="card talk">
    <p class="talk-status {% if t.status == 'Delivered' %}is-delivered{% endif %}">{{ t.status }}{% if t.event %} · {{ t.event }}{% endif %}{% if t.audience %} · {{ t.audience }}{% endif %}</p>
    <h2>{{ t.title }}</h2>
    <p>{{ t.abstract }}</p>
</article>
{% endfor %}
</div>

<div class="cta">
    <h2>Invite me to your event</h2>
    <p>Full abstracts and speaker details are on Sessionize.</p>
    <div class="actions">
        <a href="{{ site.sessionize }}" target="_blank" rel="noopener" class="btn btn-light">Sessionize profile</a>
        <a href="/connect/" class="btn btn-ghost">Contact me</a>
    </div>
</div>
