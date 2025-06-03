# 🚨 Classificador de Prioridade em Ocorrências de Desastres Naturais

## 📌 Descrição do Problema

Em contextos de desastres naturais, é essencial determinar a prioridade de atendimento com base em dados objetivos sobre os danos causados. Contudo, essa classificação muitas vezes é feita manualmente, o que pode causar atrasos e inconsistências.

Este projeto propõe um classificador automático que, com base em dados como número de mortos, desalojados, danos em moradias e infraestrutura, consegue prever se uma ocorrência deve ser tratada com **alta**, **média** ou **baixa prioridade**.

---

## 🧐 Solução Desenvolvida

O pipeline consiste nas seguintes etapas principais:

### 1. 📊 Coleta e Normalização dos Dados

* **Fonte:** Base de dados construída a partir de registros reais do S2ID (Sistema Integrado de Informações sobre Desastres) e complementada com amostras artificiais realistas.
* **Normalização:** `StandardScaler` do Scikit-learn aplicado às variáveis numéricas.

### 2. 🤖 Treinamento do Modelo

* **Algoritmo:** `RandomForestClassifier`
* **Divisão dos dados:** 80% treino / 20% teste
* **Acurácia obtida:** \~0.90 (com variança dependendo da aleatoriedade dos dados)

### 3. 💡 Predição manual

* É possível passar dados de entrada manualmente e obter a prioridade prevista.

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
| 🤖 Machine Learning | `scikit-learn`, `RandomForestClassifier` |
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
* Testar normalizadores alternativos (MinMaxScaler)
* Implantar via API para uso em tempo real
* Utilizar dados reais (ex: Defesa Civil, INMET) para refino

---

## 📍 Pitch e Demonstração

ainda vou realizar
