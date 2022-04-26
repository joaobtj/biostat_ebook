
# RMarkdown

## Criando um arquivo Rmd

Para criar um arquivo do tipo Rmd, clique em *File -> New File -> R Markdown*.

<div class="figure">
<img src="image/Rmd.png" alt="Criando um arquivo R Markdown." width="90%" />
<p class="caption">(\#fig:rmd)Criando um arquivo R Markdown.</p>
</div>

Várias opções estão disponíveis por padrão. Escolha aquela que julgar mais adequada ou então clique no botão *Create Empty Document*.

Um arquivo Rmd é composto por três componentes básicos: Cabeçalho, Texto e Código.

Abaixo, um exemplo do cabeçalho de um arquivo Rmd que exporta no formato HTML:

```yaml
---
title: "Olá R Markdown"
author: "Fulano"
date: "2022-04-19"
output: html_document
---
```

Este cabeçalho deve ser escrito entre `---` (traço triplo) e utiliza a síntaxe YAML [(pt.wikipedia.org/wiki/YAML)](https://pt.wikipedia.org/wiki/YAML).

O texto (ou narrativa) inicia logo após o cabeçalho e segue a síntaxe demonstrada na seção \@ref(rmdsintaxe). 

O código inicia com ```` ```{r} ```` (aspas triplas) em que `r` indica a linguagem utilizada e termina com ```` ``` ```` (aspas triplas) novamente. Opções do código podem ser escritas dentro das chaves: ```` ```{r, out.width="90%"} ````.

Para renderizar o arquivo, basta clicar no botão `Knit` ou então utilizar o atalho <button>Ctrl</button> + <button>Shift</button> + <button>K</button>

## Síntaxe da linguagem R Markdown {#rmdsintaxe}

A síntaxe da linguagem RMarkdown é bastante simples mas poderosa. Neste capítulo, serão apresentados os principais elementos.

A separação entre os parágrafos deve ser feita com dois espaços verticais (enter).

Para deixar um texto em *itálico*, este deve ser escrito entre `*` (asterisco simples): ``*itálico*`` = *itálico*.  Já para deixar o texto em **negrito**, este deve ser escrito entre  ``**`` (asterisco duplo): ``**negrito**`` = **negrito**. E para ***itálico e negrito***? adivinhem, `***` (asterisco triplo): ``***itálico e negrito***`` = ***itálico e negrito***.

Sobrescrito deve ficar entre `^` (circunflexo): ``m^3^/s`` = m^3^/s. Já o subscrito é escrito entre `~` (til): `H~2~O` =  H~2~O.

Um link para uma página externa: `[Site da UFSC](https://ufsc.br)` = [Site da UFSC](https://ufsc.br)

Uma lista marcada deve ter cada item precedido por um `*` (asterisco):

`* item 1`

`* item 2`

Retorna:

* item 1
* item 2

Uma lista numerada dever ter cada item precedido por um número:

`1. item 1`

`1. item 2`

`1. item 3`

Retorna:

1. item 1
1. item 2
1. item 3


Os títulos das seções são escritos após `#` (sustenido ou hashtag).

```markdown
# Título nível 1

## Título nível 2

### Título nível 3
```



Mais opções podem ser encontradas na folha de dicas do RStudio: [R Markdown Cheat Sheet](https://rstudio.com/wp-content/uploads/2015/02/rmarkdown-cheatsheet.pdf)

Muito mais informações podem ser encontradas neste livro bastante completo: [R Markdown: The Definitive Guide](https://bookdown.org/yihui/rmarkdown/)

## Formatos de saída

Os principais formatos de saída para documentos ^[não irei tratar de apresentações neste livro] são:

* `html_document` - saída em formato HTML
* `pdf_document` - saída em formato PDF
* `word_document` - saída em formato Word (.doc)
* `odt_document` - saída em formato OpenDocument (.odt) para OpenOffice e LibreOffice
* `rtf_document` - saída em formato Rich Text Format (.rtf\)



