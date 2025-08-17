# README – Atividade Ponderada: Classificação Binária com MLP

## Objetivo

O objetivo desta atividade foi desenvolver e treinar uma rede neural perceptron multicamadas (MLP) simples, utilizando Keras, para resolver um problema de classificação binária.
A tarefa consiste em prever se um cliente irá ou não comprar um produto (no dataset, um SUV) com base em suas características.

## Dataset utilizado

Foi utilizado o dataset **Social Network Ads**, disponível publicamente.
Esse conjunto de dados contém informações de clientes de uma rede social e se eles compraram (1) ou não compraram (0) um SUV.

* Número de amostras: 400 clientes
* Número de variáveis (features): 2 atributos principais

  * `Age` (idade)
  * `EstimatedSalary` (salário estimado)
* Classe alvo (y):

  * `0` → Cliente não comprou
  * `1` → Cliente comprou

Em resumo: o modelo precisa aprender a mapear idade + salário para prever se um cliente comprará ou não o produto.

## Preparação dos Dados

1. Seleção de atributos: Foram escolhidos apenas `Age` e `EstimatedSalary` como variáveis de entrada.
2. Normalização: Os dados foram escalonados para melhorar o desempenho da rede.
3. Divisão em treino e teste: O dataset foi separado em 75% para treino e 25% para teste.

## Modelo Proposto

Foi implementado um modelo sequencial simples em Keras:

* Camada de entrada: recebe os 2 atributos (idade e salário).
* Camada de saída:

  * `Dense(1, activation='sigmoid')`
  * Apenas 1 neurônio porque a saída é binária.
  * A função sigmoid gera valores entre 0 e 1 (probabilidade de compra).

### Configurações do modelo

* Otimizador: `adam` → ajusta os pesos automaticamente durante o treino.
* Função de perda: `binary_crossentropy` → usada em classificações binárias.
* Métricas:

  * `accuracy` → mede a proporção de acertos.
  * `F1-score` → mede o equilíbrio entre precisão e recall, importante quando há risco de desbalanceamento entre classes.

## Treinamento

* Épocas: 50
* Batch size: 10

Durante o treinamento, a rede ajustou seus pesos para minimizar a função de perda e aumentar a acurácia.

## Avaliação do Modelo

Após o treinamento, o modelo foi avaliado no conjunto de teste.

* Acurácia: 0.87
  O modelo acertou 87% das previsões.
* F1-score: 0.75
  O equilíbrio entre precisão e recall foi bom, mas indica que o modelo ainda confunde alguns casos da classe positiva.

## Interpretação dos Resultados

* A acurácia alta (87%) mostra que o modelo consegue acertar a maioria dos casos.
* O F1 (0.75), um pouco menor, sugere que o modelo está melhor em prever quem não compra do que quem compra.
* Isso é comum em datasets desbalanceados.

Conclusão: o modelo é simples, mas já demonstra bom desempenho para a tarefa.

## Possíveis Melhorias

1. Adicionar mais camadas e neurônios para capturar padrões não lineares mais complexos.
2. Balanceamento de classes (oversampling ou class weights) para dar mais importância aos compradores (classe 1).
3. Feature engineering, criando variáveis derivadas (faixa etária, categorias de salário, etc.).
4. Ajustar o limiar de decisão, explorando diferentes thresholds além de 0.5 para melhorar o recall da classe positiva.
5. Tuning de hiperparâmetros, ajustando taxa de aprendizado, número de épocas, entre outros.

## Conclusão

Este trabalho mostrou como implementar uma rede neural simples em Keras para resolver um problema de classificação binária.
Mesmo com uma arquitetura bastante básica, o modelo alcançou 87% de acurácia e um F1-score de 0.75, o que é um desempenho satisfatório.

Mais importante do que os números, a atividade permitiu consolidar conceitos fundamentais de redes neurais:

* Representação de dados em features,
* Uso da função sigmoid para saída binária,
* Importância da função de perda, do otimizador e das métricas,
* Interpretação crítica dos resultados e caminhos de melhoria.
