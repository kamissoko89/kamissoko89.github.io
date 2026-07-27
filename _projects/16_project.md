---
layout: page
title: Récupération après PSOD ESXi
description: Diagnostic et résolution d'un écran violet de la mort avec récupération complète de 26 VMs
img: assets/img/16.jpg
importance: 5
category: infrastructure
related_publications: false
---

**Technologies :** `VMware ESXi` `TPM` `Secure Boot` `bash`
**Niveau :** 🔴 Avancé

## Contexte

Un hôte ESXi de mon infrastructure personnelle a subi un PSOD (Purple Screen of Death), l'équivalent VMware d'un écran bleu critique, provoqué par une incohérence entre le module TPM et la configuration Secure Boot. Cet incident a rendu l'hôte et l'ensemble de ses 26 machines virtuelles inaccessibles.

## Objectif du projet

Diagnostiquer précisément la cause du PSOD, restaurer un hôte ESXi fonctionnel, et récupérer l'intégralité des 26 machines virtuelles sans perte de données.

## Outils utilisés

VMware ESXi, TPM, Secure Boot, bash, vim-cmd

## Démarche et mise en œuvre

- Analyse du message d'erreur PSOD pour identifier la cause racine : conflit entre l'état du module TPM et la configuration Secure Boot au démarrage
- Effacement (clear) du module TPM pour repartir sur un état matériel cohérent
- Réinstallation propre d'ESXi sur l'hôte affecté
- Reconnexion du stockage contenant les VMs existantes, celles-ci n'ayant pas été supprimées mais simplement rendues invisibles par la réinstallation
- Écriture d'un script combinant bash et `vim-cmd` pour ré-enregistrer automatiquement l'ensemble des 26 VMs dans l'inventaire ESXi, évitant un ré-enregistrement manuel un par un
- Vérification du bon démarrage de chaque VM et de l'intégrité de leurs données

## Résultats et livrables

- Hôte ESXi restauré et stable
- Intégralité des 26 VMs récupérées sans perte de données
- Script de ré-enregistrement automatisé des VMs, réutilisable en cas d'incident similaire

## Compétences mobilisées

- **C1** : Fournir les services liés au SI (restauration d'un service de virtualisation critique)
- **C3** : Veille technologique (diagnostic d'une erreur peu documentée)
- **C4** : Sécurité des SI (compréhension des mécanismes TPM/Secure Boot, gestion de crise)

## Retour d'expérience

Cet incident a été l'occasion de découvrir en profondeur l'interaction entre le TPM matériel et Secure Boot au niveau de l'hyperviseur, un sujet rarement rencontré en dehors d'un contexte de panne réelle.

Automatiser le ré-enregistrement des 26 VMs via script plutôt que de le faire manuellement a permis de réduire drastiquement le temps de restauration et les risques d'erreur humaine — un réflexe d'automatisation qui s'applique aussi bien en contexte homelab qu'en environnement de production.
