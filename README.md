# Trabalho T1: Interpretabilidade de Modelos de Aprendizado de Máquina

**Matéria:** Aprendizado de Máquina  
**Professora:** Drª Daniela Oliveira Ferreira do Amaral  
**Alunos:** Lucca Iãnez e Matheus Magri  

---

## Descrição do Dataset e do Problema

Neste trabalho, utilizamos um dataset público contendo estatísticas detalhadas de jogadores de futebol da temporada 2024/2025, obtido do Kaggle. O objetivo principal é classificar a posição dos jogadores em campo — Defensor, Meio-campo ou Atacante — a partir de diversas métricas de desempenho, como gols, interceptações, passes progressivos, entre outras.

O dataset possui mais de 2.800 instâncias e um conjunto diversificado de atributos numéricos, o que possibilita uma análise robusta da importância das features e da interpretabilidade dos modelos aplicados.

---

## Objetivo do Trabalho

O foco central deste trabalho é explorar a **interpretabilidade** de modelos de aprendizado de máquina, compreendendo como cada modelo realiza suas previsões e quais variáveis exercem maior influência na classificação. Para isso, treinamos e avaliamos três modelos clássicos e representativos:

- **K-Nearest Neighbors (KNN)**  
- **Árvore de Decisão (Decision Tree)**  
- **Naïve Bayes (GaussianNB)**  

---

## Metodologia

1. **Pré-processamento:**  
   - Seleção criteriosa de features relevantes e normalização das métricas por minutos jogados para evitar viés relacionado ao tempo de jogo.  
   - Divisão estratificada do dataset em conjuntos de treino (80%) e teste (20%) para preservar a distribuição das classes.  
   - Aplicação do escalonamento e transformação dos dados utilizando o método **Yeo-Johnson** para aproximar a distribuição das features à normalidade, beneficiando o desempenho dos modelos.

2. **Treinamento e Avaliação:**  
   - Utilização do método **RFECV (Recursive Feature Elimination with Cross-Validation)** para identificar as features mais importantes.  
   - Otimização dos hiperparâmetros do KNN e da Árvore de Decisão por meio de **GridSearchCV**, garantindo a melhor configuração para cada modelo.  
   - Treinamento do Naïve Bayes, que não requer ajuste complexo de hiperparâmetros.  
   - Avaliação dos modelos utilizando métricas robustas: acurácia, precisão, recall e F1-score, para garantir uma análise completa do desempenho.

3. **Interpretabilidade:**  
   - Aplicação das técnicas **LIME** e **SHAP** para interpretar predições individuais do KNN.  
   - Visualização da estrutura da Árvore de Decisão e análise das features mais influentes, facilitando a compreensão das regras de decisão.  
   - Análise das médias e variâncias das features por classe no Naïve Bayes, permitindo entender como as probabilidades condicionais impactam as previsões.

4. **Comparação e Discussão:**  
   - Comparação detalhada dos resultados e das variáveis mais relevantes apontadas por cada modelo.  
   - Criação de gráficos para visualização clara e comparativa do desempenho individual dos algoritmos.  
   - Discussão crítica sobre as limitações e vantagens de cada modelo, especialmente no que tange à interpretabilidade versus performance.

---

## Interpretabilidade dos Modelos

### 1. K-Nearest Neighbors (KNN)

- Modelo baseado na proximidade dos dados no espaço de features, sem gerar regras explícitas.  
- Interpretabilidade global limitada, pois não há coeficientes ou estruturas interpretáveis diretamente.  
- Utilização das ferramentas **LIME** e **SHAP** para explicação local das predições, identificando quais features influenciam mais a decisão para cada instância individual.

### 2. Árvore de Decisão

- Modelo altamente interpretável que gera regras de decisão claras e visualizáveis.  
- Análise da árvore permite identificar quais features são mais importantes e como elas influenciam a classificação.  
- Visualização gráfica da árvore facilita a compreensão do processo de decisão e a extração de insights.

### 3. Naïve Bayes (GaussianNB)

- Modelo probabilístico que assume independência condicional entre as features.  
- Interpretabilidade baseada na análise das médias e variâncias das features para cada classe, mostrando como as probabilidades condicionais afetam as predições.  
- Limitação importante: a suposição de independência pode não refletir a realidade, impactando a precisão do modelo.

---

## Resultados e Conclusões

- O **KNN** apresentou a melhor acurácia (~94%), porém sua interpretabilidade é limitada, exigindo o uso de técnicas externas para explicação local das decisões.  
- A **Árvore de Decisão** teve desempenho competitivo (~90%) e alta interpretabilidade, com regras claras e fácil visualização das features mais influentes.  
- O **Naïve Bayes**, apesar de mais simples, entregou resultados razoáveis (~88%) e permitiu uma análise probabilística das decisões, embora a suposição de independência das variáveis seja uma limitação.

Concluímos que a escolha do modelo ideal depende do equilíbrio desejado entre performance e interpretabilidade. Em contextos críticos, como saúde ou direito, a explicabilidade pode ser mais importante que a acurácia máxima. Ferramentas como **SHAP** e **LIME** são essenciais para interpretar modelos menos transparentes e aumentar a confiança nas decisões automatizadas.

---

## Bibliotecas Utilizadas

- **Scikit-learn**  
- **Pandas**  
- **NumPy**  
- **Matplotlib**  
- **Seaborn**  
- **SHAP**  
- **LIME**  

---

## Prazo de Entrega

O trabalho será entregue impreterivelmente até 30/09/2025, conforme solicitado.

---

**Lucca Iãnez & Matheus Magri**  
```
