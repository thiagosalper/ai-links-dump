# RESUMO VISTO NO ESTUDO DA CERTIFICACAO AWS
![alt text](images/certified.png){width=200}
## Inteligencia Artificial e Aprendizado de Maquina

### Aprendizado Supervisionado

Precisa de dados rotulados (label data)
Regressão -> dados exemplos
Exemplo de aplicação:
- Previsao do tempo
- Previsao de volume de vendas

Classificação -> dados rotulados
Exemplo de aplicação:
- Prevenção de fraudes
- Validação de spams
- Classificação binária

#### Etapas do Aprendizado Supervisionado
- Treino: treinar o modelo
- Validação: ajuste de parametros e validação de performance
- Teste: validação de performance final do modelo

#### Engenharia de Recurso
Processo de usar conhecimento especifico para selecionar e transformar dado bruto em recurso valioso. -> Ajuda a melhorar performance do modelo

- Exemplo de aplicação em dado estruturado:
> Prever valor de imóvel com base em tamanho, local, quartos.
"Criar" preço por m2 / "Selecionar" pontos importantes / "Transformar" convergir caracteristicas semelhantes de recursos

- Exemplo em dado desestruturado
> Analise de sentimento em reviews
"Converte texto em números usando TF.IDF / Extrair texto de imagens ou extrair bordas"


### Aprendizado Não Supervisionado
Objetivo é descobrir padrões, estruturas ou relacionamento em dados de entrada.
Criar e Descobrir grupos sem rotulos.

Tecnicas comuns como Crustering Association Rule Learning e Anomaly Detection.

#### Anomaly detection Technique
Ex Detecção de fraude, falhas

#### Association Rule Learning Techinique
Ex Mercado quer descobrir produtos que sao frequentemente comprados juntos.

#### Crustering Technique
Usado por grupos de daods com alguma similaridade.
Ex descobrir comportamentos de compra de um determinado grupo de clientes de um mercado.

### Aprendizado Semi-Supervisionado
Uma pequena parte da massa é rotulada e o algoritimo usa como base para rotular o restante.

### Aprendizado por Reforço RL
Um ML em que o agente aprende a tomar decisoes com base na performance de acoes para maximizar as recompensas/feedback.
Ex Games, robotica, financas, veiculos autonomos.

#### RLHF - Aprendizado por reforço com feedback humano
Chat, escolha de respostas, fine tune em modelos existentes.

### Aprendizado Auto-Supervisionado
O modelo rotula os dados de forma autonoma. Resolve problemas geralmente resolvidos por aprendizado supervisionado. Ex reconhecimento de imagem, NLP, BERT, GPT.

## Ajuste de modelos (Model Fit)
Overfitting -> bom desempenho no treino, ruim na validacao.
Underfitting -> desempenho ruim no treino, pode ser um modelo muito simples.
Balanced -> modelo equilibrado
Bias -> Vies, diferença ou erro.
High Bias -> longe da verdade, modelo desesalinhado com dados de treino, considerado um underfitting.

Reduzindo Bias -> usar modelo mais complexo, aumentar numero de recursos de aprendizado de maquina.

Variance -> quando a performance muda muito de acordo com a massa de dados de treino usada.

High Variance -> modelo é muito sensível a mudanças de dados de treino. É um caso de overfitting.

Reduzindo variance -> escolher features mais importantes, quebrar treino e dataset de treino com partes menores em outras vezes.

## Metricas de avaliacao de Modelos

F1 -> é a métrica usada para precisão

Confusion Matrix -> Usada para visualizar casos, parecido com tabela-verdade.

### Métricas principais
- Precisao: melhor quando falso positivo sao raros
- Recall: melhor quando falso negativos sao raros
- F1 Score: melhor quando queremos balanceado entre precisao e recall, especialmente em datasets desbalanceados.
- Accuracy: melhor para datasets equilibrados

AUC-ROC { 0 a 1 } *curva

MAE -> erro absoluto medio
MAPE -> erro percentual absoluto medio
RMSE -> raiz do erro quadratico medio
R2 -> mede visao da variacao do modelo

## Machine learning 
Inferencia -> Fazer previsoes sobre novos dados
Realtime ... Chatbots
Batch ... usado em analise de dados 

#### Inferencia de borda (edge)
Rodar modelos em dispositivos fracos que estao longe de conexoes ou limitados.
SLM -> latencia baixa, pouco processamento, offline 
LLM -> em server remoto, online, mais poder, alta latencia, ex api Bedrock

## Fases de projeto de Machine Learning

|O PROBLEMA| ---> |ML Enquadramento| ---> |Coleta de dados e preparo| --> |Engenharia de Recursos| --> |Treino do modelo e tunning de parametro| --> |Model Evaluation| --> |Objetivos alcançados??|
-->
| NAO | --> |Feature augmentation| --> |Daata augmentation| -- > |Volta para Coleta de dados e preparo|
--> 
| SIM | --> |Teste e deploy de modelo| --> |Predictions| --> |Monitor e debugging| --> |Add new data e retreino| --> |Volta para Colega de dados e preparo|

- Definir objetivo do negocios
- Enquandrar o problema em um ML 
- Processamento de dados 
- Desenvolvimento do Modelo 
- Analise dos dados (matriz correlacao)
- Retreino
- Deplloyment
- Monitoramento 
- Iteracoes

### Hyperparameters
Configuracao antes de iniciar o treino, define a estrutura do modelo e algoritmo de aprendizado.

Hyperparameter tunning
Encontra melhores valores para otmizar performance do modelo, melhorando precisao, diminuindo overfitting.

Como Fazer? SageMaker Automatic Model TUnning AMT. Ex Busca em tabela, Busca aleatoria

Hyperparameters importantes
Learning Rate (taxa de aprendizagem)
Batch size (tamanho do lote)
Number of Epochs 
Regularization

### Overfitting
Quando o modelo performa bem durante os dados de teste, mas nao para novos dados

O que causa?
Dados de treino muito pequenos.
Treino muito longo para dados exemplo unicos.
Muitas epocas para dados curtos.
Modelo complexo com ruido de data sample curto.

Como Previnir?
Autmente training data size
INterrompa treinamento antecipadamante
Data augmentation (diversidade de dataset)
Ajuste hiperparametros (ou adicionar-os)

### Quando Machine Learning nao é apropriada?
Quando o problema puder ser escrito em codigo de programacao, ou seja, puder ser deterministico.


## Aprendizado

### Few-shot learning 
Para impedir ataques de prompt ... template de prompt

### Copiar conteudo
Plagio de IA generativa

### TOP K
Parametro que limita numero de tokens portenciais que o modelo considera em cada etapa da geracao. Valores mais baixos resultam em textos mais facodos e conservadores, pois a escolha é restrita a um conjunto de paralavras de alta probabiliadde. Valores mais altos aumental a diversidade e a aleatoriedade. Limite o numero de palavras consideradas o que pode ser util como medidda de seguranca, mas nem sempre melhor opcao.

### TOP P 
Baseia-se na massa de probabilidade cumulativa das paralavras. Valores mais baixos levam a textos mais preciso e previsiveis. Valores mais altos resultam em saidas mais criativas e variadas. É a forma mais flexivel de controlar a aleatoriedade.

### Diferença: 
TOPK  usa numero fixo de palavras amis provaveis. TOPP usa limite de probabilidade para incluir numero variavel de palavvras que satisfacam esse limite.

### TEmperatura
Controla a aleatoriedade e a criatividade em geral.

### Overfitting (Sobreajuste)
Analogia: Um aluno que decora questoes e nao entender o assunto.

### Underfitting (Subajuste)
ANalogia: Um aluno que nao estuda o suficiente

### CNN (Redes Neurais Convolucionais)
Entende espaco , imagem estatica, frames. Deteccao de objetos em imagens, reconhecimento facial

### RNN (Redes Neurais Recorrentes)
Entende tempo, sequencia temporaal, videos. Processamento de linguagem natural, traducao, sentimento, reconhece fala, previsao de series temporarais. 


[... aqui entrei bastante nos serviso AWS para aplicacao da teoria em pratica, vou pular ...]