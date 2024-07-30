# 📊 Previsão de Estoque Inteligente na AWS com [SageMaker Canvas](https://aws.amazon.com/pt/sagemaker/canvas/)

Bem-vindo ao desafio de projeto "Previsão de Estoque Inteligente na AWS com SageMaker Canvas.

## 🚀 Passo a Passo

### 1. Selecionar Dataset

- O dataset selecionado para o treinamento do modelo de Machine Learning foi `dataset-1000-com-preco-promocional-e-renovacao-estoque.csv`, disponível no repositório fornecido pela DIO.

![screenshot dataset](https://github.com/user-attachments/assets/d89764a7-f1be-4761-8f6e-5d8d910ee7e4)

### 2. Construir/Treinar

- Com o modelo criado, a coluna target `QUANTIDADE_ESTOQUE` foi selecionada.

![screenshot modelo](https://github.com/user-attachments/assets/df19458e-736b-432f-87c2-d350f564b1b9)

- Para as configurações, foi selecionado `ID_PRODUTO` como identificador de cada item.
- O SageMaker Canvas detectou automaticamente a coluna `DATA_EVENTO` como a coluna do tipo timestamp.
- O calendário de feriados do Brasil foi ativado para aumentar a eficiência do modelo.

![screenshot configurações modelo](https://github.com/user-attachments/assets/5336f9a9-86f7-4b65-8d09-045ac9aff971)

- O modelo foi construído no modo Quick Build.

![screenshot modelo sendo construído](https://github.com/user-attachments/assets/4cc99e06-f0bd-4dda-b598-b69f99cbcd1b)

### 3. Analisar

Construção finalizada, estes foram os resultados do treinamento do modelo:

![screenshot_resultados treinamento](https://github.com/user-attachments/assets/24daadb5-0959-4ce7-80dc-a27d8814f790)

- `wQL` avalia a previsão como um todo, calculando a média da precisão em pontos específicos da distribuição chamados quantis para os quantis P10, P50 e P90.
- `MAPE` é o erro percentual (diferença percentual entre o valor médio previsto e o valor real) em média em todos os pontos de tempo.
- `WAPE` mede o desvio geral dos valores previstos em relação aos valores observados e é definido pela soma do erro absoluto normalizado pela soma da meta absoluta.
- `RMSE` é a raiz quadrada da média quadrada dos erros.
- `MASE` é a média do erro absoluto da previsão normalizada pelo erro absoluto médio de um método simples de previsão de linha de base.
- Quanto mais próximos de 0 foram os indicadores, mais precisos serão os resultados da previsão.

### 4. Prever

Previsão para o Item `1000`:

![screenshot previsão](https://github.com/user-attachments/assets/cb02a6aa-7ab1-4d24-a0dc-91bfa16b9324)

Previsão em formato de tabela:

![screenshot previsão (tabela)](https://github.com/user-attachments/assets/3e0eda8c-d1eb-48cd-afaf-c39fe0ab6ad1)

#### Percentis

Significado de cada indicador da tabela:

- `P10` (Percentil 10): Representado pela linha rosa, reflete um cenário pessimista. Ou seja, é o valor abaixo do qual 10% das observações reais estão localizadas.
- `P50` (Percentil 50): Representado pela linha verde, reflete um cenário neutro. É o valor mediano ou central das observações reais.
- `P90` (Percentil 90): Representado pela linha amarela, reflete um cenário otimista. É o valor acima do qual 90% das observações reais estão localizadas.
