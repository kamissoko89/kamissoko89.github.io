---
layout: page
title: Segmentation Réseau OpenWrt avec VLANs
description: Cloisonnement du homelab en zones isolées avec routage inter-VLAN et durcissement nftables
img: assets/img/19.jpg
importance: 19
category: reseau
related_publications: false
---

## Contexte

Un homelab hébergeant des services variés (infrastructure de virtualisation, SOC, services exposés, appareils IoT) nécessite un cloisonnement réseau rigoureux pour limiter la surface d'attaque en cas de compromission d'un segment. J'ai donc mis en place une segmentation VLAN complète sur mon routeur OpenWrt.

## Objectif du projet

Cloisonner le réseau homelab en plusieurs zones isolées selon leur niveau de confiance et leur fonction, avec un routage inter-VLAN contrôlé et un pare-feu durci.

## Outils utilisés

OpenWrt, VLANs (802.1Q), NAT masquerade, nftables, Fail2ban

## Démarche et mise en œuvre

- Définition de quatre VLANs distincts selon la fonction et le niveau de confiance : infrastructure de virtualisation, services exposés, appareils IoT/invités, administration
- Configuration des interfaces taguées VLAN sur le switch et le routeur OpenWrt
- Mise en place du routage inter-VLAN avec règles NAT masquerade pour l'accès Internet contrôlé depuis chaque zone
- Écriture de règles nftables strictes pour n'autoriser que les flux inter-VLAN explicitement nécessaires (par exemple, accès administration vers infrastructure, mais pas l'inverse)
- Déploiement de Fail2ban sur les services exposés pour bannir automatiquement les tentatives d'intrusion répétées
- Tests de cloisonnement : vérification qu'un appareil d'un VLAN ne peut pas atteindre les ressources d'un autre VLAN sans règle explicite

## Résultats et livrables

- Réseau homelab segmenté en quatre zones étanches avec règles de communication explicites
- Pare-feu nftables durci limitant fortement la surface d'attaque en cas de compromission d'un segment
- Documentation de la matrice de flux autorisés entre VLANs

## Compétences mobilisées

- **C1** : Fournir les services liés au SI (conception d'une architecture réseau adaptée aux besoins)
- **C3** : Veille technologique (bonnes pratiques de segmentation réseau)
- **C4** : Sécurité des SI (cloisonnement, réduction de la surface d'attaque, durcissement pare-feu)

## Retour d'expérience

Ce projet illustre un principe fondamental de sécurité réseau : la segmentation par zones de confiance limite drastiquement l'impact d'une compromission, un serveur exposé compromis ne pouvant pas directement atteindre l'infrastructure de virtualisation ou les outils d'administration.

La rédaction des règles nftables en mode « default deny » (tout bloquer sauf ce qui est explicitement autorisé) a demandé une cartographie précise des flux réellement nécessaires entre chaque zone, plutôt que de partir sur des règles permissives par défaut.
