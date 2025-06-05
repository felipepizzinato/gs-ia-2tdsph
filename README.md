# 🚨 Classificador de Prioridade em Ocorrências de Desastres Naturais

## 📌 Descrição do Problema

Em contextos de desastres naturais, é essencial determinar a prioridade de atendimento com base em dados objetivos sobre os danos causados. Contudo, essa classificação muitas vezes é feita manualmente, o que pode causar atrasos e inconsistências.

Este projeto propõe um classificador automatizado de prioridade que, com base em dados como número de mortos, desalojados, danos em moradias e infraestrutura, consegue prever se uma ocorrência deve ser tratada com **alta**, **média** ou **baixa prioridade**.

Boa parte da base de dados utilizada foi retirada do **S2ID - Sistema Integrado de Informações sobre Desastres**, sendo posteriormente expandida com amostras artificiais realistas para fins de balanceamento e escalabilidade.

---

## 🧐 Solução Desenvolvida

O pipeline consiste nas seguintes etapas principais:

### 1. 📊 Coleta e Preparação dos Dados

- **Fonte principal:** S2ID (Sistema Integrado de Informações sobre Desastres)
- **Complemento:** Dados sintéticos gerados artificialmente com base em padrões reais, a fim de balancear as classes e ampliar a base.
- **Pré-processamento:**
  - **Seleção de 6 variáveis numéricas com maior impacto em desastres naturais**
  - **Normalização Utilizada:**`StandardScaler`
  - **Justificativa da Escolha:**
    - Reduz o impacto de variáveis com escalas muito diferentes
    - Facilita a interpretação de gráficos e distribuições dos dados
    - Garante compatibilidade com outros algoritmos que dependem fortemente da escala
    - Ajuda na estabilidade numérica e convergência de modelos em treinamentos futuros
    - Boa prática em pipelines de Machine Learning, mantendo consistência e organização

### 2. 🌲 Treinamento do Modelo de Machine Learning

- **Algoritmo Utilizado:** `RandomForestClassifier` 
- **Justificativa da Escolha:**
  - Robusto contra overfitting mesmo com ruído ou dados parcialmente desbalanceados
  - Capaz de lidar bem com variáveis numéricas contínuas
  - Não exige normalização extrema, mas ainda se beneficia dela
  - Fácil de interpretar e ajustar hiperparâmetros
  - Excelente desempenho em classificações multiclasses com dados tabulares
- **Divisão dos dados:** 80% para treino / 20% para teste
- **Acurácia média obtida:** ~0.90 no conjunto de teste

### 3. 🔍 Predição Manual Interativa

- Foi implementada uma função para simular a entrada de uma nova ocorrência (com dados reais ou estimados).
- O usuário pode inserir os dados manualmente e obter a prioridade de resposta automaticamente.

---

## 📈 Features utilizadas

| Categoria       | Atributo                                                                                                                    |
| --------------- | --------------------------------------------------------------------------------------------------------------------------- |
| Danos Humanos   | `DH_Mortos`, `DH_Desabrigados`, `DH_Desalojados`                                                                            |
| Danos Materiais | `DM_Unidades Habitacionais Destruídas`, `DM_Instalações públicas de saúde Valor`, `DM_Instalações públicas de ensino Valor` |

---

## 🌎 Exemplo de fluxo do sistema

```
 +------------------------------+
 |   CSV com dados de ocorrência |
 +------------------------------+
               |
               v
 +---------------------------------+
 |  Normalização com StandardScaler |
 +---------------------------------+
               |
               v
 +--------------------------------+
 | Treinamento com RandomForest   |
 +--------------------------------+
               |
               v
 +------------------------------+
 | Predição da Prioridade         |
 +------------------------------+
```

---

## 📉 Resultados Obtidos

* Modelo alcançou **acurácia de 0.90** no conjunto de teste.
* Suporte equilibrado entre as classes:

  * Alta prioridade
  * Média prioridade
  * Baixa prioridade

### 📊 Exemplo de Predição Manual

```python
entrada = {
    'DH_Mortos': 0,
    'DH_Desabrigados': 5,
    'DH_Desalojados': 10,
    'DM_Unidades Habitacionais Destruídas': 0,
    'DM_Instalações públicas de saúde Valor': 0,
    'DM_Instalações públicas de ensino Valor': 0
}
testar_manual(entrada)
# Saída: Prioridade prevista: Baixa
```

---

## 🌐 Estrutura do Projeto

```
📁 projeto-ml-gs/
├── main.ipynb                       # Pipeline principal
├── data/
│   └── dataset_desafiador_1000_amostras.csv
├── model/
│   ├── modelo_rf.pkl               # Modelo RandomForest treinado
│   └── scaler.pkl                 # Objeto de normalização salvo
└── README.md                      # Documentação do projeto
```

---

## 🛠️ Tecnologias Utilizadas

| Categoria           | Ferramentas/Bibliotecas                  |
| ------------------- | ---------------------------------------- |
| 🤖 Machine Learning | `scikit-learn`, `RandomForestClassifier`, `StandardScaler` |
| 📊 Dados            | `pandas`, `numpy`                        |
| 🎨 Visualização     | `matplotlib`, `seaborn`                  |

---

## 👥 Integrantes

| Nome Completo    | RM     | Turma  |
| ---------------- | ------ | ------ |
| Eduarda Tiemi    | 554756 | 2TDSPH |
| Felipe Pizzinato | 555141 | 2TDSPH |
| Gustavo Sandrini | 557505 | 2TDSPW |

---

## 🤔 Possíveis Melhorias Futuras

* Explorar modelos supervisionados mais robustos (XGBoost, SVM)
* Implantar via API para uso em tempo real
* Utilizar dados 100% reais

---

## 📝 Conclusão

Com base nos resultados obtidos, o classificador de prioridade desenvolvido para as ocorrências de desastres naturais mostrou-se altamente eficaz. O modelo alcançou uma acurácia de 90% no conjunto de teste, o que indica que ele é capaz de classificar corretamente as ocorrências de alta, média e baixa prioridade com uma boa margem de confiança.

Além disso, a classificação equilibrada entre as classes (Alta, Média e Baixa prioridade) demonstrou que o modelo é capaz de lidar bem com dados desbalanceados e fornecer previsões precisas para todas as categorias de prioridade, sem viés para nenhuma delas.

A implementação do RandomForestClassifier, junto com a normalização dos dados utilizando o StandardScaler, foi fundamental para alcançar um bom desempenho, visto que o modelo se beneficiou da padronização das variáveis, especialmente em um conjunto de dados com características tão diversas. A utilização do RandomForest também garantiu robustez contra overfitting e alta interpretabilidade dos resultados.

---

## 📍 Pitch 

ainda vou realizar
