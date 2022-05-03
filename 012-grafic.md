# Gráficos estatísticos




> Uma imagem vale mais que mil palavras

Os gráficos estatísticos são utilizados para fazer uma representação visual dos dados. São elaborados para serem vistos por você e por outras pessoas, por isso, sempre haverá um certo nível de subjetividade na interpretação do gráfico.

Não há (muitas) regras na elaboração dos gráficos, pelo contrário, temos liberdade para elaborá-los das forma que melhor nos convém. No entanto, existem guias gerais bem estabelecidas que facilitam o processo de escolha do tipo de gráfico mais adequado para o seu conjunto de dados. Em outras palavras, uma boa metodologia aplicada na construção dos gráficos é extremamente útil para seu correto entendimento e interpretação, seja qual for o público alvo.

A Figura \@ref(fig:bad) vemos um exemplo de um gráfico ruim. Há uma quantidade considerável de poluição visual; as barras são difíceis de comparar devido à perspectiva “3D”; os rótulos estão duplicados, na legenda e no eixo vertical; as sombras não acrescentam nenhuma informação; a escolha das cores não foi muito bem feita.

(ref:bad) Um gráfico com poluição visual e de gosto duvidoso.

<div class="figure">
<img src="https://socviz.co/assets/ch-01-chartjunk-life-expectancy.png" alt="(ref:bad)" width="90%" />
<p class="caption">(\#fig:bad)(ref:bad)</p>
</div>

## O pacote `ggplot2` 

O pacote `ggplot2` foi criado por *Hadley Wickham* baseado em um conceito denominado "Gramática de Gráficos" (*Grammar of Graphics*). 

De um modo geral, a criação de gráficos com o `ggplot2` executa o mapeamento (`mapping`) dos dados para propriedades estéticas (`aes`) e geométricas (`geom_*`). Ainda, podem ser executadas transformações estatísticas (`stat_*`) e divisões (`facet_*`).
Todas essas camadas combinadas irão resultar no gráfico final.


O primeiro passo é chamar a funçao `ggplot` (sem o número 2 no final!). O argumento `data` recebe o conjunto de dados (*data.frame*) que contém os valores. Para este primeiro exemplo, vamos utilizar o conjunto de dados [*gapminder*](#gapminder). 
Ainda, vamos mapear o eixo *x* para a variável *gdpPercap* (do inglês, PIB per capita, em US Dollar) e o eixo *y* para a variável *lifeExp* (do inglês, expectativa de vida ao nascer, em anos). Fica assim:

(ref:tg1) "Pano de fundo" para um gráfico criado com o `ggplot2`


```r
library(gapminder) # carregar os dados gapminder
ggplot(
  data = gapminder,
  mapping = aes(x = gdpPercap, y = lifeExp)
)
```

<div class="figure">
<img src="012-grafic_files/figure-html/g1-1.png" alt="(ref:tg1)" width="672" />
<p class="caption">(\#fig:g1)(ref:tg1)</p>
</div>

Ops, o gráfico resultante está vazio! O que aconteceu? Esta função cria apenas o "pano de fundo" para o gráfico, uma vez que ainda não definimos nenhuma geometria para preenchê-lo.

Para completar o gráfico, basta digitar o sinal de adição `+` e chamar alguma função do tipo `geom_*`, por exemplo, `geom_point` para um gráfico de pontos ^[também conhecido como gráfico de dispersão]. Na prática, estamos adicionando (`+`) mais uma camada ao gráfico.

(ref:tg2) Gráfico de dispersão entre o PIB per capita (USS$) e a expectativa de vida ao nascer (anos).


```r
ggplot(
  data = gapminder,
  mapping = aes(x = gdpPercap, y = lifeExp)
) +
  geom_point()
```

<div class="figure">
<img src="012-grafic_files/figure-html/g2-1.png" alt="(ref:tg2)" width="672" />
<p class="caption">(\#fig:g2)(ref:tg2)</p>
</div>

Em geral, todos os gráficos produzidos com o `ggplot` seguem praticamente a mesma receita:

```r
ggplot(
  data = <data>,
  mapping = aes(x = <variável x>, 
                y = <variável y>,
                <...> = <...>)
) +
  geom_*(<...>) +
  <...>
```


Para simplificar ainda mais o código, é possível suprimir o nome dos argumentos `data` e `mapping`, pois são argumentos muito comuns em todos os gráficos criados com o `ggplot2`. Por isso, de agora em diante, neste livro, estes nomes não serão mais escritos.

(ref:ident) Outro código que produz um gráfico idêntico ao da Figura \@ref(fig:g2)


```r
ggplot(
  gapminder,
  aes(x = gdpPercap, y = lifeExp)
) +
  geom_point()
```

<div class="figure">
<img src="012-grafic_files/figure-html/g3b-1.png" alt="(ref:ident)" width="672" />
<p class="caption">(\#fig:g3b)(ref:ident)</p>
</div>


## Criando gráficos do `ggplot` como objetos

Uma forma bastante conveniente de trabalhar com os gráficos é armazenar em objetos.


```r
p <- ggplot(
  gapminder,
  aes(x = gdpPercap, y = lifeExp)
)
```

Neste código, criamos um objeto denominado `p` ^[ `p` é um nome comum para objetos do `ggplot`, mas é recomendável denominar os objetos com nomes mais descritivos quando nencessário] que contém as informações básicas do gráfico. Na sequ~encia, podemos adicionar mais elementos neste mesmo gráfico apenas adicionando (`+`) alguma função ao objeto.

(ref:ob0) Adicionando uma camada `geom_point()` ao objeto `p`


```r
p +
  geom_point()
```

<div class="figure">
<img src="012-grafic_files/figure-html/ob0-1.png" alt="(ref:ob0)" width="672" />
<p class="caption">(\#fig:ob0)(ref:ob0)</p>
</div>

(ref:ob1) Adicionando uma camada `geom_smooth()` ao objeto `p`


```r
p +
  geom_smooth()
```

```
## `geom_smooth()` using method = 'gam' and formula 'y ~ s(x, bs = "cs")'
```

<div class="figure">
<img src="012-grafic_files/figure-html/ob1-1.png" alt="(ref:ob1)" width="672" />
<p class="caption">(\#fig:ob1)(ref:ob1)</p>
</div>

(ref:ob2) Adicionando várias camadas ao objeto `p`


```r
p +
  geom_point() +
  geom_smooth()
```

```
## `geom_smooth()` using method = 'gam' and formula 'y ~ s(x, bs = "cs")'
```

<div class="figure">
<img src="012-grafic_files/figure-html/ob2-1.png" alt="(ref:ob2)" width="672" />
<p class="caption">(\#fig:ob2)(ref:ob2)</p>
</div>


