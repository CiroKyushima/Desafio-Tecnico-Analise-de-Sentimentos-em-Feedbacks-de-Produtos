#  Análise de Sentimentos em Feedbacks de Produto

##  Sobre o Projeto

Este projeto foi desenvolvido como parte do Bootcamp **AI/R Company – Fellowship Agentic AI – Data & AI**.

O desafio consistiu em analisar feedbacks textuais enviados por clientes através de diferentes canais de comunicação e construir uma solução capaz de identificar automaticamente o sentimento associado a cada comentário.

O objetivo principal foi desenvolver uma abordagem coerente para classificação de textos, realizando desde a exploração dos dados até a geração de predições para novos feedbacks, demonstrando raciocínio técnico, tratamento adequado dos dados e interpretação dos resultados.

---

##  Objetivo do Desafio

A proposta do desafio era:

- Analisar o dataset disponibilizado.
- Definir a abordagem mais adequada para o problema.
- Implementar uma solução funcional.
- Apresentar resultados obtidos.
- Discutir limitações da abordagem utilizada.
- Sugerir possíveis melhorias futuras.

---

##  Tecnologias Utilizadas

- Python
- Pandas
- NumPy
- Scikit-Learn
- Jupyter Notebook
- Matplotlib
- Seaborn
- TF-IDF

---

##  Dataset

Foram disponibilizados dois conjuntos de dados:

### Base de Treinamento

Contém os feedbacks já classificados.

| Coluna | Descrição |
|----------|------------|
| id_feedback | Identificador único |
| data_feedback | Data do feedback |
| canal | Canal de origem |
| produto | Produto relacionado |
| texto_feedback | Comentário do usuário |
| sentimento | Classe alvo |

### Base de Avaliação

Possui a mesma estrutura da base de treinamento, porém sem a coluna de sentimento, sendo utilizada para gerar as predições finais.

---

##  Análise Exploratória dos Dados

Antes do treinamento dos modelos foram realizadas etapas de exploração para compreender melhor os dados:

- Verificação de valores ausentes.
- Verificação de registros duplicados.
- Análise da distribuição das classes.
- Quantidade de produtos distintos.
- Quantidade de canais distintos.
- Avaliação inicial dos feedbacks textuais.

Essas análises permitiram compreender a qualidade dos dados e identificar possíveis necessidades de tratamento.

---

##  Pré-processamento dos Textos

Para preparar os feedbacks para os algoritmos de Machine Learning, foi realizado um pipeline simples de tratamento textual:

- Conversão para letras minúsculas.
- Remoção de acentos.
- Normalização textual.
- Transformação dos textos em vetores numéricos utilizando TF-IDF.

O objetivo foi transformar os comentários em uma representação adequada para os algoritmos de classificação.

---

##  Vetorização com TF-IDF

Foi utilizada a técnica **TF-IDF (Term Frequency – Inverse Document Frequency)** para converter os textos em variáveis numéricas.

### Configurações utilizadas

- Unigramas e Bigramas (`ngram_range=(1,2)`)
- Conversão automática para minúsculas
- Remoção de acentos
- Exclusão de termos muito raros

A utilização de bigramas permitiu capturar expressões compostas importantes para análise de sentimentos, contribuindo para um melhor desempenho dos classificadores.

---

##  Modelos Avaliados

Para identificar a melhor abordagem para o problema, foram treinados e comparados três modelos de classificação de texto:

### Modelos testados

- Multinomial Naive Bayes
- Logistic Regression
- Linear SVC

Cada modelo foi treinado utilizando a mesma representação TF-IDF, permitindo uma comparação justa entre os algoritmos.

---

##  Estratégia de Validação

Para garantir uma avaliação mais confiável dos modelos foi utilizada validação cruzada estratificada.

### Stratified K-Fold

Configuração utilizada:

- 5 folds
- Embaralhamento dos dados
- Random State = 42

Essa abordagem garante que cada divisão mantenha proporções semelhantes entre as classes positivas e negativas, reduzindo vieses na avaliação.

---

##  Avaliação dos Modelos

Os classificadores foram avaliados através das principais métricas de classificação:

- Accuracy
- Precision
- Recall
- F1-Score

Além disso, foram utilizados:

- Classification Report
- Matriz de Confusão

Essas métricas permitiram comparar o desempenho dos modelos e selecionar a melhor solução para o problema.

---

##  Comparação dos Modelos

Após o treinamento, os resultados dos três classificadores foram comparados para identificar qual apresentava melhor capacidade de generalização.

A comparação considerou:

- Desempenho médio nos folds da validação cruzada.
- Métricas de classificação.
- Consistência dos resultados.
- Capacidade de classificação em novos exemplos.

---

##  Inferência e Predições

Além da avaliação dos modelos, foi implementado um processo de inferência para analisar novos feedbacks.

Para cada comentário é possível obter:

- Classe prevista.
- Probabilidade associada à previsão.
- Comparação entre os diferentes modelos.

Para permitir estimativas de probabilidade no Linear SVC foi utilizada a técnica de calibração através do **CalibratedClassifierCV**.

---

##  Geração da Base de Submissão

Após a seleção do modelo final, foram geradas as predições da base de avaliação.

O arquivo final segue o formato solicitado no desafio:

```text
id_feedback,sentimento
1,positivo
2,negativo
3,positivo
...
```

Mantendo o identificador original do feedback e a classificação produzida pelo modelo.

---

##  Resultados

Os modelos avaliados apresentaram excelente desempenho para o conjunto de dados disponibilizado.

A comparação entre diferentes algoritmos permitiu identificar a abordagem mais adequada para a tarefa de classificação de sentimentos, fornecendo uma solução funcional capaz de analisar automaticamente novos feedbacks.

---

##  Limitações da Solução

Embora os resultados tenham sido satisfatórios, algumas limitações foram identificadas:

- Dataset relativamente pequeno.
- Dependência de padrões textuais presentes na base de treinamento.
- Dificuldade em interpretar sarcasmo e ironia.
- Ausência de compreensão semântica profunda.
- Limitações inerentes a modelos tradicionais de NLP.

---

##  Melhorias Futuras

Algumas evoluções possíveis para o projeto incluem:

- Utilização de Word Embeddings.
- Aplicação de modelos Transformer.
- Fine-tuning de BERT.
- Balanceamento avançado de classes.
- Busca de hiperparâmetros.
- Pipeline automatizado de treinamento.

---

##  Aprendizados

Este projeto proporcionou experiência prática em:

- Processamento de Linguagem Natural (NLP)
- Classificação de Textos
- Vetorização com TF-IDF
- Validação Cruzada
- Comparação de Modelos de Machine Learning
- Avaliação de Classificadores
- Geração de Predições para Dados Não Rotulados

Além disso, permitiu compreender como técnicas de IA podem auxiliar equipes de Produto e Experiência do Cliente na análise automática de grandes volumes de feedbacks.

---

##  Principais Competências Demonstradas

- Processamento de Linguagem Natural (NLP)

- Vetorização de Texto com TF-IDF

- Validação Cruzada (Stratified K-Fold)

- Comparação de Algoritmos de Machine Learning

- Avaliação de Modelos

- Classificação de Sentimentos

- Geração de Predições

- Organização de Projeto de Ciência de Dados
