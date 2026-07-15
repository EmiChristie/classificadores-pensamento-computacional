# Dados

Esta pasta reúne todos os datasets intermediários utilizados e produzidos durante o desenvolvimento dos classificadores descritos no artigo *"Identificando Automaticamente Competências do Pensamento Computacional em Questões-Problema do POSCOMP"*.

Os dados estão organizados de acordo com as duas tarefas do pipeline experimental:

1. **Classificação de Questões-Problema**;
2. **Classificação de Competências do Pensamento Computacional**.

Cada tarefa possui seu próprio classificador, com seus próprios datasets piloto, de validação, anotações humanas e resultados intermediários.

## Estrutura

```text
data
├── raw data/
└── modified data/
```

### `raw data`

Contém os dados originais utilizados como ponto de partida do experimento, também disponíveis em: https://doi.org/10.5281/zenodo.17570916

* `dataset_completo.json`: dataset original contendo todas as questões do POSCOMP.

Este arquivo nunca é modificado durante a execução dos notebooks.

---

### `modified data`

Contém todos os datasets intermediários e derivados produzidos ao longo do experimento.

Os arquivos estão organizados por classificador e por etapa experimental.

## Organização dos experimentos

Cada classificador possui três grupos principais de dados:

### `amostras_piloto`

Arquivos utilizados durante os experimentos preliminares, empregados para desenvolvimento e refinamento dos protocolos de classificação (prompts).

Contém:

* datasets sem anotação;
* classificações produzidas automaticamente pelo modelo;
* anotações realizadas pelos avaliadores humanos;
* datasets de comparação entre modelo e avaliadores.

---

### `amostras_validacao`

Arquivos utilizados na avaliação final dos classificadores.

Esta pasta reúne:

* datasets sem anotação;
* classificações produzidas pelo modelo;
* anotações humanas;
* datasets consolidados para cálculo das métricas;
* análises de divergências entre o modelo e os avaliadores.

---

## Convenções

Sempre que possível, os arquivos seguem a seguinte nomenclatura:

| Nome                                        | Descrição                                                             |
| ------------------------------------------- | --------------------------------------------------------------------- |
| `dataset_piloto`                            | Dataset utilizado na etapa piloto.                                    |
| `dataset_validacao`                         | Dataset utilizado na validação final.                                 |
| `dataset_modelo` ou `dataset_it`            | Classificações produzidas automaticamente pelo modelo/iteração atual do modelo.                |
| `dataset_av1`, `dataset_av2`, `dataset_av3` | Anotações individuais dos avaliadores humanos.                        |
| `dataset_avs`                               | Consolidação das avaliações humanas.                                  |
| `dataset_comparacao`                        | Dataset utilizado para comparar classificações humanas e automáticas. |

### Estrutura dos datasets

Os datasets desta pasta podem ser divididos em três categorias: **datasets finais**, **datasets intermediários** e **datasets de análise de divergências**.

#### Datasets finais

Após a validação, cada classificador produz um dataset final contendo as classificações obtidas. Esses resultados podem ser encontrados na pasta `results`.

Os datasets finais preservam todas as colunas presentes no POSCOMP Dataset original e adicionam as classificações produzidas pelos classificadores.

| Coluna              | Descrição                                                                                                                                                                                                       |
| ------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `id`                | Identificador único da questão.                                                                                                                                                                                 |
| `edicao`            | Ano da edição do POSCOMP.                                                                                                                                                                                       |
| `numero`            | Número da questão na prova.                                                                                                                                                                                     |
| `enunciado`         | Texto completo da questão.                                                                                                                                                                                      |
| `alternativas`      | Alternativas da questão.                                                                                                                                                                                        |
| `area_conhecimento` | Área de conhecimento original do POSCOMP.                                                                                                                                                                       |
| `area`              | Área principal utilizada no dataset original.                                                                                                                                                                   |
| `subarea`           | Subárea utilizada no dataset original.                                                                                                                                                                          |
| `gabarito`          | Alternativa correta da questão.                                                                                                                                                                                 |
| `atributo_rag`      | Atributo presente no dataset original.                                                                                                                                                                          |
| `ehQuestaoProblema` | Classificação produzida pelo classificador de questões-problema (`true` para questão-problema e `false` para questão direta).                                                                                   |
| `comp_*`            | Colunas booleanas indicando a presença (`true`) ou ausência (`false`) de cada competência do Pensamento Computacional. Essas colunas são preenchidas apenas para questões classificadas como questões-problema. |

As competências são representadas pelas seguintes colunas:

* `comp_decomposicao`
* `comp_reconhecimento_padroes`
* `comp_abstracao`
* `comp_algoritmos`
* `comp_generalizacao`

---

### Datasets intermediários

Os datasets intermediários registram todas as classificações produzidas durante os experimentos, permitindo reproduzir as análises e calcular as métricas apresentadas no artigo.

Além da identificação da questão e do prompt utilizado, cada competência possui diferentes conjuntos de colunas:

* `it1_*`, `it2_*` e `it3_*`: classificações produzidas nas três execuções independentes do modelo;
* `av1_*`, `av2_*` e `av3_*`: classificações realizadas individualmente pelos três avaliadores humanos;
* `its_*`: classificação final do modelo, obtida por voto majoritário entre as três execuções;
* `avs_*`: classificação final humana, obtida por voto majoritário entre os avaliadores.

Essa organização permite comparar diretamente as decisões do modelo e dos avaliadores em cada competência ou julgamento sobre a natureza da questão.

---

### Datasets de análise de divergências

Os arquivos de análise de divergências documentam os casos em que houve discordância entre o modelo e os avaliadores humanos.

Para o classificador de competências, cada registro contém:

* a competência analisada;
* a classificação do modelo;
* a classificação dos avaliadores;
* a justificativa produzida pelo modelo;
* indicadores de caso limítrofe;
* informações sobre discordâncias entre avaliadores;
* identificação de erros do modelo e respectivas justificativas.

Já para o classificador de questões-problema, são registradas:

* as três classificações independentes do modelo;
* as três avaliações humanas;
* as médias utilizadas para decisão por maioria;
* a justificativa produzida pelo modelo;
* indicadores de casos limítrofes;
* identificação de erros e discordâncias humanas.

Esses arquivos foram utilizados durante a análise qualitativa dos resultados apresentada no artigo.


## Qual pasta utilizar?

Dependendo do objetivo, diferentes conjuntos de dados devem ser utilizados. Para:

* **Executar o pipeline completo,** carregue os arquivos correspondentes ao experimento (piloto ou validação) antes de iniciar o notebook. Durante a execução, diversos arquivos serão atualizados automaticamente.
* **Reproduzir apenas as análises,** utilize os datasets finais disponíveis na pasta `results`, que já contêm todas as classificações necessárias.
* **Inspecionar as avaliações humanas,** consulte as pastas `anotacoes_humanas`.
* **Analisar divergências entre humanos e o modelo,** utilize os arquivos presentes em `analise_de_divergencias` da etapa de validação do classificador desejado.

**Note que** diversos notebooks sobrescrevem automaticamente alguns arquivos intermediários durante a execução. Recomenda-se manter uma cópia dos datasets originais caso sejam realizadas novas classificações utilizando outros modelos ou diferentes configurações de prompt.
