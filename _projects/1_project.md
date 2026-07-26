---
layout: page
title: Infrastructure VMware complète
description: Déploiement d'une infrastructure vSphere avec supervision, sécurité et sauvegarde
img: assets/img/1.jpg
importance: 1
category: infrastructure
related_publications: false
---

## Objectif du projet

Concevoir et déployer une infrastructure complète basée sur VMware vSphere (ESXi + vCenter), avec des machines virtuelles configurées, un firewall pfSense, une supervision avec Centreon et une sauvegarde automatisée via Veeam.

## Contexte

Dans le cadre de ma formation en Licence ASSR et de mon travail à l'École nationale des Greffes, j'ai conçu une infrastructure complète pour simuler un SI d'entreprise, intégrant la virtualisation, la supervision, la sécurité et la sauvegarde.

## Outils utilisés

VMware ESXi, vCenter, PowerCLI, pfSense, Centreon, Veeam Backup & Replication

## Démarche et mise en œuvre

- Déploiement de deux hôtes ESXi intégrés dans vCenter
- Utilisation de PowerCLI pour l'automatisation du déploiement des VMs
- Configuration d'un firewall pfSense avec VLANs et règles NAT
- Installation de Centreon pour la supervision (ping, services, alertes)
- Mise en place de Veeam pour sauvegarder les VMs
- Rédaction d'une documentation complète (scripts, schéma réseau, procédures)

## Résultats et livrables

- Infrastructure stable et fonctionnelle
- Script PowerCLI opérationnel
- Sauvegardes journalières automatisées
- Supervision active et centralisée
- Documentation technique détaillée

## Compétences mobilisées

- **C1** : Fournir les services liés au SI
- **C2** : Collaborer avec les acteurs (documentation, échange technique)
- **C3** : Assurer une veille sur VMware, Centreon, Veeam
- **C4** : Sécuriser le SI avec firewall, VLANs, sauvegardes

## Retour d'expérience

Ce projet m'a permis d'approfondir mes compétences techniques en virtualisation et sécurité. La configuration des VLANs sur pfSense a été un défi majeur, nécessitant des recherches avancées.

J'ai aussi gagné en rigueur documentaire, ce qui est essentiel en environnement professionnel.
