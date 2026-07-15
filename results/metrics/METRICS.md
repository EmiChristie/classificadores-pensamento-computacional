# Métricas

Esta pasta reúne as métricas gerais decorrentes dos experimentos de validação apresentados no artigo *"Identificando Automaticamente Competências do Pensamento Computacional em Questões-Problema do POSCOMP"*, calculadas a partir da comparação das classificações produzidas pelo modelo com o gabarito obtido a partir das anotações dos avaliadores humanos. Além disso, também reúne métricas de achados sobre o dataset do POSCOMP como um todo.


## Coeficiente de Concordância Kappa (K)

A principal métrica utilizada neste trabalho é o **coeficiente de concordância Kappa**.

Diferentemente da simples porcentagem de acertos, o índice K considera a concordância esperada ao acaso, tornando-se uma medida mais adequada para avaliar a similaridade entre as classificações do modelo e dos avaliadores humanos.

Neste trabalho, a interpretação dos valores segue a escala proposta por Landis e Koch:

| Valor de $\kappa$ | Interpretação               |
| ----------------- | --------------------------- |
| < 0,00            | Concordância pobre          |
| 0,00 – 0,20       | Concordância leve           |
| 0,21 – 0,40       | Concordância razoável       |
| 0,41 – 0,60       | Concordância moderada       |
| 0,61 – 0,80       | Concordância substancial    |
| 0,81 – 1,00       | Concordância quase perfeita |

## Concordância bruta

Em algumas análises também é apresentada a **concordância bruta**, correspondente à porcentagem de decisões em que o modelo e os avaliadores humanos produziram exatamente a mesma classificação.

Essa métrica é utilizada apenas como medida descritiva e complementa a interpretação do coeficiente K.

## Organização dos arquivos

Esta pasta divide-se nos diretórios:

- `achados_dataset`, que reúne valores interessantes de distribuição das categorias observadas no dataset do POSCOMP.
- `experimentos_validacao`, que reúne as métricas de comparação entre as classificações do modelo na etapa de validação de cada classificador, frente ao gabarito composto pelo voto majoritário dos avaliadores humanos.

## Como interpretar?

Os resultados desta pasta devem ser interpretados considerando que o objetivo dos classificadores **não é maximizar a quantidade de classificações positivas**, mas sim reproduzir, da forma mais fiel possível, as decisões tomadas pelos avaliadores humanos.

Assim, quanto maior o valor do **coeficiente Kappa (K)** e da **concordância bruta**, maior a similaridade entre as classificações produzidas pelo modelo e o gabarito humano.

Além das métricas de concordância, alguns arquivos apresentam estatísticas descritivas sobre o dataset do POSCOMP, como a proporção de questões-problema e a frequência de ocorrência de cada competência do Pensamento Computacional. Essas métricas não avaliam o desempenho do classificador, mas descrevem as características observadas no conjunto de questões após a aplicação do pipeline de classificação.

Devido à natureza não determinística dos Grandes Modelos de Linguagem, pequenas variações nos valores podem ocorrer quando os experimentos são reproduzidos. Entretanto, espera-se que os resultados mantenham o mesmo comportamento geral e conduzam às mesmas conclusões apresentadas no artigo.
