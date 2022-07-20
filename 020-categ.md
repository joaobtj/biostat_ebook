
# Dados categóricos

Algumas variáveis – como gênero, espécie e cor – são categóricas por natureza. Outras variáveis categóricas são criadas pelo agrupamento em classes dos valores de uma variável quantitativa – como grupos etários.

A relação entre duas variáveis categóricas é frequentemente demonstrada em uma Tabela de dupla entrada, que também é conhecida por Tabela de contingência.

Para analisar dados categóricos, usamos contagens ou percentuais de indivíduos que pertencem a cada uma das várias categorias.

:::{.example #tab2 name="Tabela de dupla entrada - teste qui-quadrado"}

A Tabela abaixo apresenta os resultados de um estudo da recorrência de infecções do trato urinário (ITU) em mulheres que acabaram de se curar de uma ITU com antibióticos e que, então, passam a usar um de três tratamentos por um período de seis meses (suco de uva-do-monte diariamente, bebida diária com lactobacilos ou nenhuma bebida).

Ambas as variáveis, tratamento e resultado, são agrupados em categorias. O resultado é categórico aqui porque uma ou mais recorrências de ITU durante o período de seis meses constituem uma única categoria, “Recorrência”.


```r
Bebida <- c("1.Suco de uva-do-monte", "2.Bebida de lactobacilos", "3.Nenhuma bebida")
ITU <- rep(c("1.Recorrencia", "2.Sem recorrencia"), e = 3)
freq1 <- c(8, 19, 18, 42, 30, 32)
df1 <- data.frame(Bebida, ITU, freq1)
tab1 <- xtabs(freq1 ~ Bebida + ITU, data = df1)

gmodels::CrossTable(tab1, expected = TRUE, prop.chisq = TRUE)
```

```
## 
##  
##    Cell Contents
## |-------------------------|
## |                       N |
## |              Expected N |
## | Chi-square contribution |
## |           N / Row Total |
## |           N / Col Total |
## |         N / Table Total |
## |-------------------------|
## 
##  
## Total Observations in Table:  149 
## 
##  
##                          | ITU 
##                   Bebida |     1.Recorrencia | 2.Sem recorrencia |         Row Total | 
## -------------------------|-------------------|-------------------|-------------------|
##   1.Suco de uva-do-monte |                 8 |                42 |                50 | 
##                          |            15.101 |            34.899 |                   | 
##                          |             3.339 |             1.445 |                   | 
##                          |             0.160 |             0.840 |             0.336 | 
##                          |             0.178 |             0.404 |                   | 
##                          |             0.054 |             0.282 |                   | 
## -------------------------|-------------------|-------------------|-------------------|
## 2.Bebida de lactobacilos |                19 |                30 |                49 | 
##                          |            14.799 |            34.201 |                   | 
##                          |             1.193 |             0.516 |                   | 
##                          |             0.388 |             0.612 |             0.329 | 
##                          |             0.422 |             0.288 |                   | 
##                          |             0.128 |             0.201 |                   | 
## -------------------------|-------------------|-------------------|-------------------|
##         3.Nenhuma bebida |                18 |                32 |                50 | 
##                          |            15.101 |            34.899 |                   | 
##                          |             0.557 |             0.241 |                   | 
##                          |             0.360 |             0.640 |             0.336 | 
##                          |             0.400 |             0.308 |                   | 
##                          |             0.121 |             0.215 |                   | 
## -------------------------|-------------------|-------------------|-------------------|
##             Column Total |                45 |               104 |               149 | 
##                          |             0.302 |             0.698 |                   | 
## -------------------------|-------------------|-------------------|-------------------|
## 
##  
## Statistics for All Table Factors
## 
## 
## Pearson's Chi-squared test 
## ------------------------------------------------------------
## Chi^2 =  7.290006     d.f. =  2     p =  0.02612133 
## 
## 
## 
```


Essa é uma tabela de dupla entrada porque descreve a relação entre duas variáveis categóricas. Tratamento é a variável linha, porque cada linha na tabela descreve as mulheres que receberam um dos três tratamentos. Resultado é a variável coluna, porque cada coluna descreve um possível resultado conforme classificado no estudo. As entradas na tabela são as contagens de participantes do estudo em cada classe de tratamento por resultado.

A estatística qui-quadrado é X^2^ = 7,29. O valor P é pequeno, cerca de 0,026.

Há evidência bastante forte de que a recorrência de ITU seja diferente conforme o tipo de bebida utilizada no tratamento.

Há menor recorrência em mulheres que beberam suco de uva-do-monte, pois a recorrência para o Suco de uva-do-monte apresentou o maior valor de contribuição para o qui-quadrado (3,339). O valor esperado era de 15,1 recorrências, enquanto que foi observado um valor bem menor, de apenas 8 recorrências.

:::


## O paradoxo de Simpson

Como no caso de variáveis quantitativas, os efeitos de variáveis ocultas podem mudar ou mesmo inverter relações entre duas variáveis categóricas. Aqui está um exemplo que demonstra as surpresas com as quais um usuário de dados desavisado pode se defrontar.

:::{.example #paradoxsimpson name="Helicópteros médicos salvam vidas?"}

Vítimas de acidentes são, algumas vezes, transportadas por helicóptero do local do acidente para um hospital. Helicópteros economizam tempo. Eles também salvam vidas?

Vamos comparar os percentuais de vítimas de acidentes que morrem quando resgatadas por helicóptero e por transporte usual, por rodovia, e levadas a um hospital. A seguir, estão dados hipotéticos que ilustram uma dificuldade prática:



```
## 
##  
##    Cell Contents
## |-------------------------|
## |                       N |
## |           N / Col Total |
## |-------------------------|
## 
##  
## Total Observations in Table:  1300 
## 
##  
##                  | transporte 
##           sobrev | 1.Helicóptero |     2.Rodovia |     Row Total | 
## -----------------|---------------|---------------|---------------|
## 1.Não sobreviveu |            64 |           260 |           324 | 
##                  |         0.320 |         0.236 |               | 
## -----------------|---------------|---------------|---------------|
##     2.Sobreviveu |           136 |           840 |           976 | 
##                  |         0.680 |         0.764 |               | 
## -----------------|---------------|---------------|---------------|
##     Column Total |           200 |          1100 |          1300 | 
##                  |         0.154 |         0.846 |               | 
## -----------------|---------------|---------------|---------------|
## 
## 
```

Vemos que 32% (64 dentre 200) dos pacientes transportados por helicóptero morreram, comparados com apenas 24% (260 dentre 1100) dos outros. Essa estatística parece desencorajadora.

A explicação é que o helicóptero é enviado, na maior parte das vezes, para acidentes graves; logo, as vítimas transportadas por helicópteros, com maior frequência, estão mais gravemente feridas que as outras vítimas. Elas têm mais chance de morrer a despeito do tipo de transporte do resgate.

A seguir, estão os mesmos dados decompostos segundo a gravidade do acidente.
Primeiro, para os acidentes graves:



```
## 
##  
##    Cell Contents
## |-------------------------|
## |                       N |
## |           N / Col Total |
## |-------------------------|
## 
##  
## Total Observations in Table:  200 
## 
##  
##                  | transporte 
##           sobrev | 1.Helicóptero |     2.Rodovia |     Row Total | 
## -----------------|---------------|---------------|---------------|
## 1.Não sobreviveu |            48 |            60 |           108 | 
##                  |         0.480 |         0.600 |               | 
## -----------------|---------------|---------------|---------------|
##     2.Sobreviveu |            52 |            40 |            92 | 
##                  |         0.520 |         0.400 |               | 
## -----------------|---------------|---------------|---------------|
##     Column Total |           100 |           100 |           200 | 
##                  |         0.500 |         0.500 |               | 
## -----------------|---------------|---------------|---------------|
## 
## 
```

E para os acidentes menos graves: 


```
## 
##  
##    Cell Contents
## |-------------------------|
## |                       N |
## |           N / Col Total |
## |-------------------------|
## 
##  
## Total Observations in Table:  1100 
## 
##  
##                  | transporte 
##           sobrev | 1.Helicóptero |     2.Rodovia |     Row Total | 
## -----------------|---------------|---------------|---------------|
## 1.Não sobreviveu |            16 |           200 |           216 | 
##                  |         0.160 |         0.200 |               | 
## -----------------|---------------|---------------|---------------|
##     2.Sobreviveu |            84 |           800 |           884 | 
##                  |         0.840 |         0.800 |               | 
## -----------------|---------------|---------------|---------------|
##     Column Total |           100 |          1000 |          1100 | 
##                  |         0.091 |         0.909 |               | 
## -----------------|---------------|---------------|---------------|
## 
## 
```

Entre as vítimas de acidentes graves, o helicóptero salva 52% (52 dentre 100), comparadas a 40% para transporte rodoviário.

Se examinarmos apenas os acidentes de menor gravidade, 84% da vítimas transportadas por helicóptero sobrevivem versus 80% das transportadas por rodovia.

Ambos os grupos de vítimas têm maior taxa de sobrevivência quando resgatados por helicóptero.

Em princípio, parece paradoxal que o helicóptero seja melhor para ambos os grupos de vítimas, mas pior quando as vítimas são consideradas em conjunto.

A gravidade do acidente era uma variável oculta que, antes de ser revelada, escondia a verdadeira relação entre sobrevivência e meio de transporte para um hospital.

Uma associação ou comparação que vale para cada um de vários grupos pode ter sua direção invertida quando os dados são combinados para formar um grupo único. Essa inversão é chamada de paradoxo de Simpson.

O exame cuidadoso dos dados fornece a explicação. Metade dos pacientes transportados por helicóptero é de acidentes graves, comparada com apenas 100 dentre 1100 pacientes transportados por rodovia. Logo, o helicóptero conduz pacientes com mais chance de morrer.

::: 



