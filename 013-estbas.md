



# Estatística Básica 

Neste capítulo, iremos estudar alguns itens que podem ser compreendidos como a base das análises estatísticas, pois são usados transversalmente em muitos outros assuntos tratados posteriormente.

Para facilitar o entendimento, alguns dos próximos exemplos utilizarão os dados obtidos em uma população conforme descrito a seguir.

Considere uma população com 150 árvores pertencente a um reflorestamento de Mogno Africano. O DAP destas árvores foi medido aos 5 anos após o plantio e os dados são mostrados na tabela abaixo:






```{=html}
<div id="bcekuceuya" style="overflow-x:auto;overflow-y:auto;width:auto;height:auto;">
<style>html {
  font-family: -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, Oxygen, Ubuntu, Cantarell, 'Helvetica Neue', 'Fira Sans', 'Droid Sans', Arial, sans-serif;
}

#bcekuceuya .gt_table {
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

#bcekuceuya .gt_heading {
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

#bcekuceuya .gt_title {
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

#bcekuceuya .gt_subtitle {
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

#bcekuceuya .gt_bottom_border {
  border-bottom-style: solid;
  border-bottom-width: 2px;
  border-bottom-color: #D3D3D3;
}

#bcekuceuya .gt_col_headings {
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

#bcekuceuya .gt_col_heading {
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

#bcekuceuya .gt_column_spanner_outer {
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

#bcekuceuya .gt_column_spanner_outer:first-child {
  padding-left: 0;
}

#bcekuceuya .gt_column_spanner_outer:last-child {
  padding-right: 0;
}

#bcekuceuya .gt_column_spanner {
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

#bcekuceuya .gt_group_heading {
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

#bcekuceuya .gt_empty_group_heading {
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

#bcekuceuya .gt_from_md > :first-child {
  margin-top: 0;
}

#bcekuceuya .gt_from_md > :last-child {
  margin-bottom: 0;
}

#bcekuceuya .gt_row {
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

#bcekuceuya .gt_stub {
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

#bcekuceuya .gt_stub_row_group {
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

#bcekuceuya .gt_row_group_first td {
  border-top-width: 2px;
}

#bcekuceuya .gt_summary_row {
  color: #333333;
  background-color: #FFFFFF;
  text-transform: inherit;
  padding-top: 8px;
  padding-bottom: 8px;
  padding-left: 5px;
  padding-right: 5px;
}

#bcekuceuya .gt_first_summary_row {
  border-top-style: solid;
  border-top-color: #D3D3D3;
}

#bcekuceuya .gt_first_summary_row.thick {
  border-top-width: 2px;
}

#bcekuceuya .gt_last_summary_row {
  padding-top: 8px;
  padding-bottom: 8px;
  padding-left: 5px;
  padding-right: 5px;
  border-bottom-style: solid;
  border-bottom-width: 2px;
  border-bottom-color: #D3D3D3;
}

#bcekuceuya .gt_grand_summary_row {
  color: #333333;
  background-color: #FFFFFF;
  text-transform: inherit;
  padding-top: 8px;
  padding-bottom: 8px;
  padding-left: 5px;
  padding-right: 5px;
}

#bcekuceuya .gt_first_grand_summary_row {
  padding-top: 8px;
  padding-bottom: 8px;
  padding-left: 5px;
  padding-right: 5px;
  border-top-style: double;
  border-top-width: 6px;
  border-top-color: #D3D3D3;
}

#bcekuceuya .gt_striped {
  background-color: rgba(128, 128, 128, 0.05);
}

#bcekuceuya .gt_table_body {
  border-top-style: solid;
  border-top-width: 2px;
  border-top-color: #D3D3D3;
  border-bottom-style: solid;
  border-bottom-width: 2px;
  border-bottom-color: #D3D3D3;
}

#bcekuceuya .gt_footnotes {
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

#bcekuceuya .gt_footnote {
  margin: 0px;
  font-size: 90%;
  padding-left: 4px;
  padding-right: 4px;
  padding-left: 5px;
  padding-right: 5px;
}

#bcekuceuya .gt_sourcenotes {
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

#bcekuceuya .gt_sourcenote {
  font-size: 90%;
  padding-top: 4px;
  padding-bottom: 4px;
  padding-left: 5px;
  padding-right: 5px;
}

#bcekuceuya .gt_left {
  text-align: left;
}

#bcekuceuya .gt_center {
  text-align: center;
}

#bcekuceuya .gt_right {
  text-align: right;
  font-variant-numeric: tabular-nums;
}

#bcekuceuya .gt_font_normal {
  font-weight: normal;
}

#bcekuceuya .gt_font_bold {
  font-weight: bold;
}

#bcekuceuya .gt_font_italic {
  font-style: italic;
}

#bcekuceuya .gt_super {
  font-size: 65%;
}

#bcekuceuya .gt_two_val_uncert {
  display: inline-block;
  line-height: 1em;
  text-align: right;
  font-size: 60%;
  vertical-align: -0.25em;
  margin-left: 0.1em;
}

#bcekuceuya .gt_footnote_marks {
  font-style: italic;
  font-weight: normal;
  font-size: 75%;
  vertical-align: 0.4em;
}

#bcekuceuya .gt_asterisk {
  font-size: 100%;
  vertical-align: 0;
}

#bcekuceuya .gt_slash_mark {
  font-size: 0.7em;
  line-height: 0.7em;
  vertical-align: 0.15em;
}

#bcekuceuya .gt_fraction_numerator {
  font-size: 0.6em;
  line-height: 0.6em;
  vertical-align: 0.45em;
}

#bcekuceuya .gt_fraction_denominator {
  font-size: 0.6em;
  line-height: 0.6em;
  vertical-align: -0.05em;
}
</style>
<table class="gt_table">
  
  
  <tbody class="gt_table_body">
    <tr><td class="gt_row gt_right">14.80</td>
<td class="gt_row gt_right">12.26</td>
<td class="gt_row gt_right">13.77</td>
<td class="gt_row gt_right">14.28</td>
<td class="gt_row gt_right">15.01</td>
<td class="gt_row gt_right">12.83</td>
<td class="gt_row gt_right">14.98</td>
<td class="gt_row gt_right">14.77</td>
<td class="gt_row gt_right">12.88</td>
<td class="gt_row gt_right">13.77</td></tr>
    <tr><td class="gt_row gt_right">11.59</td>
<td class="gt_row gt_right">14.44</td>
<td class="gt_row gt_right">12.52</td>
<td class="gt_row gt_right">14.12</td>
<td class="gt_row gt_right">10.44</td>
<td class="gt_row gt_right">16.19</td>
<td class="gt_row gt_right">13.59</td>
<td class="gt_row gt_right">10.92</td>
<td class="gt_row gt_right">11.42</td>
<td class="gt_row gt_right">15.64</td></tr>
    <tr><td class="gt_row gt_right">13.54</td>
<td class="gt_row gt_right">10.87</td>
<td class="gt_row gt_right">12.80</td>
<td class="gt_row gt_right">16.48</td>
<td class="gt_row gt_right">14.78</td>
<td class="gt_row gt_right">15.31</td>
<td class="gt_row gt_right">16.83</td>
<td class="gt_row gt_right">14.69</td>
<td class="gt_row gt_right">12.63</td>
<td class="gt_row gt_right">13.09</td></tr>
    <tr><td class="gt_row gt_right">12.79</td>
<td class="gt_row gt_right">11.78</td>
<td class="gt_row gt_right">10.94</td>
<td class="gt_row gt_right">13.77</td>
<td class="gt_row gt_right">13.48</td>
<td class="gt_row gt_right">10.60</td>
<td class="gt_row gt_right">13.00</td>
<td class="gt_row gt_right">13.78</td>
<td class="gt_row gt_right">12.38</td>
<td class="gt_row gt_right">7.92</td></tr>
    <tr><td class="gt_row gt_right">15.59</td>
<td class="gt_row gt_right">11.02</td>
<td class="gt_row gt_right">11.85</td>
<td class="gt_row gt_right">13.50</td>
<td class="gt_row gt_right">14.97</td>
<td class="gt_row gt_right">13.49</td>
<td class="gt_row gt_right">13.80</td>
<td class="gt_row gt_right">15.21</td>
<td class="gt_row gt_right">14.14</td>
<td class="gt_row gt_right">12.22</td></tr>
    <tr><td class="gt_row gt_right">11.46</td>
<td class="gt_row gt_right">14.42</td>
<td class="gt_row gt_right">13.32</td>
<td class="gt_row gt_right">11.39</td>
<td class="gt_row gt_right">14.55</td>
<td class="gt_row gt_right">10.04</td>
<td class="gt_row gt_right">15.13</td>
<td class="gt_row gt_right">11.09</td>
<td class="gt_row gt_right">12.05</td>
<td class="gt_row gt_right">10.98</td></tr>
    <tr><td class="gt_row gt_right">11.96</td>
<td class="gt_row gt_right">10.78</td>
<td class="gt_row gt_right">11.49</td>
<td class="gt_row gt_right">11.80</td>
<td class="gt_row gt_right">10.87</td>
<td class="gt_row gt_right">12.91</td>
<td class="gt_row gt_right">12.48</td>
<td class="gt_row gt_right">10.34</td>
<td class="gt_row gt_right">12.79</td>
<td class="gt_row gt_right">11.73</td></tr>
    <tr><td class="gt_row gt_right">10.84</td>
<td class="gt_row gt_right">11.69</td>
<td class="gt_row gt_right">13.78</td>
<td class="gt_row gt_right">11.21</td>
<td class="gt_row gt_right">15.16</td>
<td class="gt_row gt_right">11.79</td>
<td class="gt_row gt_right">11.96</td>
<td class="gt_row gt_right">14.34</td>
<td class="gt_row gt_right">13.63</td>
<td class="gt_row gt_right">12.86</td></tr>
    <tr><td class="gt_row gt_right">12.09</td>
<td class="gt_row gt_right">10.36</td>
<td class="gt_row gt_right">12.59</td>
<td class="gt_row gt_right">16.02</td>
<td class="gt_row gt_right">12.00</td>
<td class="gt_row gt_right">14.24</td>
<td class="gt_row gt_right">13.70</td>
<td class="gt_row gt_right">12.09</td>
<td class="gt_row gt_right">11.84</td>
<td class="gt_row gt_right">9.86</td></tr>
    <tr><td class="gt_row gt_right">12.75</td>
<td class="gt_row gt_right">11.05</td>
<td class="gt_row gt_right">15.00</td>
<td class="gt_row gt_right">10.64</td>
<td class="gt_row gt_right">12.89</td>
<td class="gt_row gt_right">11.48</td>
<td class="gt_row gt_right">13.89</td>
<td class="gt_row gt_right">11.84</td>
<td class="gt_row gt_right">11.95</td>
<td class="gt_row gt_right">11.99</td></tr>
    <tr><td class="gt_row gt_right">12.29</td>
<td class="gt_row gt_right">15.57</td>
<td class="gt_row gt_right">12.50</td>
<td class="gt_row gt_right">15.84</td>
<td class="gt_row gt_right">8.78</td>
<td class="gt_row gt_right">11.29</td>
<td class="gt_row gt_right">10.16</td>
<td class="gt_row gt_right">11.65</td>
<td class="gt_row gt_right">15.60</td>
<td class="gt_row gt_right">14.07</td></tr>
    <tr><td class="gt_row gt_right">11.61</td>
<td class="gt_row gt_right">13.88</td>
<td class="gt_row gt_right">13.47</td>
<td class="gt_row gt_right">16.68</td>
<td class="gt_row gt_right">12.91</td>
<td class="gt_row gt_right">14.52</td>
<td class="gt_row gt_right">15.55</td>
<td class="gt_row gt_right">10.00</td>
<td class="gt_row gt_right">13.76</td>
<td class="gt_row gt_right">12.22</td></tr>
    <tr><td class="gt_row gt_right">14.15</td>
<td class="gt_row gt_right">14.57</td>
<td class="gt_row gt_right">16.71</td>
<td class="gt_row gt_right">13.46</td>
<td class="gt_row gt_right">12.10</td>
<td class="gt_row gt_right">11.36</td>
<td class="gt_row gt_right">12.60</td>
<td class="gt_row gt_right">13.33</td>
<td class="gt_row gt_right">16.45</td>
<td class="gt_row gt_right">9.80</td></tr>
    <tr><td class="gt_row gt_right">14.87</td>
<td class="gt_row gt_right">15.46</td>
<td class="gt_row gt_right">15.38</td>
<td class="gt_row gt_right">10.96</td>
<td class="gt_row gt_right">13.91</td>
<td class="gt_row gt_right">12.64</td>
<td class="gt_row gt_right">14.39</td>
<td class="gt_row gt_right">11.69</td>
<td class="gt_row gt_right">11.05</td>
<td class="gt_row gt_right">11.55</td></tr>
    <tr><td class="gt_row gt_right">10.74</td>
<td class="gt_row gt_right">14.46</td>
<td class="gt_row gt_right">11.16</td>
<td class="gt_row gt_right">12.49</td>
<td class="gt_row gt_right">12.85</td>
<td class="gt_row gt_right">14.55</td>
<td class="gt_row gt_right">11.98</td>
<td class="gt_row gt_right">14.24</td>
<td class="gt_row gt_right">14.87</td>
<td class="gt_row gt_right">11.13</td></tr>
  </tbody>
  
  
</table>
</div>
```


Os dados também podem ser acessados no arquivo [dap.csv](data/dap.csv).




## Medidas de centro

**Média**

A média aritmética é a medida de centro mais comum.

**Mediana**

É o ponto do meio de uma distribuição, o número em relação ao qual metade das observações é menor, e metade, maior.
