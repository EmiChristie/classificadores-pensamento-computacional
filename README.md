# Identificando Automaticamente Competências do Pensamento Computacional em Questões-Problema do POSCOMP

Repositório dos artefatos do artigo *"Identificando Automaticamente Competências do Pensamento
Computacional em Questões-Problema do POSCOMP"*
Este projeto investiga se Grandes Modelos de Linguagem (LLMs) são capazes de classificar questões educacionais de maneira semelhante a avaliadores humanos.

A pesquisa replica a arquitetura de classificação de áreas do conhecimento proposta por Araújo Júnior ([2025](https://doi.org/10.5753/sbie.2025.12854)) e a adapta para as tarefas de classificação no contexto do Pensamento Computacional investigadas por Costa ([2018](https://www.researchgate.net/publication/328749802_Classificacao_Automatica_de_Questoes_Problema_de_Matematica_para_Aplicacoes_do_Pensamento_Computacional_na_Educacao), [2022](https://dspace.sti.ufcg.edu.br/handle/riufcg/29027)), sendo elas:

- **Identificação de questões-problema**, distinguindo questões que exigem raciocínio contextualizado daquelas de resolução direta;
- **Identificação das Competências do Pensamento Computacional** mobilizadas por cada questão;

Os experimentos foram conduzidos utilizando questões históricas do POSCOMP (Exame Nacional de Pós-Graduação em Ciência da Computação) de 2002 a 2024 como estudo de caso.

---

## Competências classificadas

Neste estudo, cinco competências foram consideradas nas classificações:

|Competência|Definição|
|----------|----------|
|Decomposição|Dividir o problema ou o objeto de análise em partes menores, analisando cada parte separadamente antes de integrar as conclusões.|
|Reconhecimento de Padrões|Identificar regularidades, estruturas recorrentes, analogias ou correspondências, seja em dados, em código, em comportamento de algoritmos ou variantes de um mesmo conceito.|
|Abstração|Identificar e focar nos elementos essenciais do problema, ignorando detalhes concretos irrelevantes, para trabalhar com uma representação simplificada.|
|Algoritmos|Elaborar, compreender, analisar ou executar uma sequência ordenada e finita de passos para atingir um objetivo.|
|Generalização|Estender uma conclusão, regra ou estratégia obtida para um caso particular a um conjunto mais amplo; ou formular uma regra geral a partir de casos específicos apresentados.|

As quatro primeiras dizem respeito às competências previstas pela [BNCC-Computação](http://basenacionalcomum.mec.gov.br/images/BNCC_publicacao.pdf), acrescidas de Generalização, uma competência emergente em trabalhos da área.

---

## Estrutura do repositório
```
├── src/
│ ├── Classificador_de_Competencias_do_PC.ipynb
│ ├── Classificador_de_Questoes_Problema.ipynb
│ └── analysis/
│ 
├── data/ 
│ ├── raw data/ 
│ ├── modified data/ 
│ | ├── classificador_questoes_problema/
│ | └── classificador_competencias/
│ 
├── scripts/
│ 
├── results/ 
│ ├── classificador_questoes_problema/
│ ├── classificador_competencias/
│ └── metrics/
│ 
├── prompts/
│ 
├── README.md 
└── LICENSE
```
---

## Requisitos

- Python 3.11+ (ver `environment.yml` para a versão exata)
- Chave de API do provedor de LLM utilizado `gpt-5.4`

---

## Como reproduzir o experimento

1. **Clone este repositório**
```
git clone https://github.com/EmiChristie/classificadores-pensamento-computacional.git
```
```
cd classificadores-pensamento-computacional
```

3. **Instale as dependências do projeto**

```
pip install -r requirements.txt
```

3. **Configure sua chave da OpenAI**

Crie um arquivo .env contendo:

```
OPENAI_API_KEY=SUA_CHAVE
```

ou insira diretamente sua chave no notebook, na seção "Instalação de dependências" (não recomendado):

```
API_KEY="sua chave"
```

4. **Execute os notebooks da pasta [src](https://github.com/EmiChristie/classificadores-pensamento-computacional/tree/5d2238b95779716f78e9feecc9f72dfa70d0b42b/src)**

5. Alternativamente aos passos 3 e 4, para não gerar custos de chamadas à API da OpenAI, **execute os notebooks da pasta [src/analysis]()** para reproduzir apenas a etapa de análises, usando os dados disponibilizados neste repositório.

### Parâmetros congelados

| Parâmetro     | Valor            |
|---------------|------------------|
| Modelo        |  GPT 5.4 |
| temperature   | 0.7 (mantida do experimento original)      |
| execuções     | 3 (etapa de validação)                |
| voto          | maioria (≥ 2 de 3) |

---

## Dados utilizados

O experimento utiliza do [dataset do POSCOMP](https://doi.org/10.5281/zenodo.17570916), que, até o momento da pesquisa, contém as edições de 2002 a 2024 do exame, totalizando 1.340 questões. O dataset original abrange todas as questões históricas, à exceção daquelas com elementos gráficos.

No [repositório do Zenodo](https://doi.org/10.5281/zenodo.21345318) deste projeto, e na pasta [results](https://github.com/EmiChristie/classificadores-pensamento-computacional/tree/e7fb0c3a1b305ab5f3ec9607ea4da7bfacb205cb/results), os datasets modificados podem ser acessados, contendo anotações sobre a natureza das questões (problema ou direta) e a presença ou ausência de cada competência do Pensamento Computacional.


### Para replicar o experimento com novas questões, recomenda-se que:

- 30 questões sejam utilizadas no experimento piloto, até que você esteja satisfeito com seu protocolo de classificação;
- Cerca de 10% do seu dataset seja utilizado no experimento de validação, com questões distintas das questões piloto, para validar se o protocolo de classificação produz resultados satisfatórios.

Caso seu dataset tenha menos de 300 questões, como ocorreu na classificação de competências nas questões-problema do POSCOMP (apenas 209 questões foram identificadas como questão-problema), recomenda-se seguir a metodologia adotada na pesquisa original, definindo que:

- 20 questões sejam utilizadas no experimento piloto, até que você esteja satisfeito com seu protocolo de classificação;
- 30 questões sejam utilizadas no experimento de validação, com questões distintas das questões piloto, para validar se o protocolo de classificação produz resultados satisfatórios.

---

## Resultados esperados

Após a execução, você deve obter métricas próximas às reportadas no artigo, persistidas na pasta [results/metrics](). Devido à variabilidade inerente às respostas de Grandes Modelos de Linguagem, é possível que suas métricas não sejam exatamente iguais às obtidas originalmente, mas espera-se que o comportamento geral se mantenha. Em linhas gerais:

- A porcentagem de questões-problema identificadas no dataset de validação e no dataset completo é próxima de 15%;
- O classificador de questões-problema apresenta concordância quase perfeita com os avaliadores humanos (Kappa próximo a 0,8);
- O classificador de competências apresenta concordância substancial ou quase perfeita para todas as competências, sendo ```Abstração``` a competência com menor concordância;
- As competências ```Algoritmos``` e ```Abstração``` figuram entre as mais frequentemente identificadas nas questões-problema do POSCOMP;
- As análises estatísticas, tabelas e figuras geradas pelos notebooks devem apresentar padrões semelhantes aos discutidos no artigo, ainda que pequenas diferenças numéricas possam ocorrer.

## Instruções adicionais

Cada pasta contém seu próprio arquivo de documentação. Para entender melhor como o experimento foi construído, o que cada pasta contém e a estrutura dos dados processados, recomenda-se a leitura de:

- [DATA.md](https://github.com/EmiChristie/classificadores-pensamento-computacional/blob/main/data/DATA.md)
- [RESULTS.md](https://github.com/EmiChristie/classificadores-pensamento-computacional/blob/main/results/RESULTS.md)
- [SCRIPTS.md](https://github.com/EmiChristie/classificadores-pensamento-computacional/blob/main/scripts/SCRIPTS.md)
- [SOURCE_CODE.md](https://github.com/EmiChristie/classificadores-pensamento-computacional/blob/main/src/SOURCE_CODE.md)
- [PROMPTS.md](https://github.com/EmiChristie/classificadores-pensamento-computacional/blob/main/prompts/PROMPTS.md)
