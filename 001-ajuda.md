

# Procurando (e pedindo) ajuda para o R

Antes de pedir ajuda, é sempre uma boa prática estudar para tentar resolver por si mesmo. A grande maioria dos pacotes e funções do R possuem uma boa documentação com exemplos de utilização. Também há diversos fóruns na web especializados com respostas para as perguntas mais frequente e sites com tutoriais detalhados.

Infelizmente, muitos dos textos de ajuda estão na língua inglesa. Aproveite esta chance para treinar e melhorar sua leitura em inglês.

## As funções `help` e `?`

As funções  `help` e `?` fornecem acesso à documentação no próprio R e são equivalentes entre si.

Experimente digitar `?sum` para ver a documentação desta função:

<div class="figure">
<img src="image/helpsum.png" alt="Ajuda da função `sum`" width="90%" />
<p class="caption">(\#fig:helpsum)Ajuda da função `sum`</p>
</div>

Na documentação, é usual haver uma parte com exemplos de uso da função. Estes exemplos podem ser executados com a função `example`:


```r
example(sum) 
```

```
## 
## sum> ## Pass a vector to sum, and it will add the elements together.
## sum> sum(1:5)
## [1] 15
## 
## sum> ## Pass several numbers to sum, and it also adds the elements.
## sum> sum(1, 2, 3, 4, 5)
## [1] 15
## 
## sum> ## In fact, you can pass vectors into several arguments, and everything gets added.
## sum> sum(1:2, 3:5)
## [1] 15
## 
## sum> ## If there are missing values, the sum is unknown, i.e., also missing, ....
## sum> sum(1:5, NA)
## [1] NA
## 
## sum> ## ... unless  we exclude missing values explicitly:
## sum> sum(1:5, NA, na.rm = TRUE)
## [1] 15
```


## Stack Overflow

O [stackoverflow.com](https://stackoverflow.com/) é um site bem organizado especializado na discussão de assuntos relativos à programação. Tópicos marcados com a tag "r" chegam a mais de 440 mil ^[ano de 2022]. Para acessar todos os tópicos com a tag "r", acesse [stackoverflow.com/questions/tagged/r](https://stackoverflow.com/questions/tagged/r).

Este site tem a vantagem de ser bem fácil de fazer buscas. Tente digitar, na caixa de buscas, a seguinte expressão: [r] logistic regression fit^[Suas buscas terão mais resultados se usar as palavras-chave em inglês.]

<div class="figure">
<img src="image/stackoverflow.png" alt="Busca no site (stackoverflow.com)[(https://stackoverflow.com]" width="90%" />
<p class="caption">(\#fig:stack)Busca no site (stackoverflow.com)[(https://stackoverflow.com]</p>
</div>


## Pedir ajuda ao seu professor {#ajuda-professor}


Antes de tudo, vou mostrar um exemplo de como não pedir ajuda ao professor (Figura \@ref(fig:ajudaprof):


<div class="figure">
<img src="image/ajudaprof.jpg" alt="É difícil ajudar com uma foto da tela com baixa qualidade" width="90%" />
<p class="caption">(\#fig:ajudaprof)É difícil ajudar com uma foto da tela com baixa qualidade</p>
</div>

É muito difícil conseguir ajudar baseado apenas em uma foto da tela, ainda mais de baixa qualidade e difícil de ler/entender.^[Baseado em fatos reais.]

Formular uma boa pergunta é 90% do desafio e, muitas vezes, o processo de formular a pergunta já fornece a própria resposta.

Para conseguir ajuda mais rápida e com maior chance de ser adequadamente respondida, siga alguma destas recomendações: 


* Compacte^[Com algum programa como o [7-zip.com](https://www.7-zip.org/)] e compartilhe todo o diretório do seu projeto;
* Compartilhe seu projeto do RStudio Cloud (Seção \@ref(rcloud));
* Utilize o pacote `reprex` (Seção \@ref(reprex)).




## O pacote `reprex` {#reprex}

*Reprex* é a sigla para *reproducible example*, ou exemplo reproduzível. O código que você deseja compartilhar deve ser renderizado dentro da função `reprex::reprex`, como código completo dentro de chaves `{ }`.

```r
reprex::reprex({
  y <- c(1,2,3,4,"a")
  mean(y)
})
```

Esta função cria um arquivo renderizado com o exemplo e também envia o resultado direto para a área de transferência para poder ser colado com o <button>Ctrl</button> + <button>V</button>.

 O resultado da função acima pode ser visto abaixo:



``` r
y <- c(1,2,3,4,"a")
mean(y)
#> Warning in mean.default(y): argumento não é numérico nem lógico: retornando NA
#> [1] NA
```

















