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
- Interpretabilidade limitada, pois não há coeficientes ou estruturas interpretáveis diretamente.  
- Utilização das ferramentas **LIME** e **SHAP** para explicação local das predições, identificando quais features influenciam mais a decisão para cada instância individual.
- Imagem de Referência:
  
  <img width="526" height="609" alt="image" src="https://github.com/user-attachments/assets/26c43370-e637-4695-b9d1-feccacb19928" />

Análisando o SHAP, confirmou-se que o modelo KNN aprendeu padrões que são **coerentes** com a realidade do futebol. As *features* mais importantes influenciam a classificação exatamente na direção esperada para cada posição.

| Feature | Direção de Alto Valor (Cor Rosa/Vermelha) | Impacto na Previsão | Coerência Tática |
| :--- | :--- | :--- | :--- |
| **xG/90s** (Gols Esperados por 90 min) | Alto valor | Puxa a previsão para **posições ofensivas (Atacantes)**. | Maior volume de chances de gol é a métrica primária de um atacante. |
| **Clr/90s** (Cortas/Clearances por 90 min) | Alto valor | Puxa a previsão para **posições defensivas (Defensores)**. | Ações defensivas primárias, esperadas de zagueiros e laterais defensivos. |
| **PrgP/90s** (Passes Progressivos por 90 min) | Alto valor | Puxa a previsão para **posições de Meio-Campo** (Meias e Volantes). | Indicador-chave de jogadores que constroem o jogo e conectam a defesa ao ataque. |
 
- Considerações Finais: Ele funciona com base na proximidade dos dados no espaço das features, ou seja, classifica uma nova amostra olhando para os seus vizinhos mais próximos, o que é intuitivo localmente, mas difícil de ser interpretado.



---



### 2. Árvore de Decisão
 
- Realizamos uma análise detalhada da árvore gerada, o que possibilitou identificar as features mais importantes e compreender como cada uma delas influencia o processo de classificação.
-  Imagem de Referência:
     
 <img width="853" height="563" alt="image" src="https://github.com/user-attachments/assets/9158fe35-0e83-453a-9502-59e4cfeb99a6" />

 --
  
- A visualização gráfica da árvore facilita a compreensão do fluxo de decisões tomadas pelo modelo, permitindo a extração de insights claros sobre as regras que determinam a classificação.
-  Imagem de Referência:
     
<img width="1256" height="650" alt="image" src="https://github.com/user-attachments/assets/053dc64c-5537-4a0e-a689-96a1494f8042" /> 


- Considerações Finais: A Árvore de Decisão é um modelo altamente interpretável, pois estrutura suas decisões em regras simples e hierárquicas que podem ser facilmente visualizadas e entendidas. Essa transparência torna o modelo especialmente útil para aplicações que exigem explicações claras e confiáveis das decisões automatizadas, como demonstrado nas imagens de referência acima.



---


  
### 3. Naïve Bayes (GaussianNB)

- O modelo Naïve Bayes é altamente interpretável, pois baseia suas decisões em probabilidades condicionais calculadas a partir das distribuições das features em cada classe.
- A visualização dessas estatísticas por meio de heatmaps permite identificar facilmente quais features possuem valores médios significativamente diferentes entre as classes, evidenciando sua importância para a classificação.
- -  Imagem de Referência:
     
<img width="1034" height="362" alt="image" src="https://github.com/user-attachments/assets/65396cae-2b56-43b9-843c-17a9c49fac80" />

Obs. Entretanto, a hipótese de independência entre as features, embora simplifique o modelo e aumente sua interpretabilidade, pode limitar sua precisão em casos onde as variáveis são correlacionadas.


---

## Resultados e Conclusões

- O **KNN** apresentou a melhor acurácia (~94%), porém sua interpretabilidade é limitada, exigindo o uso de técnicas externas para explicação local das decisões.  
- A **Árvore de Decisão** teve desempenho competitivo (~90%) e alta interpretabilidade, com regras claras e fácil visualização das features mais influentes.  
- O **Naïve Bayes**, apesar de mais simples, entregou resultados razoáveis (~88%) e permitiu uma análise probabilística das decisões.

Concluímos que a escolha do modelo ideal depende do equilíbrio desejado entre performance e interpretabilidade. Apresar de não estarmos satisfeitos com as métricas do Naïve Bayes, ele pode ser muito útil, já que sua alta iterpretabilidade pode favorecer em cenários específicos. Por exemplo, em certos contextos críticos, como na área da saúde ou do direito, a explicabilidade pode ser mais importante que a acurácia máxima.

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
