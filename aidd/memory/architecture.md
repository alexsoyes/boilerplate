# System Architecture - Save Link Discord Bot

## Overview

Architecture microservices pour un bot Discord intelligent qui automatise la sauvegarde de liens vers le dépôt GitHub ai-driven-dev/ressources via Claude Code.

## Components Architecture

### 1. Discord Bot Service

- **Technology**: TypeScript + Discord.js
- **Responsibilities**:
  - Gestion des commandes slash `/save-link`
  - Authentification et autorisation (rôle "ambassadeur")
  - Interface utilisateur Discord
  - Validation des entrées utilisateur
  - Feedback et notifications

### 2. GitHub Integration Service

- **Technology**: TypeScript + Octokit (GitHub API)
- **Responsibilities**:
  - Création automatique de pull requests
  - Gestion des permissions GitHub
  - Intégration avec le dépôt ai-driven-dev/ressources
  - Gestion des branches et commits

### 3. Claude Code GitHub Action

- **Technology**: GitHub Actions + Claude Code
- **Responsibilities**:
  - Déclenchement automatique sur création de PR
  - Extraction de métadonnées des liens
  - Analyse intelligente du contenu
  - Placement automatique dans le README
  - Gestion des erreurs et commentaires
  - Extraction automatique de métadonnées via MCP
  - Analyse intelligente du contenu web
  - Catégorisation automatique
  - Validation et normalisation des liens

## Data Flow

```
[Discord User]
    ↓ /save-link <url> [description]
[Discord Bot Service]
    ↓ Role validation
    ↓ Input sanitization
[GitHub Integration Service]
    ↓ Create PR with metadata
[GitHub Repository]
    ↓ Webhook trigger
[Claude Code GitHub Action]
    ↓ Link analysis
    ↓ Metadata extraction
    ↓ README modification
[Pull Request Update]
    ↓ Success/Error feedback
[Discord Bot Service]
    ↓ User notification
[Discord User]
```

## Tech Stack

### Backend

- **Runtime**: Node.js 22+ (latest)
- **Language**: TypeScript
- **Discord**: Discord.js v14
- **GitHub**: Octokit REST API
- **HTTP Client**: Fetch API (native)
- **Validation**: Zod
- **Logging**: Winston

### CI/CD

- **GitHub Actions**: Claude Code integration
- **Deployment**: Docker containers (self-hosted)
- **Environment**: GitHub Secrets + Docker env files
- **Orchestration**: Docker Compose

### External Services

- **Discord API**: Bot interactions
- **GitHub API**: Repository management
- **Claude Code**: AI-powered analysis
- **MCP Tools**: Web fetching et metadata extraction

## Logging Schema (Optionnel)

### Link Submissions Log

```typescript
interface LinkSubmissionLog {
  id: string;
  discordUserId: string;
  discordUsername: string;
  url: string;
  description?: string;
  prNumber: number;
  status: "pending" | "processed" | "merged" | "failed";
  createdAt: Date;
  processedAt?: Date;
  // Métadonnées extraites par Claude Code via MCP
  metadata?: {
    title: string;
    description: string;
    category: string;
    favicon?: string;
  };
}
```

## Security Architecture

### Authentication & Authorization

- **Discord OAuth2**: Bot token authentication
- **GitHub Token**: Repository access with minimal permissions
- **Role-based Access**: "ambassadeur" role verification
- **Rate Limiting**: Per-user and global limits

### Data Protection

- **Input Validation**: URL sanitization and validation
- **Environment Variables**: Sensitive data isolation
- **Secrets Management**: GitHub Secrets for tokens
- **Logging**: Structured logging without sensitive data

## Deployment Architecture

### Development Environment

```
Local Development
├── Discord Bot (localhost:3000)
├── GitHub Webhook Tunnel (ngrok)
└── Test Discord Server
```

### Production Environment

```text
Production Self-Hosted
├── Discord Bot (Docker Container)
├── GitHub Actions (Claude Code)
├── Docker Compose Stack
└── Production Discord Server
```

## Error Handling Strategy

### Cascade Error Management

1. **Discord Level**: User-friendly error messages
2. **GitHub Level**: PR comments with technical details
3. **Claude Code Level**: Fallback to manual review
4. **System Level**: Comprehensive logging and monitoring

### Retry Logic

- **GitHub API**: Exponential backoff
- **Discord API**: Rate limit handling
- **Claude Code**: Fallback to basic metadata extraction

## Performance Considerations

### Scalability

- **Concurrent Processing**: Queue-based link processing
- **Rate Limiting**: Discord and GitHub API limits
- **Caching**: Metadata caching for duplicate links
- **Resource Management**: Memory-efficient processing

### Monitoring

- **Health Checks**: Bot availability monitoring
- **Metrics**: Processing time, success rates
- **Alerts**: Critical failure notifications
- **Logging**: Structured logging with correlation IDs

## Alternative Architectures

### Option 1: Serverless Architecture

- **Pros**: Cost-effective, automatic scaling
- **Cons**: Cold start latency, limited processing time
- **Use Case**: Low-volume usage

### Option 2: Event-Driven Architecture

- **Pros**: Better decoupling, easier testing
- **Cons**: More complex setup, additional infrastructure
- **Use Case**: High-volume, multi-bot scenarios

### Option 3: Modular Monolithic Architecture (Recommandé)

- **Pros**: Simple deployment, easy debugging, extensible pour nouvelles commandes
- **Cons**: Croissance complexité avec le temps
- **Use Case**: Bot Discord évolutif avec multiples commandes futures

## Technical Challenges

### Challenge 1: Claude Code Integration

- **Issue**: API rate limits and processing time
- **Solution**: Async processing with status updates
- **Fallback**: Basic metadata extraction

### Challenge 2: Duplicate Link Detection

- **Issue**: Same resource with different URLs
- **Solution**: URL normalization and content comparison
- **Fallback**: Manual review flagging

### Challenge 3: README Structure Maintenance

- **Issue**: Maintaining consistent format
- **Solution**: Template-based generation with validation
- **Fallback**: Separate section for problematic entries

### Challenge 4: Discord Bot Reliability

- **Issue**: Bot downtime affecting user experience
- **Solution**: Health monitoring and auto-restart
- **Fallback**: Manual processing workflow

## Implementation Phases

### Phase 1: Discord Bot Service

- Configuration du bot Discord avec commandes slash
- Authentification et gestion des rôles
- Intégration GitHub pour création de PR
- Validation des entrées et gestion d'erreurs
- Système de feedback utilisateur

### Phase 2: GitHub Actions + Claude Code

- Configuration des GitHub Actions
- Intégration Claude Code avec MCP
- Développement des prompts pour extraction de métadonnées
- Logique de placement intelligent dans README
- Gestion des erreurs et fallbacks

### Phase 3: Dockerisation et Déploiement

- Création du Dockerfile optimisé pour Node.js
- Configuration docker-compose pour développement
- Scripts de déploiement et mise à jour
- Configuration des variables d'environnement
- Monitoring et logs Docker
- Documentation d'installation serveur

## Next Steps

1. **Infrastructure Setup**: Discord application and GitHub repository configuration
2. **Development Environment**: Local development setup with ngrok for webhooks
3. **MVP Implementation**: Core functionality with basic error handling
4. **Testing Strategy**: Unit tests, integration tests, and user acceptance testing
5. **Deployment Pipeline**: CI/CD setup with staging and production environments
