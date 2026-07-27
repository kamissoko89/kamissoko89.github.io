---
layout: page
title: Supervision avec Centreon
description: Déploiement d'une solution de monitoring pour surveiller disponibilité et services critiques
img: assets/img/projet7-couverture.jpg
importance: 7
category: infrastructure
related_publications: false
---

{% include figure.liquid path="assets/img/projet7-couverture.jpg" title="Supervision avec Centreon" class="img-fluid rounded z-depth-1" %}

## Contexte

La supervision réseau est un pilier essentiel du maintien en condition opérationnelle d'une infrastructure informatique. Dans le cadre de mon infrastructure virtuelle, j'ai mis en place une solution de supervision basée sur Centreon, afin de surveiller l'état des serveurs, des services critiques et de garantir une réactivité en cas de panne.

## Objectif du projet

Déployer une solution de supervision avec Centreon pour :
- Suivre en temps réel la disponibilité des équipements
- Détecter les anomalies (ping, services, ressources)
- Être alerté automatiquement en cas de panne
- Centraliser les métriques sur une interface web lisible

## Outils utilisés

Centreon, Linux (Oracle/CentOS), SNMP, SSH, VMware, pfSense

## Schéma d'architecture

{% include figure.liquid path="assets/img/projet7-schema.png" title="Schéma de supervision" class="img-fluid rounded z-depth-1" %}

## Démarche et mise en œuvre

- Installation de Centreon sur une VM Linux dédiée
- Configuration réseau et accès à l'interface Web d'administration
- Ajout des hôtes (VMs, routeur, pare-feu pfSense)
- Paramétrage des services à surveiller (ping, HTTP, espace disque, CPU…)
- Intégration avec l'infrastructure VMware via les plugins disponibles
- Mise en place d'alertes par e-mail et tableau de bord

## Réalisations et livrables

- Solution Centreon opérationnelle
- Supervision active d'une dizaine de machines et services
- Alertes en cas de perte de connexion ou surcharge
- Tableau de bord centralisé
- Documentation d'installation + captures des interfaces
- Captures des états (OK / Warning / Critical)

## Résultats & Captures

**Dashboard principal**

{% include figure.liquid path="assets/img/projet7-dashboard.png" title="Dashboard Centreon" class="img-fluid rounded z-depth-1" %}

**Vue globale des hôtes supervisés**

{% include figure.liquid path="assets/img/projet7-allcentreon.png" title="Vue globale Centreon" class="img-fluid rounded z-depth-1" %}

**Disponibilité des services**

{% include figure.liquid path="assets/img/projet7-dispo.jpg" title="Disponibilité des services" class="img-fluid rounded z-depth-1" %}

## Compétences mobilisées

- **C1** : Fournir les services liés au SI (mise en place d'un outil essentiel au fonctionnement du SI)
- **C3** : Veille technologique (recherche de templates, plugins, résolution d'erreurs Linux)
- **C4** : Sécurité des SI (surveillance des anomalies CPU anormal, ports ouverts, anticipation des pannes)

## Retour d'expérience

Ce projet m'a permis de découvrir l'environnement professionnel de supervision avec Centreon. J'ai appris à organiser la surveillance de façon claire, à configurer des seuils critiques adaptés, et à anticiper les problèmes.

Les principales difficultés ont été liées aux dépendances système lors de l'installation et à la configuration SNMP sur certains équipements.

Je prévois d'explorer Zabbix ou Grafana pour comparer les approches visuelles et les intégrations. La supervision est un élément indispensable dans toute infrastructure sérieuse.
