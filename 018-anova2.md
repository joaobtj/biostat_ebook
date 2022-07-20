



# Análise de Variância para 2 fatores

Também conhecida como *2-way Anova*, é utilizada quando um estudo ou experimento é desenhado para responder a mais questões que uma Anova para 1 fator é capaz de responder.

É muito comum comparar tratamentos que são combinações de dois fatores independentes.

A inferência para uma Anova de dois fatores é feita da seguinte forma:

1. Faça gráficos das médias dos grupos
* Procure por interação
* Procure por efeitos principais
2. Faça o teste F para três questões:
* Há interação?
* Há efeito principal para o primeiro fator?
* Há efeito principal para o segundo fator?

A seguir veremos três exemplos que ilustram várias situações da Anova de 2 fatores.

:::{.example #anova2a name="Análise de Variância para dois fatores - interação não significativa"}


A reprodução tem um custo fisiológico alto. Uma dieta rica em proteínas pode aumentar a capacidade reprodutiva de moscas das frutas.

Um experimento avaliou a porcentagem de gordura corporal em 40 fêmeas de mosca das frutas alimentadas com 4 dietas enriquecidas com proteínas (ou não) nas doses de 0, 1, 3 e 7 g.

O experimento usou moscas selvagens e mutantes com ciclo reprodutivo mais longo.

A resposta foi a porcentagem de gordura corporal após duas semanas da dieta, contidas no arquivo [mosca.xlsx](data/mosca.xlsx).

São três grupos de hipóteses a serem testadas:

* H~0~: não há interação entre os genótipos e quantidade de proteína na porcentagem de gordura corporal de moscas.  
* H~1~: há interação entre os genótipos e quantidade de proteína na porcentagem de gordura corporal de moscas. 

* H~0~: a quantidade de proteína não influencia na porcentagem de gordura corporal de moscas.  
* H~1~:a quantidade de proteína influencia na porcentagem de gordura corporal de moscas.  

* H~0~: o genótipo não influencia na porcentagem de gordura corporal de moscas.  
* H~1~: o genótipo influencia na porcentagem de gordura corporal de moscas.  


Análise exploratória: 


```r
mosca <- readxl::read_excel("data/mosca.xlsx") %>%
  mutate(
    genotipo = factor(genotipo),
    proteina = factor(proteina)
  )


mosca %>%
  group_by(genotipo, proteina) %>%
  summarise(
    n = n(),
    media = mean(gordura),
    desvpad = sd(gordura),
    var = var(gordura)
  )
```

```
## `summarise()` has grouped output by 'genotipo'. You can override using the
## `.groups` argument.
```

```
## # A tibble: 8 × 6
## # Groups:   genotipo [2]
##   genotipo proteina     n media desvpad    var
##   <fct>    <fct>    <int> <dbl>   <dbl>  <dbl>
## 1 mutante  0            5  24.2   1.76   3.09 
## 2 mutante  1            5  23.3   2.51   6.32 
## 3 mutante  3            5  14.6   3.17  10.1  
## 4 mutante  7            5  13.0   2.71   7.33 
## 5 selvagem 0            5  25.6   1.50   2.24 
## 6 selvagem 1            5  22.3   1.72   2.96 
## 7 selvagem 3            5  15.1   0.691  0.477
## 8 selvagem 7            5  11.6   1.06   1.13
```

```r
## Boxplot - Efeito principal fator A
boxplot(gordura ~ genotipo, data = mosca)
```

<img src="018-anova2_files/figure-html/unnamed-chunk-2-1.png" width="672" />

```r
## Boxplot - Efeito principal fator B
boxplot(gordura ~ proteina, data = mosca)
```

<img src="018-anova2_files/figure-html/unnamed-chunk-2-2.png" width="672" />

```r
## Boxplot - Interação
boxplot(gordura ~ genotipo * proteina, data = mosca)
```

<img src="018-anova2_files/figure-html/unnamed-chunk-2-3.png" width="672" />

```r
## Gráfico da interação
with(mosca, interaction.plot(genotipo, proteina, gordura))
```

<img src="018-anova2_files/figure-html/unnamed-chunk-2-4.png" width="672" />

```r
with(mosca, interaction.plot(proteina, genotipo, gordura))
```

<img src="018-anova2_files/figure-html/unnamed-chunk-2-5.png" width="672" />

Efetuamos a Análise de Variância para os efeitos principais e para a interação:


```r
aov_mosca <- lm(gordura ~ genotipo * proteina, data = mosca)

anova(aov_mosca)
```

```
## Analysis of Variance Table
## 
## Response: gordura
##                   Df  Sum Sq Mean Sq F value    Pr(>F)    
## genotipo           1    0.13    0.13  0.0315    0.8602    
## proteina           3 1113.37  371.12 88.3984 1.429e-15 ***
## genotipo:proteina  3   12.91    4.30  1.0247    0.3947    
## Residuals         32  134.35    4.20                      
## ---
## Signif. codes:  0 '***' 0.001 '**' 0.01 '*' 0.05 '.' 0.1 ' ' 1
```

A interação (p-valor=0,395) e o efeito principal para genótipo (p-valor=0,86) são pequenos (não significativos). O efeito principal para proteína (p-valor < 0,001) é grande (significativo).

Verificação do presuposto da Normalidade.


```r
## curtose
aov_mosca %>%
  residuals() %>%
  moments::kurtosis()
```

```
## [1] 2.495927
```

```r
## assimetria
aov_mosca %>%
  residuals() %>%
  moments::skewness()
```

```
## [1] 0.3766119
```

```r
## Teste de Shapiro-Wilk
aov_mosca %>%
  residuals() %>%
  shapiro.test()
```

```
## 
## 	Shapiro-Wilk normality test
## 
## data:  .
## W = 0.97295, p-value = 0.444
```

```r
## Gráfico dos quantis normais
aov_mosca %>%
  residuals() %>%
  qqnorm()
aov_mosca %>%
  residuals() %>%
  qqline()
```

<img src="018-anova2_files/figure-html/unnamed-chunk-4-1.png" width="672" />

```r
## Histograma
aov_mosca %>%
  residuals() %>%
  hist()
```

<img src="018-anova2_files/figure-html/unnamed-chunk-4-2.png" width="672" />

```r
## Ramo e folhas
aov_mosca %>%
  residuals() %>%
  stem()
```

```
## 
##   The decimal point is at the |
## 
##   -3 | 5
##   -2 | 66410
##   -1 | 965443310
##   -0 | 95333
##    0 | 0134466779
##    1 | 3799
##    2 | 146
##    3 | 68
##    4 | 0
```

Verificação do presuposto da homogeneidade das variâncias



```r
## razão maior/menor desvio-padrão
mosca %>%
  group_by(genotipo, proteina) %>%
  summarise(desvpad = sd(gordura)) %>%
  mutate(razao = max(desvpad) / desvpad)
```

```
## `summarise()` has grouped output by 'genotipo'. You can override using the
## `.groups` argument.
```

```
## # A tibble: 8 × 4
## # Groups:   genotipo [2]
##   genotipo proteina desvpad razao
##   <fct>    <fct>      <dbl> <dbl>
## 1 mutante  0          1.76   1.80
## 2 mutante  1          2.51   1.26
## 3 mutante  3          3.17   1   
## 4 mutante  7          2.71   1.17
## 5 selvagem 0          1.50   1.15
## 6 selvagem 1          1.72   1   
## 7 selvagem 3          0.691  2.49
## 8 selvagem 7          1.06   1.62
```

```r
## boxplot condicional dos resíduos
boxplot(residuals(aov_mosca) ~ genotipo * proteina, data = mosca)
```

<img src="018-anova2_files/figure-html/unnamed-chunk-5-1.png" width="672" />

```r
## resíduos vs ajustados
plot(aov_mosca, 1)
```

<img src="018-anova2_files/figure-html/unnamed-chunk-5-2.png" width="672" />

```r
## teste de Bartlett
bartlett.test(residuals(aov_mosca) ~ paste0(genotipo, proteina), data = mosca)
```

```
## 
## 	Bartlett test of homogeneity of variances
## 
## data:  residuals(aov_mosca) by paste0(genotipo, proteina)
## Bartlett's K-squared = 10.739, df = 7, p-value = 0.1504
```

```r
## teste de Levene
car::leveneTest(residuals(aov_mosca) ~ paste0(genotipo, proteina), data = mosca)
```

```
## Warning in leveneTest.default(y = y, group = group, ...): group coerced to
## factor.
```

```
## Levene's Test for Homogeneity of Variance (center = median)
##       Df F value Pr(>F)
## group  7  1.3106 0.2773
##       32
```

Pela análise do conjunto dos resultados acima, não há evidência de violação dos pressupostos.


Teste de comparação de médias para o efeito principal do fator proteína:


```r
tk_proteina <- emmeans::emmeans(aov_mosca, ~proteina, contr = "tukey")
```

```
## NOTE: Results may be misleading due to involvement in interactions
```

```r
## contrastes
tk_proteina$contrasts
```

```
##  contrast              estimate    SE df t.ratio p.value
##  proteina0 - proteina1     2.06 0.916 32   2.254  0.1307
##  proteina0 - proteina3    10.03 0.916 32  10.950  <.0001
##  proteina0 - proteina7    12.61 0.916 32  13.763  <.0001
##  proteina1 - proteina3     7.97 0.916 32   8.697  <.0001
##  proteina1 - proteina7    10.55 0.916 32  11.509  <.0001
##  proteina3 - proteina7     2.58 0.916 32   2.812  0.0395
## 
## Results are averaged over the levels of: genotipo 
## P value adjustment: tukey method for comparing a family of 4 estimates
```

```r
## Intervalo de confiança
tk_proteina$contrasts %>% confint()
```

```
##  contrast              estimate    SE df lower.CL upper.CL
##  proteina0 - proteina1     2.06 0.916 32  -0.4177     4.55
##  proteina0 - proteina3    10.03 0.916 32   7.5513    12.52
##  proteina0 - proteina7    12.61 0.916 32  10.1283    15.09
##  proteina1 - proteina3     7.97 0.916 32   5.4863    10.45
##  proteina1 - proteina7    10.55 0.916 32   8.0633    13.03
##  proteina3 - proteina7     2.58 0.916 32   0.0943     5.06
## 
## Results are averaged over the levels of: genotipo 
## Confidence level used: 0.95 
## Conf-level adjustment: tukey method for comparing a family of 4 estimates
```

```r
## letras (CLD)
tk_proteina$emmeans %>% multcomp::cld(Letters = letters)
```

```
##  proteina emmean    SE df lower.CL upper.CL .group
##  7          12.3 0.648 32     11.0     13.6  a    
##  3          14.9 0.648 32     13.5     16.2   b   
##  1          22.8 0.648 32     21.5     24.1    c  
##  0          24.9 0.648 32     23.6     26.2    c  
## 
## Results are averaged over the levels of: genotipo 
## Confidence level used: 0.95 
## P value adjustment: tukey method for comparing a family of 4 estimates 
## significance level used: alpha = 0.05 
## NOTE: Compact letter displays can be misleading
##       because they show NON-findings rather than findings.
##       Consider using 'pairs()', 'pwpp()', or 'pwpm()' instead.
```

```r
## plot
tk_proteina$emmeans %>% plot()
```

<img src="018-anova2_files/figure-html/unnamed-chunk-6-1.png" width="672" />

Teste de comparação de médias para o efeito principal do fator genótipo:


```r
tk_genotipo <- emmeans::emmeans(aov_mosca, ~genotipo, contr = "tukey")
```

```
## NOTE: Results may be misleading due to involvement in interactions
```

```r
## contrastes
tk_genotipo$contrasts
```

```
##  contrast           estimate    SE df t.ratio p.value
##  mutante - selvagem    0.115 0.648 32   0.177  0.8602
## 
## Results are averaged over the levels of: proteina
```

```r
## Intervalo de confiança
tk_genotipo$contrasts %>% confint()
```

```
##  contrast           estimate    SE df lower.CL upper.CL
##  mutante - selvagem    0.115 0.648 32     -1.2     1.43
## 
## Results are averaged over the levels of: proteina 
## Confidence level used: 0.95
```

```r
## letras (CLD)
tk_genotipo$emmeans %>% multcomp::cld(Letters = letters)
```

```
##  genotipo emmean    SE df lower.CL upper.CL .group
##  selvagem   18.7 0.458 32     17.7     19.6  a    
##  mutante    18.8 0.458 32     17.8     19.7  a    
## 
## Results are averaged over the levels of: proteina 
## Confidence level used: 0.95 
## significance level used: alpha = 0.05 
## NOTE: Compact letter displays can be misleading
##       because they show NON-findings rather than findings.
##       Consider using 'pairs()', 'pwpp()', or 'pwpm()' instead.
```

```r
## plot
tk_genotipo$emmeans %>% plot()
```

<img src="018-anova2_files/figure-html/unnamed-chunk-7-1.png" width="672" />

Conclusão: Maiores quantidade de proteína na dieta levam a menores taxas de gordura corporal. O genótipo da mosca das frutas tem um efeito pequeno na gordura corporal para qualquer quantidade de proteína.


:::

O próximo exemplo ilustra uma situação em que a interação é significativa, mas os efeitos principais são grandes e mais importantes.



:::{.example #anova2b name="Análise de Variância para dois fatores - interação significativa mas com efeitos principais grandes e mais importantes"}

Fungos micorrízicos estão presentes nas raízes de muitas plantas. Eles tem uma relação simbiótica com a planta.

Um experimento comparou o efeito da adição de nitrogênio em dois genótipos de tomate, um selvagem suscetível a micorrizas e um mutante não suscetível.

O nitrogênio foi adicionado nas doses de 0, 28 e 10 kg/ha.

Seis plantas foram aleatoriamente designadas a cada grupo.

A variável resposta é a porcentagem de fósforo nas plantas depois de 19 semanas [(tomate.xlsx)](data/tomate.xlsx).

São três grupos de hipóteses a serem testadas:

* H~0~ : não há interação entre os genótipos e doses de nitrogênio na porcentagem de fósforo em plantas de tomate.
* H~1~: há interação entre os genótipos e doses de nitrogênio na porcentagem de fósforo em plantas de tomate.

* H~0~: o genótipo não influencia na porcentagem de fósforo em plantas de tomate.
* H~1~: o genótipo influencia na porcentagem de fósforo em plantas de tomate.

* H~0~: as doses de nitrogênio não influenciam na porcentagem de fósforo em plantas de tomate.
* H~1~: as doses de nitrogênio influenciam na porcentagem de fósforo em plantas de tomate.

Análise exploratória: 


```r
tomate <- readxl::read_excel("data/tomate.xlsx") %>%
  mutate(
    genotipo = factor(genotipo),
    nitrogenio = factor(nitrogenio)
  )


tomate %>%
  group_by(genotipo, nitrogenio) %>%
  summarise(
    n = n(),
    media = mean(fosforo),
    desvpad = sd(fosforo),
    var = var(fosforo)
  )
```

```
## `summarise()` has grouped output by 'genotipo'. You can override using the
## `.groups` argument.
```

```
## # A tibble: 6 × 6
## # Groups:   genotipo [2]
##   genotipo nitrogenio     n media desvpad      var
##   <fct>    <fct>      <int> <dbl>   <dbl>    <dbl>
## 1 mutante  0              6 0.248  0.0306 0.000937
## 2 mutante  28             6 0.207  0.0242 0.000587
## 3 mutante  160            6 0.182  0.0147 0.000217
## 4 selvagem 0              6 0.512  0.0833 0.00694 
## 5 selvagem 28             6 0.423  0.0455 0.00207 
## 6 selvagem 160            6 0.318  0.0462 0.00214
```

```r
## Boxplot - Efeito principal fator A
boxplot(fosforo ~ genotipo, data = tomate)
```

<img src="018-anova2_files/figure-html/unnamed-chunk-8-1.png" width="672" />

```r
## Boxplot - Efeito principal fator B
boxplot(fosforo ~ nitrogenio, data = tomate)
```

<img src="018-anova2_files/figure-html/unnamed-chunk-8-2.png" width="672" />

```r
## Boxplot - Interação
boxplot(fosforo ~ genotipo * nitrogenio, data = tomate)
```

<img src="018-anova2_files/figure-html/unnamed-chunk-8-3.png" width="672" />

```r
## Gráfico da interação
with(tomate, interaction.plot(genotipo, nitrogenio, fosforo))
```

<img src="018-anova2_files/figure-html/unnamed-chunk-8-4.png" width="672" />

```r
with(tomate, interaction.plot(nitrogenio, genotipo, fosforo))
```

<img src="018-anova2_files/figure-html/unnamed-chunk-8-5.png" width="672" />

Efetuamos a Análise de Variância para os efeitos principais e para a interação:


```r
aov_tomate <- lm(fosforo ~ genotipo * nitrogenio, data = tomate)

anova(aov_tomate)
```

```
## Analysis of Variance Table
## 
## Response: fosforo
##                     Df  Sum Sq Mean Sq F value    Pr(>F)    
## genotipo             1 0.38028 0.38028 177.148 4.019e-14 ***
## nitrogenio           2 0.10140 0.05070  23.618 6.911e-07 ***
## genotipo:nitrogenio  2 0.02462 0.01231   5.735  0.007777 ** 
## Residuals           30 0.06440 0.00215                      
## ---
## Signif. codes:  0 '***' 0.001 '**' 0.01 '*' 0.05 '.' 0.1 ' ' 1
```

A interação é significativa (p-valor = 0,0077), mas ela é pequena comparada com os efeitos principais.

O efeito principal para genótipos (p-valor < 0,001) nos mostra que tomates selvagens com micorrizas tem maiores níveis de fósforo para todas as doses de nitrogênio, devido ao benefício da simbiose.

O efeito principal para nitrogênio (p-valor < 0,001) mostra que os níveis de fósforo diminuem com o aumento da dose de nitrogênio.

Verificação dos presupostos da Normalidade e Homogeneidade das Variâncias (análise não mostrada): não há evidência de violação dos pressupostos.



Teste de comparação de médias para o efeito principal do fator nitrogênio:


```r
tk_nitrogenio <- emmeans::emmeans(aov_tomate, ~nitrogenio, contr = "tukey")
```

```
## NOTE: Results may be misleading due to involvement in interactions
```

```r
## contrastes
tk_nitrogenio$contrasts
```

```
##  contrast                     estimate     SE df t.ratio p.value
##  nitrogenio0 - nitrogenio28      0.065 0.0189 30   3.436  0.0048
##  nitrogenio0 - nitrogenio160     0.130 0.0189 30   6.873  <.0001
##  nitrogenio28 - nitrogenio160    0.065 0.0189 30   3.436  0.0048
## 
## Results are averaged over the levels of: genotipo 
## P value adjustment: tukey method for comparing a family of 3 estimates
```

```r
## Intervalo de confiança
tk_nitrogenio$contrasts %>% confint()
```

```
##  contrast                     estimate     SE df lower.CL upper.CL
##  nitrogenio0 - nitrogenio28      0.065 0.0189 30   0.0184    0.112
##  nitrogenio0 - nitrogenio160     0.130 0.0189 30   0.0834    0.177
##  nitrogenio28 - nitrogenio160    0.065 0.0189 30   0.0184    0.112
## 
## Results are averaged over the levels of: genotipo 
## Confidence level used: 0.95 
## Conf-level adjustment: tukey method for comparing a family of 3 estimates
```

```r
## letras (CLD)
tk_nitrogenio$emmeans %>% multcomp::cld(Letters = letters)
```

```
##  nitrogenio emmean     SE df lower.CL upper.CL .group
##  160         0.250 0.0134 30    0.223    0.277  a    
##  28          0.315 0.0134 30    0.288    0.342   b   
##  0           0.380 0.0134 30    0.353    0.407    c  
## 
## Results are averaged over the levels of: genotipo 
## Confidence level used: 0.95 
## P value adjustment: tukey method for comparing a family of 3 estimates 
## significance level used: alpha = 0.05 
## NOTE: Compact letter displays can be misleading
##       because they show NON-findings rather than findings.
##       Consider using 'pairs()', 'pwpp()', or 'pwpm()' instead.
```

```r
## plot
tk_nitrogenio$emmeans %>% plot()
```

<img src="018-anova2_files/figure-html/unnamed-chunk-10-1.png" width="672" />

Teste de comparação de médias para o efeito principal do fator genótipo:


```r
tk_genotipo <- emmeans::emmeans(aov_tomate, ~genotipo, contr = "tukey")
```

```
## NOTE: Results may be misleading due to involvement in interactions
```

```r
## contrastes
tk_genotipo$contrasts
```

```
##  contrast           estimate     SE df t.ratio p.value
##  mutante - selvagem   -0.206 0.0154 30 -13.310  <.0001
## 
## Results are averaged over the levels of: nitrogenio
```

```r
## Intervalo de confiança
tk_genotipo$contrasts %>% confint()
```

```
##  contrast           estimate     SE df lower.CL upper.CL
##  mutante - selvagem   -0.206 0.0154 30   -0.237   -0.174
## 
## Results are averaged over the levels of: nitrogenio 
## Confidence level used: 0.95
```

```r
## letras (CLD)
tk_genotipo$emmeans %>% multcomp::cld(Letters = letters)
```

```
##  genotipo emmean     SE df lower.CL upper.CL .group
##  mutante   0.212 0.0109 30    0.190    0.235  a    
##  selvagem  0.418 0.0109 30    0.395    0.440   b   
## 
## Results are averaged over the levels of: nitrogenio 
## Confidence level used: 0.95 
## significance level used: alpha = 0.05 
## NOTE: Compact letter displays can be misleading
##       because they show NON-findings rather than findings.
##       Consider using 'pairs()', 'pwpp()', or 'pwpm()' instead.
```

```r
## plot
tk_genotipo$emmeans %>% plot()
```

<img src="018-anova2_files/figure-html/unnamed-chunk-11-1.png" width="672" />

Conclusão:

Tomates selvagens com micorrizas tem níveis maiores de fósforo que mutantes sem micorrizas.

O nitrogênio reduz o nível de fosforo nas plantas.

A redução é maior nas plantas selvagens, mas esta interação não é muito grande em termos práticos.

::: 


Por último, temos um exemplo em que há uma forte interação que faz os efeitos principais sem sentido. Uma Anova de dois fatores com um efeito de interação forte é frequentemente mais difícil de interpretar.



:::{.example #anova2c name="Análise de Variância para dois fatores - interação significativa"}

Milho com maior conteúdo de aminoácidos pode ser vantajoso na alimentação animal. Nove tratamentos foram arranjados em um fatorial 3x3:

* Milho normal e duas variedades alteradas: opaque-2 e floury-2
* Doses de proteína na dieta: 20, 16 e 12%

As dietas milho+proteína foram usadas na alimentação de 90 pintinhos machos de 1 dia. A variável resposta é o peso (em gramas) após 21 dias [milho.xlsx](data/milho.xlsx).

Qual combinação de milho e proteína leva ao maior aumento de peso?


Há três grupos de hipóteses serem testadas:

* H~0~ : não há interação entre as variedade de milho e a quantidade de proteína.
* H~1~: há interação entre as variedade de milho e a quantidade de proteína.

* H~0~: a quantidade de proteína não influencia no peso dos pintinhos.
* H~1~: a quantidade de proteína influencia no peso dos pintinhos.

* H~0~: a variedade de milho não influencia no peso dos pintinhos.
* H~1~: a variedade de milho influencia no peso dos pintinhos.


Análise exploratória: 


```r
milho <- readxl::read_excel("data/milho.xlsx") %>%
  mutate(
    variedade = factor(variedade),
    proteina = factor(proteina)
  )


milho %>%
  group_by(variedade, proteina) %>%
  summarise(
    n = n(),
    media = mean(peso),
    desvpad = sd(peso),
    var = var(peso)
  )
```

```
## `summarise()` has grouped output by 'variedade'. You can override using the
## `.groups` argument.
```

```
## # A tibble: 9 × 6
## # Groups:   variedade [3]
##   variedade proteina     n media desvpad   var
##   <fct>     <fct>    <int> <dbl>   <dbl> <dbl>
## 1 flou      12          10  271.    32.1 1033.
## 2 flou      16          10  434.    49.7 2474.
## 3 flou      20          10  465.    49.2 2416.
## 4 norm      12          10  195.    50.5 2553.
## 5 norm      16          10  389.    48.1 2314.
## 6 norm      20          10  486.    38.7 1496.
## 7 opaq      12          10  264.    26.0  675.
## 8 opaq      16          10  339.    54.4 2959.
## 9 opaq      20          10  438.    61.2 3741.
```

```r
## Boxplot - Efeito principal fator A
boxplot(peso ~ variedade, data = milho)
```

<img src="018-anova2_files/figure-html/unnamed-chunk-12-1.png" width="672" />

```r
## Boxplot - Efeito principal fator B
boxplot(peso ~ proteina, data = milho)
```

<img src="018-anova2_files/figure-html/unnamed-chunk-12-2.png" width="672" />

```r
## Boxplot - Interação
boxplot(peso ~ variedade * proteina, data = milho)
```

<img src="018-anova2_files/figure-html/unnamed-chunk-12-3.png" width="672" />

```r
## Gráfico da interação
with(milho, interaction.plot(variedade, proteina, peso))
```

<img src="018-anova2_files/figure-html/unnamed-chunk-12-4.png" width="672" />

```r
with(milho, interaction.plot(proteina, variedade, peso))
```

<img src="018-anova2_files/figure-html/unnamed-chunk-12-5.png" width="672" />

Efetuamos a Análise de Variância para os efeitos principais e para a interação:


```r
aov_milho <- lm(peso ~ variedade * proteina, data = milho)
anova(aov_milho)
```

```
## Analysis of Variance Table
## 
## Response: peso
##                    Df Sum Sq Mean Sq  F value    Pr(>F)    
## variedade           2  31137   15568   7.1265   0.00141 ** 
## proteina            2 745621  372810 170.6557 < 2.2e-16 ***
## variedade:proteina  4  60894   15223   6.9686 7.143e-05 ***
## Residuals          81 176951    2185                       
## ---
## Signif. codes:  0 '***' 0.001 '**' 0.01 '*' 0.05 '.' 0.1 ' ' 1
```

Verificação dos presupostos da Normalidade e Homogeneidade das Variâncias (análise não mostrada): não há evidência de violação dos pressupostos.

Desdobramento da interação: variedade dentro de cada nível de proteína.


```r
## Desdobramento da interação
phia::testInteractions(aov_milho, fixed="proteina", across="variedade")
```

```
## F Test: 
## P-value adjustment method: holm
##           variedade1 variedade2 Df Sum of Sq       F    Pr(>F)    
## 12              7.66     -68.39  2     35065  8.0256 0.0013218 ** 
## 16             95.47      50.28  2     45616 10.4404 0.0002773 ***
## 20             27.16      47.48  2     11350  2.5977 0.0806380 .  
## Residuals                       81    176951                      
## ---
## Signif. codes:  0 '***' 0.001 '**' 0.01 '*' 0.05 '.' 0.1 ' ' 1
```

```r
## Teste de Tukey para a interação
tk_variedade <- emmeans::emmeans(aov_milho, ~proteina|variedade, contr = "tukey")

## Contrastes
tk_variedade$contrasts
```

```
## variedade = flou:
##  contrast                estimate   SE df t.ratio p.value
##  proteina12 - proteina16   -162.8 20.9 81  -7.790  <.0001
##  proteina12 - proteina20   -193.8 20.9 81  -9.273  <.0001
##  proteina16 - proteina20    -31.0 20.9 81  -1.483  0.3046
## 
## variedade = norm:
##  contrast                estimate   SE df t.ratio p.value
##  proteina12 - proteina16   -193.7 20.9 81  -9.266  <.0001
##  proteina12 - proteina20   -290.2 20.9 81 -13.883  <.0001
##  proteina16 - proteina20    -96.5 20.9 81  -4.617  <.0001
## 
## variedade = opaq:
##  contrast                estimate   SE df t.ratio p.value
##  proteina12 - proteina16    -75.0 20.9 81  -3.589  0.0016
##  proteina12 - proteina20   -174.3 20.9 81  -8.340  <.0001
##  proteina16 - proteina20    -99.3 20.9 81  -4.751  <.0001
## 
## P value adjustment: tukey method for comparing a family of 3 estimates
```

```r
## Intervalo de confiança
tk_variedade$contrasts %>% confint()
```

```
## variedade = flou:
##  contrast                estimate   SE df lower.CL upper.CL
##  proteina12 - proteina16   -162.8 20.9 81   -212.7   -112.9
##  proteina12 - proteina20   -193.8 20.9 81   -243.7   -143.9
##  proteina16 - proteina20    -31.0 20.9 81    -80.9     18.9
## 
## variedade = norm:
##  contrast                estimate   SE df lower.CL upper.CL
##  proteina12 - proteina16   -193.7 20.9 81   -243.6   -143.8
##  proteina12 - proteina20   -290.2 20.9 81   -340.1   -240.3
##  proteina16 - proteina20    -96.5 20.9 81   -146.4    -46.6
## 
## variedade = opaq:
##  contrast                estimate   SE df lower.CL upper.CL
##  proteina12 - proteina16    -75.0 20.9 81   -124.9    -25.1
##  proteina12 - proteina20   -174.3 20.9 81   -224.2   -124.4
##  proteina16 - proteina20    -99.3 20.9 81   -149.2    -49.4
## 
## Confidence level used: 0.95 
## Conf-level adjustment: tukey method for comparing a family of 3 estimates
```

```r
## letras (CLD)
tk_variedade$emmeans %>% multcomp::cld(Letters = letters)
```

```
## variedade = flou:
##  proteina emmean   SE df lower.CL upper.CL .group
##  12          271 14.8 81      242      301  a    
##  16          434 14.8 81      405      464   b   
##  20          465 14.8 81      436      495   b   
## 
## variedade = norm:
##  proteina emmean   SE df lower.CL upper.CL .group
##  12          195 14.8 81      166      225  a    
##  16          389 14.8 81      360      418   b   
##  20          486 14.8 81      456      515    c  
## 
## variedade = opaq:
##  proteina emmean   SE df lower.CL upper.CL .group
##  12          264 14.8 81      234      293  a    
##  16          339 14.8 81      309      368   b   
##  20          438 14.8 81      409      467    c  
## 
## Confidence level used: 0.95 
## P value adjustment: tukey method for comparing a family of 3 estimates 
## significance level used: alpha = 0.05 
## NOTE: Compact letter displays can be misleading
##       because they show NON-findings rather than findings.
##       Consider using 'pairs()', 'pwpp()', or 'pwpm()' instead.
```

```r
## plot
tk_variedade$emmeans %>% plot()
```

<img src="018-anova2_files/figure-html/unnamed-chunk-14-1.png" width="672" />


Desdobramento da interação: proteína dentro de cada nível de variedade.


```r
## Desdobramento da interação
phia::testInteractions(aov_milho, fixed="variedade", across="proteina")
```

```
## F Test: 
## P-value adjustment method: holm
##           proteina1 proteina2 Df Sum of Sq      F    Pr(>F)    
## flou        -193.82    -30.99  2    216801 49.621 1.708e-14 ***
## norm        -290.19    -96.50  2    436794 99.972 < 2.2e-16 ***
## opaq        -174.32    -99.30  2    152920 35.000 1.109e-11 ***
## Residuals                     81    176951                     
## ---
## Signif. codes:  0 '***' 0.001 '**' 0.01 '*' 0.05 '.' 0.1 ' ' 1
```

```r
## Teste de Tukey para a interação
tk_proteina <- emmeans::emmeans(aov_milho, ~variedade|proteina, contr = "tukey")

## Contrastes
tk_proteina$contrasts
```

```
## proteina = 12:
##  contrast    estimate   SE df t.ratio p.value
##  flou - norm    76.05 20.9 81   3.638  0.0014
##  flou - opaq     7.66 20.9 81   0.366  0.9287
##  norm - opaq   -68.39 20.9 81  -3.272  0.0044
## 
## proteina = 16:
##  contrast    estimate   SE df t.ratio p.value
##  flou - norm    45.19 20.9 81   2.162  0.0840
##  flou - opaq    95.47 20.9 81   4.567  0.0001
##  norm - opaq    50.28 20.9 81   2.405  0.0479
## 
## proteina = 20:
##  contrast    estimate   SE df t.ratio p.value
##  flou - norm   -20.32 20.9 81  -0.972  0.5965
##  flou - opaq    27.16 20.9 81   1.299  0.3997
##  norm - opaq    47.48 20.9 81   2.271  0.0657
## 
## P value adjustment: tukey method for comparing a family of 3 estimates
```

```r
## Intervalo de confiança
tk_proteina$contrasts %>% confint()
```

```
## proteina = 12:
##  contrast    estimate   SE df lower.CL upper.CL
##  flou - norm    76.05 20.9 81   26.144    126.0
##  flou - opaq     7.66 20.9 81  -42.246     57.6
##  norm - opaq   -68.39 20.9 81 -118.296    -18.5
## 
## proteina = 16:
##  contrast    estimate   SE df lower.CL upper.CL
##  flou - norm    45.19 20.9 81   -4.716     95.1
##  flou - opaq    95.47 20.9 81   45.564    145.4
##  norm - opaq    50.28 20.9 81    0.374    100.2
## 
## proteina = 20:
##  contrast    estimate   SE df lower.CL upper.CL
##  flou - norm   -20.32 20.9 81  -70.226     29.6
##  flou - opaq    27.16 20.9 81  -22.746     77.1
##  norm - opaq    47.48 20.9 81   -2.426     97.4
## 
## Confidence level used: 0.95 
## Conf-level adjustment: tukey method for comparing a family of 3 estimates
```

```r
## letras (CLD)
tk_proteina$emmeans %>% multcomp::cld(Letters = letters)
```

```
## proteina = 12:
##  variedade emmean   SE df lower.CL upper.CL .group
##  norm         195 14.8 81      166      225  a    
##  opaq         264 14.8 81      234      293   b   
##  flou         271 14.8 81      242      301   b   
## 
## proteina = 16:
##  variedade emmean   SE df lower.CL upper.CL .group
##  opaq         339 14.8 81      309      368  a    
##  norm         389 14.8 81      360      418   b   
##  flou         434 14.8 81      405      464   b   
## 
## proteina = 20:
##  variedade emmean   SE df lower.CL upper.CL .group
##  opaq         438 14.8 81      409      467  a    
##  flou         465 14.8 81      436      495  a    
##  norm         486 14.8 81      456      515  a    
## 
## Confidence level used: 0.95 
## P value adjustment: tukey method for comparing a family of 3 estimates 
## significance level used: alpha = 0.05 
## NOTE: Compact letter displays can be misleading
##       because they show NON-findings rather than findings.
##       Consider using 'pairs()', 'pwpp()', or 'pwpm()' instead.
```

```r
## plot
tk_proteina$emmeans %>% plot()
```

<img src="018-anova2_files/figure-html/unnamed-chunk-15-1.png" width="672" />

Há um efeito importante da interação:

O milho normal é o pior para 12% de proteína e o melhor para 20%. Floury é o melhor para 12% e 16% de proteína. Opaque é sempre inferior ao Floury, mas melhor que o normal somente para 12% de proteína.

Apesar de haver um efeito principal para variedade e proteína, estes são menos importantes devido a interação.

![](data:image/png;base64,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){width="90%"}

Conclusão:

* Maior dose de proteína ajuda a acelerar o ganho de peso.
* Os três tipos de milho não diferem quando a dieta tem 20% de proteína.
* Floury é melhor quando a dose de proteína é de 16% e 20%.

:::