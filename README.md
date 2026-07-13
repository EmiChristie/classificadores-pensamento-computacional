# Identificando Automaticamente Competências do Pensamento Computacional em Questões-Problema do POSCOMP

Repositório dos artefatos do artigo "Identificando Automaticamente Competências do Pensamento
Computacional em Questões-Problema do POSCOMP"

### Sobre o projeto

Este projeto investiga se Grandes Modelos de Linguagem (LLMs) são capazes de classificar questões educacionais de maneira semelhante a avaliadores humanos.

A pesquisa replica a arquitetura de classificação de áreas do conhecimento proposta por Araújo Júnior (2025) e a adapta para as tarefas de classificação no contexto do Pensamento Computacional investigadas por Costa (2018, 2022), sendo elas:

- Identificação de questões-problema, distinguindo questões que exigem raciocínio contextualizado daquelas de resolução direta;
- Identificação das Competências do Pensamento Computacional mobilizadas por cada questão;

Os experimentos foram conduzidos utilizando questões históricas do POSCOMP (Exame Nacional de Pós-Graduação em Ciência da Computação) de 2002 a 2024 como estudo de caso.

### Competências classificadas

Neste estudo, cinco competências foram consideradas nas classificações:

- Decomposição
- Reconhecimento de Padrões
- Abstração
- Algoritmos
- Generalização

As quatro primeiras dizem respeito às competências previstas pela BNCC-Computação, acrescidas de Generalização, uma competência emergente em trabalhos da área.

### Dados utilizados

O experimento utiliza do [dataset do POSCOMP](https://doi.org/10.5281/zenodo.17570916), que, até o momento da pesquisa, contém as edições de 2002 a 2024 do exame, totalizando 1.340 questões. O dataset original abrange todas as questões históricas, à exceção daquelas com elementos gráficos.

No [repositório do Zenodo](https://doi.org/10.5281/zenodo.21345318) deste projeto, e na pasta [results](https://github.com/EmiChristie/classificadores-pensamento-computacional/tree/e7fb0c3a1b305ab5f3ec9607ea4da7bfacb205cb/results), os datasets modificados podem ser acessados, contendo anotações sobre a natureza das questões (problema ou direta) e a presença ou ausência de cada competência do Pensamento Computacional.

### Estrutura do repositório
```
├── src/ 
│ 
├── data/ 
│ ├── raw/ 
│ ├── modified/ 
│ | ├── classificador_questoes_problema/
│ | └── classificador_competencias/
│ 
├── scripts/
│ 
├── results/ 
│ ├── classificador_questoes_problema/
│ └── classificador_competencias/
│ 
├── README.md 
└── LICENSE
```
### Instruções para reprodutibilidade

1. Clone este repositório.
```git clone https://github.com/EmiChristie/classificadores-pensamento-computacional.git```
```cd classificadores-pensamento-computacional```

2. Instale as dependências do projeto.

```pip install -r requirements.txt```

3. Configure sua chave da OpenAI.

export OPENAI_API_KEY="SUA_CHAVE"

ou crie um arquivo .env contendo:

OPENAI_API_KEY=SUA_CHAVE

4. Execute os notebooks da pasta [src](https://github.com/EmiChristie/classificadores-pensamento-computacional/tree/5d2238b95779716f78e9feecc9f72dfa70d0b42b/src)

5. [OPCIONAL] Caso deseje reproduzir os gráficos da pasta [scripts/charts](https://github.com/EmiChristie/classificadores-pensamento-computacional/tree/5d2238b95779716f78e9feecc9f72dfa70d0b42b/scripts/charts), que são apenas versões embelezadas dos gráficos dos notebooks produzidos para o artigo execute os scripts da pasta [scripts](https://github.com/EmiChristie/classificadores-pensamento-computacional/tree/5d2238b95779716f78e9feecc9f72dfa70d0b42b/scripts)
