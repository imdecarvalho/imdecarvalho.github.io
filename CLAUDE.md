# CLAUDE.md

Este repo é o site pessoal de Isabella de Carvalho (https://imdecarvalho.github.io), publicado no GitHub Pages com Jekyll nativo (sem tema externo; plugins só jekyll-seo-tag e jekyll-sitemap). O GitHub faz o build a cada mudança na `main`. Não existe build local; não instale nada.

A Isabella não programa. Ela pede mudanças em linguagem natural, em inglês ou português. Responda na língua dela, em linguagem simples, sem jargão técnico (diga "publiquei a alteração", não "fiz commit").

## Estrutura do repo

```
_config.yml              nome, email, LinkedIn, foto, CV, plugins
_data/i18n.yml           textos fixos da interface em EN e FR (frase sob a foto, cidade, rótulos)
_includes/content/en/    O TEXTO DO SITE em inglês: home.md, research.md, experience.md
_includes/content/fr/    o mesmo texto em francês
_includes/components/    peças do layout: context.html (idioma/modo), icon.html (ícones), papers.html (lista de artigos)
_layouts/                default.html (base de todas as páginas: navbar, rodapé), home.html (foto + coluna), page.html, paper.html
_pages/en/ e _pages/fr/  "cascas" das páginas (+ subpasta dark/ para o modo escuro). Não editar.
_research/               artigos (um .md por artigo)
assets/css/style.css     todo o visual
assets/img/              profile.jpg (foto), daisies.svg (margaridas do fundo)
files/                   cv.pdf e papers/ (PDFs dos artigos)
_docs/                   especificação original e modelo de artigo (fora do site)
```

O site é bilíngue (inglês e francês) e tem modo claro (padrão) e escuro, **sem JavaScript**: cada página existe em 4 endereços (`/research/`, `/dark/research/`, `/fr/research/`, `/fr/dark/research/`). Os arquivos em `_pages/` são só "cascas" e **não devem ser editados**: o texto de cada página fica num único arquivo por idioma em `_includes/content/en/` e `_includes/content/fr/`, e as 2 cascas (claro/escuro) de cada idioma incluem esse arquivo. O visual é um só para todas as páginas: `_layouts/default.html` + `assets/css/style.css`.

## Onde fica cada informação

**Toda mudança de conteúdo é feita nos dois idiomas** (EN e FR), com o mesmo conteúdo. Se ela escrever só num idioma, traduzir para o outro; cargos e nomes oficiais (ex.: "Junior Data and Policy Analyst", nomes de cursos) ficam no original.

| Pedido sobre... | Arquivo |
|---|---|
| Nome, email, LinkedIn, descrição no Google, foto ligada/desligada | `_config.yml` |
| Frase sob a foto ("Master's candidate..."), cidade, textos fixos da interface | `_data/i18n.yml` (EN e FR) |
| Bio, interesses, formação, idiomas | `_includes/content/en/home.md` e `_includes/content/fr/home.md` |
| Pesquisa individual, bolsas, disciplinas com pesquisa | `_includes/content/en/research.md` e `.../fr/research.md`, seção Research / Recherche |
| MUN, jornal de direito, projetos em grupo, clubes | `_includes/content/en/research.md` e `.../fr/research.md`, seção Projects / Projets |
| Artigo ou paper completo | novo arquivo em `_research/<nome-curto>.md` (modelo em `_docs/paper-template.md`) + PDF em `files/papers/` |
| Estágios, empregos, voluntariado | `_includes/content/en/experience.md` e `.../fr/experience.md` |
| CV ou foto | `files/cv.pdf`, `assets/img/profile.jpg` (manter o nome; foto quadrada, 480×480, JPEG < 60 KB, sem metadados) |

Na dúvida entre Research e Projects: trabalho individual com pergunta de pesquisa vai em Research; atividade em grupo ou extracurricular vai em Projects.

## Formatos

Entrada de experiência, projeto ou formação: título (`###`, preto e maior), subtítulo com organização, cidade e datas (linha seguida de `{: .meta}`, cinza) e texto (cinza-escuro). Linhas em branco exatamente como abaixo:

    ### Role

    Organization, City · Mon YYYY to Mon YYYY
    {: .meta}

    One or two sentences on what she did and the result. [Link](url)

As seções da página são títulos `##`.

Em francês, datas no formato `juin 2024 – août 2024` (mês minúsculo, travessão).

Artigo em `_research/` (só em inglês; a página aparece nas duas versões da aba Research): copiar `_docs/paper-template.md`. Front matter com title, date, status, supervisor, abstract, pdf, full_text. Notas de rodapé no formato kramdown `[^1]`. A linha `* Table of contents` + `{:toc}` gera o índice. `full_text: false` por padrão: a página mostra só o resumo e "Full text available on request", e o botão PDF fica escondido. Só mudar para `true` se ela confirmar que pode publicar o texto completo. A aba Research lista os artigos sozinha.

Pendências ficam como comentários Liquid, que não aparecem no site nem no código-fonte da página:

    {% comment %} TODO: ... {% endcomment %}

## Regras

- Sem JavaScript. Idioma e modo claro/escuro ficam no endereço da página; não adicionar scripts.
- Página nova: criar o texto em `_includes/content/en/` e `fr/`, e as 4 cascas em `_pages/en/`, `_pages/en/dark/`, `_pages/fr/`, `_pages/fr/dark/` copiando as existentes (mudar `ref`, `title`, `nav_order`, `permalink`).
- Pedido de conteúdo: editar só os arquivos da tabela. `_layouts/`, `_includes/` (exceto `_includes/content/`), `assets/` e o resto do `_config.yml` só mudam se ela pedir mudança visual explicitamente.
- O site existe em inglês e francês; nunca em português, mesmo quando o pedido vier em português.
- Seguir o formato das entradas existentes; mais recente primeiro.
- Tom sóbrio e acadêmico: frases curtas, sem autopromoção, sem formato STAR, sem emojis.
- Não inventar datas, títulos, coautores ou resultados. Se faltar algo, perguntar.
- Nunca publicar telefone, endereço ou dados de terceiros.
- Imagens com menos de 300 KB.
- Commits: autora "Isabella de Carvalho <imdecarvalho@users.noreply.github.com>". Nunca mencionar Claude no commit (sem linha Co-Authored-By nem atribuição em pull requests).
- Antes de publicar, resumir em 2 ou 3 linhas o que vai mudar e esperar um "ok".
- Depois de publicar, avisar que o site atualiza em cerca de 1 minuto e dar o link da página alterada.
