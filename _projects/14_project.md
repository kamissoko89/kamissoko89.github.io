---
layout: page
title: Infrastructure DNS et PKI Homelab
description: DNS split-horizon, certificats automatisés et distribution PKI sur infrastructure personnelle
img: assets/img/14.jpg
importance: 14
category: infrastructure
related_publications: false
---

## Contexte

La gestion manuelle des certificats et de la résolution DNS sur un homelab multi-services (Proxmox, ESXi, NAS, applications web internes) devient rapidement ingérable sans une infrastructure dédiée. J'ai donc conçu une architecture DNS et PKI complète et automatisée.

## Objectif du projet

Mettre en place une résolution DNS interne cohérente avec accès externe maîtrisé, ainsi qu'une gestion automatisée des certificats HTTPS pour l'ensemble des services du homelab.

## Outils utilisés

Unbound (résolveur récursif), AdGuard Home (réécritures DNS, filtrage), acme.sh, Cloudflare (DNS et API), Nginx Proxy Manager (Docker)

## Démarche et mise en œuvre

- Déploiement d'Unbound comme résolveur récursif sur une LXC AdGuard, pour une résolution DNS indépendante des fournisseurs tiers
- Configuration d'AdGuard Home pour les réécritures DNS internes, permettant un accès par nom de domaine cohérent sur tout le réseau
- Mise en place d'acme.sh avec challenge DNS-01 via l'API Cloudflare pour la génération automatisée de certificats wildcard ECC pour le domaine personnel
- Génération d'un certificat RSA dédié pour ESXi, la génération complète (fullchain) provoquant des instabilités sur ce système (`hostd`)
- Développement d'un script de déploiement automatique des certificats vers Proxmox, PBS et ESXi
- Déploiement de Nginx Proxy Manager en conteneur Docker, avec création programmatique des hôtes proxy via API

## Résultats et livrables

- Résolution DNS split-horizon fonctionnelle : accès interne direct, accès externe maîtrisé via proxy
- Renouvellement automatique des certificats sans exposition de service, éliminant toute dépendance à un challenge HTTP public
- Script de distribution de certificats réutilisable pour l'ensemble de l'infrastructure

## Compétences mobilisées

- **C1** : Fournir les services liés au SI (conception d'une architecture DNS/PKI cohérente)
- **C3** : Veille technologique (choix des outils, compréhension des enjeux PKI)
- **C4** : Sécurité des SI (chiffrement systématique, automatisation réduisant les erreurs manuelles)

## Retour d'expérience

Ce projet illustre bien la différence entre une solution qui fonctionne « une fois » et une infrastructure réellement maintenable dans le temps. La découverte de la limitation spécifique d'ESXi avec les certificats fullchain a été un cas d'école sur l'importance de tester chaque composant individuellement avant de généraliser une solution.

L'architecture split-horizon reste un point d'attention permanent : toute modification de topologie réseau doit être répercutée de manière cohérente entre le DNS interne et la configuration du proxy externe.
