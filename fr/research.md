---
layout: page
lang: fr
ref: research
title: Recherche et projets
nav_order: 2
permalink: /fr/research/
---

## Recherche

**Chercheuse associée (Research Fellow), études sur le génocide et la violence de masse**, Schaeffer Center for the Study of Genocide, AUP · printemps 2026 – aujourd'hui\\
Bourse de recherche sélective ; projet dirigé par le Pr Stephen Sawyer : *Nation-Building, Identity Absolutism, and Religious Mass Violence in 16th-Century France*. Étude de cas comparative du massacre de la Saint-Barthélemy (1572) à Paris et à Lyon, qui examine comment l'autorisation des élites et les institutions civiques, judiciaires et religieuses ont coordonné une violence fondée sur l'identité. Recherches aux Archives municipales de Lyon, aux Archives départementales du Rhône, aux Archives nationales et à la Bibliothèque nationale de France.

{% comment %} Les articles du dossier _research s'affichent ici automatiquement, du plus récent au plus ancien. {% endcomment %}
{% assign papers = site.research | sort: "date" | reverse %}
{% if papers.size > 0 %}
### Articles

<ul class="papers">
{% for paper in papers %}<li><a href="{{ paper.url | relative_url }}">{{ paper.title }}</a><span class="meta">{{ paper.status }} · {{ paper.date | date: "%Y" }}</span>{% if paper.abstract %}<span class="summary">{{ paper.abstract | strip_html | truncatewords: 28 }}</span>{% endif %}</li>
{% endfor %}</ul>
{% endif %}

### Recherches dans le cadre des cours

- *Politics of Identification in the French Wars of Religion*, étude dirigée
- Projet de recherche sur le génocide arménien, cours Racism and Nationalism
- L'État islamique, le terrorisme transnational et la faillite de l'État en Irak et en Syrie, cours Politics of the Middle East
- La crise au Yémen, cours World Politics (conflits civils, prolifération nucléaire, cybersécurité)
- Analyse de la crise des réfugiés syriens, cours Borders and Security
- Droit des réfugiés, cours International Law

## Projets

**Membre fondatrice et éditrice**, AUP Undergraduate Law Journal, Center for Critical Democracy · automne 2026 – aujourd'hui\\
Membre fondatrice de la première revue juridique étudiante de l'AUP et du club associé. Vérification des recherches juridiques, édition des contributions d'étudiants et d'enseignants, participation à la conception du projet et à sa communication. Premier numéro prévu au printemps 2027.

{% comment %} TODO: ajouter les années, conférences, comités et prix du MUN. {% endcomment %}
**Déléguée senior**, Model United Nations, AUP\\
Conférence avec la Sorbonne ; simulation en cours d'un comité sur l'intervention étrangère dans le conflit au Soudan.

**Membre**, Global Humanitarian Awareness Club et Law Society, AUP

## Méthodes et compétences

- Méthodes : recherche en archives, analyse comparative de cas, analyse de politiques publiques et de données, édition juridique et académique
- Outils : Zotero, Excel, Tableau, Python, Microsoft Office
- Cours de visualisation de données et de statistiques appliquées
