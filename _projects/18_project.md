---
layout: page
title: Migration Windows Server 2022 vers 2025
description: Upgrade in-place d'un contrôleur de domaine avec résolution ADPREP et corruption WMI
img: assets/img/18.jpg
importance: 18
category: infrastructure
related_publications: false
---

## Contexte

Le maintien à jour des contrôleurs de domaine est essentiel pour la sécurité et la compatibilité de l'infrastructure Active Directory. La migration in-place d'un serveur Windows Server 2022 vers 2025 s'est révélée technique, nécessitant la résolution de plusieurs incidents en cascade.

## Objectif du projet

Réaliser la montée de version in-place d'un contrôleur de domaine de Windows Server 2022 vers 2025, en préservant l'intégrité de l'annuaire Active Directory.

## Outils utilisés

Windows Server 2022/2025, Active Directory, ADPREP, WMI, gestion des pilotes d'impression

## Démarche et mise en œuvre

- Sauvegarde complète du contrôleur de domaine avant intervention
- Libération d'espace disque, contrainte bloquante initiale pour le lancement du programme d'installation
- Exécution des commandes ADPREP (préparation forêt et domaine) pour étendre le schéma Active Directory à la version 2025
- Diagnostic et réparation d'une corruption du dépôt WMI, empêchant le bon fonctionnement de certains services après upgrade
- Résolution de blocages liés à des pilotes d'impression obsolètes incompatibles avec la nouvelle version
- Vérification complète du bon fonctionnement d'Active Directory après migration (réplication, authentification, GPO)

## Résultats et livrables

- Contrôleur de domaine migré avec succès vers Windows Server 2025
- Schéma Active Directory étendu et fonctionnel
- Documentation des incidents rencontrés et de leur résolution, réutilisable pour de futures migrations

## Compétences mobilisées

- **C1** : Fournir les services liés au SI (maintien en condition opérationnelle du service d'annuaire)
- **C3** : Veille technologique (diagnostic de la corruption WMI, recherche de solutions spécifiques)
- **C4** : Sécurité des SI (mise à jour vers une version supportée, intégrité de l'annuaire préservée)

## Retour d'expérience

Cette migration a mis en évidence la nécessité d'anticiper plusieurs types de blocages lors d'un upgrade in-place d'un contrôleur de domaine : espace disque, compatibilité des pilotes, et intégrité des composants système comme WMI.

La réparation du dépôt WMI en particulier a nécessité une approche méthodique de diagnostic, isolant le composant fautif avant d'appliquer une correction plutôt que de repartir sur une réinstallation complète.
