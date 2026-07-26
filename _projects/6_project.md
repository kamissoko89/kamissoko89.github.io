---
layout: page
title: Déploiement Veeam Backup & Replication
description: Sauvegarde automatisée d'une infrastructure VMware et validation d'un plan de reprise après sinistre
img: assets/img/6.jpg
importance: 6
category: infrastructure
related_publications: false
---

## Objectif du projet

Installer, configurer et tester Veeam Backup & Replication pour protéger une infrastructure VMware (ESXi + vCenter) via des sauvegardes automatisées.

Ce projet avait aussi pour but de valider un scénario de reprise après sinistre (PRA).

## Contexte

Dans mon lab VMware (ESXi + vCenter), la sauvegarde des VMs était essentielle pour garantir la sécurité des données. J'ai donc choisi Veeam, outil reconnu pour sa fiabilité, sa puissance et sa facilité de restauration.

Le but était d'avoir une politique de sauvegarde claire, testée, documentée, et adaptée à une PME ou un lab réel.

## Démarche et mise en œuvre

**Outils utilisés** : Veeam Backup & Replication, ESXi, vCenter, Windows Server

**Étapes clés** :
- Installation de Veeam sur un Windows Server
- Ajout de vCenter comme source de VMs
- Création de jobs de sauvegarde :
  - choix des VMs critiques
  - fréquence (quotidienne)
  - cible de stockage (NAS)
  - durée de rétention
- Tests de restauration :
  - VMs complètes
  - fichiers individuels
  - PRA simulé
- Journalisation et supervision des jobs

## Réalisations et livrables

- Plateforme Veeam opérationnelle
- Jobs automatisés quotidiens
- Tests de restauration réussis (VM complète + fichiers)
- Documentation complète (captures, schéma, étapes)

## Compétences mobilisées

- **C1** : Fournir les services liés au SI (mise en place de sauvegarde centralisée, automatisée et intégrée à une infra existante)
- **C4** : Sécurité des SI (plan de sauvegarde solide, PRA testé, stockage isolé, gestion des risques de perte de données)

## Retour d'expérience

Projet indispensable dans tout environnement pro ou perso. J'ai pris conscience que sauvegarder ne suffit pas : il faut tester la restauration.

Le plus compliqué a été d'optimiser le stockage sans saturer le disque et de définir des plages horaires de sauvegarde efficaces.

Avec le recul, je mettrais en place une restauration automatique planifiée pour renforcer la fiabilité du système. Ce projet m'a réellement permis de comprendre la notion d'infrastructure résiliente.
