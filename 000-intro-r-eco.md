

# (PART\*) O ecossistema R {-} 

# Introdução - O ecossistema R {-#intro-r}

![](https://www.r-project.org/logo/Rlogo.svg){width=50px}

O R ([www.r-project.org](https://www.r-project.org)) é uma linguagem de programação *open-source*, distribuído sob a licença GNU, e multiplataforma, disponível para Windows, MacOS e algumas distribuições Linux. Embora esteja se tornando cada vez mais de uso geral, ele foi originalmente concebido como uma linguagem de programação estatística. Dessa forma, além de análises estatísticas, é capaz de produzir representações gráficas de altíssima qualidade, além de relatórios. 

Foi criado por Ross Ihaka e Robert Gentleman^[O nome R vem das iniciais dos nomes dos autores.] na Universidade de Auckland, Nova Zelândia. Atualmente, é desenvolvido pela *R Foundation*.

É amplamente utilizado pelas grandes empresas, órgãos governamentais e, claro, na pesquisa acadêmica.

A popularidade do R nas ciências tem sido demonstrada por diversos estudos, como o de @Recology, em que os autores analisaram mais de 60 mil artigos publicados nos principais periódicos da área de Ecologia e observaram um aumento linear do uso do R como ferramenta principal para a análise de dados. 


![](https://esajournals.onlinelibrary.wiley.com/cms/asset/ab2bdcf1-af62-4e5e-bd0c-32f60c1138c7/ecs22567-fig-0001-m.png)<!-- -->



## Pacotes do R {-}

O R conta com uma comunidade grande e ativa *(useR!)* que está sempre contribuindo com a melhoria do programa por meio do desenvolvimento de pacotes que estendem as funções originais da linguagem R. Atualmente, ^[ano de 2022] o site do *CRAN (Comprehensive R Archive Network)* conta com mais de 18 mil^[Consulte o número atualizado em https://cran.r-project.org/web/packages/] pacotes para o R.

Os pacotes disponíveis no CRAN são facilmente instalados por meio de funções disponiveis no próprio R. Também há a possibilidade de instalar pacotes diretamente do [GitHub](https://github.com/), local em que muitos dos desenvolvedores de pacotes *open-source* hospedam seus trabalhos. 

## RStudio {-}

O [RStudio](https://www.rstudio.com/) é um ambiente de desenvolvimento integrado - IDE^[do inglês *Integrated Development Environment*] com versão *open-source* e comercial.

Foi desenvolvido para aumentar a produtividade dos usuários. Inclui um console, um editor com destaque visual com suporte a execução direta do código, e ferramentas para manejar arquivos, plotagens, histórico, entre outros.

## RStudio Cloud {-#rcloud}

É uma versão do RStudio que pode ser acessado via navegador, de modo que nada precisa ser instalado na máquina localmente.

Além de poder utilizar todas as funcionalidades do R e do RStudio, com o RStudio Cloud é mais fácil compartilhar os projetos com sua equipe.

Para começar a utilizar, basta criar uma conta no site [rstudio.cloud](https://rstudio.cloud/). Existe uma conta gratuita que pode ser suficiente para usuários ocasionais. Para quem necessitar, existem também planos pagos.

## Tidyverse {-}

O universo [*Tidyverse*](https://www.tidyverse.org/) é uma coleção de pacotes para o R elaborados para a ciência dos dados (*data science*). Todos os pacotes compartilham uma filosofia, gramática e estrutura de dados. As funções facilitam a comunicação entre humanos e máquina em comparação com as funções básicas do R.

Para instalar todos os pacotes *tidyverse*:

```r
install.packages("tidyverse")
```

Entre os principais pacotes do *tidyverse* estão:

* `ggplot2`: criar gráficos de altíssima qualidade;
* `dplyr`: manipulação de dados;
* `tidyr`: organização de dados;
* `readr`: leitura de arquivos externos, como csv;
* `purrr`: programação funcional, permite substituir os loops convencionais;
* `tibble`: reinterpretação do quadro de dados (*data-frame*) original;
* `stringr`: trabalhar com textos (*strings*);
* `forcats`: trabalhar com fatores (*factor*).

Existem ainda muitos outros pacotes que podem ser consultados aqui: [www.tidyverse.org/packages](https://www.tidyverse.org/packages/)


## RMarkdown {-}

O Markdown é uma linguagem de marcação em texto puro (*plain text*), em que são utilizadas marcações (muito sutis) para títulos, links e formatações em geral. Seu resultado é bastante legível mesmo sem processamento, diferente de outras linguagens, como HTML ou Latex que requerem muitas tags para formatar o texto.

Uma extensão do Markdown original é a linguagem RMarkdown. Esta é uma poderosa ferramenta que permite combinar as análises e os relatórios em um mesmo documento, pois permite  incluir códigos em R ao longo do documento.

De modo geral, o pacote `knitr` executa os códigos em R e converte o documento de RMarkdown para Markdown. O pacote `pandoc` renderiza o documento Markdown para o formato desejado, que pode ser HTML, PDF, Word, entre muitos outros. 
Mais informações podem ser encontradas em: [R Markdown: The Definitive Guide](https://bookdown.org/yihui/rmarkdown/) e [R Markdown Cookbook](https://bookdown.org/yihui/rmarkdown-cookbook/)

<!-- Os pacotes do *tidyverse* auxiliam nos seguintes passos da análise de dados: -->

<!-- ```{r echo=FALSE} -->
<!-- DiagrammeR::grViz( -->
<!--   "digraph G { -->
<!-- rankdir=LR -->

<!--      compound=true -->

<!--     subgraph cluster { -->
<!--  node [style=filled] -->
<!--         Transformar Visualizar Modelar -->
<!--         label = 'Entender' -->
<!--         color=blue -->
<!--     } -->
<!-- Importar->Organizar -->
<!-- Transformar->Visualizar -->
<!-- Visualizar->Modelar -->
<!-- Modelar->Transformar -->

<!--     Organizar -> Transformar [lhead=cluster] -->
<!--     Modelar->Comunicar[ltail=cluster] -->
<!-- }" -->
<!-- ) -->
<!-- ``` -->
<!-- Adaptado de @R4ds. -->


