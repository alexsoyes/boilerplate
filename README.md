# AI-Driven Dev Boilerplate

Ce dépôt va nous servir de base d'outils "vibe-codé" mais ultra qualitatif.

<https://app.excalidraw.com/l/7ad586Zigro/AM1hDZ1xzOA>

## Roadmap

**Légende :** 🔄 En cours | 📋 Planifié | ✅ Terminé | ⏸️ En pause

### 🛠️ Outils de développement

| Fonctionnalité | Responsable | Use Case | Statut |
|---|---|---|---|
| **Modèle PRD** | @alexsoyes | Remplacer le template actuel par des PRD structurés et qualitatifs | 🔄 |
| **Système de tâches** | @alexsoyes | Documenter Claude Code et capitaliser sur les retours TM | 📋 |

### 🤖 Automatisation & CI/CD

| Fonctionnalité | Responsable | Use Case | Statut |
|---|---|---|---|
| **GitHub Actions** | @mickael | Automatiser création/résolution d'issues via commandes Claude | 📋 |

### 🧠 Intelligence & RAG

| Fonctionnalité | Responsable | Use Case | Statut |
|---|---|---|---|
| **RAG avec QDrant** | - | Vérifier l'existence de code similaire avant développement | 📋 |
| **MCP Tools** | - | Outils QDrant (refresh, search) + Context 7 + Deep Graph | 📋 |

### 📋 Workflow & Processus

| Fonctionnalité | Responsable | Use Case | Statut |
|---|---|---|---|
| **Rules & Prompts** | - | Standardiser règles et prompts pour la cohérence du code | 📋 |
| **Agents** | - | Automatiser tâches répétitives via agents spécialisés | 📋 |
| **Sémantique des prompts** | Chris | Approche sémantique pour améliorer la précision ([sever](https://github.com/AvitalTamir/sever)) | 📋 |
| **Vibe Coding Flow** | - | Documenter le workflow "vibe-codé" reproductible | 📋 |

## Projet d'exemple - Bot Discord

Premier projet concret utilisant ce boilerplate pour démontrer ses capacités.

### 🎯 Objectif

Créer un bot Discord "Save Link" qui permet de sauvegarder et organiser des liens partagés dans les canaux.

### 📋 Fonctionnalités prévues

- Détection automatique des liens dans les messages
- Sauvegarde avec tags et catégories
- Commandes de recherche et récupération
- Interface web pour consultation

## Comment utiliser ce dépôt ?

### Créer un PRD

Actuellement basé sur le modèle de PRD de <https://github.com/eyaltoledano/claude-task-master/blob/main/.taskmaster/templates/example_prd.txt>.

👉 Il est pas terrible, on va l'améliorer.

## Packages

Quelques packages utiles :

- [`ccusage`](https://github.com/ryoppippi/ccusage) : Voir la consommation de Claude Code.

## MCP

La liste des MCPs que l'on a déjà configuré :

- [`sequential-thinking`](https://github.com/modelcontextprotocol/servers/tree/main/src/sequentialthinking)
