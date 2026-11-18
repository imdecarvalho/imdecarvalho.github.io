---
title: Research and Projects
nav_order: 2
permalink: /research/
---

## Research

**Research Fellow, Genocide and Mass Violence Studies**, Schaeffer Center for the Study of Genocide, AUP · Spring 2026 to present\\
Competitive fellowship; project supervised by Prof. Stephen Sawyer: *Nation-Building, Identity Absolutism, and Religious Mass Violence in 16th-Century France*. Comparative case study of the St. Bartholomew's Day Massacre (1572) in Paris and Lyon, examining how elite authorisation and civic, judicial and religious institutions coordinated identity-based violence. Archival research at the Archives Municipales de Lyon, Archives Départementales du Rhône, Archives Nationales and Bibliothèque nationale de France.

{% comment %} Papers in the _research folder are listed here automatically, newest first. {% endcomment %}
{% assign papers = site.research | sort: "date" | reverse %}
{% if papers.size > 0 %}
### Papers

<ul class="papers">
{% for paper in papers %}<li><a href="{{ paper.url | relative_url }}">{{ paper.title }}</a><span class="meta">{{ paper.status }} · {{ paper.date | date: "%Y" }}</span>{% if paper.abstract %}<span class="summary">{{ paper.abstract | strip_html | truncatewords: 28 }}</span>{% endif %}</li>
{% endfor %}</ul>
{% endif %}

### Course research

- *Politics of Identification in the French Wars of Religion*, directed study
- Armenian Genocide research project, Racism and Nationalism
- ISIS, transnational terrorism and state failure in Iraq and Syria, Politics of the Middle East
- The Yemen crisis, World Politics (civil conflicts, nuclear proliferation, cyber security)
- Syrian refugee crisis analysis, Borders and Security
- Refugee law, International Law

## Projects

**Founding Member and Editor**, AUP Undergraduate Law Journal, Center for Critical Democracy · Fall 2026 to present\\
Founding member of the first undergraduate law journal at AUP and its student club. Fact-checks legal research, edits student and faculty submissions, and contributes to concept development and outreach. First issue expected Spring 2027.

{% comment %} TODO: add MUN years, conferences, committees and awards. {% endcomment %}
**Senior Delegate**, Model United Nations, AUP\\
Conference with the Sorbonne; current committee simulation on foreign intervention in the Sudan conflict.

**Member**, Global Humanitarian Awareness Club and Law Society, AUP

## Methods and skills

- Methods: archival research, comparative case analysis, policy and data analysis, legal and academic editing
- Tools: Zotero, Excel, Tableau, Python, Microsoft Office
- Coursework in Data Visualization and Applied Statistics
