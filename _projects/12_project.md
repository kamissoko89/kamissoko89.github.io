---
layout: page
title: Outil d'Onboarding Automatisé
description: Génération automatique de fiches d'accueil PDF à partir d'Excel via VBA et Python
img: assets/img/12.jpg
importance: 12
category: automatisation
related_publications: false
---

## Contexte

À l'École Nationale des Greffes, l'arrivée de nouveaux agents nécessitait la création manuelle et répétitive de fiches d'accueil (identifiants, équipements, procédures). Ce processus chronophage était source d'erreurs et manquait de traçabilité.

## Objectif du projet

Développer un outil permettant de générer automatiquement une fiche d'accueil PDF personnalisée pour chaque nouvel agent, à partir d'un simple bouton dans un fichier Excel.

## Outils utilisés

Excel, VBA, Python (openpyxl, reportlab)

## Démarche et mise en œuvre

- Conception d'un fichier Excel de saisie centralisant les informations du nouvel agent (nom, service, matériel attribué, comptes à créer)
- Développement d'une macro VBA déclenchée par un bouton, appelant un script Python en arrière-plan
- Écriture du script Python avec `openpyxl` pour lire les données Excel
- Génération de la fiche d'accueil au format PDF avec `reportlab`, incluant mise en page et éléments graphiques
- Résolution des problèmes de configuration : gestion du PATH système pour l'appel Python depuis VBA, dépendances des modules
- Tests sur plusieurs postes pour garantir la portabilité de l'outil

## Résultats et livrables

- Outil opérationnel réduisant le temps de création d'une fiche d'accueil de plusieurs dizaines de minutes à quelques secondes
- Réduction des erreurs de saisie grâce à la centralisation des données
- Documentation d'installation et d'utilisation pour les autres membres de l'équipe

## Compétences mobilisées

- **C1** : Fournir les services liés au SI (automatisation d'un processus métier)
- **C2** : Collaborer avec les acteurs (outil destiné à être utilisé par toute l'équipe support)
- **C3** : Veille technologique (choix des bibliothèques Python adaptées à la génération de documents)

## Retour d'expérience

Ce projet m'a permis de développer une solution pont entre un outil bureautique classique (Excel/VBA) et un langage de script plus puissant (Python), une approche pragmatique pour moderniser un processus existant sans bouleverser les habitudes des utilisateurs.

La principale difficulté a été la gestion des chemins et dépendances entre VBA et l'environnement Python, nécessitant une bonne compréhension du fonctionnement du PATH système Windows.
