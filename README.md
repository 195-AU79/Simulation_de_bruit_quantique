# Simulation Quantique - BMV V3.1

## Description

Ce projet implémente une simulation de bruit quantique pour le projet BMV (Bragg Mirror Vibration). La simulation calcule le bruit d'accélération résiduel d'un système de mesure ultra-sensible, en tenant compte du bruit de sol, de l'atténuation mécanique et du bruit thermique (Langevin).

## Objectif

Valider qu'une masse inertielle de **250 mg** à une température de **10 mK** permet d'atteindre un seuil de bruit inférieur à **1×10⁻¹⁵ m/s²/√Hz** dans la bande de mesure de 20 Hz à 500 Hz.

## Caractéristiques

- **Masse** : 250 mg (0.25 gramme)
- **Température** : 10 mK
- **Fréquence d'échantillonnage** : 10 kHz
- **Durée de simulation** : 10 secondes
- **Seuil cible** : 1×10⁻¹⁵ m/s²/√Hz
- **Bande de mesure** : 20 Hz - 500 Hz

## Modèle Physique

La simulation prend en compte trois sources de bruit principales :

1. **Bruit de sol** : Bruit blanc filtré par un filtre passe-bas de 0.1 Hz
2. **Atténuation mécanique** : Simulation d'un étage pendulaire + métamatériau avec une atténuation effective de -180 dB
3. **Bruit thermique (Langevin)** : Agitation thermique calculée selon la formule de fluctuation-dissipation

Le système utilise un piège optique mou à 0.2 Hz avec un facteur de qualité Q = 10¹⁰ (vide extrême).

## Installation

### Prérequis

- Python 3.7 ou supérieur
- pip (gestionnaire de paquets Python)

### Dépendances

Installez les dépendances nécessaires :

```bash
pip install -r requirements.txt
```

Les bibliothèques requises sont :
- `numpy` : Calculs numériques
- `scipy` : Traitement du signal et filtres
- `matplotlib` : Visualisation des résultats

## Utilisation

Exécutez simplement le script principal :

```bash
python main.py
```

Le script va :
1. Générer le signal de bruit total
2. Calculer le spectre de densité de puissance (PSD)
3. Afficher les résultats dans la console
4. Générer un graphique sauvegardé sous `bmv_v3_1_success.png`

## Résultats

Le script affiche :
- Le bruit mesuré dans la bande 20 Hz - 500 Hz
- Le seuil cible
- Le verdict de validation ([SUCCESS] ou [FAILURE])

Un graphique log-log est généré montrant :
- Le spectre de bruit total
- La ligne de seuil à 1×10⁻¹⁵ m/s²/√Hz
- La zone de détection possible

## Structure du Code

```
main.py
├── Paramètres physiques (masse, température, seuil)
├── Fonction run_simulation()
│   ├── Génération du bruit de sol
│   ├── Atténuation mécanique
│   └── Calcul du bruit thermique (Langevin)
├── Analyse spectrale (Welch)
└── Visualisation et verdict
```

## Validation

Le code utilise une graine aléatoire fixe (`np.random.seed(42)`) pour garantir la reproductibilité des résultats.

**Résultat attendu** : [SUCCESS] - L'inertie de 250mg suffit à écraser le bruit thermique et atteindre le seuil requis.

## Fichiers Générés

- `bmv_v3_1_success.png` : Graphique du spectre de bruit avec le seuil de détection

## Version

**V3.1** - Validation finale
- Label "Seuil Graviton" remplacé par "Seuil"
- Validation de l'inertie de 250mg pour atteindre < 1e-15

## Auteur

Projet BMV - Simulation Quantique


