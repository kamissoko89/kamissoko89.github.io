---
layout: page
title: VPN WireGuard sur serveur Debian
description: Tunnel VPN chiffré pour accès distant sécurisé à une infrastructure personnelle
img: assets/img/projet10-couverture.jpg
importance: 10
category: reseau
related_publications: false
---

{% include figure.liquid path="assets/img/projet10-couverture.jpg" title="VPN WireGuard sur serveur Debian" class="img-fluid rounded z-depth-1" %}

## Objectif du projet

Déployer un VPN léger, rapide et sécurisé basé sur WireGuard pour établir une connexion chiffrée à distance vers mon infrastructure personnelle hébergée localement.

## Contexte

Dans un souci d'accès sécurisé à distance à mes machines (serveurs, pfSense, NAS) depuis l'extérieur, j'ai décidé de mettre en place un tunnel VPN basé sur WireGuard, réputé pour sa simplicité, ses performances et son chiffrement moderne.

L'objectif était d'interconnecter un VPS Debian (accessible 24/7 sur Internet) à mon réseau personnel via WireGuard, et de permettre l'accès depuis plusieurs postes clients (PC, mobile…).

## Outils utilisés

WireGuard (paquet wireguard sur Debian), VPS Debian 12 (chez LWS), postes clients (Linux, Windows, Android), pfSense (réseau local), UFW (règles pare-feu)

## Schéma d'architecture

{% include figure.liquid path="assets/img/projet10-schema.png" title="Schéma de l'infrastructure VPN" class="img-fluid rounded z-depth-1" %}

## Démarche et mise en œuvre

- Installation de WireGuard sur le VPS (`apt install wireguard`)
- Génération des clés (privées/publiques) pour le serveur et chaque client
- Configuration du fichier `wg0.conf` sur le serveur :
  - Interface VPN avec IP locale dédiée
  - Port d'écoute UDP personnalisé
  - Ajout de la clé publique du client
- Ouverture du port 51820/UDP dans UFW
- Configuration des clients (PC et téléphone) :
  - Appairage avec les clés
  - Attribution d'une IP VPN unique par client
- Tests de connectivité : ping entre le client et le VPS, redirection vers le réseau interne
- Démarrage automatique de WireGuard au boot du serveur

## Résultats et livrables

- Tunnel VPN actif et chiffré (testé avec ping, curl ifconfig.me, wg show)
- Plusieurs clients configurés (PC, smartphone Android)
- Script d'ajout automatique de nouveaux pairs (génération clé + conf)
- Documentation complète : wg0.conf, captures WireGuard client, schéma de tunnel, pare-feu
- Procédure d'installation et d'ajout d'un utilisateur

## Résultats & Captures

**Configuration du serveur WireGuard**

{% include figure.liquid path="assets/img/projet10-config.png" title="Configuration serveur WireGuard" class="img-fluid rounded z-depth-1" %}

**État du tunnel (handshake)**

{% include figure.liquid path="assets/img/projet10-tunnel.png" title="État du tunnel" class="img-fluid rounded z-depth-1" %}

**Configuration du pare-feu**

{% include figure.liquid path="assets/img/projet10-parefeu.png" title="Ouverture du port UDP et forwarding" class="img-fluid rounded z-depth-1" %}

**Gestion des clients**

{% include figure.liquid path="assets/img/projet10-clients.png" title="Gestion des clients" class="img-fluid rounded z-depth-1" %}
{% include figure.liquid path="assets/img/projet10-qr.png" title="QR code de configuration client" class="img-fluid rounded z-depth-1" %}

## Compétences mobilisées

- **C1** : Fournir les services liés au SI (déploiement et configuration d'un tunnel VPN pour la connexion distante sécurisée)
- **C4** : Sécurité des SI (chiffrement des connexions, gestion de clés privées/publiques, filtrage des ports)

## Retour d'expérience

Ce projet m'a permis de mieux comprendre la configuration des tunnels VPN, la gestion des clés, et les règles de routage/NAT nécessaires à l'interconnexion distante.

WireGuard s'est révélé plus performant et facile à déployer qu'OpenVPN. La seule difficulté a été la configuration du routage entre le VPS et mon réseau personnel.

À refaire, j'essaierais aussi des outils comme PiVPN pour simplifier l'ajout de clients via une interface Web.
