---
layout: page
title: Migration Proxmox VE 8 vers 9
description: Upgrade majeur d'un cluster Proxmox avec résolution de blocages Ceph et systemd-boot
img: assets/img/15.jpg
importance: 15
category: infrastructure
related_publications: false
---

## Contexte

Le maintien à jour d'une infrastructure de virtualisation est essentiel pour bénéficier des correctifs de sécurité et des nouvelles fonctionnalités. La migration de Proxmox VE 8 vers la version 9 sur mon homelab s'est révélée plus complexe que prévu, nécessitant la résolution de plusieurs blocages techniques successifs.

## Objectif du projet

Réaliser la montée de version complète du nœud Proxmox ThinkCentre de la version 8 vers la version 9, sans perte de données ni interruption prolongée de service.

## Outils utilisés

Proxmox VE, Ceph, systemd-boot, APT

## Démarche et mise en œuvre

- Sauvegarde préalable de la configuration et des VMs critiques avant toute intervention
- Purge complète des composants Ceph résiduels bloquant la mise à jour, malgré leur absence d'utilisation active sur ce nœud
- Résolution d'un blocage lié à systemd-boot, empêchant la finalisation de l'upgrade du bootloader
- Exécution de la migration package par package avec vérification des dépendances à chaque étape
- Tests de démarrage et de fonctionnement des VMs après upgrade
- Documentation détaillée du parcours de résolution pour référence future

## Résultats et livrables

- Nœud Proxmox migré avec succès vers la version 9 sans perte de VM
- Procédure documentée de résolution des blocages Ceph et systemd-boot, réutilisable pour de futures migrations
- Infrastructure repositionnée sur une base à jour pour la suite des projets homelab

## Compétences mobilisées

- **C1** : Fournir les services liés au SI (maintien en condition opérationnelle de l'infrastructure de virtualisation)
- **C3** : Veille technologique (recherche de solutions face à des blocages non documentés de façon exhaustive)
- **C4** : Sécurité des SI (mise à jour vers une version supportée et corrigée)

## Retour d'expérience

Ce projet illustre une réalité fréquente en administration système : une montée de version « standard » peut révéler des résidus de configuration invisibles au quotidien (ici, des composants Ceph jamais réellement utilisés mais toujours référencés). La résolution méthodique, étape par étape, en isolant chaque blocage avant de passer au suivant, s'est révélée être la seule approche fiable.

Ce type d'incident renforce l'importance de la sauvegarde systématique avant toute opération de maintenance majeure.
