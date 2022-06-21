
# Análise de Variância

Os procedimentos t de duas amostras comparam as médias de duas populações ou as respostas médias a dois tratamentos em um experimento.

Naturalmente, os estudos nem sempre comparam apenas dois grupos. Precisamos de um método que compare qualquer quantidade de médias.


## Comparação de várias médias

Os métodos estatísticos para se lidar com comparações múltiplas geralmente apresentam dois passos:

1.Um teste geral para verificarmos se há boa evidência de quaisquer diferenças entre os parâmetros que desejamos comparar.

2.Uma análise de acompanhamento detalhada para decidirmos quais parâmetros são diferentes e estimarmos o tamanho das diferenças.

## A ideia da Análise de Variância

Considere a população com 150 árvores pertencente a um reflorestamento de Mogno Africano (Capítulo 6).

Suponha que retiremos 5 amostras aleatórias desta população com 8 indivíduos em cada amostra.




```{=html}
<div id="tjdigtdsnt" style="overflow-x:auto;overflow-y:auto;width:auto;height:auto;">
<style>html {
  font-family: -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, Oxygen, Ubuntu, Cantarell, 'Helvetica Neue', 'Fira Sans', 'Droid Sans', Arial, sans-serif;
}

#tjdigtdsnt .gt_table {
  display: table;
  border-collapse: collapse;
  margin-left: auto;
  margin-right: auto;
  color: #333333;
  font-size: 16px;
  font-weight: normal;
  font-style: normal;
  background-color: #FFFFFF;
  width: auto;
  border-top-style: solid;
  border-top-width: 2px;
  border-top-color: #A8A8A8;
  border-right-style: none;
  border-right-width: 2px;
  border-right-color: #D3D3D3;
  border-bottom-style: solid;
  border-bottom-width: 2px;
  border-bottom-color: #A8A8A8;
  border-left-style: none;
  border-left-width: 2px;
  border-left-color: #D3D3D3;
}

#tjdigtdsnt .gt_heading {
  background-color: #FFFFFF;
  text-align: center;
  border-bottom-color: #FFFFFF;
  border-left-style: none;
  border-left-width: 1px;
  border-left-color: #D3D3D3;
  border-right-style: none;
  border-right-width: 1px;
  border-right-color: #D3D3D3;
}

#tjdigtdsnt .gt_title {
  color: #333333;
  font-size: 125%;
  font-weight: initial;
  padding-top: 4px;
  padding-bottom: 4px;
  padding-left: 5px;
  padding-right: 5px;
  border-bottom-color: #FFFFFF;
  border-bottom-width: 0;
}

#tjdigtdsnt .gt_subtitle {
  color: #333333;
  font-size: 85%;
  font-weight: initial;
  padding-top: 0;
  padding-bottom: 6px;
  padding-left: 5px;
  padding-right: 5px;
  border-top-color: #FFFFFF;
  border-top-width: 0;
}

#tjdigtdsnt .gt_bottom_border {
  border-bottom-style: solid;
  border-bottom-width: 2px;
  border-bottom-color: #D3D3D3;
}

#tjdigtdsnt .gt_col_headings {
  border-top-style: solid;
  border-top-width: 2px;
  border-top-color: #D3D3D3;
  border-bottom-style: solid;
  border-bottom-width: 2px;
  border-bottom-color: #D3D3D3;
  border-left-style: none;
  border-left-width: 1px;
  border-left-color: #D3D3D3;
  border-right-style: none;
  border-right-width: 1px;
  border-right-color: #D3D3D3;
}

#tjdigtdsnt .gt_col_heading {
  color: #333333;
  background-color: #FFFFFF;
  font-size: 100%;
  font-weight: normal;
  text-transform: inherit;
  border-left-style: none;
  border-left-width: 1px;
  border-left-color: #D3D3D3;
  border-right-style: none;
  border-right-width: 1px;
  border-right-color: #D3D3D3;
  vertical-align: bottom;
  padding-top: 5px;
  padding-bottom: 6px;
  padding-left: 5px;
  padding-right: 5px;
  overflow-x: hidden;
}

#tjdigtdsnt .gt_column_spanner_outer {
  color: #333333;
  background-color: #FFFFFF;
  font-size: 100%;
  font-weight: normal;
  text-transform: inherit;
  padding-top: 0;
  padding-bottom: 0;
  padding-left: 4px;
  padding-right: 4px;
}

#tjdigtdsnt .gt_column_spanner_outer:first-child {
  padding-left: 0;
}

#tjdigtdsnt .gt_column_spanner_outer:last-child {
  padding-right: 0;
}

#tjdigtdsnt .gt_column_spanner {
  border-bottom-style: solid;
  border-bottom-width: 2px;
  border-bottom-color: #D3D3D3;
  vertical-align: bottom;
  padding-top: 5px;
  padding-bottom: 5px;
  overflow-x: hidden;
  display: inline-block;
  width: 100%;
}

#tjdigtdsnt .gt_group_heading {
  padding-top: 8px;
  padding-bottom: 8px;
  padding-left: 5px;
  padding-right: 5px;
  color: #333333;
  background-color: #FFFFFF;
  font-size: 100%;
  font-weight: initial;
  text-transform: inherit;
  border-top-style: solid;
  border-top-width: 2px;
  border-top-color: #D3D3D3;
  border-bottom-style: solid;
  border-bottom-width: 2px;
  border-bottom-color: #D3D3D3;
  border-left-style: none;
  border-left-width: 1px;
  border-left-color: #D3D3D3;
  border-right-style: none;
  border-right-width: 1px;
  border-right-color: #D3D3D3;
  vertical-align: middle;
}

#tjdigtdsnt .gt_empty_group_heading {
  padding: 0.5px;
  color: #333333;
  background-color: #FFFFFF;
  font-size: 100%;
  font-weight: initial;
  border-top-style: solid;
  border-top-width: 2px;
  border-top-color: #D3D3D3;
  border-bottom-style: solid;
  border-bottom-width: 2px;
  border-bottom-color: #D3D3D3;
  vertical-align: middle;
}

#tjdigtdsnt .gt_from_md > :first-child {
  margin-top: 0;
}

#tjdigtdsnt .gt_from_md > :last-child {
  margin-bottom: 0;
}

#tjdigtdsnt .gt_row {
  padding-top: 8px;
  padding-bottom: 8px;
  padding-left: 5px;
  padding-right: 5px;
  margin: 10px;
  border-top-style: solid;
  border-top-width: 1px;
  border-top-color: #D3D3D3;
  border-left-style: none;
  border-left-width: 1px;
  border-left-color: #D3D3D3;
  border-right-style: none;
  border-right-width: 1px;
  border-right-color: #D3D3D3;
  vertical-align: middle;
  overflow-x: hidden;
}

#tjdigtdsnt .gt_stub {
  color: #333333;
  background-color: #FFFFFF;
  font-size: 100%;
  font-weight: initial;
  text-transform: inherit;
  border-right-style: solid;
  border-right-width: 2px;
  border-right-color: #D3D3D3;
  padding-left: 5px;
  padding-right: 5px;
}

#tjdigtdsnt .gt_stub_row_group {
  color: #333333;
  background-color: #FFFFFF;
  font-size: 100%;
  font-weight: initial;
  text-transform: inherit;
  border-right-style: solid;
  border-right-width: 2px;
  border-right-color: #D3D3D3;
  padding-left: 5px;
  padding-right: 5px;
  vertical-align: top;
}

#tjdigtdsnt .gt_row_group_first td {
  border-top-width: 2px;
}

#tjdigtdsnt .gt_summary_row {
  color: #333333;
  background-color: #FFFFFF;
  text-transform: inherit;
  padding-top: 8px;
  padding-bottom: 8px;
  padding-left: 5px;
  padding-right: 5px;
}

#tjdigtdsnt .gt_first_summary_row {
  border-top-style: solid;
  border-top-color: #D3D3D3;
}

#tjdigtdsnt .gt_first_summary_row.thick {
  border-top-width: 2px;
}

#tjdigtdsnt .gt_last_summary_row {
  padding-top: 8px;
  padding-bottom: 8px;
  padding-left: 5px;
  padding-right: 5px;
  border-bottom-style: solid;
  border-bottom-width: 2px;
  border-bottom-color: #D3D3D3;
}

#tjdigtdsnt .gt_grand_summary_row {
  color: #333333;
  background-color: #FFFFFF;
  text-transform: inherit;
  padding-top: 8px;
  padding-bottom: 8px;
  padding-left: 5px;
  padding-right: 5px;
}

#tjdigtdsnt .gt_first_grand_summary_row {
  padding-top: 8px;
  padding-bottom: 8px;
  padding-left: 5px;
  padding-right: 5px;
  border-top-style: double;
  border-top-width: 6px;
  border-top-color: #D3D3D3;
}

#tjdigtdsnt .gt_striped {
  background-color: rgba(128, 128, 128, 0.05);
}

#tjdigtdsnt .gt_table_body {
  border-top-style: solid;
  border-top-width: 2px;
  border-top-color: #D3D3D3;
  border-bottom-style: solid;
  border-bottom-width: 2px;
  border-bottom-color: #D3D3D3;
}

#tjdigtdsnt .gt_footnotes {
  color: #333333;
  background-color: #FFFFFF;
  border-bottom-style: none;
  border-bottom-width: 2px;
  border-bottom-color: #D3D3D3;
  border-left-style: none;
  border-left-width: 2px;
  border-left-color: #D3D3D3;
  border-right-style: none;
  border-right-width: 2px;
  border-right-color: #D3D3D3;
}

#tjdigtdsnt .gt_footnote {
  margin: 0px;
  font-size: 90%;
  padding-left: 4px;
  padding-right: 4px;
  padding-left: 5px;
  padding-right: 5px;
}

#tjdigtdsnt .gt_sourcenotes {
  color: #333333;
  background-color: #FFFFFF;
  border-bottom-style: none;
  border-bottom-width: 2px;
  border-bottom-color: #D3D3D3;
  border-left-style: none;
  border-left-width: 2px;
  border-left-color: #D3D3D3;
  border-right-style: none;
  border-right-width: 2px;
  border-right-color: #D3D3D3;
}

#tjdigtdsnt .gt_sourcenote {
  font-size: 90%;
  padding-top: 4px;
  padding-bottom: 4px;
  padding-left: 5px;
  padding-right: 5px;
}

#tjdigtdsnt .gt_left {
  text-align: left;
}

#tjdigtdsnt .gt_center {
  text-align: center;
}

#tjdigtdsnt .gt_right {
  text-align: right;
  font-variant-numeric: tabular-nums;
}

#tjdigtdsnt .gt_font_normal {
  font-weight: normal;
}

#tjdigtdsnt .gt_font_bold {
  font-weight: bold;
}

#tjdigtdsnt .gt_font_italic {
  font-style: italic;
}

#tjdigtdsnt .gt_super {
  font-size: 65%;
}

#tjdigtdsnt .gt_two_val_uncert {
  display: inline-block;
  line-height: 1em;
  text-align: right;
  font-size: 60%;
  vertical-align: -0.25em;
  margin-left: 0.1em;
}

#tjdigtdsnt .gt_footnote_marks {
  font-style: italic;
  font-weight: normal;
  font-size: 75%;
  vertical-align: 0.4em;
}

#tjdigtdsnt .gt_asterisk {
  font-size: 100%;
  vertical-align: 0;
}

#tjdigtdsnt .gt_slash_mark {
  font-size: 0.7em;
  line-height: 0.7em;
  vertical-align: 0.15em;
}

#tjdigtdsnt .gt_fraction_numerator {
  font-size: 0.6em;
  line-height: 0.6em;
  vertical-align: 0.45em;
}

#tjdigtdsnt .gt_fraction_denominator {
  font-size: 0.6em;
  line-height: 0.6em;
  vertical-align: -0.05em;
}
</style>
<table class="gt_table">
  
  <thead class="gt_col_headings">
    <tr>
      <th class="gt_col_heading gt_columns_bottom_border gt_right" rowspan="1" colspan="1">am1</th>
      <th class="gt_col_heading gt_columns_bottom_border gt_right" rowspan="1" colspan="1">am2</th>
      <th class="gt_col_heading gt_columns_bottom_border gt_right" rowspan="1" colspan="1">am3</th>
      <th class="gt_col_heading gt_columns_bottom_border gt_right" rowspan="1" colspan="1">am4</th>
      <th class="gt_col_heading gt_columns_bottom_border gt_right" rowspan="1" colspan="1">am5</th>
    </tr>
  </thead>
  <tbody class="gt_table_body">
    <tr><td class="gt_row gt_right">14.69</td>
<td class="gt_row gt_right">15.31</td>
<td class="gt_row gt_right">12.91</td>
<td class="gt_row gt_right">12.88</td>
<td class="gt_row gt_right">10.98</td></tr>
    <tr><td class="gt_row gt_right">11.96</td>
<td class="gt_row gt_right">11.78</td>
<td class="gt_row gt_right">9.86</td>
<td class="gt_row gt_right">14.57</td>
<td class="gt_row gt_right">11.46</td></tr>
    <tr><td class="gt_row gt_right">11.13</td>
<td class="gt_row gt_right">14.55</td>
<td class="gt_row gt_right">12.64</td>
<td class="gt_row gt_right">14.80</td>
<td class="gt_row gt_right">12.49</td></tr>
    <tr><td class="gt_row gt_right">11.05</td>
<td class="gt_row gt_right">14.97</td>
<td class="gt_row gt_right">12.79</td>
<td class="gt_row gt_right">14.14</td>
<td class="gt_row gt_right">15.60</td></tr>
    <tr><td class="gt_row gt_right">14.24</td>
<td class="gt_row gt_right">13.77</td>
<td class="gt_row gt_right">13.80</td>
<td class="gt_row gt_right">11.80</td>
<td class="gt_row gt_right">10.84</td></tr>
    <tr><td class="gt_row gt_right">16.19</td>
<td class="gt_row gt_right">15.64</td>
<td class="gt_row gt_right">15.57</td>
<td class="gt_row gt_right">12.52</td>
<td class="gt_row gt_right">10.96</td></tr>
    <tr><td class="gt_row gt_right">12.75</td>
<td class="gt_row gt_right">7.92</td>
<td class="gt_row gt_right">13.88</td>
<td class="gt_row gt_right">12.50</td>
<td class="gt_row gt_right">13.48</td></tr>
    <tr><td class="gt_row gt_right">14.15</td>
<td class="gt_row gt_right">13.09</td>
<td class="gt_row gt_right">16.71</td>
<td class="gt_row gt_right">12.09</td>
<td class="gt_row gt_right">12.60</td></tr>
  </tbody>
  
  
</table>
</div>
```






Estes dados podem ser encontrados no arquivo [dap5.csv](data/dap5.csv)

Uma Análise de Variância pode ser executada com as funções `lm` e `anova`, como a seguir:


```r
aov_dap5 <- lm(dap~amostra, data=dap5)
anova(aov_dap5)
```

```
## Analysis of Variance Table
## 
## Response: dap
##           Df  Sum Sq Mean Sq F value Pr(>F)
## amostra    4   7.371  1.8428  0.5075 0.7305
## Residuals 35 127.091  3.6312
```




Queremos testar a hipótese nula de que não há diferenças entre os diâmetros médios das cinco populações de onde as amostras foram retiradas:

H~0~:μ~1~ = μ~2~ = μ~3~ = μ~~4 = μ~5~

A hipótese alternativa é a de que há alguma diferença, isto é, nem todas as três médias populacionais são iguais:

H~1~: nem todas as médias μ são iguais

A priori, sabemos que as cinco amostras foram aleatoriamente retiradas da mesma população. Logo, o teste F da Análise de Variância é não significativo (como esperado). Seu p-valor foi de 0.73 e, por isso, não rejeitamos a hipótese H~0~, ou seja, não há evidências que os diâmetros médios das amostras sejam diferentes ou que venham de populações diferentes.

Mas o que occoreria se houvesse um efeito aditivo em cada uma das amostras?
Vamos supor que a amostra 1 tenha um efeito aditivo de +5 unidades no DAP. A amostra 2 de -5, a amostra 3 de +3, a amostra 4 de +2 e, por fim, a amostra 5 não tenha nenhum efeito aditivo. O resultado é este mostrado no arquivo [dap5p.csv](data/dap5p.csv)





```{=html}
<div id="xzcvtvieoo" style="overflow-x:auto;overflow-y:auto;width:auto;height:auto;">
<style>html {
  font-family: -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, Oxygen, Ubuntu, Cantarell, 'Helvetica Neue', 'Fira Sans', 'Droid Sans', Arial, sans-serif;
}

#xzcvtvieoo .gt_table {
  display: table;
  border-collapse: collapse;
  margin-left: auto;
  margin-right: auto;
  color: #333333;
  font-size: 16px;
  font-weight: normal;
  font-style: normal;
  background-color: #FFFFFF;
  width: auto;
  border-top-style: solid;
  border-top-width: 2px;
  border-top-color: #A8A8A8;
  border-right-style: none;
  border-right-width: 2px;
  border-right-color: #D3D3D3;
  border-bottom-style: solid;
  border-bottom-width: 2px;
  border-bottom-color: #A8A8A8;
  border-left-style: none;
  border-left-width: 2px;
  border-left-color: #D3D3D3;
}

#xzcvtvieoo .gt_heading {
  background-color: #FFFFFF;
  text-align: center;
  border-bottom-color: #FFFFFF;
  border-left-style: none;
  border-left-width: 1px;
  border-left-color: #D3D3D3;
  border-right-style: none;
  border-right-width: 1px;
  border-right-color: #D3D3D3;
}

#xzcvtvieoo .gt_title {
  color: #333333;
  font-size: 125%;
  font-weight: initial;
  padding-top: 4px;
  padding-bottom: 4px;
  padding-left: 5px;
  padding-right: 5px;
  border-bottom-color: #FFFFFF;
  border-bottom-width: 0;
}

#xzcvtvieoo .gt_subtitle {
  color: #333333;
  font-size: 85%;
  font-weight: initial;
  padding-top: 0;
  padding-bottom: 6px;
  padding-left: 5px;
  padding-right: 5px;
  border-top-color: #FFFFFF;
  border-top-width: 0;
}

#xzcvtvieoo .gt_bottom_border {
  border-bottom-style: solid;
  border-bottom-width: 2px;
  border-bottom-color: #D3D3D3;
}

#xzcvtvieoo .gt_col_headings {
  border-top-style: solid;
  border-top-width: 2px;
  border-top-color: #D3D3D3;
  border-bottom-style: solid;
  border-bottom-width: 2px;
  border-bottom-color: #D3D3D3;
  border-left-style: none;
  border-left-width: 1px;
  border-left-color: #D3D3D3;
  border-right-style: none;
  border-right-width: 1px;
  border-right-color: #D3D3D3;
}

#xzcvtvieoo .gt_col_heading {
  color: #333333;
  background-color: #FFFFFF;
  font-size: 100%;
  font-weight: normal;
  text-transform: inherit;
  border-left-style: none;
  border-left-width: 1px;
  border-left-color: #D3D3D3;
  border-right-style: none;
  border-right-width: 1px;
  border-right-color: #D3D3D3;
  vertical-align: bottom;
  padding-top: 5px;
  padding-bottom: 6px;
  padding-left: 5px;
  padding-right: 5px;
  overflow-x: hidden;
}

#xzcvtvieoo .gt_column_spanner_outer {
  color: #333333;
  background-color: #FFFFFF;
  font-size: 100%;
  font-weight: normal;
  text-transform: inherit;
  padding-top: 0;
  padding-bottom: 0;
  padding-left: 4px;
  padding-right: 4px;
}

#xzcvtvieoo .gt_column_spanner_outer:first-child {
  padding-left: 0;
}

#xzcvtvieoo .gt_column_spanner_outer:last-child {
  padding-right: 0;
}

#xzcvtvieoo .gt_column_spanner {
  border-bottom-style: solid;
  border-bottom-width: 2px;
  border-bottom-color: #D3D3D3;
  vertical-align: bottom;
  padding-top: 5px;
  padding-bottom: 5px;
  overflow-x: hidden;
  display: inline-block;
  width: 100%;
}

#xzcvtvieoo .gt_group_heading {
  padding-top: 8px;
  padding-bottom: 8px;
  padding-left: 5px;
  padding-right: 5px;
  color: #333333;
  background-color: #FFFFFF;
  font-size: 100%;
  font-weight: initial;
  text-transform: inherit;
  border-top-style: solid;
  border-top-width: 2px;
  border-top-color: #D3D3D3;
  border-bottom-style: solid;
  border-bottom-width: 2px;
  border-bottom-color: #D3D3D3;
  border-left-style: none;
  border-left-width: 1px;
  border-left-color: #D3D3D3;
  border-right-style: none;
  border-right-width: 1px;
  border-right-color: #D3D3D3;
  vertical-align: middle;
}

#xzcvtvieoo .gt_empty_group_heading {
  padding: 0.5px;
  color: #333333;
  background-color: #FFFFFF;
  font-size: 100%;
  font-weight: initial;
  border-top-style: solid;
  border-top-width: 2px;
  border-top-color: #D3D3D3;
  border-bottom-style: solid;
  border-bottom-width: 2px;
  border-bottom-color: #D3D3D3;
  vertical-align: middle;
}

#xzcvtvieoo .gt_from_md > :first-child {
  margin-top: 0;
}

#xzcvtvieoo .gt_from_md > :last-child {
  margin-bottom: 0;
}

#xzcvtvieoo .gt_row {
  padding-top: 8px;
  padding-bottom: 8px;
  padding-left: 5px;
  padding-right: 5px;
  margin: 10px;
  border-top-style: solid;
  border-top-width: 1px;
  border-top-color: #D3D3D3;
  border-left-style: none;
  border-left-width: 1px;
  border-left-color: #D3D3D3;
  border-right-style: none;
  border-right-width: 1px;
  border-right-color: #D3D3D3;
  vertical-align: middle;
  overflow-x: hidden;
}

#xzcvtvieoo .gt_stub {
  color: #333333;
  background-color: #FFFFFF;
  font-size: 100%;
  font-weight: initial;
  text-transform: inherit;
  border-right-style: solid;
  border-right-width: 2px;
  border-right-color: #D3D3D3;
  padding-left: 5px;
  padding-right: 5px;
}

#xzcvtvieoo .gt_stub_row_group {
  color: #333333;
  background-color: #FFFFFF;
  font-size: 100%;
  font-weight: initial;
  text-transform: inherit;
  border-right-style: solid;
  border-right-width: 2px;
  border-right-color: #D3D3D3;
  padding-left: 5px;
  padding-right: 5px;
  vertical-align: top;
}

#xzcvtvieoo .gt_row_group_first td {
  border-top-width: 2px;
}

#xzcvtvieoo .gt_summary_row {
  color: #333333;
  background-color: #FFFFFF;
  text-transform: inherit;
  padding-top: 8px;
  padding-bottom: 8px;
  padding-left: 5px;
  padding-right: 5px;
}

#xzcvtvieoo .gt_first_summary_row {
  border-top-style: solid;
  border-top-color: #D3D3D3;
}

#xzcvtvieoo .gt_first_summary_row.thick {
  border-top-width: 2px;
}

#xzcvtvieoo .gt_last_summary_row {
  padding-top: 8px;
  padding-bottom: 8px;
  padding-left: 5px;
  padding-right: 5px;
  border-bottom-style: solid;
  border-bottom-width: 2px;
  border-bottom-color: #D3D3D3;
}

#xzcvtvieoo .gt_grand_summary_row {
  color: #333333;
  background-color: #FFFFFF;
  text-transform: inherit;
  padding-top: 8px;
  padding-bottom: 8px;
  padding-left: 5px;
  padding-right: 5px;
}

#xzcvtvieoo .gt_first_grand_summary_row {
  padding-top: 8px;
  padding-bottom: 8px;
  padding-left: 5px;
  padding-right: 5px;
  border-top-style: double;
  border-top-width: 6px;
  border-top-color: #D3D3D3;
}

#xzcvtvieoo .gt_striped {
  background-color: rgba(128, 128, 128, 0.05);
}

#xzcvtvieoo .gt_table_body {
  border-top-style: solid;
  border-top-width: 2px;
  border-top-color: #D3D3D3;
  border-bottom-style: solid;
  border-bottom-width: 2px;
  border-bottom-color: #D3D3D3;
}

#xzcvtvieoo .gt_footnotes {
  color: #333333;
  background-color: #FFFFFF;
  border-bottom-style: none;
  border-bottom-width: 2px;
  border-bottom-color: #D3D3D3;
  border-left-style: none;
  border-left-width: 2px;
  border-left-color: #D3D3D3;
  border-right-style: none;
  border-right-width: 2px;
  border-right-color: #D3D3D3;
}

#xzcvtvieoo .gt_footnote {
  margin: 0px;
  font-size: 90%;
  padding-left: 4px;
  padding-right: 4px;
  padding-left: 5px;
  padding-right: 5px;
}

#xzcvtvieoo .gt_sourcenotes {
  color: #333333;
  background-color: #FFFFFF;
  border-bottom-style: none;
  border-bottom-width: 2px;
  border-bottom-color: #D3D3D3;
  border-left-style: none;
  border-left-width: 2px;
  border-left-color: #D3D3D3;
  border-right-style: none;
  border-right-width: 2px;
  border-right-color: #D3D3D3;
}

#xzcvtvieoo .gt_sourcenote {
  font-size: 90%;
  padding-top: 4px;
  padding-bottom: 4px;
  padding-left: 5px;
  padding-right: 5px;
}

#xzcvtvieoo .gt_left {
  text-align: left;
}

#xzcvtvieoo .gt_center {
  text-align: center;
}

#xzcvtvieoo .gt_right {
  text-align: right;
  font-variant-numeric: tabular-nums;
}

#xzcvtvieoo .gt_font_normal {
  font-weight: normal;
}

#xzcvtvieoo .gt_font_bold {
  font-weight: bold;
}

#xzcvtvieoo .gt_font_italic {
  font-style: italic;
}

#xzcvtvieoo .gt_super {
  font-size: 65%;
}

#xzcvtvieoo .gt_two_val_uncert {
  display: inline-block;
  line-height: 1em;
  text-align: right;
  font-size: 60%;
  vertical-align: -0.25em;
  margin-left: 0.1em;
}

#xzcvtvieoo .gt_footnote_marks {
  font-style: italic;
  font-weight: normal;
  font-size: 75%;
  vertical-align: 0.4em;
}

#xzcvtvieoo .gt_asterisk {
  font-size: 100%;
  vertical-align: 0;
}

#xzcvtvieoo .gt_slash_mark {
  font-size: 0.7em;
  line-height: 0.7em;
  vertical-align: 0.15em;
}

#xzcvtvieoo .gt_fraction_numerator {
  font-size: 0.6em;
  line-height: 0.6em;
  vertical-align: 0.45em;
}

#xzcvtvieoo .gt_fraction_denominator {
  font-size: 0.6em;
  line-height: 0.6em;
  vertical-align: -0.05em;
}
</style>
<table class="gt_table">
  
  <thead class="gt_col_headings">
    <tr>
      <th class="gt_col_heading gt_columns_bottom_border gt_right" rowspan="1" colspan="1">am1</th>
      <th class="gt_col_heading gt_columns_bottom_border gt_right" rowspan="1" colspan="1">am2</th>
      <th class="gt_col_heading gt_columns_bottom_border gt_right" rowspan="1" colspan="1">am3</th>
      <th class="gt_col_heading gt_columns_bottom_border gt_right" rowspan="1" colspan="1">am4</th>
      <th class="gt_col_heading gt_columns_bottom_border gt_right" rowspan="1" colspan="1">am5</th>
    </tr>
  </thead>
  <tbody class="gt_table_body">
    <tr><td class="gt_row gt_right">19.69</td>
<td class="gt_row gt_right">10.31</td>
<td class="gt_row gt_right">15.91</td>
<td class="gt_row gt_right">14.88</td>
<td class="gt_row gt_right">10.98</td></tr>
    <tr><td class="gt_row gt_right">16.96</td>
<td class="gt_row gt_right">6.78</td>
<td class="gt_row gt_right">12.86</td>
<td class="gt_row gt_right">16.57</td>
<td class="gt_row gt_right">11.46</td></tr>
    <tr><td class="gt_row gt_right">16.13</td>
<td class="gt_row gt_right">9.55</td>
<td class="gt_row gt_right">15.64</td>
<td class="gt_row gt_right">16.80</td>
<td class="gt_row gt_right">12.49</td></tr>
    <tr><td class="gt_row gt_right">16.05</td>
<td class="gt_row gt_right">9.97</td>
<td class="gt_row gt_right">15.79</td>
<td class="gt_row gt_right">16.14</td>
<td class="gt_row gt_right">15.60</td></tr>
    <tr><td class="gt_row gt_right">19.24</td>
<td class="gt_row gt_right">8.77</td>
<td class="gt_row gt_right">16.80</td>
<td class="gt_row gt_right">13.80</td>
<td class="gt_row gt_right">10.84</td></tr>
    <tr><td class="gt_row gt_right">21.19</td>
<td class="gt_row gt_right">10.64</td>
<td class="gt_row gt_right">18.57</td>
<td class="gt_row gt_right">14.52</td>
<td class="gt_row gt_right">10.96</td></tr>
    <tr><td class="gt_row gt_right">17.75</td>
<td class="gt_row gt_right">2.92</td>
<td class="gt_row gt_right">16.88</td>
<td class="gt_row gt_right">14.50</td>
<td class="gt_row gt_right">13.48</td></tr>
    <tr><td class="gt_row gt_right">19.15</td>
<td class="gt_row gt_right">8.09</td>
<td class="gt_row gt_right">19.71</td>
<td class="gt_row gt_right">14.09</td>
<td class="gt_row gt_right">12.60</td></tr>
  </tbody>
  
  
</table>
</div>
```





A Anális de Variância, com estes valores atualizados, fica assim:


```r
aov_dap5p <- lm(dap~amostra, data=dap5p)
anova(aov_dap5p)
```

```
## Analysis of Variance Table
## 
## Response: dap
##           Df Sum Sq Mean Sq F value    Pr(>F)    
## amostra    4 482.71 120.678  33.234 1.791e-11 ***
## Residuals 35 127.09   3.631                      
## ---
## Signif. codes:  0 '***' 0.001 '**' 0.01 '*' 0.05 '.' 0.1 ' ' 1
```




Para as mesmas hipóteses anteriores, o teste F da Análise de Variância é significativo (p-valor ~ 0). Neste caso, rejeitamos a hipótese H~0~ e podemos concluir que há evidências de que as amostras tenham médias de diâmetro diferentes ou que seja oriundas de populações diferentes.

