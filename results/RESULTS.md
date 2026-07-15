# Resultados

Esta pasta reúne os principais artefatos produzidos ao final da execução dos classificadores descritos no artigo *"Identificando Automaticamente Competências do Pensamento Computacional em Questões-Problema do POSCOMP"*.

Os arquivos disponibilizados correspondem aos resultados finais do pipeline experimental de cada classificador, e servem tanto para a reprodução das análises quanto para inspeção direta das classificações produzidas pelos modelos.

## Conteúdo

A pasta contém os seguintes artefatos:

* **Datasets classificados:** versões finais dos datasets produzidos em cada etapa do pipeline, contendo as classificações realizadas pelos modelos.
* **Métricas de avaliação:** arquivo CSV contendo as métricas obtidas durante a validação experimental, utilizadas nas análises apresentadas no artigo.

## Organização

Os datasets correspondem às duas etapas do processo de classificação:

1. **Classificação de questões-problema**, responsável por identificar se cada questão é uma questão-problema ou uma questão direta.
2. **Classificação das competências do Pensamento Computacional**, aplicada às questões identificadas como questões-problema.

Além das versões produzidas automaticamente pelos classificadores, também são disponibilizadas as versões híbridas, nas quais as classificações automáticas são substituídas pelas anotações humanas para as questões pertencentes ao conjunto de validação.

## Relação com os notebooks

Os arquivos desta pasta são gerados pelos notebooks presentes em `src/notebooks` e utilizados pelos notebooks da pasta `src/analises` para produzir as tabelas, gráficos e métricas apresentadas no artigo.

Caso o usuário execute novamente o pipeline de classificação, estes arquivos poderão ser sobrescritos com os novos resultados obtidos. Devido à variabilidade inerente ao comportamento de Grandes Modelos de Linguagem, os resultados obtidos podem não ser totalmente iguais, embora espera-se que sigam o mesmo comportamento geral dos artefatos aqui disponibilizados.
