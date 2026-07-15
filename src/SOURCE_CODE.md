# Código-Fonte

Esta pasta reúne os notebooks Jupyter que implementam o pipeline completo de classificação descrito no artigo *"Identificando Automaticamente Competências do Pensamento Computacional em Questões-Problema do POSCOMP"*.

Os notebooks foram desenvolvidos originalmente no **Google Colab** e constituem a implementação de referência utilizada durante a pesquisa.

## Organização

O pipeline está dividido em duas etapas sequenciais:

1. **Classificador de Questões-Problema**

   * Classifica cada questão do POSCOMP como questão-problema ou questão direta.
   * Produz o dataset que servirá de entrada para a etapa seguinte.
   * Adiciona a coluna ```ehQuestaoProblema``` ao dataset base.

2. **Classificador de Competências do Pensamento Computacional**

   * Processa apenas as questões identificadas como questões-problema.
   * Identifica as competências do Pensamento Computacional mobilizadas por cada questão:

     * Decomposição;
     * Reconhecimento de Padrões;
     * Abstração;
     * Algoritmos;
     * Generalização.
    
## Dados necessários

Antes de executar qualquer notebook, é necessário disponibilizar os arquivos de entrada correspondentes à etapa desejada.

Além do dataset original do POSCOMP, cada etapa utiliza algum arquivo auxiliar que não é gerado automaticamente, como as anotações produzidas pelos avaliadores humanos. Todos os arquivos necessários para cada experimento estão documentados em `DATA.md`.

Como forma de simplificar a preparação do ambiente, recomenda-se carregar **todos os arquivos** da pasta correspondente ao experimento que será executado. Durante a execução, os arquivos gerados automaticamente pelos notebooks substituirão aqueles inicialmente carregados, quando aplicável.

Por exemplo, para reproduzir o experimento piloto do classificador de questões-problema, basta carregar todo o conteúdo da pasta:

```text
data/modified_data/classificador_questoes_problema/amostras_piloto/
```

O mesmo procedimento pode ser adotado para as demais etapas do pipeline, utilizando sempre a pasta correspondente à etapa executada.


## Como executar

Os notebooks podem ser executados diretamente no **Google Colab** ou em qualquer ambiente compatível com Jupyter Notebook.

Antes da execução:

1. Instale as dependências do projeto utilizando o arquivo `requirements.txt`;
2. Configure uma chave válida da API da OpenAI, pois os classificadores utilizam o modelo GPT-5.4.

Para reproduzir o experimento completo, execute os notebooks na ordem em que aparecem nesta pasta:

1. Classificador de Questões-Problema;
2. Classificador de Competências do Pensamento Computacional.

Essa sequência preserva o fluxo original da pesquisa, uma vez que a saída da primeira etapa constitui a entrada da segunda.

## Saídas

Ao final da execução, os notebooks produzem:

* os datasets classificados de cada etapa;
* métricas de avaliação dos classificadores;
* tabelas e gráficos utilizados nas análises;
* arquivos que alimentam os resultados disponíveis na pasta `results`.

**Note que**, devido à natureza não determinística dos Grandes Modelos de Linguagem, novas execuções podem produzir pequenas variações nas classificações e nas métricas obtidas. Espera-se, entretanto, que os resultados preservem os mesmos padrões gerais e as mesmas conclusões apresentadas no artigo.

## Executando apenas as análises

Caso o objetivo seja apenas reproduzir as análises apresentadas no artigo, sem executar novamente o processo de classificação, basta utilizar os notebooks disponíveis na pasta src/analysis. Esses notebooks utilizam os datasets finais gerados durante o experimento original, eliminando a necessidade de novas chamadas à API da OpenAI.

Embora seja recomendável executá-los na mesma ordem da execução completa para acompanhar o fluxo da pesquisa, eles são independentes entre si e podem ser executados em qualquer ordem, pois utilizam apenas os resultados previamente gerados.
