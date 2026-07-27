---
layout: page
title: Portail Captif Multi-Zones pfSense
description: Authentification LDAP et invités, filtrage web et traçabilité RGPD
img: assets/img/projet2-couverture.jpg
importance: 3
category: securite
related_publications: false
---

{% include figure.liquid path="assets/img/projet2-couverture.jpg" title="Portail Captif Multi-Zones pfSense" class="img-fluid rounded z-depth-1" %}

## Objectif du projet

- **Protection de l'accès réseau** : portail captif imposant une authentification préalable
- **Double authentification** : LDAP pour les internes, code temporaire pour les invités
- **Filtrage Internet** via Squid/SquidGuard pour bloquer les contenus inadaptés (RGPD & mineurs)
- **Traçabilité et journalisation** : archivage des logs pendant 1 an
- Solution open source, évolutive et reproductible, pouvant être déployée dans d'autres établissements

## Contexte

Dans le cadre d'un projet réalisé pour un collège accueillant des mineurs, il a été décidé de mettre en place une solution de sécurisation et de contrôle d'accès réseau. L'environnement technique repose sur une infrastructure virtualisée VMware ESXi et exploite des solutions open source afin de garantir robustesse, coût réduit et conformité légale.

L'objectif principal était de sécuriser les accès au réseau Wi-Fi et filaire, en différenciant :
- Les utilisateurs internes (authentifiés via LDAP)
- Les invités (accès ponctuel via code temporaire envoyé par email)

## Cahier des charges

- **Accès interne** : LDAP centralisé pour le personnel/élèves
- **Accès invité** : génération automatique de codes envoyés par email
- **Sécurité** : filtrage web (SquidGuard), authentification obligatoire, logs
- **Traçabilité légale** : conservation des accès et navigation ≥ 1 an
- **Virtualisation** : hébergement sur ESXi (VM pfSense, VM test, serveur LDAP)

## Architecture visée

- 1 VM pfSense (pare-feu, DHCP, DNS, portail captif, NAT, filtrage)
- 1 serveur LDAP (authentification interne)
- 1 serveur SMTP (envoi des codes invités)
- Squid + SquidGuard (proxy et filtrage web)
- Stockage externe (logs et sauvegardes)
- Deux VLANs distincts : LAN interne (LDAP) et LAN invité (portail captif + codes temporaires)

## Schéma d'architecture

{% include figure.liquid path="assets/img/projet2-schema.jpg" title="Schéma réseau du portail" class="img-fluid rounded z-depth-1" %}

## Démarche et mise en œuvre

- Installation pfSense sur une VM ESXi (2 interfaces : WAN/LAN)
- Configuration réseau : plan IP + segmentation interne/invités
- Mise en place du portail captif :
  - Zone LDAP → connexion avec serveur d'annuaire
  - Zone invité → formulaire + génération code temporaire
- Filtrage Internet : installation Squid + SquidGuard, import des blacklists (sites adultes, paris, etc.)
- SMTP : configuration plugin pfSense pour envoi automatique des identifiants invités
- Journalisation : activation Syslog vers serveur externe + rétention 1 an
- Tests : PC Windows, smartphone Android → authentification OK, filtrage OK, logs générés

## Résultats et livrables

- Portail captif fonctionnel et accessible sur PC/mobile
- Double mode d'authentification (LDAP + Invités)
- Filtrage opérationnel (sites interdits bloqués)
- Traçabilité complète (logs centralisés)
- Documentation livrée : cahier des charges, guide de déploiement, schéma d'architecture, procédures utilisateurs

## Résultats & Captures

**Interface du portail invité**

{% include figure.liquid path="assets/img/projet2-invite.jpg" title="Portail invité" class="img-fluid rounded z-depth-1" %}

**Connexion via LDAP**

{% include figure.liquid path="assets/img/projet2-login-ldap.jpg" title="Connexion LDAP" class="img-fluid rounded z-depth-1" %}

**Portail connecté côté invité**

{% include figure.liquid path="assets/img/projet2-connected.jpg" title="Portail connecté invité" class="img-fluid rounded z-depth-1" %}

**Portail sur mobile**

{% include figure.liquid path="assets/img/projet2-mobile.jpg" title="Vue mobile du portail" class="img-fluid rounded z-depth-1" %}

## Problèmes rencontrés et solutions

- **LDAP** : mauvaise configuration du DN → corrigée via tests avec `ldapsearch`
- **Isolation VLAN** : trafic invité fuyait vers LAN → corrigé par règles pfSense strictes
- **Filtrage SquidGuard** : certaines listes trop larges → adaptation des règles pour éviter faux positifs

## Compétences mobilisées

- **C1** : Fournir les services liés au SI (mise en place d'un service réseau sécurisé et documenté)
- **C2** : Collaborer avec les acteurs (rédaction de cahier des charges, documentation claire)
- **C3** : Veille technologique (étude comparée pfSense/Squid/SquidGuard, conformité RGPD)
- **C4** : Sécuriser le SI (filtrage web, VLAN, traçabilité, sauvegardes)

## Retour d'expérience

Ce projet m'a permis d'approfondir la gestion d'accès réseau et l'intégration LDAP, de comprendre les enjeux légaux (RGPD, journalisation), de travailler sur la segmentation réseau via pfSense et le filtrage web avec Squid/SquidGuard, et de développer des compétences en documentation technique (guide, procédures, schéma).

**Améliorations possibles :**
- Ajout d'IDS/IPS (Snort/Suricata)
- Automatisation via Ansible pour déploiement multi-sites
