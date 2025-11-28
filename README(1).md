# 🧠 Deep Learning Project — Regression & Multi-Class Classification  
Master Sécurité IT & Big Data – FST Tanger  
**Rapport détaillé du TP Deep Learning**

---

## 📌 Introduction

Ce travail s’inscrit dans le cadre du laboratoire Deep Learning. L’objectif est d’appliquer différentes techniques de machine learning et de deep learning sur deux problématiques distinctes :

1. **Régression** : prédire le prix de clôture d’un actif financier.  
2. **Classification multi-classe** : prédire le type de panne dans un système industriel (Maintenance prédictive).

Au travers de ces deux projets, plusieurs techniques ont été manipulées :  
✔ Pré-traitement des données  
✔ Analyse exploratoire (EDA)  
✔ Construction de modèles neuronaux (MLP) sous PyTorch  
✔ Régularisation (Dropout, BatchNorm, Weight Decay)  
✔ Optimisation des hyperparamètres (GridSearchCV + Skorch)  
✔ Visualisation des courbes Loss / Accuracy  
✔ Calcul et interprétation des métriques de performance  

---

# 🧩 PARTIE I — RÉGRESSION (Prédiction du prix de clôture)

## 1️⃣ Pré-traitement et Analyse Exploratoire (EDA)

### ✔ Vérification de la qualité des données
- Aucun *manquant*, aucun *doublon*
- Nettoyage des colonnes inutiles

### ✔ Analyse statistique et corrélations
- Corrélation quasi parfaite entre `open`, `high`, `low`, `close`
- Volume faiblement corrélé → information complémentaire

### ✔ Visualisations
- Histogrammes, heatmap, scatterplots

---

## 2️⃣ Modèle PyTorch (MLP)

- Architecture : 128 → 64 → 32  
- Activation : ReLU  
- Optimizer : Adam  
- Loss : MSELoss  

Résultat :  
- **Très faible erreur** en train et test  
- Modèle convergent, pas d’overfitting

---

## 3️⃣ Grid Search — Optimisation

Paramètres testés : LR, architectures, batch size, epochs, optimizers.  
Meilleurs hyperparamètres :  

- **LR = 0.01**  
- **Optimiseur = Adam**  
- **Architecture = [128,64,32]**  
- **Test Loss ≈ 0.000416**

---

## 4️⃣ Visualisation — Loss et R²

- Courbes Loss montrent une convergence rapide  
- R² très élevé → forte capacité explicative

---

## 5️⃣ Régularisation

- Dropout  
- Batch Normalization  
- L2 Weight Decay  

→ Modèle plus stable, meilleure généralisation

---

# 🧩 PARTIE II — CLASSIFICATION MULTI-CLASSE

## 1️⃣ Prétraitement

Classes : Heat Dissipation, No Failure, Overstrain, Power Failure, Random, Tool Wear.

Étapes :  
✔ Encodage LabelEncoder  
✔ Normalisation StandardScaler  
✔ Vérification outliers/distributions

---

## 2️⃣ Analyse Exploratoire

- Déséquilibre important des classes  
- Corrélation entre température & process temp  
- Boxplots par type de panne

---

## 3️⃣ Équilibrage — SMOTE

SMOTE a permis d’obtenir un dataset **totalement équilibré**, améliorant la capacité du modèle à classifier les classes rares.

---

## 4️⃣ Modèle PyTorch

Architecture finale :  
- 128 → 64 → 32  
- Dropout = 0.2  
- BatchNorm  
- Adam  
- CrossEntropyLoss  

Accuracy test : **97–98%**

---

## 5️⃣ Grid Search (Skorch)

Meilleurs hyperparamètres :  
- LR = 0.001  
- Dropout = 0.2  
- Hidden layers = [128, 64, 32]  
- Batch size = 512  
- Optimizer = Adam  

Cross-val accuracy = **95.88%**

---

## 6️⃣ Courbes Loss & Accuracy

- Aucune trace d’overfitting  
- Accuracy validation ≈ 0.98+  
- Très bonne stabilité

---

## 7️⃣ Évaluation

### 🔥 Résultats finaux :

| Métrique | Train | Test |
|----------|--------|--------|
| Accuracy | **99.07%** | **98.82%** |
| Precision | 99.09% | 98.84% |
| Recall | 99.07% | 98.82% |
| F1-Score | 99.06% | 98.80% |

La matrice de confusion montre une classification presque parfaite.

---

# 📝 Synthèse — Ce que j’ai appris

- Analyse exploratoire poussée  
- Prétraitement (normalisation, encodage, SMOTE)  
- Implémentation d’un MLP PyTorch  
- Régularisation et optimisation  
- Évaluation complète d’un modèle DL  
- Visualisation des métriques  

---

# 📌 Conclusion

Le projet a permis d’appliquer toutes les étapes avancées du Deep Learning.  
Les résultats atteignent jusqu’à **99% d’accuracy**, confirmant la qualité des modèles développés.

---  
