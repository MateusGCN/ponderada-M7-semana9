# aprendizado contínuo em sistema conversacional

## Introdução

Trabalhos recentes mostraram que grandes Modelos de Linguagem (LM), como o T5 (Raffel et al., 2019) e o GPT-3 (Brown et al., 2020), têm a capacidade de armazenar uma quantidade enorme de conhecimento mundial em seus parâmetros quando pré-treinados em um vasto corpus de texto (Petroni et al., 2019). Esses LMs pré-treinados mostraram potencial para servir como bases de conhecimento quando sondados para conhecimento mundial sem nenhum ajuste fino através da tarefa LAnguage Model Analysis (LAMA) (Petroni et al., 2019), que exige a sondagem de LMs para conhecimento mundial de forma zero-shot através de preenchimento de lacunas, e resultados promissores utilizando o conhecimento mundial codificado quando ajustados em várias Tarefas de Linguagem Intensiva em Conhecimento (KILT) (Petroni et al., 2021), por exemplo, resposta a perguntas e diálogos abertos informados.

## Solução Proposta

### Medindo a Retenção de Conhecimento Mundial Invariante ao Tempo:
Definimos conhecimento mundial invariante ao tempo como a informação presente em D0 que não tem possibilidade de entrar em conflito com informações de D1. Por exemplo, se a informação sobre o local de nascimento de Barack Obama está presente em D0, é improvável que D1 contenha informações que contradigam esse fato. Além disso, classificamos instâncias onde os carimbos de tempo são fixos, como "Cristiano Ronaldo jogou em 2010", como invariante ao tempo. Essas instâncias invariáveis ao tempo não devem ser alteradas à medida que os LMs são continuamente pré-treinados em D1. Para medir quanto da informação invariante ao tempo é perdida devido ao esquecimento catastrófico durante o pré-treinamento contínuo, criamos o INVARIANTLAMA, um subconjunto do LAMA (Petroni et al., 2019), consistindo apenas em frases de preenchimento invariante ao tempo detalhadas no Apêndice B.1.

### Novo Corpus de Texto para Modelagem de Linguagem
Para que os LMs renovem seu conhecimento interno, eles precisam ser continuamente pré-treinados em um novo corpus de texto D1 que possui informações atualizadas e novas. Idealmente, D1 deve ser muito menor do que D0, pois um D1 grande, equivalente ao tamanho de D0, resultará em custos computacionais massivos, semelhantes a treinar os LMs do zero. Para construir D1, rastreamos artigos de notícias recentemente publicados na web, criando o CC-RECENTNEWS.
