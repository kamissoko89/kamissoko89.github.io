---
layout: page
title: Audit de sécurité avec Lynis
description: Audit et durcissement d'un poste Linux Debian, rapport de conformité avant/après
img: assets/img/3.jpg
importance: 3
category: securite
related_publications: false
---

## Objectif du projet

Concevoir un audit de sécurité d'un poste Linux avec l'outil Lynis, identifier les failles, puis appliquer les recommandations pour durcir le système. Un rapport de conformité avant/après a été établi pour évaluer les progrès.

Lynis est un logiciel libre d'audit de sécurité extensible pour les ordinateurs ou machines virtuelles utilisant des systèmes d'exploitation tels qu'AIX, FreeBSD, HP-UX, Linux, macOS, NetBSD, OpenBSD, Solaris et autres dérivés d'Unix ou de type POSIX. Il assiste les administrateurs systèmes et les professionnels de la sécurité dans la tâche d'examen rapide (scan) d'un système et de ses défenses de sécurité, dans un but de durcissement.

## Contexte

Dans le cadre de ma formation en Licence ASSR, j'ai mené un audit de sécurité sur une machine Debian 12, en environnement isolé. L'objectif était de découvrir les risques potentiels sur un poste de travail, via une analyse complète fournie par Lynis.

## Outils utilisés

Lynis, Linux Debian 12, UFW, Fail2ban, Shell

## Démarche et mise en œuvre

- **Préparation** : installation de Debian, snapshot système
- **Installation de Lynis** : depuis les dépôts GitHub
- **Audit initial** : `sudo lynis audit system`
- **Analyse du rapport** : identification des services risqués, modules non sécurisés, permissions faibles
- **Correctifs appliqués** :
  - Désactivation des services inutiles
  - Activation du pare-feu UFW
  - Installation de fail2ban
  - Révision des permissions, configuration sudoers
- **Audit final** : comparaison des scores

## Résultats et livrables

- Rapport d'audit avant/après
- Liste des vulnérabilités et correctifs
- Captures d'écran
- Script de durcissement partiel

## Compétences mobilisées

**C4 – Sécurité des SI** : identification des failles, mise en place de durcissement, veille sur les recommandations Lynis, gestion des permissions et des services systèmes.

## Retour d'expérience

Ce projet m'a permis de découvrir les attentes d'un audit sécurité. J'ai été confronté à des notions avancées comme la configuration du kernel, le filtrage réseau ou le durcissement des modules PAM.

À refaire, j'irais plus loin dans l'automatisation via des scripts bash ou des outils comme OpenVAS ou Nessus pour compléter l'analyse.
