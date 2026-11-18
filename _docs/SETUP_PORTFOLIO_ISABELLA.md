# Setup: portfolio acadêmico de Isabella de Carvalho

Este arquivo é a especificação completa. Leia tudo antes de começar. Siga as etapas na ordem e pare nos pontos marcados **[PARAR]** para esperar o humano.

---

## 1. Objetivo

Criar o site pessoal da Isabella de Carvalho (estudante de International and Comparative Politics na American University of Paris, formatura em 2027), substituindo o site atual feito no Canva (isabelladecarvalho.my.canva.site).

Requisitos:
- Sóbrio e acadêmico, no estilo de malojan.github.io/website, joaoguedesneto.github.io e nataliaumansky.github.io: uma coluna, nome e afiliação no topo, bio, páginas de pesquisa e experiência, CV em PDF.
- A Isabella não programa. Depois de pronto, ela atualiza o site só conversando com o Claude. Todo o conteúdo fica em Markdown e o `CLAUDE.md` do repo diz ao Claude onde editar.
- Build e publicação feitos inteiramente pelo GitHub Pages. Nada instalado na máquina dela.

---

## 2. Tecnologia (decidido, não mudar)

| Peça | Escolha |
|---|---|
| Gerador | Jekyll nativo do GitHub Pages (versão 3.x controlada pelo GitHub) |
| Markdown | kramdown (padrão do Jekyll): notas de rodapé, tabelas, índice automático |
| Templates | Liquid, num único `_layouts/default.html` (mais `_layouts/paper.html` para artigos) |
| Visual | Um `assets/style.css` escrito à mão. Sem tema externo, sem Tailwind, sem Bootstrap |
| JavaScript | Nenhum |
| Fontes | Google Fonts via `<link>` no layout |
| Plugins | Só `jekyll-seo-tag` e `jekyll-sitemap` |
| Deploy | GitHub Pages, modo "Deploy from a branch", `main`, pasta raiz |
| Não usar | Gemfile, package.json, GitHub Actions, Node, Astro, Hugo, remote_theme |

Não existe preview local. Não instale Ruby nem Jekyll. A validação visual é feita no site publicado (o build leva 1 a 2 minutos depois do push).

---

## 3. Estrutura de arquivos

```
<usuario>.github.io/
├── _config.yml           nome, email, LinkedIn, descrição, plugins, coleção
├── index.md              Home: bio, interesses, formação, idiomas
├── research.md           Research and Projects: pesquisa, projetos, métodos
├── experience.md         Experience: profissional e voluntariado
├── _research/            coleção: uma página por artigo ou projeto longo
│   └── (vazio no início)
├── files/
│   ├── cv.pdf
│   ├── photo.jpg         opcional
│   └── papers/           PDFs e imagens dos artigos
├── _layouts/
│   ├── default.html
│   └── paper.html
├── assets/
│   └── style.css
├── _docs/                este arquivo (excluído do build)
├── CLAUDE.md             regras de edição (conteúdo na seção 9)
└── README.md             instruções simples para a Isabella (seção 10)
```

Regras de organização:
- Um `.md` por aba, não um por item. Seções da aba são subtítulos `##`.
- O menu é gerado a partir do front matter das páginas (`title`, `nav_order`). Ordem: Home, Research and Projects, Experience, CV (link para `files/cv.pdf`).
- Um projeto só ganha página própria em `_research/` quando tiver texto longo (artigo, paper). A aba Research lista essas páginas sozinha, por data.

### `_config.yml` (base)

```yaml
title: "Isabella de Carvalho"
tagline: "International and Comparative Politics · The American University of Paris"
description: "Final-year International and Comparative Politics student at the American University of Paris, researching mass violence, international security and conflict."
url: "https://<usuario>.github.io"
lang: en
email: "TODO: confirmar"
linkedin: "https://www.linkedin.com/in/isabella-maria-decarvalho"
cv: "/files/cv.pdf"
photo: ""            # "/files/photo.jpg" se ela quiser foto

plugins:
  - jekyll-seo-tag
  - jekyll-sitemap

collections:
  research:
    output: true
    permalink: /research/:name/

defaults:
  - scope: { type: research }
    values: { layout: paper }
  - scope: { path: "" }
    values: { layout: default }

exclude: [_docs, CLAUDE.md, README.md]
```

### Coleção `_research/` (artigos)

Cada artigo tem dois formatos: o PDF oficial em `files/papers/` e uma página `.md` legível no navegador.

```markdown
---
title: "Nation-Building, Identity Absolutism, and Religious Mass Violence in 16th-Century France"
date: 2026-05-01
status: Working paper
supervisor: Prof. Stephen Sawyer
abstract: "Comparative case study of the St. Bartholomew's Day Massacre (1572) in Paris and Lyon..."
pdf: /files/papers/st-bartholomew.pdf
full_text: false
---

## Introduction
Texto com notas de rodapé[^1].

[^1]: Archives Municipales de Lyon, ...
```

- `paper.html` mostra no topo: título, status, orientador, data, resumo e botão "PDF". Abaixo, índice das seções (`{:toc}` do kramdown) e o texto.
- `full_text: false`: mostra só o cabeçalho, o resumo e "Full text available on request". Publicar o texto completo conta como publicação prévia, então o padrão é `false` até a Isabella confirmar com o orientador.
- Em `research.md`, um loop Liquid lista os itens da coleção (título, status, resumo de 1 linha, link), do mais recente ao mais antigo, acima da lista de pesquisas de disciplina.

---

## 4. Design

- Coluna de ~680px, muito espaço em branco, sem ícones coloridos, sem animação.
- Manter a identidade do site atual, mais contida: fundo creme claro (~#f6f1ea), texto quase preto (~#1c1c1c), terracota (~#c97b5f) só no nome e nos links.
- Títulos em serifada display (Cormorant Garamond ou EB Garamond); corpo em serifada de leitura (Source Serif 4), 18px, line-height ~1.6.
- Menu discreto em texto no topo; rodapé com email, LinkedIn e ano.
- Modo escuro automático (`prefers-color-scheme`), mantendo contraste AA.
- Responsivo: no celular, menu em uma linha que quebra e margens de 20px.
- Formato visual das entradas:
  ```markdown
  **Role**, Organization, City · Mon YYYY to Mon YYYY
  One or two sentences on what she did and the result.
  ```
- Sem formato STAR, sem gráficos de habilidades, sem barras de idioma.

---

## 5. Conteúdo do site (em inglês)

Fonte: CV dela para a PSIA (novembro 2026) mais o site do Canva. O site é genérico, **não citar a PSIA nem nenhum programa específico**. Não inventar nada; o que faltar fica como `<!-- TODO: ... -->`.

### Home (`index.md`)

Bio (pode reescrever levemente, mantendo os fatos):
> I am a final-year International and Comparative Politics student at the American University of Paris, with a minor in History, and a research fellow at the Schaeffer Center for the Study of Genocide. My research looks at how states and societies escalate toward mass violence and how it can be prevented, currently through religious violence in sixteenth-century France. My coursework spans international conflict, security, international law and political history. I am applying to Master's programmes in international security for 2027.

Research interests: Mass violence and genocide studies · International security · Conflict analysis · International law and refugee law · Migration policy

Education:
- **B.A. in International and Comparative Politics, Minor in History**, The American University of Paris · 2023 to 2027. Honors Program; Provost's List; Schaeffer Center for the Study of Genocide Scholarship. GPA 3.66/4.0 <!-- TODO: confirmar se ela quer mostrar o GPA -->
- **High School Diploma**, Rudolf Steiner School, New York · 2019 to 2023

Languages: English (native), Portuguese (native), Spanish (fluent), French (advanced)

### Research and Projects (`research.md`)

**Research**

- **Research Fellow, Genocide and Mass Violence Studies**, Schaeffer Center for the Study of Genocide, AUP · Spring 2026 to present
  Competitive fellowship; project supervised by Prof. Stephen Sawyer: *Nation-Building, Identity Absolutism, and Religious Mass Violence in 16th-Century France*. Comparative case study of the St. Bartholomew's Day Massacre (1572) in Paris and Lyon, examining how elite authorisation and civic, judicial and religious institutions coordinated identity-based violence. Archival research at the Archives Municipales de Lyon, Archives Départementales du Rhône, Archives Nationales and Bibliothèque nationale de France.

- Course research projects (lista curta, 1 linha cada):
  - *Politics of Identification in the French Wars of Religion*, directed study
  - Armenian Genocide research project, Racism and Nationalism
  - ISIS, transnational terrorism and state failure in Iraq and Syria, Politics of the Middle East
  - The Yemen crisis, World Politics (civil conflicts, nuclear proliferation, cyber security)
  - Syrian refugee crisis analysis, Borders and Security
  - Refugee law, International Law

**Projects**

- **Founding Member and Editor**, AUP Undergraduate Law Review, Center for Critical Democracy · Fall 2026 to present <!-- TODO: confirmar nome oficial: "Law Review" ou "Law Journal" -->
  Founding member of the first undergraduate law journal at AUP and its student club. Fact-checks legal research, edits student and faculty submissions, and contributes to concept development and outreach. First issue expected Spring 2027.
- **Senior Delegate**, Model United Nations, AUP <!-- TODO: anos, conferências, prêmios -->
  Conference with the Sorbonne; current committee simulation on foreign intervention in the Sudan conflict.
- **Member**, Global Humanitarian Awareness Club and Law Society, AUP

**Methods and skills**

- Methods: archival research, comparative case analysis, policy and data analysis, legal and academic editing
- Tools: Zotero, Excel, Tableau, Python, Microsoft Office
- Coursework in Data Visualization and Applied Statistics

### Experience (`experience.md`)

**Professional**

- **Junior Data and Policy Analyst**, NYC Department of Citywide Administrative Services (DCAS), New York · Jun 2024 to Aug 2024 <!-- TODO: confirmar título oficial; o Canva dizia "Purchasing Division Intern" -->
  Reviewed and cross-referenced city procurement records to assess how equity policies for women- and minority-owned businesses (M/WBE) were applied in practice; delivered analysis the division could act on.
- **Election Poll Worker**, Local Judicial Election, Kings County, Brooklyn · Jun 2023
  Registered and checked in voters, keeping a legally compliant polling site running accurately.

**Volunteer**

- **Humanitarian Volunteer**, Global Works, San Juan, Puerto Rico · May 2023 to Jun 2023
  Hurricane Maria reconstruction and community support, working in Spanish.
- **Residential Care Volunteer**, Camphill Kimberton Hills, Pennsylvania · May 2022 to Jun 2022
  Daily care and activity support for adults with disabilities in a self-sustaining farm community.

Os empregos em café e loja (Zia Café, Eli Zabar's) **não** entram no site.

### Correções já aplicadas acima

"Word Politics" → "World Politics"; "Schaefffer" → "Schaeffer"; "Recipiant" → "Recipient"; nomes próprios com maiúscula (Pennsylvania, Hurricane Maria, Camphill Kimberton Hills).

---

## 6. Pendências com a Isabella

Não bloqueiam a criação; ficam como TODO no site até ela responder.

1. Email público: imdecarvalho@outlook.com (CV) ou idecarvalhofha@outlook.com (Canva)?
2. Título no DCAS: "Junior Data and Policy Analyst" ou "Purchasing Division Intern"?
3. Nome oficial do jornal: "Undergraduate Law Review" ou "Undergraduate Law Journal"?
4. CV em PDF geral (não a versão PSIA) e **sem telefone**.
5. Foto: sim ou não.
6. Mostrar o GPA: sim ou não.
7. MUN: conferências, anos, comitês, prêmios.
8. Paper do Schaeffer: publicar só o resumo ou o texto completo (confirmar com o orientador)?

---

## 7. Etapas de execução

**[PARAR] Etapa 1, humano:** criar a conta GitHub da Isabella, criar o repo público `<usuario>.github.io`, clonar nesta pasta. Informar o `<usuario>`.

**Etapa 2, Claude:** criar todos os arquivos da seção 3 com o conteúdo da seção 5 e o design da seção 4. Copiar este arquivo para `_docs/`. Criar `CLAUDE.md` (seção 9) e `README.md` (seção 10). Se `files/cv.pdf` não existir ainda, criar o link mesmo assim e deixar um TODO.

**Etapa 3, Claude:** revisar antes do primeiro push:
- todos os links internos usam `{{ '/caminho' | relative_url }}`
- `{% seo %}` no `<head>`
- nenhum telefone ou endereço em nenhum arquivo
- nenhum plugin fora da lista
- listar ao humano todos os TODOs restantes

**[PARAR] Etapa 4, humano:** aprovar, `git push`, depois ativar Settings → Pages → Deploy from a branch → `main` / `(root)`.

**Etapa 5, Claude + humano:** abrir `https://<usuario>.github.io` e ajustar o visual em rodadas curtas (fontes, espaçamento, celular, modo escuro). Cada rodada: mudança pequena, commit, push, esperar 1 a 2 minutos, conferir.

**[PARAR] Etapa 6, humano:** conectar o Claude da Isabella ao GitHub e testar com ela dois pedidos reais (ex.: "Add my MUN conference to Projects", "Replace my CV"). Anotar no README se as mudanças entram direto na `main` ou viram pull request (nesse caso ela clica em Merge).

**Etapa 7, humano:** checagem final (celular, preview do link no LinkedIn e WhatsApp, PDF abre), atualizar o link no LinkedIn dela, desativar o site do Canva.

Tempo estimado: 1h30 a 2h de sessão, sendo a etapa 5 a mais longa.

---

## 8. Restrições

- Não inventar fatos, datas, títulos, prêmios ou coautores.
- Não publicar telefone, endereço ou dados de terceiros.
- Não adicionar dependências, temas, Actions ou JavaScript.
- Imagens com menos de 300 KB.
- Texto do site em inglês; conversa com o humano em português.

---

## 9. Conteúdo do `CLAUDE.md` (copiar para a raiz do repo)

```markdown
# CLAUDE.md

Este repo é o site pessoal de Isabella de Carvalho, publicado no GitHub Pages com Jekyll nativo (sem tema externo; plugins só jekyll-seo-tag e jekyll-sitemap). O GitHub faz o build a cada mudança na `main`. Não existe build local; não instale nada.

A Isabella não programa. Ela pede mudanças em linguagem natural, em inglês ou português. Responda na língua dela, em linguagem simples, sem jargão técnico (diga "publiquei a alteração", não "fiz commit").

## Onde fica cada informação

| Pedido sobre... | Arquivo |
|---|---|
| Nome, email, LinkedIn, descrição no Google | `_config.yml` |
| Bio, interesses, formação, idiomas | `index.md` |
| Pesquisa individual, bolsas, disciplinas com pesquisa | `research.md`, seção Research |
| MUN, jornal de direito, projetos em grupo, clubes | `research.md`, seção Projects |
| Artigo ou paper completo | novo arquivo em `_research/<nome-curto>.md` + PDF em `files/papers/` |
| Estágios, empregos, voluntariado | `experience.md` |
| CV ou foto | `files/cv.pdf`, `files/photo.jpg` (manter o nome do arquivo) |

Na dúvida entre Research e Projects: trabalho individual com pergunta de pesquisa vai em Research; atividade em grupo ou extracurricular vai em Projects.

## Formatos

Entrada de experiência ou projeto:
    **Role**, Organization, City · Mon YYYY to Mon YYYY
    One or two sentences on what she did and the result. [Link](url)

Artigo em `_research/`: front matter com title, date, status, supervisor, abstract, pdf, full_text. Notas de rodapé no formato kramdown `[^1]`. `full_text: false` por padrão; só mudar para true se ela confirmar que pode publicar o texto completo.

## Regras

- Pedido de conteúdo: editar só os arquivos da tabela. `_layouts/`, `assets/` e o resto do `_config.yml` só mudam se ela pedir mudança visual explicitamente.
- O texto do site é sempre em inglês, mesmo quando o pedido vier em português.
- Seguir o formato das entradas existentes; mais recente primeiro.
- Tom sóbrio e acadêmico: frases curtas, sem autopromoção, sem formato STAR, sem emojis.
- Não inventar datas, títulos, coautores ou resultados. Se faltar algo, perguntar.
- Nunca publicar telefone, endereço ou dados de terceiros.
- Imagens com menos de 300 KB.
- Antes de publicar, resumir em 2 ou 3 linhas o que vai mudar e esperar um "ok".
- Depois de publicar, avisar que o site atualiza em cerca de 1 minuto e dar o link da página alterada.
```

---

## 10. Conteúdo do `README.md` (para a Isabella, em inglês simples)

```markdown
# My website

Live at https://<usuario>.github.io

## How to update it

Open Claude, choose this repository, and ask in plain words. Examples:

- "Add the MUN conference in London to Projects, I was chair of the Security Council, March 2027."
- "Update my bio: I was accepted to the Master's in International Security."
- "Here is my new CV, replace the old one."
- "Turn this Word file into a paper page in Research, abstract only for now."

Claude will tell you what it is going to change and wait for your OK. The site updates about one minute after.

<!-- Etapa 6: anotar aqui se é preciso clicar em "Merge" no GitHub depois de cada mudança. -->

## Uploading a file yourself (optional)

On github.com, open the `files` folder, click "Add file" then "Upload files". To replace your CV, upload a file with exactly the same name: `cv.pdf`.
```
