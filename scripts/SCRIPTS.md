# Scripts

Esta pasta contém os scripts utilizados para gerar as versões finais dos gráficos apresentados no artigo *"Identificando Automaticamente Competências do Pensamento Computacional em Questões-Problema do POSCOMP"*.

Embora os notebooks da pasta `src` produzam automaticamente todas as visualizações necessárias para a análise dos resultados, algumas figuras passaram por ajustes visuais para serem inseridas no artigo de forma mais legível e esteticamente agradável.

**Note que** apenas os gráficos efetivamente utilizados na versão final do artigo possuem uma versão nesta pasta.

## Tecnologias utilizadas

* JavaScript
* Apache ECharts

## Como executar

- Cada gráfico é disponibilizado como um arquivo HTML independente.
- Para visualizá-lo, basta abrir o arquivo correspondente em qualquer navegador moderno.

Os scripts contêm os dados utilizados na publicação inseridos diretamente no código. Portanto, os gráficos **não são atualizados automaticamente** quando os notebooks de classificação ou análise são executados novamente.

Caso deseje gerar as figuras utilizando novos resultados, basta substituir os valores presentes no script HTML pelos dados produzidos na nova execução dos notebooks. Alternativamente, o conteúdo do arquivo pode ser copiado para o editor online do Apache ECharts para facilitar a edição e a visualização do gráfico durante o desenvolvimento.
