
#### Modèles mathématiques de la perception

Les modèles mathématiques de la perception visent à quantifier la relation entre les stimuli physiques et les réponses perceptives. Voici un aperçu des principaux modèles, en commençant par Fechner : 

#### 1. Loi de Fechner (1860) : La psychophysique

La loi de Fechner établit un lien mathématique entre l’intensité physique d’un stimulus (_S_) et l’intensité perçue (_P_), selon une relation logarithmique :

- **Principe** : 
	À mesure que l’intensité d’un stimulus augmente, la perception de cette intensité croît plus lentement. Cela reflète la saturation des systèmes sensoriels.

- **Application** : 
	Mesure de seuils perceptifs (seuil absolu et différentiel). Elle s’appuie sur les travaux de Weber (_∆S/S = constant_), intégrant l’idée de seuil différentiel minimal (JND, _just noticeable difference_).

###### Formule
**1. Loi de Fechner (1860)**
$P = k \cdot \log(S)$

• **P** : Perception de l’intensité du stimulus.
• **S** : Intensité physique du stimulus.
• **k** : Constante proportionnelle.

#### 2. Loi de Stevens (1957) : La puissance

La loi de Fechner a été étendue par Stevens pour expliquer des cas où la relation logarithmique échoue. La loi de Stevens utilise une fonction puissance :

- **Paramètre** : 
	Varie selon le type de stimulus (par exemple, la lumière, le son, ou la douleur).
	- Lumière : (compression perceptive).
	- Douleur : (amplification perceptive).
	
- **Avantage** : 
	Plus flexible et précis que la loi de Fechner pour divers types de stimuli.

###### Formule
$P = k \cdot S^n$

• **P** : Perception de l’intensité.
• **S** : Intensité physique du stimulus.
• **k** : Constante de proportionnalité.
• **n** : Exposant spécifique au type de stimulus (compression ou amplification).

#### 3. Modèle probabiliste de la perception

Ce modèle postule que la perception est influencée par des processus stochastiques liés à la variabilité des systèmes sensoriels :

• La **théorie de détection du signal (TSD)** formalise la perception dans un contexte incertain, intégrant des concepts comme le bruit sensoriel et les critères décisionnels.

• Utilise des indices comme la **d-prime (****)** pour quantifier la sensibilité sensorielle :

###### Formule
**Sensibilité perceptive ($d{\prime}$) :**

$d{\prime} = \frac{\mu_{\text{signal}} - \mu_{\text{bruit}}}{\sigma}$

• $\mu_{\text{signal}}$: Moyenne des réponses au signal.
• $\mu_{\text{bruit}}$ : Moyenne des réponses au bruit.
• $\sigma$ : Écart-type commun.

#### 4. Modèles Bayésiens

Les modèles bayésiens de la perception (fin du 20ᵉ siècle) s’appuient sur la probabilité conditionnelle pour expliquer comment les individus intègrent les informations sensorielles et contextuelles :

• **Formule de Bayes** :
	• **Idée clé** : La perception est une combinaison de la probabilité a priori (attentes) et des données sensorielles.

###### Formule de Bayes :

$P(\text{État | Stimulus}) = \frac{P(\text{Stimulus | État}) \cdot P(\text{État})}{P(\text{Stimulus})}$
  

• $P(\text{État | Stimulus})$ : Probabilité de l’état donné le stimulus.
• $P(\text{Stimulus | État})$ : Probabilité d’observer le stimulus pour un état donné.
• $P(\text{État})$ : Probabilité a priori de l’état.
• $P(\text{Stimulus})$ : Probabilité totale du stimulus.

#### 5. Modèles neuraux modernes

Les approches contemporaines intègrent la dynamique neuronale pour modéliser la perception :

• **Modèle de codage prédictif** : 
	Le cerveau utilise des prédictions internes pour interpréter les stimuli et minimise les erreurs de prédiction.
	
• **Codage neuronal** : 
	Lien entre l’intensité du stimulus et les potentiels d’action (loi de fréquence de décharge).

###### Erreur de prédiction minimisée $(E)$ :

$E = \sum_{i=1}^n (x_i - \hat{x}_i)^2$

• $x_i$ : Stimulus réel observé.
• $\hat{x}_i$ : Stimulus prédit par le modèle.
• $E$ : Somme des erreurs quadratiques.

#### Synthèse des modèles

Les modèles de Fechner et Stevens ont jeté les bases de la psychophysique, tandis que les théories probabilistes et bayésiennes ont approfondi notre compréhension des mécanismes perceptifs en incorporant le bruit, l’incertitude et l’inférence cognitive. Ces modèles sont utilisés dans de nombreux domaines, tels que l’ergonomie, les interfaces homme-machine, et les neurosciences.