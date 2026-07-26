---
layout: page
title: Contrôleur de Domaine Active Directory
description: Déploiement AD DS, GPO et centralisation de la gestion des utilisateurs sous Windows Server
img: assets/img/8.jpg
importance: 8
category: infrastructure
related_publications: false
---

## Contexte

Dans le cadre de ma formation, j'ai souhaité mettre en œuvre une infrastructure Windows Server avec un contrôleur de domaine Active Directory (AD DS). L'objectif était de centraliser la gestion des utilisateurs et des ressources, comme dans un environnement d'entreprise.

Ce projet s'inscrit dans une logique de simulation d'infrastructure réelle, avec des clients intégrés au domaine, des règles GPO, et une gestion centralisée de l'authentification.

## Objectif du projet

Déployer un serveur Active Directory sous Windows Server, intégrer des postes clients, configurer les services DNS/DHCP liés, et appliquer des GPOs (Group Policies) pour contrôler les postes à distance.

## Démarche et mise en œuvre

**Outils utilisés** : Windows Server 2022, Windows 10, AD DS, DNS, DHCP, GPO, VMware Workstation

**Étapes clés** :
- Installation de Windows Server 2022 sur une VM dédiée
- Ajout du rôle AD DS (Active Directory Domain Services)
- Promotion du serveur en tant que contrôleur de domaine
- Configuration du DNS pour la résolution des noms internes
- Création d'unités organisationnelles (OU) : utilisateurs, ordinateurs, services
- Intégration de clients Windows 10 au domaine
- Mise en place de GPO (ex : blocage du panneau de configuration, mot de passe fort)
- Installation du rôle DHCP pour attribuer dynamiquement des IP aux clients
- Création de scripts de connexion automatique (scripts de logon)

## Réalisations et livrables

- Domaine fonctionnel et clients intégrés
- GPO appliquées selon les profils
- Tests de connexion, sécurité, et accès
- Captures d'écran de l'environnement
- Documentation de l'installation et de la configuration

## Compétences mobilisées

- **C1** : Fournir les services liés au SI (configuration d'un domaine, intégration d'utilisateurs et clients, déploiement d'outils systèmes)
- **C4** : Sécurité des SI (application de règles de sécurité via GPO, contrôle d'accès, renforcement du SI via politiques d'annuaire)

## Retour d'expérience

Ce projet m'a permis de maîtriser l'administration d'un annuaire Active Directory et d'en comprendre les enjeux : sécurité, organisation, et gestion centralisée.

Les GPOs sont très puissantes mais nécessitent une bonne planification pour éviter les erreurs. J'ai appris à résoudre les problèmes de réplication DNS et d'intégration client.

Si c'était à refaire, je testerais également RSAT et la gestion multi-sites avec plusieurs DC.
