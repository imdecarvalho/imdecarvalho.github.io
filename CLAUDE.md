# CLAUDE.md

Este repo é o site pessoal de Isabella de Carvalho (https://imdecarvalho.github.io), publicado no GitHub Pages com Jekyll nativo (sem tema externo; plugins só jekyll-seo-tag e jekyll-sitemap). O GitHub faz o build a cada mudança na `main`. Não existe build local; não instale nada.

A Isabella não programa. Ela pede mudanças em linguagem natural, em inglês ou português. Responda na língua dela, em linguagem simples, sem jargão técnico (diga "publiquei a alteração", não "fiz commit").

## Onde fica cada informação

O site é bilíngue: inglês na raiz, francês em `fr/`. **Toda mudança de conteúdo é feita nos dois idiomas** (EN e FR), com o mesmo conteúdo. Se ela escrever só num idioma, traduzir para o outro; cargos e nomes oficiais (ex.: "Junior Data and Policy Analyst", nomes de cursos) ficam no original.

| Pedido sobre... | Arquivo |
|---|---|
| Nome, email, LinkedIn, descrição no Google, foto ligada/desligada | `_config.yml` |
| Frase sob a foto ("Master's candidate..."), cidade, textos fixos da interface | `_data/i18n.yml` (EN e FR) |
| Bio, interesses, formação, idiomas | `index.md` e `fr/index.md` |
| Pesquisa individual, bolsas, disciplinas com pesquisa | `research.md` e `fr/research.md`, seção Research / Recherche |
| MUN, jornal de direito, projetos em grupo, clubes | `research.md` e `fr/research.md`, seção Projects / Projets |
| Artigo ou paper completo | novo arquivo em `_research/<nome-curto>.md` (modelo em `_docs/paper-template.md`) + PDF em `files/papers/` |
| Estágios, empregos, voluntariado | `experience.md` e `fr/experience.md` |
| CV ou foto | `files/cv.pdf`, `files/photo.jpg` (manter o nome do arquivo) |

Na dúvida entre Research e Projects: trabalho individual com pergunta de pesquisa vai em Research; atividade em grupo ou extracurricular vai em Projects.

## Formatos

Entrada de experiência ou projeto (o `\\` no fim da primeira linha é a quebra de linha; uma linha em branco entre entradas):

    **Role**, Organization, City · Mon YYYY to Mon YYYY\\
    One or two sentences on what she did and the result. [Link](url)

Em francês, datas no formato `juin 2024 – août 2024` (mês minúsculo, travessão).

Artigo em `_research/` (só em inglês; a página aparece nas duas versões da aba Research): copiar `_docs/paper-template.md`. Front matter com title, date, status, supervisor, abstract, pdf, full_text. Notas de rodapé no formato kramdown `[^1]`. A linha `* Table of contents` + `{:toc}` gera o índice. `full_text: false` por padrão: a página mostra só o resumo e "Full text available on request", e o botão PDF fica escondido. Só mudar para `true` se ela confirmar que pode publicar o texto completo. A aba Research lista os artigos sozinha.

Pendências ficam como comentários Liquid, que não aparecem no site nem no código-fonte da página:

    {% comment %} TODO: ... {% endcomment %}

## Regras

- Pedido de conteúdo: editar só os arquivos da tabela. `_layouts/`, `_includes/`, `assets/` e o resto do `_config.yml` só mudam se ela pedir mudança visual explicitamente.
- O site existe em inglês e francês; nunca em português, mesmo quando o pedido vier em português.
- Seguir o formato das entradas existentes; mais recente primeiro.
- Tom sóbrio e acadêmico: frases curtas, sem autopromoção, sem formato STAR, sem emojis.
- Não inventar datas, títulos, coautores ou resultados. Se faltar algo, perguntar.
- Nunca publicar telefone, endereço ou dados de terceiros.
- Imagens com menos de 300 KB.
- Commits: autora "Isabella de Carvalho <imdecarvalho@users.noreply.github.com>". Nunca mencionar Claude no commit (sem linha Co-Authored-By nem atribuição em pull requests).
- Antes de publicar, resumir em 2 ou 3 linhas o que vai mudar e esperar um "ok".
- Depois de publicar, avisar que o site atualiza em cerca de 1 minuto e dar o link da página alterada.
