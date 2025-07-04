# AI-Driven Dev Boilerplate

Ce dépôt va nous servir de base d'outils "vibe-codé" mais ultra qualitatif.

<https://app.excalidraw.com/l/7ad586Zigro/AM1hDZ1xzOA>

## Roadmap

Ce dépôt est en cours de construction, voici les grandes lignes de la roadmap :

PRP :

- feature instructions
- search existing code
- feature plan

- [ ] Ajouter un modèle de PRD `@alexsoyes`
  - [ ] Avoir un template correct en partant de l'AIDD
  - [ ] Aller check BMAD
- [ ] Créer un projet d'exemples
  - [ ] Bot AIDD
- [ ] Gérer le système de tâches `@alexsoyes`
  - [ ] Notes de pourquoi Claude Code
  - [ ] Retours sur TM
- [ ] Ajouter les GitHub Actions pour automatiser les issues `@mickael`
  - [ ] Config Action
  - [ ] Créer commandes claude pour aller les créer + les résoudre
- [ ] RAG
  - [ ] QDrant avec MCP docker
  - [ ] Usecase : checker si du code a déjà été écrit
  - [ ] Partage de volume
- [ ] MCP
  - [ ] Tool pour attaquer QDrant : refresh, search
  - [ ] Context 7
  - [ ] Deep Graph
- [ ] Rules
- [ ] Prompts
- [ ] Agents
- [ ] Sémantic des prompts
  - [ ] Chris
  - [ ] <https://github.com/AvitalTamir/sever>
- [ ] Vibe Coding Flow, avoir un vrai workflow
  - [ ] Crafter un doc

## Comment utiliser ce dépôt ?

### Créer un PRD

Actuellement basé sur le modèle de PRD de <https://github.com/eyaltoledano/claude-task-master/blob/main/.taskmaster/templates/example_prd.txt>.

👉 Il est pas terrible, on va l'améliorer.

## Packages

Quelques packages utiles :

- [`ccusage`](https://github.com/ryoppippi/ccusage) : Voir la consommation de Claude Code.
- [`task-master-ai`](https://github.com/eyaltoledano/claude-task-master) : Gérer les tâches depuis un PRD.

## MCP

La liste des MCPs que l'on a déjà configuré :

- `task-master-ai` : Gérer les tâches depuis un PRD.
