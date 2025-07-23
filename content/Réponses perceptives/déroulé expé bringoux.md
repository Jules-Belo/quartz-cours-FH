
# Protocole Global de Mesure de l’Audition avec Exposition Sonore et Évaluation Audiométrique

[fondation pour l'audition](https://www.fondationpourlaudition.org/plus-dun-milliard-de-jeunes-risque-pour-leur-audition-1089?utm_source=chatgpt.com)

## Objectif
Ce protocole vise à évaluer les seuils auditifs et les réponses auditives des participants en utilisant des tests audiométriques à l'aide d'outils standardisés. L'objectif est de mesurer les capacités auditives dans un environnement contrôlé et de comparer les résultats entre différents groupes de participants. La population d'étude concerne les étudiants, nous évaluerons leur perception des risques ainsi qu'une potentielle diminution de la qualité de leur audition suite à des inductions de musiques de différents genres.

## 1. Méthode

### Matériel

#### Audiomètre 
##### Mesures Audiométriques
- **Fréquences de test** : 250-8000 Hz (ISO 8253-1:2010)
- **Ordre des fréquences** : 1000 → 2000 → 3000 → 4000 → 8000 → 500 → 250 Hz (BSA, 2018)
##### Configuration du Test
- **Calibration selon ISO 389-1 (2017)** : Norme établissant les exigences pour la calibration des équipements audiométriques afin d’assurer des mesures précises des seuils auditifs.

#### Induction de bruit

##### Téléphone et casque audio
- Volume sonore maximum à 85 dB
	- Variation entre 60dB et 85dB
- Casque audio : [Marshall Major IV](https://www.marshall.com/fr/fr/product/major-iv?pid=1005773&srsltid=AfmBOoo4QmdPY6b_44XGxkUcSLbPVWC6UjQJd72QstOCvAEjR-5sCqdl)

##### Musiques sélectionner
- Conditions forte et désagréables (grande variabilité de fréq) : 
	- Feeling Alive (Panda Dub)
	- Disaster (KSLV Noh)
	- Psychotic Symphony (Panda Dub)
	- 141 Schneescheiber (TAKTSÖRER)

- Condition calme et agréable (peu de variabilité de fréq) : 
	- Bicycle Riders (Edgar Rothermich)
	- Rain God (Hermanos Gutiérrez)
	- Song of the beach (Arcade Fire)
	- Lily's Dance (Million Eyes)
	- Mesa Redonda (Hermanos Gutiérrez)
## 2. Population
- **Cible** : Étudiants âgés de 18 à 25 ans (Niskar et al., 2001) en bonne santé.
- **Critères d’exclusion** :
  - Troubles auditifs préexistants
  - Exposition récente à des niveaux sonores élevés (Serra et al., 2014)

## 3. Déroulement du Test (120 minutes)

### Phase 1 : Accueil et Consentement (15 min)
- Accueil des participants et obtention du consentement éclairé.
- Questionnaire sur la perception des risques et les comportements individuels.

### Phase 2 : Exposition Sonore (30 min)
- Exposition sonore continue à 85 dB (Keppler et al., 2015).
- Musique choisie (non standardisée) pour analyser les fréquences dominantes à un niveau compris entre 65 et 85dB.

#### Objectif de la phase
Évaluer le seuil auditif de chaque participant pour différentes fréquences avant l’exposition sonore.

#### Étapes de la procédure
###### 1. Préparation du matériel
   - Vérification de la calibration de l’audiomètre selon la norme ISO 389-1 (2017).
   - Vérification de l’état et du confort des casques.
   - S’assurer que le niveau de bruit de fond est inférieur à 35 dB (ISO 8253-1:2010).

###### 2. Tests individuels pour chaque oreille
   - Les tests sont effectués séparément pour chaque oreille sous 3 conditions différentes :
     - **Condition 2** : Exposition à un bruit calme agréable (35 dB).
     - **Condition 3** : Exposition à un bruit fort désagréable (85 dB).

###### 3. Procédure de mesure
   - Commencer par la fréquence de 1000 Hz, puis chaque fréquence suivante sera testée selon un ordre spécifique.
   - **Fréquence initiale de 1000 Hz** : Tester sous différentes intensités (de 40 dB à 10 dB).
   - **Fréquences suivantes** :  2000 Hz → 3000 Hz → 4000 Hz → 8000 Hz → 6000 Hz → 500 Hz → 250 Hz.
   - **Délais entre les stimulations** : 2-5 secondes
   - **validation et information ==(à vérifier)==** : un des expérimentateur sera placé face à la personne réalisant l'audiogramme en essayant de ne pas déranger sa concentration. Le participant a les deux poignets posé sur la table avec l'index tendu et il indiquera s'il a entendu une réponse en levant l'index du côté de la stimulation (D/G). Lorsqu'il ne répond pas alors qu'une stim a eu lieu, on peut considérer qu'il n'a pas entendu.

### Phase 3 : Pause Silencieuse (15 min)
- Temps de repos sans exposition sonore (environnement calme).

### Phase 4 : Audiométrie Post-Exposition (30 min)
- Répétition de la procédure de la phase 2 après l’exposition sonore pour comparer les seuils d’audition avant et après l’exposition.

## 4. Analyse des Données

### Méthode de Collecte des Résultats
| Participant | Oreille | Fréquence (Hz) | Condition   | Seuil Initial (dB) | Seuil Final (dB) |
| ----------- | ------- | -------------- | ----------- | ------------------ | ---------------- |
| 1           | Droite  | 1000           | Condition 1 | 40                 | 10               |
| ...         | ...     | ...            | ...         | ...                | ...              |
analyse stats sur R



---
## Sources

- **ISO 8253-1:2010** : *Acoustics – Audiometric test methods – Part 1: Basic pure tone air and bone conduction threshold audiometry*.
- **ISO 389-1:2017** : *Acoustics – Reference levels for the calibration of audiometric equipment – Part 1: Reference threshold of hearing under free-field and diffuse-field listening conditions*.
- **Niskar et al., 2001** : Niskar, A. S., Kieszak, S. M., Holmes, A., Esteban, E., & Rubin, C. (2001). *Prevalence of hearing loss among children 6 to 19 years of age: United States, 1999–2004*. The Journal of the American Medical Association, 291(5), 667–672.
- **Serra et al., 2014** : Serra, P. L., Doolan, M., & Richards, R. (2014). *Noise exposure and hearing loss in young adults*. International Journal of Audiology, 53(12), 837–846.
- **Keppler et al., 2015** : Keppler, H., Steenwijk, M. M., & De Boer, J. (2015). *The impact of noise exposure on hearing thresholds in young adults: A longitudinal study*. Occupational Medicine, 65(4), 314–318.
- **British Society of Audiology, 2018** : British Society of Audiology. (2018). *Guidelines for pure-tone audiometry*. https://www.thebsa.org.uk/