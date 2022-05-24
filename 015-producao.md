# Produção de dados

A produção de dados, no contexto da bioestatística, nos ajuda a responder questões científicas de interesse. Assim, podemos considerar uma das etapas mais importantes do método científico, pois mesmo as análises mais modernas e rebuscadas não serão capazes de "melhorar" os dados oriundos de estudos mal planejados ou mal executados.

Para um planejamento bem elaborado, precisamos responder a várias perguntas:

* Qual o objetivo do estudo?
* Quem é a população e quem é a amostra?
* Quais as variáveis de interesse?
* Quais os possíveis resultados?
* Quais os métodos estatísticos serão utilizados?
* Quais as possíveis fontes de viés destes estudo?


:::{.example #mosca name="Mosca das frutas"}


Pesquisadores da evolução desejam estudar o impacto de diferentes dietas sobre a fecundidade de moscas de frutas.

O primeiro passo da produção de dados para essa questão é a especificação da população que desejamos descrever. Os pesquisadores estão interessados na relação entre dieta e fecundidade, mais que na descrição da espécie de moscas de frutas. 

Assim, a população realmente amostrada poderia ser todas as moscas de frutas selvagens do mundo ou qualquer subpopulação de moscas de frutas não essencialmente diferente das de frutas selvagens. 

Os pesquisadores nesse estudo escolheram obter as moscas de frutas de uma colônia de reprodução em Massachusetts. A vantagem é que a população de interesse, nesse caso, é semelhante à usada por outros pesquisadores da área que também encomendaram moscas de frutas dessa mesma colônia. A desvantagem é que essas podem não ser representativas da população de moscas de frutas selvagens.

O segundo passo envolve a escolha do que queremos medir: Como quantificamos “fecundidade”? 

Aqui, fecundidade é definida como a habilidade da fêmea de pôr ovos. Para acompanhar essas pequenas criaturas, os pesquisadores mantiveram-nas em frascos que continham um suprimento de alimento representativo das dietas em estudo. O número de ovos postos por fêmea então foi contado, examinando-se o conteúdo de cada frasco. 

:::



Esses exemplo apresenta um importante problema: nem todos os estudos estatísticos usam amostras extraídas diretamente da população inteira de interesse. Experimentos, em particular, raramente o fazem, devido a considerações práticas e éticas. 
Os pesquisadores no experimento da mosca de fruta realmente não podiam capturar moscas de todo o mundo. A consequência é que as conclusões do experimento não podem ser estendidas diretamente a todas as moscas de frutas. 

Se os resultados podem também se aplicar a uma população maior de moscas de frutas (a colônia inteira em Massachusetts ou mesmo toda a população de moscas de frutas selvagens), **é um argumento biológico, não estatístico**.


## Amostras e estudos observacionais

### Planejamentos amostrais ruins

Antes de tudo, vamos demonstrar alguns planejamentos amostrais ruins. O planejamento amostral mais fácil — mas não o melhor — apenas escolhe os indivíduos mais à mão. Essa é a chamada **amostra de conveniência** e, em geral, produz dados não representativos.

:::{.example #conv name="Amostra de conveniência"}

Se estivéssemos interessados em descobrir o percentual de adultos que tomam vitaminas e suplementos minerais, por exemplo, poderíamos ir a um shopping e perguntar às pessoas que encontrássemos. No entanto, uma amostra em um shopping certamente super-representará a classe média e pessoas aposentadas e sub-representará as pessoas mais pobres. Isto acontecerá em quase todas as vezes que extrairmos tal amostra, ou seja, é um erro sistemático causado por um planejamento amostral ruim, não apenas por má sorte em uma amostra. 

:::

Outro planejamento amostral viesado, a **amostra de resposta voluntária**, permite que os indivíduos escolham se participam ou não. 

Todas as pesquisas de resposta escrita, telefonemas ou online são exemplos de amostras de resposta voluntária. 

Esses tipos de amostra são viesados porque pessoas com opiniões fortes tendem a responder mais. A questão é que pessoas que se dão o trabalho de responder a um convite aberto não são, em geral, representativas de qualquer população claramente definida. 

 Infelizmente, amostras de conveniência e de resposta voluntária tornaram-se muito populares na mídia, porque são baratas e, em geral, (equivocadamente) sensacionalistas.


### Amostragem aleatória

Uma amostra aleatória, ou seja, escolhida pelo acaso, não permite nem o favoritismo por quem faz a amostra, nem a autosseleção por parte de quem responde. A escolha de uma amostra aleatória ataca o viés, ao atribuir a todos os indivíduos a mesma chance de serem escolhidos.


**Amostra Aleatória Simples **

Consiste em *n* indivíduos da população, escolhidos de tal maneira que todos os conjuntos de *n* indivíduos tenham a mesma chance de serem selecionados.

**Amostra Aleatória Estratificada**

Fazer amostras de grupos importantes dentro da população e, então, combiná-las. Os indivíduos selecionados de cada grupo devem ser proporcionais à sua participação na população.

Por exemplo, podemos amostrar grupos étnicos em um primeiro nível e depois amostrar homens e mulheres separadamente em um segundo nível. 

Este processo garante a inclusão tanto de grupos majoritários quanto minoritários.

**Amostra Aleatória de Múltiplos Estágios**

Envolve a escolha de Amostras Aleatórias Simples (AAS) dentro de Amostras Aleatórias Simples. 

Por exemplo, deseja-se amostrar estudantes do ensino fundamental de todo o Brasil para um estudo. Primeiro, escolhe-se uma AAS dos Estados do Brasil. Para cada Estado, escolhe-se uma AAS das escolas. Para cada escola, extrai-se uma AAS de estudantes. 

Isso é mais prático que a seleção direta de uma AAS de estudantes de todas as partes.


## Estudos observacionais

Nos estudos observacionais, o pesquisador mede mas não intervém no estudo, ou seja, apenas observa os acontecimentos naturais. 
Os principais tipos de estudos observacionais são o Controle de caso e Coorte.

### Estudo de Controle de Caso

Em um estudo observacional de controle de caso, sujeitos-caso são selecionados com base em um resultado definido, e um grupo de controle de sujeitos é selecionado separadamente para servir como linha de base com a qual o grupo-caso é comparado.

Os estudos de controle de caso começam com duas amostras de indivíduos, selecionados por seus diferentes resultados, e procura por fatores de exposição no passado dos indivíduos que difiram entre os dois grupos. É chamada de abordagem retrospectiva, pois o estudo se inicia já como resultado observado. 

O principal desafio está na identificação de uma amostra aleatória de indivíduos-controle similares, tanto quanto possível, aos sujeitos-caso. 

É bastante utiliizado quando a resposta observada é rara na população. Por exemplo, um traço encontrado em cerca de um em mil indivíduos exigiria uma amostra aleatória de dez mil para se observar, talvez, cerca de dez indivíduos com o traço de interesse. 


:::{.example #casocontrole name="Aflatoxicose no Quênia"}


Aflatoxinas são compostos tóxicos secretados por um fungo encontrado em cultivos doentes. A aflatoxicose é um raro, mas grave envenenamento, que resulta da ingestão de aflatoxinas em alimento contaminado. 

O Quênia teve um surto de aflatoxicose em 2004, que resultou em mais de três mil casos de falência de fígado. O Ministério da Saúde do Quênia suspeitou que a armazenagem imprópria do milho fosse, em parte, responsável pelo surto. 
Perguntou-se a 40 pacientes-caso e 80 controles saudáveis como tinham armazenado e preparado o milho.

Os pacientes-caso foram selecionados aleatoriamente de uma lista de indivíduos admitidos em um hospital durante o surto de 2004, devido à icterícia aguda inexplicada. 

A seleção dos controles foi cuidadosamente pensada, de modo que fossem tão semelhantes quanto possível aos pacientes-caso, de forma relevante: indivíduos da mesma aldeia do paciente que não haviam tido qualquer história de sintomas de icterícia. 

A seleção de indivíduos que viviam na mesma aldeia garantia que os sujeitos-controle partilhassem o mesmo solo, microclima e práticas agrícolas que os pacientes-caso. 

Uma análise descritiva preliminar dos dados do surto sugeria que o solo, o microclima e as práticas agrícolas poderiam ser fatores influentes, mas não a idade e o gênero.

Uma conclusão do estudo foi que a armazenagem imprópria do milho estava associada a uma taxa mais alta de aflatoxicose.

O estudo da aflatoxicose teve controles cuidadosamente selecionados, permitindo ao pesquisador encontrar causas plausíveis para a epidemia.

:::

Na abordagem retrospectiva, deve-se tomar muito cuidado pois memórias não são sempre precisas, e o viés de lembrança pode ser um fator de confundimento. Por exemplo, os indivíduos hospitalizados por falência aguda do fígado podem ter lembranças diferentes das dos sujeitos-controle, possivelmente porque o assunto interessa mais a eles. 

### Estudo de Coorte

Em um estudo de coorte, sujeitos semelhantes são arrolados e observados em intervalos regulares, durante um longo período.

Esses são estudos prospectivos, que registram, em intervalos regulares, toda espécie de informação relevante sobre os participantes do estudo. 

Quando o estudo termina, os indivíduos que desenvolveram uma condição são, então, comparados com os não afetados. 

Diferentemente dos estudos de controle de caso, os estudos de coorte são muito caros e se adaptam melhor à investigação de resultados comuns.

:::{.example #coorte name="Estudo da Saúde de Enfermeiras"}


O Estudo da Saúde de Enfermeiras é um dos maiores estudos observacionais prospectivos, destinado ao exame de fatores que possam afetar as principais doenças crônicas femininas. 

Desde 1976, o estudo acompanhou uma coorte de mais de 100.000 enfermeiras registradas, com a ideia de que enfermeiras seriam capazes de responder com precisão a questionários com formulação médica. 

A cada dois anos, as enfermeiras que participavam do estudo recebiam um questionário de acompanhamento sobre doenças e tópicos relativos à saúde, como dieta e estilo de vida. As taxas de resposta ao questionário são de cerca de 90%, para cada ciclo de dois anos.

Uma das descobertas do estudo foi a de que a prática de caminhada, quando tinham entre 50 e 60 anos, melhorou sua memória aos 70 anos.

Apesar do pedido para que essas mulheres fizessem um teste cognitivo, o planejamento do estudo ainda era observacional, porque todas as mulheres amostradas faziam o teste, e os pesquisadores não as alocavam aleatoriamente a diferentes regimes de caminhada. 

Na verdade, eles observaram que as mulheres que caminharam mais durante seus 50 e 60 anos terminavam com melhor memória na idade de 70 anos ou mais. 

Por exemplo, pode ser que as mulheres com melhor saúde fossem também mais capazes de caminhar e menos propensas à perda de memória. Portanto, não podemos concluir, sem ambiguidade, que caminhar tenha efeito de proteção contra perda de memória.


:::



## Planejamento de Experimentos

 Os indivíduos estudados em um experimento são, em geral, chamados sujeitos

 As variáveis explicativas em um experimento são chamadas fatores.

 Um tratamento é uma condição experimental específica aplicada aos sujeitos. 

 Se um experimento tiver vários fatores, um tratamento será uma combinação de valores específicos de cada fator.


:::{.example #dieta name="Efeito protetor da dieta do Mediterrâneo"}

As populações mediterrâneas são conhecidas por terem menos doenças do coração e alguns tipos de câncer. Sua dieta, rica em fibras naturais, vitaminas e ácido oleico, tem sido apontada como uma explicação desse fenômeno.

Para testar essa hipótese, um experimento associou 605 sobreviventes de um primeiro ataque cardíaco para seguirem, por cinco anos, uma dieta do tipo Mediterrâneo ou uma dieta da Associação Americana do Coração. 

Os pacientes foram avaliados regularmente, e uma variedade de resultados foi registrada, desde níveis de ácido graxo no plasma até ocorrências de câncer ou ataque do coração ou morte (cardíaca, câncer ou outra). 

A associação a uma ou outra dieta foi aleatória, e os dois grupos não diferiam substancialmente nos aspectos demográficos. Possíveis fatores de confundimento, como fumo e níveis de atividade, foram monitorados de perto e incluídos na análise estatística, mas não foram restringidos ou impostos.

* Há um único fator: “dieta”. 

* Esse experimento compara dois tratamentos: dieta Mediterrâneo e dieta AAC. 

* Os sujeitos são sobreviventes de um primeiro ataque cardíaco, 

* Há muitas variáveis resposta, registradas durante cinco anos, como câncer e ataque do coração. 

::: 

:::{.example #pintinho name="Efeito da variedade do milho e teor proteico no crescimento de pintinhos"}


Novas variedades de milho, com conteúdo de aminoácido alterado, podem ter maior valor nutricional que o milho padrão, que tem baixa quantidade de aminoácido lisina. 

Um experimento compara duas novas variedades, chamadas opaque-2 e floury-2, com o milho normal. 

Os pesquisadores misturaram dietas de milho-soja, usando cada tipo de milho em cada um de três níveis de proteína: 12%, 16% e 20%. 

Eles deram cada dieta a 10 pintinhos machos com um dia de nascidos e registraram seus ganhos de peso depois de 21 dias. O ganho de peso dos pintinhos é uma medida do valor nutricional da dieta.

* Esse experimento tem dois fatores: variedade do milho, com três níveis (opaque-2, floury-2 e normal), e nível de proteína, com três níveis (12%, 16%, 20%). 

* As nove combinações de ambos os fatores formam nove tratamentos. 

* Os indivíduos são os pintinhos machos com um dia

* A variável resposta é o ganho de peso depois de 21 dias sob a dieta de tratamento.  

:::


### Vantagem dos experimentos 

Experimentos são o método preferido para o exame do efeito de uma variável sobre outra. Pela imposição de um tratamento específico de interesse e controle de outras influências, podemos localizar causa e efeito. Planejamentos estatísticos são, em geral, essenciais para experimentos eficazes. Para entendermos por quê, vamos começar com um exemplo de um mau planejamento.


:::{.example #ncontrol name="Um experimento não controlado"}


O congelamento gástrico foi introduzido nos anos 1960 por um proeminente cirurgião como método para aliviar a dor da úlcera. 

Os pacientes deviam engolir um balão vazio, posteriormente enchido com um líquido refrigerado, para esfriar o revestimento do estômago e reduzir a produção de ácido e reduzir a dor. 

Um grupo de sujeitos (os pacientes) foi exposto ao tratamento (congelamento gástrico), e o resultado (redução da dor) foi observado. 

**Sujeitos → Congelamento gástrico → Redução da dor**

Os procedimentos realizados mostraram que o congelamento gástrico realmente reduzia a dor da úlcera, e o tratamento foi recomendado com base nessa evidência.

:::

Mas, o que teria acontecido se tivéssemos deixado os pacientes em paz? A dor deles teria diminuído mesmo sem intervenção? 

E se os pacientes fossem inclinados a dizer que estavam se sentindo melhor (talvez porque esperassem melhorar ou para agradar o experimentador)? 

E se os pacientes realmente se sentissem melhor, mas devido ao cuidado e à atenção que recebiam e que os faziam se sentir bem no geral, não às condições do congelamento do revestimento do estômago? 

Essa é uma possibilidade real, e melhoras psicológicas semelhantes foram documentadas em muitos experimentos humanos. 

Chamamos isso de efeito **placebo.**

O efeito do congelamento gástrico é confundido com o de duas variáveis ocultas: 

* melhora natural, espontânea,

* melhora psicológica devido ao cuidado médico. 

Devido ao confundimento, a melhora do sujeito não pode ser inequivocamente atribuída ao efeito do congelamento gástrico. 


### Experimentos comparativos

A solução para o confundimento do exemplo anterior é a realização de um experimento comparativo:

* Alguns pacientes fazem o tratamento de congelamento gástrico
* Outros pacientes semelhantes realizam um processo simulado
  * Controle em relação ao efeito placebo
* Outros realizam nenhum procedimento
  * Controle em relação ao efeito de melhora natural

A maioria dos experimentos bem planejados compara dois ou mais tratamentos. 

Um **grupo experimental** é um grupo de indivíduos que recebe um tratamento cujo efeito desejamos entender.

Um ***controle*** ou **testemunha** é um tratamento que se destina a servir como parâmetro com o qual o grupo experimental é comparado.

Um **placebo** é um tratamento de controle falso (por exemplo, uma pílula de açúcar), mas que não se distingue do tratamento no grupo experimental.

O efeito placebo é documentado apenas em experimentos humanos, em contextos tão diversos como estudo da asma ou pressão sanguínea alta. O efeito é particularmente forte quando a variável resposta é a dor. Os mecanismos desse efeito mente-corpo são desconhecidos, mas não sem fundamentação biológica. Sabemos que o sistema nervoso interage com o imunológico e que a depressão, por exemplo, suprime a resposta imune.



:::{.example #control name="Um experimento controlado"}


O experimento simples, do exemplo anterior, foi seguido, muitos anos depois, por um experimento controlado aleatorizado

Pacientes que se submetiam ao congelamento gástrico eram comparados com pacientes semelhantes que se submetiam a tratamento semelhante, exceto pelo fato de o líquido bombeado não ser refrigerado (placebo). 

* 34% de melhora – congelamento gástrico  
* 38% de melhora - placebo

Esse experimento comparativo demonstrou que o resfriamento do revestimento do estômago não era mais eficaz para a redução da dor de úlcera que um procedimento falso. O tratamento foi, então, abandonado.

:::


### Planejamento completamente aleatorizado

Em um planejamento experimental completamente aleatorizado, todos os sujeitos são distribuídos aleatoriamente entre os tratamentos. A associação aleatória dos sujeitos forma grupos que devem ser semelhantes em todos os aspectos antes de ser aplicado o tratamento. 

O planejamento comparativo garante que outras influências, diferentes dos tratamentos experimentais, operem igualmente em todos os grupos. Assim, diferenças na resposta média se devem aos tratamentos ou ao papel do acaso na alocação aleatória dos sujeitos aos tratamentos.

Essa última afirmativa merece mais reflexão. Mesmo com um excelente planejamento experimental, nunca podemos dizer que qualquer diferença entre dois grupos seja inteiramente devida ao tratamento aplicado. Variáveis, por definição, variam de indivíduo para indivíduo, e, portanto, um grupo de indivíduos certamente fornecerá um resultado diferente de outro grupo, mesmo nas mesmas condições.

### Princípios do planejamento experimental

Os princípios básicos do planejamento de experimentos são:

1. **Controle** os efeitos de variáveis ocultas na resposta de modo mais simples, pela comparação de dois ou mais tratamentos.

2. **Aleatorize** – use o acaso impessoal para associar os sujeitos aos tratamentos.

3. **Repita** - use sujeitos suficientes em cada grupo para reduzir a variação do acaso nos resultados.




### Planejamentos de dados emparelhados 

Um planejamento de dados emparelhados compara exatamente dois tratamentos, usando uma série de indivíduos proximamente relacionados dois a dois, ou cada indivíduo duas vezes.

Escolha pares de sujeitos que sejam, tanto quanto possível, comparáveis. Esses podem ser indivíduos do mesmo gênero, idade, peso e altura ou geneticamente relacionados, como gêmeos ou animais nascidos da mesma ninhada. A alocação aleatória dos sujeitos aos tratamentos é feita dentro de cada par, e não para todos os sujeitos ao mesmo tempo. Use o acaso para decidir qual dos sujeitos do par recebe o primeiro tratamento. O outro daquele par recebe o outro tratamento. A ordem dos tratamentos pode influenciar a resposta do sujeito, de modo que aleatorizamos a ordem para cada sujeito. 

Às vezes, cada “par” em um planejamento de dados emparelhados consiste em apenas um sujeito, que recebe ambos os tratamentos, um após o outro. Cada sujeito serve como seu próprio controle.

Planejamentos completamente aleatorizados são os planejamentos estatísticos mais simples para experimentos. Eles ilustram claramente os princípios de controle, aleatorização e número adequado de sujeitos. Contudo, eles frequentemente são inferiores a planejamentos estatísticos mais elaborados. Em particular, emparelhar os sujeitos de várias formas pode produzir resultados mais precisos que uma simples aleatorização.


Planejamentos de dados emparelhados usam os princípios de comparação de tratamento e aleatorização. No entanto, a aleatorização não é completa – não alocamos aleatoriamente todos os sujeitos de uma vez aos dois tratamentos. Em vez disso, aleatorizamos apenas dentro de cada par. Isso permite que o emparelhamento reduza o efeito da variação entre os sujeitos. Ser capaz de distinguir um planejamento de dados emparelhados de um completamente aleatorizado é crítico, pois impacta a análise estatística e conclusões.



### Planejamento em blocos

Um bloco é um grupo de indivíduos semelhantes em algum aspecto que se espera poder afetar a resposta aos tratamentos. Em um planejamento em blocos, a alocação aleatória dos indivíduos aos tratamentos é feita separadamente dentro de cada bloco. Um planejamento em blocos combina a ideia da criação de grupos de tratamento equivalentes pelo emparelhamento com o princípio de formação aleatória de grupos de tratamento. 

Blocos são outra forma de controle. Eles controlam os efeitos de algumas variáveis externas ao trazê-las para o experimento na forma de blocos.

:::{.example #bloco name="Diferenças de gênero"}


O progresso de um tipo de câncer difere em mulheres e homens. Assim, um experimento clínico para a comparação de três terapias para esse câncer trata gênero como uma variável de bloco. São feitas duas aleatorizações separadas, uma que associa os sujeitos mulheres aos tratamentos e a outra que associa os homens. 


Os blocos permitem que se extraiam conclusões separadas sobre cada um deles, por exemplo, sobre homens e mulheres. Também permitem conclusões gerais mais precisas, porque as diferenças sistemáticas entre homens e mulheres podem ser removidas quando estudamos os efeitos gerais das três terapias. 

Um pesquisador experiente formará blocos com base nas mais importantes e inevitáveis fontes de variabilidade entre as unidades experimentais. A aleatorização, então, fará a média dos efeitos da variação restante e permitirá uma comparação não viesada dos tratamentos.

:::

### Cuidados com a experimentação

O sucesso de um experimento depende de nossa capacidade de tratar todos os sujeitos de forma idêntica em todos os aspectos, exceto pelos tratamentos que, de fato, estão sendo comparados. Viés do experimentador ou do sujeito são problemas reais, que podem prejudicar experimentos e estudos observacionais. Viés pessoal pode desviar nossas percepções e coleta de dados em observações de campo



Uma forma de evitar estes vieses é a utiliação dos experimentos **duplos-cegos**.
Nestes experimentos, nem os sujeitos e nem as pessoas que interagem com eles sabem qual tratamento cada um está recebendo. Na prática, no entanto, controles ótimos não são sempre alcançáveis. Há situações em que o uso de um placebo é antiético. 

O cegamento nem sempre é prático. Imagine a complexidade de se manter o acompanhamento de pílulas ativas e inativas para vários tratamentos diferentes sob as condições de duplo-cego, envolvendo centenas de sujeitos, durante vários anos. O cegamento nem sempre é uma opção se os pacientes são capazes de diferenciar o tratamento de um falso.

Contudo, a fraqueza potencial mais séria de experimentos é a falta de realismo. Os sujeitos, tratamentos ou contexto de um experimento podem não duplicar realisticamente as condições que, de fato, desejamos estudar. 


:::{.example #real name="Carcinogenicidade da sacarina"}


A carcinogenicidade de um produto é a sua propensão a induzir o câncer quando usado, ingerido ou simplesmente presente no ambiente. A sacarina tem sido usada como adoçante artificial por quase um século. 

Devido à evidência experimental de carcinogenicidade em ratos, a sacarina foi incluída no Relatório sobre cancerígenos dos Estados Unidos em 1981, como potencial cancerígeno em humanos.

No entanto, exames mais detalhados de cânceres de bexiga urinária observados em ratos indicam que o mecanismo biológico desse câncer é específico para o sistema urinário de ratos e relacionado com o consumo de sacarina em concentrações improváveis de representar consumo humano realista. 

A sacarina foi oficialmente retirada da lista em 2005, com a conclusão: *“os fatores que se pensava contribuir para a indução de tumor pela sacarina sódica em ratos não têm ocorrência esperada em humanos”.*

:::

A falta de realismo pode limitar nossa capacidade de aplicar as conclusões de um experimento a contextos de maior interesse. Muitos pesquisadores desejam generalizar suas conclusões a algum contexto mais amplo que o do experimento real. 

A análise estatística de um experimento não pode nos dizer até que ponto os resultados podem ser generalizados. A capacidade de se estender conclusões para além do contexto experimental depende de uma profunda discussão dos **méritos biológicos** do experimento e da **representatividade** dos sujeitos usados. 

 


### Ética na experimentação

Desde humanos a animais e ecossistemas, a experimentação precisa ser cuidadosamente pensada, não apenas para ser estatisticamente poderosa e elegante, mas também para ser responsável. A ética experimental trata de todas as questões que devemos fazer antes, durante e depois da experimentação. 


