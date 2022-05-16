---
output: html_document
editor_options: 
  chunk_output_type: console
---




# Introdução à inferência

A inferência estatística fornece métodos para se tirarem conclusões sobre uma população a partir de dados amostrais.

* Intervalos de confiança: para se estimar o valor de um parâmetro de uma população
* Testes de significância ou Teste de hipóteses: para se avaliar a evidência a favor ou contra uma afirmativa sobre uma população. 

Assim, o objetivo de uma amostragem é inferirmos, a partir dos dados amostrais, alguma conclusão sobre a população mais ampla que a amostra representa, associada a uma probabilidade. 

Nos exemplos deste capítulo, utilizaremos a população descrita no início do capítulo \@ref(estbas). Também iremos utilizar um processo de amostragem aleatório para extrair amostra(s) desta população.


## Intervalo de Confiança para a média populacional

O Intervalo de Confiança (IC) é uma estimativa de um intervalo que contém um parâmetro populacional.

Utilizaremos a função `t.test` para calcular um Intervalo de Confiança para a média.


:::{.example #icm name="Intervalo de Confiança para a média"}

Considere o conjunto de dados [dap.csv](data/dap.csv). Por serem dados de uma população, vamos fazer uma amostragem (`sample`) de 10 indivíduos e calcular o IC de 95% ^[valor padrão da função `t.test`].






```r
sample(dap, 10) %>% t.test()
```

```
## 
## 	One Sample t-test
## 
## data:  .
## t = 23.04, df = 9, p-value = 2.598e-09
## alternative hypothesis: true mean is not equal to 0
## 95 percent confidence interval:
##  12.01668 14.63332
## sample estimates:
## mean of x 
##    13.325
```

O *output* da função `t.test` contém muitas informções, mas por hora, vamos nos focar apenas no intervalo de confiança, indicado pelo texto *95 percent confidence interval*

Assim, o intervalo de confiança para a média populacional desta amostra está entre 12.02 e 14.63. Em outras palavras, estamos 95% confiantes que a média populacional do DAP de árvores de Mogno Africano está compreendidade entre 12.02 cm e 14.63 cm.

O valor da média amostral, 13.33 cm, é a estimativa central e pode ser entendida como uma estimativa não enviesada da média populacional. 

:::

A amostra deste exemplo vem de uma população conhecida, cuja média populacional é 12.95 cm. Vejam que a média amostral e a média populacional diferem entre si, mas o IC calculado contém a média populacional. 

A interpretação que devemos fazer do IC de 95% é que 95 em 100 amostras feitas na população irão conter a média populacional. Vejamos a explicação no exemplo \@ref(exm:icsimula) com o uso de simulação.


:::{.example #icsimula name="Intervalo de Confiança para a média - simulações"}

Considere o conjunto de dados [dap.csv](data/dap.csv). 

Inicialmente, criamos uma função que faz uma amostragem de *n* elementos e retorna os valores inferior e superior do IC calculado. 




```r
## Função que amostra n elementos e retorna os valores inferior e superior do IC calculado
## data = conjunto de dados de onde será retirada a amostra
## n_sample = tamanho da amostra
ic <- function(data, n_sample) {
  ic_sample <- sample(data, n_sample) %>% t.test()
  return(ic_sample$conf.int)
}
```

Em seguida, com o uso da função `replicate`, realizamos 100 simulações deste processo:




```r
## 100 simulações com a função replicate
ic_simul <- replicate(100, ic(dap, 10))

## mostrar apenas os primeiros valores do resultado
ic_simul %>%
  t() %>%
  head()
```

```
##          [,1]     [,2]
## [1,] 12.01668 14.63332
## [2,] 11.91541 14.35859
## [3,] 11.74785 14.71015
## [4,] 11.66021 14.33979
## [5,] 11.34152 14.68648
## [6,] 13.02743 15.27057
```

Quantos dos IC simulados não contém a verdadeira média^[Este valor já é conhecido: 12.95] populacional?




Por meio de uma análise gráfica:

<div class="figure">
<img src="014-infer_files/figure-html/unnamed-chunk-7-1.png" alt="Intervalos de confiança simulados para várias amostragens de uma população. A média populacional é representada pela linha vertical violeta " width="672" />
<p class="caption">(\#fig:unnamed-chunk-7)Intervalos de confiança simulados para várias amostragens de uma população. A média populacional é representada pela linha vertical violeta </p>
</div>

Calculando a proporção de ICs que não contém a média populacional.


```r
(ic_simul[1, ] > mean(dap) | ic_simul[2, ] < mean(dap)) %>% mean()
```

```
## [1] 0.06
```

Estes resultados mostram que 6 dos 100 ICs simulados não contém a média populacional. 

:::