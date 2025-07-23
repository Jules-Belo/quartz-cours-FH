data = `psychophysics_data.csv`

# code python
```python
#!/usr/bin/env python3
# -*- coding: utf-8 -*-
"""
Created on Thu Jan 23 16:01:36 2025

@author: julesbelo
"""




"""
	Une courbe en forme de S (sigmoïde) montrant la relation entre stimulus et réponse.
	•	Une ligne rouge indiquant le seuil de 50% de détection.
	•	Le seuil estimé indiqué sur le graphique et affiché en console.
"""

#%% charger les données

import pandas as pd
import matplotlib.pyplot as plt
import numpy as np
# Charger le fichier avec le bon encodage
df = pd.read_csv('/Users/julesbelo/Downloads/psychophysics_data.csv', sep=';', encoding='ISO-8859-1',na_values=['(vide)'])

# Afficher les premières lignes pour vérifier
print(df.head())


# Vérifier si des valeurs manquantes existent
print(df.isnull().sum())

# Supprimer les lignes contenant des valeurs NaN
df.dropna(inplace=True)

# Convertir les colonnes en types numériques après nettoyage
df['Stimulus'] = df['Stimulus'].astype(float)
df['Response'] = df['Response'].astype(int)

# Vérification après nettoyage
print(df.head())

#%% Calculer la proportion de réponses positives pour chaque stimulus


# Grouper les données par stimulus et calculer la proportion de réponses positives (moyenne)
seuil_data = df.groupby('Stimulus')['Response'].mean()

# Afficher les résultats
print(seuil_data)


#%%  Tracer la courbe psychométrique

plt.plot(seuil_data.index, seuil_data.values, marker='o', linestyle='-')
plt.xlabel('Stimulus')
plt.ylabel('Proportion de réponses positives')
plt.title('Méthode des stimuli constants')

# Ajouter la ligne de seuil à 50% pour identifier le seuil sensoriel
plt.axhline(y=0.5, color='r', linestyle='--', label='Seuil 50%')
plt.legend()

plt.grid()
plt.show()


#%% Trouver le stimulus correspondant au seuil de 50%

# Interpolation linéaire pour estimer le seuil à 50%
seuil_stimulus = np.interp(0.5, seuil_data.values, seuil_data.index)
print(f"Le seuil estimé est : {seuil_stimulus:.3f}")
#0.45

#%% Analyse de la fonction psychométrique (modélisation sigmoidale)


from scipy.optimize import curve_fit

# Définition d'une fonction sigmoïde
def sigmoid(x, x0, k):
    return 1 / (1 + np.exp(-k * (x - x0)))

# Ajustement de la courbe sigmoïde
popt, _ = curve_fit(sigmoid, seuil_data.index, seuil_data.values, p0=[0.5, 10])

# Générer des points pour la courbe ajustée
x_fit = np.linspace(min(seuil_data.index), max(seuil_data.index), 100)
y_fit = sigmoid(x_fit, *popt)

# Tracé des données et de la courbe ajustée
plt.scatter(seuil_data.index, seuil_data.values, label='Données')
plt.plot(x_fit, y_fit, label='Ajustement sigmoïde', color='red')
plt.axhline(0.5, linestyle='--', color='gray', label='Seuil 50%')
plt.xlabel('Stimulus')
plt.ylabel('Proportion de réponses positives')
plt.legend()
plt.title('Ajustement Sigmoïde - Fonction Psychométrique')
plt.grid()
plt.show()

# Affichage du seuil psychométrique estimé
print(f"Seuil estimé (x0) : {popt[0]:.3f}")
print(f"Pente (k) : {popt[1]:.3f}")


#%% Analyse ROC (Receiver Operating Characteristic)

from sklearn.metrics import roc_curve, auc

# Création d'une courbe ROC
fpr, tpr, _ = roc_curve(df['Response'], df['Stimulus'])
roc_auc = auc(fpr, tpr)

# Tracé de la courbe ROC
plt.plot(fpr, tpr, label=f'ROC curve (AUC = {roc_auc:.2f})')
plt.plot([0, 1], [0, 1], linestyle='--', color='gray')
plt.xlabel('Taux de faux positifs')
plt.ylabel('Taux de vrais positifs')
plt.title('Analyse ROC')
plt.legend()
plt.grid()
plt.show()

#%% Calcul du seuil de discrimination (just noticeable difference, JND)

# Calcul de la discrimination (différence entre stimuli proches)
differences = df['Stimulus'].diff().dropna()
JND = differences.mean()

print(f"Différence perceptible moyenne (JND) : {JND:.3f}")
# Différence perceptible moyenne (JND) : -0.001

#%% Histogramme des réponses pour analyser la distribution

plt.hist(df[df['Response'] == 1]['Stimulus'], bins=10, alpha=0.7, label='Détection')
plt.hist(df[df['Response'] == 0]['Stimulus'], bins=10, alpha=0.7, label='Non détection')
plt.xlabel('Stimulus')
plt.ylabel('Fréquence')
plt.title('Distribution des réponses')
plt.legend()
plt.grid()
plt.show()
```
# explications

## Chargement et nettoyage des données

### Objectif
Importer et préparer les données pour l'analyse.

### Explications des étapes
- Chargement du fichier CSV avec un encodage spécifique (`ISO-8859-1`) et gestion des valeurs manquantes représentées par `'(vide)'`.
- Vérification de la présence de valeurs manquantes avec `df.isnull().sum()`.
- Suppression des lignes contenant des valeurs manquantes avec `df.dropna(inplace=True)`.
- Conversion des colonnes en types appropriés (`Stimulus` en `float`, `Response` en `int`).
- Affichage des premières lignes pour vérifier le nettoyage.

### Importance
Cela garantit que les données sont propres et dans le bon format avant l'analyse.

---

## Calcul de la proportion de réponses positives

### Objectif
Calculer le taux de détection pour chaque niveau de stimulus.

### Explications des étapes
- `df.groupby('Stimulus')['Response'].mean()` regroupe les données par valeur de stimulus et calcule la moyenne des réponses (1 = détection, 0 = non-détection).
- Résultat : un tableau où chaque stimulus est associé à un pourcentage de réponses positives.

### Importance
Cela permet de visualiser comment la réponse évolue en fonction de l'intensité du stimulus.

---

## Tracé de la courbe psychométrique

### Objectif
Visualiser la relation stimulus-réponse.

### Explications des étapes
- `plt.plot()` trace la courbe représentant la proportion de détection en fonction du stimulus.
- Une ligne rouge (`plt.axhline()`) est ajoutée à 50 % pour identifier le seuil sensoriel.
- `plt.grid()` ajoute une grille pour améliorer la lisibilité.

### Importance
Cela permet d'analyser visuellement le point auquel le stimulus est détecté dans 50 % des cas.

---

## Estimation du seuil par interpolation linéaire

### Objectif
Trouver le stimulus correspondant à une proportion de détection de 50 %.

### Explications des étapes
- La fonction `np.interp(0.5, seuil_data.values, seuil_data.index)` estime la valeur du stimulus pour laquelle la réponse est de 50 %.
- Résultat affiché : la valeur du stimulus estimée à 50 % de détection.

### Importance
C'est une méthode simple pour estimer le seuil sensoriel de manière linéaire.

---

## Ajustement d'une fonction sigmoïde

### Objectif
Modéliser la relation stimulus-réponse à l'aide d'une fonction sigmoïde.

### Explications des étapes

#### Définition de la fonction sigmoïde


$$y = \frac{1}{1 + e^{-k(x - x_0)}}$$

-  $x_0$ est le seuil estimé (point d'inflexion)
-  $k$  contrôle la pente (sensibilité)

#### Ajustement des paramètres
- `curve_fit(sigmoid, seuil_data.index, seuil_data.values, p0=[0.5, 10])` ajuste la courbe aux données initiales avec des valeurs de départ.

### Importance
La sigmoïde est un modèle couramment utilisé en psychophysique, car elle représente bien la transition progressive entre la non-perception et la perception.

---

## Analyse ROC (Receiver Operating Characteristic)

### Objectif
Évaluer la performance de la détection en termes de vrais et faux positifs.

### Explications des étapes
- `roc_curve(df['Response'], df['Stimulus'])` calcule le taux de faux positifs (FPR) et de vrais positifs (TPR).
- `auc(fpr, tpr)` calcule l'aire sous la courbe (AUC), indicateur de performance.
- Tracé de la courbe ROC avec une diagonale représentant un modèle aléatoire.

### Importance
Cela permet d'évaluer la capacité du système à discriminer les stimuli détectés des stimuli non détectés.

---

## Calcul du seuil de discrimination (JND - Just Noticeable Difference)

### Objectif
Déterminer la plus petite différence perceptible entre deux stimuli.

### Explications des étapes
- `df['Stimulus'].diff().dropna()` calcule la différence entre chaque stimulus consécutif.
- `JND = differences.mean()` donne la moyenne des différences perceptibles.
- Résultat : estimation du plus petit changement détectable.

### Importance
Le JND est un indicateur clé en psychophysique pour comprendre la sensibilité sensorielle.

---

## Histogramme des réponses

### Objectif
Visualiser la distribution des détections et non-détections.

### Explications des étapes
- `plt.hist()` est utilisé pour afficher deux histogrammes superposés :
  - En bleu pour les réponses positives (détection).
  - En orange pour les réponses négatives (non-détection).
- Ajout de légendes et de titres pour l'interprétation.

### Importance
Cela permet d'analyser la répartition des réponses selon les niveaux de stimulus.

