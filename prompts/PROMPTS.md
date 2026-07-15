# Prompts

Esta pasta reúne os prompts utilizados pelos classificadores descritos no artigo *"Identificando Automaticamente Competências do Pensamento Computacional em Questões-Problema do POSCOMP"*.

Os prompts representam os principais artefatos metodológicos da pesquisa, definindo o comportamento esperado do modelo de linguagem durante as diferentes etapas do experimento.

## Modelo utilizado

Todos os experimentos foram executados utilizando o **GPT-5.4**, acessado por meio da API da OpenAI.

Os classificadores adotam uma abordagem baseada em **prompt engineering**, isto é, o modelo não passou por qualquer etapa de fine-tuning ou treinamento supervisionado. Todo o conhecimento necessário para a tarefa é especificado diretamente nos prompts, por meio de definições, critérios de classificação, exemplos e restrições sobre o formato da resposta. Essa abordagem permite a fácil adaptação dos classificadores para outras áreas, contextos e disciplinas.

## Organização

Os prompts estão divididos em duas categorias:

### Protocolos de classificação

Os protocolos de classificação constituem o núcleo dos classificadores.

Cada protocolo define:

* o objetivo da tarefa;
* os critérios utilizados para a classificação;
* as regras de decisão;
* o formato esperado da resposta.

Os seguintes protocolos estão disponíveis:

* **Classificador de Questões-Problema:** define os critérios para distinguir questões-problema de questões diretas.
* **Classificador de Competências do Pensamento Computacional:** define os critérios para identificar as competências de Decomposição, Reconhecimento de Padrões, Abstração, Algoritmos e Generalização.

Esses prompts são enviados ao modelo durante a etapa principal de classificação e determinam os resultados produzidos pelos classificadores.

## Prompts de análise de divergências

Após a validação dos classificadores, foram utilizados prompts específicos para apoiar a análise qualitativa das divergências entre o modelo e o gabarito composto pelo voto majoritário dos avaliadores humanos.

Esses prompts solicitam ao modelo justificativas para suas decisões e auxiliam na investigação de casos em que houve discordância. Os resultados produzidos por esses prompts foram utilizados exclusivamente durante a etapa de análise dos resultados apresentada no artigo, compondo uma etapa posterior à de classificação.

## Desenvolvimento dos protocolos de classificação

Os protocolos disponibilizados nesta pasta correspondem às versões finais utilizadas nos experimentos de validação.

Durante o desenvolvimento da pesquisa, os prompts passaram por diversas iterações, refinadas a partir dos experimentos piloto. Apenas as versões finais, responsáveis pelos resultados reportados no artigo, foram persistidas neste repositório.

## Reutilização

Os prompts podem ser adaptados para outros modelos de linguagem ou para novos conjuntos de questões educacionais. Entretanto, diferenças entre modelos, versões ou parâmetros de inferência podem produzir variações nas classificações obtidas.

Para reproduzir os resultados apresentados no artigo, recomenda-se utilizar o mesmo modelo (GPT-5.4) e manter os parâmetros de inferência descritos na metodologia.
