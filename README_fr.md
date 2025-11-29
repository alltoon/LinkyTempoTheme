# 🎨 Thème Linky Tempo pour Home Assistant

[![hacs_badge](https://img.shields.io/badge/HACS-Custom-41BDF5.svg)](https://github.com/hacs/integration)

Un thème léger conçu spécifiquement pour le **Tableau de bord Énergie** de Home Assistant. Il remplace les couleurs par défaut du graphique par le code couleur officiel de l'offre **EDF Tempo** (Bleu, Blanc, Rouge).

![Aperçu du Dashboard](https://github.com/alltoon/LinkyTempoTheme/raw/main/preview.png)
*(Image d'illustration - Ajoutez une capture d'écran nommée preview.png dans votre dépôt)*

## Ce que fait ce thème

Ce thème ne modifie pas l'apparence globale de votre Home Assistant (qui reste claire ou sombre selon vos préférences). Il agit uniquement sur :

1.  **La palette du Dashboard Énergie :** Les 6 premières sources d'électricité prennent les couleurs exactes de Tempo (HC/HP Bleu, Blanc, Rouge).
2.  **Le thème n'est pas magique :** Il vient completer l'intégration LinkyTempo : `https://github.com/alltoon/LinkyTempo`

## Installation

### Option 1 : Via HACS (Recommandé)

1.  Ouvrez **HACS** dans Home Assistant.
2.  Allez dans l'onglet **Interface** (Frontend).
3.  Cliquez sur le menu (3 points en haut à droite) > **Dépôts personnalisés**.
4.  Ajoutez l'URL de ce dépôt : `https://github.com/alltoon/LinkyTempoTheme`.
5.  Catégorie : **Thème**.
6.  Cliquez sur "Ajouter", cherchez "Linky Tempo Theme" dans la liste et installez-le.

### Option 2 : Manuelle

1.  Créez un fichier `linky_tempo.yaml` dans le dossier `themes/` de votre configuration Home Assistant.
2.  Copiez le contenu du fichier `themes/linky_tempo.yaml` de ce dépôt dedans.

## Activation

Pour que Home Assistant prenne en compte le thème, vous devez suivre ces deux étapes :

### 1. Déclarer le dossier de thèmes
Ouvrez votre fichier `/config/configuration.yaml` et assurez-vous que ces lignes sont présentes :

```yaml
frontend:
  themes: !include_dir_merge_named themes
```

***Note :*** Si vous venez d'ajouter cette ligne, redémarrez Home Assistant.

### 2. Sélectionner le thème

Chaque utilisateur doit activer le thème sur son profil :

- Cliquez sur votre Nom d'utilisateur (en bas à gauche de la barre latérale).

- Dans la section Thème, **sélectionnez** Linky Tempo Theme.

## Configuration du Dashboard Énergie (TRÈS IMPORTANT)

Le Dashboard Énergie attribue les couleurs dans l'ordre d'arrivée des sources (la 1ère source prend la couleur 1, la 2ème prend la couleur 2, etc.).

Pour que les couleurs correspondent aux bonnes tranches tarifaires, vous devez respecter strictement cet ordre d'ajout :

1. Allez dans Paramètres > Tableaux de bord > Énergie.

2. Dans la section "Consommation d'électricité", supprimez vos sources actuelles (icône poubelle).

Ajoutez-les à nouveau une par une dans cet ordre précis :

| Ordre | Capteur `(Sensor)` à ajouter | Couleur qui sera affichée |
|-------|------------------------------|---------------------------|
| 1     | 🔵 `..._bleu_heures_creuses`   | Bleu Foncé                |
| 2     | 🔵 `..._bleu_heures_pleines`   | Bleu Clair                |
| 3     | ⚪️ `..._blanc_heures_creuses`  | Gris / Blanc              |
| 4     | ⚪️ `..._blanc_heures_pleines`  | Gris Clair                |
| 5     | 🔴 `..._rouge_heures_creuses`  | Rouge Foncé               |
| 6     | 🔴 `..._rouge_heures_pleines`  | Rouge Clair               |

Rafraîchissez votre page `(F5)` ou `(cmd + R)`. Vos graphiques sont maintenant aux couleurs Tempo ! 🎉

## Liens

Conçu pour l'intégration : [Linky Tempo](https://github.com/alltoon/LinkyTempo) pour Home Assistant.