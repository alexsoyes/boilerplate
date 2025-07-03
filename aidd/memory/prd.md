# Product Requirements Document (PRD) - Discord Link Aggregator Bot

## Overview

Extensible Discord bot that allows users with the "ambassador" role to save links with context, which are automatically organized in the GitHub repository ai-driven-dev/ressources via pull requests.

## Core Features

- **Command `/save-link <url> <description>`** : Simple interface to save a link
- **Ambassador role verification** : Only authorized users can use the functionality
- **Automatic link analysis** : Web parser to extract title, content and determine category
- **Duplicate prevention** : Verify that the link doesn't already exist in the repository
- **Intelligent placement** : Automatically organize in the correct README section
- **Standardized PR creation** : Format respecting repository conventions (name, link, description, status ✅, tested by)

## User Experience

- **Target user** : Discord members with "ambassador" role
- **User flow** :
  1. User types `/save-link <url> <description>`
  2. Bot verifies permissions
  3. Bot analyzes link and checks for duplicates
  4. Bot creates PR with link placed in correct section
  5. Bot confirms PR creation to user

## Technical Architecture

- **Discord Bot** : Discord.js or Python (discord.py)
- **GitHub API** : Repository reading and PR creation
- **Web Parser** : Link analysis for metadata extraction
- **Matching System** : Duplicate detection algorithm
- **Modular Architecture** : Extensible for future features

## Development Roadmap

### Phase 1 (MVP)

- Basic Discord command `/save-link`
- Permission verification (ambassador role)
- Simple web parser for title and description extraction
- Basic duplicate checking (exact URL)
- PR creation with manual placement in generic section

### Phase 2 (Enhancement)

- AI-powered intelligent placement in appropriate sections
- Advanced duplicate detection (similar domains, close content)
- Enhanced web parser (enriched metadata extraction)
- Automatic PR format validation

## Logical Dependency Chain

1. **Discord bot infrastructure** : Basic configuration, authentication, commands
2. **GitHub integration** : API connection, repository reading, PR creation
3. **Web parser** : Link metadata extraction
4. **Duplicate system** : Verification algorithm
5. **Intelligent placement** : Categorization and organization logic

## Risks and Mitigations

- **Technical risk** : GitHub API rate limiting → Cache implementation and retry logic
- **Duplicate risk** : Insufficient detection → Progressive matching algorithm
- **Placement risk** : Poor categorization → Human review system via PR
- **Permission risk** : Discord role management → Strict permission validation

## Appendix

- **Target repository** : <https://github.com/ai-driven-dev/ressources>
- **Current structure** : README organized by sections with standardized format
- **Resource format** : Name, official link, description, status, tested by
- **Required role** : "ambassador" on Discord
