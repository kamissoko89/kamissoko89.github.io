---
layout: page
title: Portail Captif avec Authentification SMS OTP
description: Solution d'authentification réseau par code SMS pour l'accès invité à l'École Nationale des Greffes
img: assets/img/11.jpg
importance: 11
category: securite
related_publications: false
---

## Contexte

Dans le cadre de mes fonctions à l'École Nationale des Greffes (Ministère de la Justice), un besoin d'accès réseau sécurisé pour les visiteurs et intervenants externes a été identifié. La solution devait garantir une traçabilité conforme aux exigences légales (LCEN) tout en restant simple d'usage.

## Objectif du projet

Mettre en place un portail captif avec authentification par code temporaire envoyé par SMS, afin de sécuriser l'accès réseau des invités tout en assurant la traçabilité légale des connexions.

## Outils utilisés

pfSense, AllMySMS (API d'envoi de SMS), PHP, PostgreSQL, Stormshield (pare-feu périmétrique)

## Démarche et mise en œuvre

- Configuration du portail captif sur pfSense pour rediriger les nouveaux appareils vers une page d'authentification
- Développement d'un backend PHP pour gérer la demande de code, l'envoi via l'API AllMySMS et la validation
- Mise en place d'une base PostgreSQL pour stocker les sessions, numéros de téléphone et horodatages de connexion
- Intégration avec le pare-feu périmétrique Stormshield pour le filtrage et la remontée de logs
- Mise en conformité LCEN : conservation des logs de connexion sur la durée légale requise
- Tests multi-appareils (smartphones, ordinateurs portables) pour valider le parcours utilisateur

## Résultats et livrables

- Portail captif fonctionnel avec authentification SMS opérationnelle
- Base de données de traçabilité conforme aux exigences LCEN
- Documentation technique (architecture, configuration pfSense, schéma de flux)
- Solution reproductible pour d'autres sites du Ministère

## Compétences mobilisées

- **C1** : Fournir les services liés au SI (conception et déploiement d'un service d'accès réseau sécurisé)
- **C3** : Veille technologique (choix d'API SMS, conformité réglementaire LCEN)
- **C4** : Sécurité des SI (authentification, traçabilité, filtrage réseau)

## Retour d'expérience

Ce projet m'a permis de combiner développement (PHP, PostgreSQL) et administration réseau (pfSense, Stormshield) sur une problématique réelle en environnement ministériel exigeant. La contrainte de conformité légale (LCEN) a été un point d'attention particulier, nécessitant une réflexion sur la durée et le format de conservation des logs.

L'intégration entre le pare-feu périmétrique et le portail applicatif a demandé une bonne compréhension du flux réseau de bout en bout.
