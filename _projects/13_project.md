---
layout: page
title: Déploiement d'un SOC Open Source
description: Centre opérationnel de sécurité personnel avec Wazuh, Suricata, OpenCTI, TheHive et Shuffle
img: assets/img/13.jpg
importance: 13
category: securite
related_publications: false
---

## Contexte

Dans une démarche de montée en compétences en cybersécurité, en lien direct avec mon Master Cybersécurité au CNAM Bretagne, j'ai entrepris de déployer un SOC (Security Operations Center) complet sur mon infrastructure personnelle, afin de comprendre de bout en bout la chaîne de détection, d'analyse et de réponse aux incidents.

## Objectif du projet

Construire un environnement de supervision de sécurité intégrant détection d'intrusion, gestion des informations et événements de sécurité (SIEM), threat intelligence et orchestration de la réponse à incident (SOAR).

## Outils utilisés

Wazuh (SIEM/EDR), Suricata (IDS/IPS, ~49 000 signatures actives), OpenCTI (threat intelligence, intégration MISP), TheHive (gestion des incidents), Shuffle (SOAR), Proxmox VE

## Démarche et mise en œuvre

- Déploiement de Suricata sur la VM Sentinelle pour l'inspection du trafic réseau en profondeur
- Installation et configuration de Wazuh pour la collecte et la corrélation des logs (agents déployés sur plusieurs VMs)
- Mise en place d'OpenCTI avec intégration MISP pour enrichir les alertes avec de la threat intelligence
- Déploiement de TheHive pour la création et le suivi structuré des cas d'incident
- Configuration de Shuffle pour orchestrer automatiquement des workflows de réponse (enrichissement, notification, escalade)
- Interconnexion des différents outils via API pour créer une chaîne de traitement cohérente, de la détection jusqu'à la réponse

## Résultats et livrables

- SOC fonctionnel avec détection réseau, corrélation de logs et gestion structurée des incidents
- Workflows d'orchestration automatisés pour accélérer le traitement des alertes
- Environnement d'entraînement continu pour l'analyse de sécurité, directement réutilisable dans le cadre académique et professionnel

## Compétences mobilisées

- **C3** : Veille technologique (suivi des évolutions de l'écosystème SOC open source)
- **C4** : Sécurité des SI (détection, analyse et réponse aux incidents de sécurité)

## Retour d'expérience

Ce projet, encore en évolution, m'a permis de comprendre concrètement l'articulation entre les différentes briques d'un SOC moderne — un SIEM seul ne suffit pas sans threat intelligence ni capacité d'orchestration de la réponse.

L'intégration entre outils hétérogènes (formats de logs, API, référentiels de données différents) a été l'un des principaux défis techniques, formateur pour la suite de mon parcours en cybersécurité.
