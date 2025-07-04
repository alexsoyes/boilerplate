# Product Requirements Document (PRD) - Save Link Discord Bot

## Overview

Bot Discord intelligent développé en TypeScript qui permet aux utilisateurs avec le rôle "ambassadeur" de sauvegarder des liens avec description optionnelle. Le bot crée automatiquement une pull request sur le dépôt GitHub ai-driven-dev/ressources, puis utilise Claude Code via GitHub Actions pour analyser le lien, extraire les métadonnées et insérer intelligemment la ressource au bon endroit dans le README, respectant le format et l'organisation existante.

## Core Features

- **Commande Discord `/save-link <url> [description]`** : Interface simple pour sauvegarder un lien avec description optionnelle
- **Vérification du rôle ambassadeur** : Seuls les utilisateurs autorisés peuvent utiliser la fonctionnalité
- **Validation URL avancée** : Vérification HTTP status, détection doublons, normalisation URL
- **Création automatique de PR** : Génération d'une pull request sur le dépôt GitHub ai-driven-dev/ressources
- **Intégration Claude Code** : Action GitHub automatique qui analyse le lien et place intelligemment la ressource
- **Extraction automatique de métadonnées** : Titre, description et catégorisation automatique du lien
- **Format standardisé** : Insertion respectant le format existant (Nom, Description en français, Statut 🔥, Testé par)
- **Feedback utilisateur** : Retour avec lien vers la PR créée
- **Gestion d'erreurs** : Commentaires automatiques sur la PR en cas de problème
- **Architecture extensible** : Structure modulaire pour futures commandes Discord

## User Experience

- **Utilisateur cible** : Membres Discord avec le rôle "ambassadeur"
- **Flow utilisateur** :
  1. Utilisateur tape `/save-link <url> [description]` sur Discord
  2. Bot vérifie les permissions (rôle ambassadeur)
  3. Bot crée une PR sur GitHub avec les informations de base
  4. GitHub Action déclenche Claude Code pour analyser le lien
  5. Claude Code extrait les métadonnées et insère la ressource au bon endroit
  6. Bot confirme la création de la PR avec le lien vers celle-ci
  7. Review manuelle obligatoire avant merge

## Technical Architecture

- **Bot Discord** : TypeScript avec Discord.js
- **GitHub API** : Création et gestion des pull requests
- **Claude Code GitHub Actions** : Traitement intelligent des PRs avec analyse de liens
- **Architecture modulaire** : Séparation claire entre bot Discord et logique GitHub
- **Système de templates** : Prompts prédéfinis pour Claude Code
- **Gestion des erreurs** : Logs et commentaires automatiques sur les PRs

## Development Roadmap

### Phase 1 (MVP)

- Configuration bot Discord avec commande `/save-link`
- Vérification des permissions (rôle ambassadeur)
- Création basique de PR sur GitHub
- Configuration GitHub Action avec Claude Code
- Extraction simple de métadonnées (titre, description)
- Placement manuel dans une section générique
- Feedback utilisateur avec lien PR

### Phase 2 (Enhancement)

- Placement intelligent automatique dans les bonnes sections
- Détection avancée de doublons
- Amélioration des prompts Claude Code
- Gestion avancée des erreurs
- Système de fallback en cas d'échec
- Métriques et monitoring

## Logical Dependency Chain

1. **Infrastructure bot Discord** : Configuration, authentification, commandes slash
2. **Intégration GitHub** : API connection, création de PR, gestion des repos
3. **GitHub Action Claude Code** : Configuration, prompts, traitement automatique
4. **Extraction de métadonnées** : Analyse des liens, extraction d'informations
5. **Placement intelligent** : Logique de catégorisation et insertion dans README
6. **Système de feedback** : Retour utilisateur et gestion d'erreurs

## Risks and Mitigations

- **Risque technique** : Limitation des API GitHub → Cache et logique de retry
- **Risque de placement** : Mauvaise catégorisation → Prompts optimisés et fallback
- **Risque de doublons** : Ressources déjà existantes → Détection avant insertion
- **Risque de permissions** : Gestion des rôles Discord → Validation stricte
- **Risque Claude Code** : Échec de l'analyse → Commentaires d'erreur et intervention manuelle
- **Risque de format** : Non-respect de la structure → Templates et validation

## Appendix

- **Dépôt cible** : <https://github.com/ai-driven-dev/ressources>
- **Documentation Claude Code** : <https://docs.anthropic.com/en/docs/claude-code/github-actions>
- **Format des ressources** : Nom (avec lien), Description (français), Statut (🔥 par défaut), Testé par (nom utilisateur Discord)
- **Rôle requis** : "ambassador" sur Discord
- **Langage** : TypeScript pour le bot, français pour les descriptions
- **Review** : Manuelle obligatoire avant merge
- **Gestion d'erreurs** : Commentaires automatiques sur PR en cas de problème
