---
layout: page
title: Script PowerShell - Arrêt sécurisé infra VMware
description: Automatisation PowerCLI de l'arrêt ordonné des VMs et hôtes ESXi pour scénario de PRA
img: assets/img/projet9-couverture.png
importance: 9
category: automatisation
related_publications: false
---

{% include figure.liquid path="assets/img/projet9-couverture.png" title="Script PowerShell - Arrêt sécurisé infra VMware" class="img-fluid rounded z-depth-1" %}

## Objectif du projet

Mettre en place un script PowerShell avec PowerCLI afin d'automatiser l'arrêt sécurisé des machines virtuelles et des hôtes ESXi, dans un ordre défini, en cas de coupure planifiée ou de test de PRA.

## Contexte

Dans une infrastructure virtualisée, un arrêt brutal (coupure de courant, crash système) peut entraîner des pertes de données ou une corruption des VMs.

Ce projet visait à simuler un plan de reprise d'activité (PRA) dans mon lab VMware, en automatisant l'arrêt propre des machines virtuelles, suivi de l'extinction des hôtes ESXi.

## Outils utilisés

PowerShell, PowerCLI, VMware vCenter, Windows Server (poste d'administration)

## Schéma d'architecture

{% include figure.liquid path="assets/img/projet9-schema.png" title="Schéma de l'infrastructure" class="img-fluid rounded z-depth-1" %}

## Démarche et mise en œuvre

- Installation de PowerCLI sur un poste Windows avec PowerShell
- Connexion au vCenter via PowerCLI `Connect-VIServer`
- Création d'un fichier de configuration listant les VMs dans l'ordre de priorité
- Développement du script :
  - Vérification de l'état des VMs
  - Arrêt progressif avec `Stop-VM`
  - Journalisation des résultats
- Extinction des hôtes ESXi avec `Stop-VMHost` une fois les VMs arrêtées
- Ajout de logs ou notifications en fin d'exécution
- Tests fonctionnels en environnement réel (lab local)

## Résultats et livrables

- Script PowerShell opérationnel pour l'arrêt sécurisé de l'infra
- Fichier de configuration externe (JSON/TXT)
- Captures d'exécution du script (PowerShell ISE)
- Documentation des commandes utilisées et gestion des erreurs

## Résultats & Captures

**Résultats de l'exécution du script**

{% include figure.liquid path="assets/img/projet9-resultats.png" title="Résultats du script PowerShell" class="img-fluid rounded z-depth-1" %}

## Compétences mobilisées

- **C1** : Fournir les services liés au SI
- **C2** : Collaborer avec les acteurs IT (documentation claire)
- **C4** : Sécuriser le SI (plan de reprise, automatisation d'arrêt d'urgence)

## Retour d'expérience

Ce projet m'a permis de développer mes compétences PowerShell et PowerCLI, tout en me sensibilisant aux bonnes pratiques d'un PRA.

J'ai appris à structurer un script critique, gérer les erreurs, et documenter chaque étape.

Une meilleure anticipation des coupures permet de sécuriser l'infrastructure et d'éviter les interventions manuelles risquées.
