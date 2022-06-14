


# Testes para duas amostras

## Teste t para dados emparelhados


Para comparar as respostas aos dois tratamentos em um planejamento de dados emparelhados, determine a diferença entre as respostas em cada par. Em seguida, aplique o procedimento t de uma amostra a essas diferenças.


:::{.example #par name="Teste t para dados emparelhados"}

Pesquisadores perguntaram se odores agradáveis teriam o efeito de melhorar o desempenho de estudantes.

Vinte e um sujeitos trabalharam em um labirinto com lápis e papel, usando uma máscara inodora ou com perfume floral, em ordem aleatória.

Há evidência de que os sujeitos resolveram o labirinto mais depressa usando a máscara com perfume?

Os dados podem ser encontrados no arquivo [floral.xlsx](data/floral.xlsx)



```r
floral <- readxl::read_excel("data/floral.xlsx")

t.test(floral$sem, floral$com, paired=TRUE)
```

```
## 
## 	Paired t-test
## 
## data:  floral$sem and floral$com
## t = 0.34938, df = 20, p-value = 0.7305
## alternative hypothesis: true mean difference is not equal to 0
## 95 percent confidence interval:
##  -4.755061  6.668394
## sample estimates:
## mean difference 
##       0.9566667
```

Alternativamente, o teste t pode ser aplicado às diferenças entre as respostas de cada par.


```r
t.test(floral$sem - floral$com)
```

```
## 
## 	One Sample t-test
## 
## data:  floral$sem - floral$com
## t = 0.34938, df = 20, p-value = 0.7305
## alternative hypothesis: true mean is not equal to 0
## 95 percent confidence interval:
##  -4.755061  6.668394
## sample estimates:
## mean of x 
## 0.9566667
```

Os dados não apoiam a afirmativa (p-valor = 0,73) de que perfumes florais melhorem o desempenho.

* A média do tempo de execução do labirinto com perfume foi de 49.06
* A média do tempo de execução do labirinto sem perfume foi de 50.01
* O IC para a diferença foi de -4,75 a +6,66 segundos.
* A melhora média (amostral) foi de apenas 0,95 segundos.

:::



## Teste t para duas amostras

O fato de uma diferença observada entre duas médias amostrais ser surpreendente depende da dispersão das observações, bem como das duas médias.

Médias muito diferentes podem ocorrer apenas devido ao acaso, se as observações individuais variarem bastante.


:::{.example #testet name="Teste t para duas amostras"}

Latas de alumínio são feitas a partir de grandes lingotes sólidos, prensados sob rolos de alta pressão e cortados como biscoitos a partir de folhas finas.

Uma companhia afirma que um novo processo de fabricação diminui a quantidade de alumínio necessária para se fazer uma lata e, portanto, diminui o peso.

Obtiveram-se amostras aleatórias independentes de latas de alumínio feitas pelos processos velho e novo, e o peso (em gramas) de cada uma é dado no arquivo (lata.xlsx)[data/lata.xlsx].

Há alguma evidência de que as latas de alumínio feitas pelo novo processo tenham um peso médio populacional menor?



```r
lata <- readxl::read_excel("data/lata.xlsx")

t.test(lata$antigo, lata$novo)
```

```
## 
## 	Welch Two Sample t-test
## 
## data:  lata$antigo and lata$novo
## t = 2.587, df = 39.742, p-value = 0.01345
## alternative hypothesis: true difference in means is not equal to 0
## 95 percent confidence interval:
##  0.1002432 0.8168996
## sample estimates:
## mean of x mean of y 
##  14.30857  13.85000
```

Há evidências (p-valor = 0,013) de que as latas de alumínio fabricadas pelo processo novo sejam mais leves do que as fabricadas pelo processo antigo.

O Intervalo de Confiança de 95% para a diferença de peso entre as latas fabricadas pelo processo novo e antigo é de 0,10 a 0,82 gramas mais leve pelo processo novo.


:::
