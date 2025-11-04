# PIB France - Modélisation et Prévision

Ce dépôt contient un projet d'analyse et de modélisation consacré à l'étude et la prévision du Produit Intérieur Brut (PIB) de la France. Le travail principal est présenté sous la forme d'un notebook Jupyter (par ex. `pib_modelisation.ipynb`) qui montre l'ingénierie des données, l'analyse exploratoire, la modélisation statistique et par apprentissage automatique, ainsi que la génération de prévisions et de visualisations.

## Table des matières

- [Présentation](#présentation)
- [Contenu du dépôt](#contenu-du-dépôt)
- [Fonctionnalités](#fonctionnalités)
- [Technologies utilisées](#technologies-utilisées)
- [Installation](#installation)
- [Préparation des données](#préparation-des-données)
- [Utilisation](#utilisation)
- [Résultats et visualisations](#résultats-et-visualisations)

## Présentation

L'objectif est d'explorer les séries temporelles macroéconomiques liées au PIB français, de comparer plusieurs approches de modélisation (régressions, modèles ARIMA/ETS, modèles à composantes, modèles basés sur le machine learning et le deep learning) et de produire des prévisions à court et moyen terme. Le notebook documente le pipeline complet : collecte, nettoyage, transformation, entraînement de modèles, évaluation et visualisation.

## Contenu du dépôt

- `pib_modelisation.ipynb` — Notebook principal (prétraitement, EDA, modèles, évaluation, prévisions).
- `README.md` — (Ce fichier) présentation et instructions.
- `les principaux jeux de données nécessaires.csv`

Remarque : certains fichiers de données ne sont pas fournis pour des raisons de taille ou de licence. Voir la section "Préparation des données" pour les sources et comment récupérer les fichiers.

## Fonctionnalités

- Import et nettoyage des séries temporelles macroéconomiques (PIB, consommation, investissement, exportations, etc.).
- Analyse exploratoire (trend, saisonnalité, corrélations, décomposition STL).
- Prétraitement (différenciation, transformation Box-Cox, créations de variables temporelles).
- Modèles statistiques : ARIMA, SARIMA, ETS.
- Modèles de machine learning : régression linéaire, Random Forest, XGBoost.
- Modèles de deep learning pour séries temporelles : LSTM/GRU (si nécessaire).
- Évaluation : train/validation, métriques (RMSE, MAE, MAPE, R²) et backtesting.
- Visualisations des séries, des composants, et des prévisions.
- Export des résultats et des modèles pour déploiement.

## Technologies utilisées

- Python 3.x
- pandas, numpy (manipulation des données)
- matplotlib, seaborn, plotly (visualisation)
- scikit-learn (modèles classiques, métriques)
- statsmodels (ARIMA, ETS, décomposition)
- prophet (optionnel pour prévision)
- xgboost (optionnel)
- tensorflow / keras (LSTM/GRU si utilisé)
- jupyter / jupyterlab

## Installation

1. Cloner le dépôt :
   ```bash
   git clone https://github.com/JasserChihi/PIB_France_Modelisation.git
   cd PIB_France_Modelisation
   ```

2. (Optionnel) Créer et activer un environnement virtuel :
   ```bash
   python -m venv venv
   source venv/bin/activate  # Linux / macOS
   venv\Scripts\activate     # Windows
   ```

3. Installer les dépendances :
   
   - Installer manuellement les paquets principaux :
     ```bash
     pip install pandas numpy matplotlib seaborn scikit-learn statsmodels jupyter
     ```

## Préparation des données

1. Sources possibles pour les séries du PIB et variables macroéconomiques :
   - Banque mondiale / World Bank ([https://data.worldbank.org](https://data.worldbank.org/country/france))
   
2. Télécharger les fichiers (CSV ou série temporelle) .

3. Vérifier les colonnes et le format date (ex. colonnes `date` au format `YYYY-MM-DD` ou `YYYY-Qn` pour trimestriel). Adapter le notebook si les noms/format diffèrent.

4. Exemple minimal de préparation dans le notebook :
   - Conversion de la colonne date en index temporel :
     ```python
     df['date'] = pd.to_datetime(df['date'])
     df = df.set_index('date').sort_index()
     ```
   - Remplissage/traitement des valeurs manquantes, normalisation si nécessaire.

## Utilisation

- Ouvrir et exécuter le notebook localement :
  ```bash
  jupyter notebook pib_modelisation.ipynb
  ```
  puis exécuter les cellules (Shift+Enter) dans l'ordre.

- Exécuter dans Google Colab :
  1. Aller sur https://colab.research.google.com/
  2. Ouvrir le notebook depuis GitHub : File → Open notebook → GitHub → collez l'URL du fichier `pib_modelisation.ipynb`.
  3. Monter un Google Drive ou uploader les fichiers CSV nécessaires.

## Résultats et visualisations

Le notebook génère généralement :
- Graphiques de la série historique (niveau, croissance).
- Décomposition trend/saisonnalité/residu (STL).
- Comparaison des prévisions issues de plusieurs modèles.
- Courbes d'erreur (RMSE, MAE) sur validation/backtest.
- Scénarios de prévision à court et moyen terme (ex. 1 à 8 trimestres).

Exemples de métriques que vous trouverez dans le notebook :
- RMSE, MAE, MAPE pour chaque modèle.
- R² pour modèles de régression.
- Visualisation des intervalles de confiance (si pris en charge par le modèle).

## Extensions recommandées

- Ajout de variables explicatives supplémentaires (consommation, inflation, taux d'intérêt, indicateurs avancés).
- Automatisation du pipeline (scripts pour téléchargement et mise à jour des séries).
- Déploiement d'une API pour servir les prévisions (FastAPI / Flask).
- Mise en place d'un backtesting systématique et d'une surveillance des performances.

---

## Auteur : Jasser Chihi  
Pour toute question, suggestion ou bug, ouvrez une issue sur le dépôt ou contactez-moi directement.
