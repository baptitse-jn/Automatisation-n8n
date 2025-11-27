# Automatisation N8N - MyWai

Collection de workflows n8n pour l'automatisation des processus métier. Une vision 360° du business avec des automatisations modulaires et scalables.

## Structure du repo

```
Automatisation-n8n/
├── workflows/                      # Workflows organisés par domaine métier
│   ├── marketing/                  # Email, Social Media, SEO, Content
│   ├── commercial/                 # CRM, Lead Gen, Prospection
│   ├── communication/              # Interne, Externe, Social Listening
│   ├── operations/                 # Project Management, Data Sync
│   ├── finance/                    # Facturation, Dépenses
│   ├── rh/                         # Recrutement, Onboarding
│   ├── customer-service/           # Support, Chatbots
│   ├── ai-agents/                  # Agents IA transversaux
│   └── veille/                     # Veille tech, marché, concurrence
├── templates/                      # Templates et snippets réutilisables
├── docs/                           # Documentation complète
├── config/                         # Configurations partagées
└── assets/                         # Images et diagrammes
```

## Workflows disponibles

### Veille
| Workflow | Description | Trigger |
|----------|-------------|---------|
| [Agent Veille IA](./workflows/veille/tech/) | Extraction Feedly → Recherche web → Rédaction Claude → Notion | Quotidien 9h |

### AI Agents
| Workflow | Description | Trigger |
|----------|-------------|---------|
| [AI Agent Multi Tools FR](./workflows/ai-agents/multi-tools/) | Agent multi-outils en français | Manuel |

### Operations
| Workflow | Description | Trigger |
|----------|-------------|---------|
| [Google Calendar AI Agent](./workflows/operations/task-automation/) | Agent IA pour gestion calendrier | Manuel |

### Finance
| Workflow | Description | Trigger |
|----------|-------------|---------|
| [Expense Tracker AI Agent](./workflows/finance/expense-tracking/) | Agent IA pour suivi des dépenses | Manuel |

## Quick Start

1. **Cloner ce repo**
   ```bash
   git clone https://github.com/baptitse-jn/Automatisation-n8n.git
   ```

2. **Ouvrir n8n** (Cloud ou self-hosted)

3. **Importer un workflow**
   - Aller dans Workflows > Import from File
   - Sélectionner le `.json` souhaité

4. **Configurer les credentials**
   - Voir [Configuration](./docs/getting-started/configuration.md)

5. **Activer le workflow**

## Stack technique

| Catégorie | Technologies |
|-----------|--------------|
| **Orchestration** | n8n |
| **IA** | Claude (Anthropic), Mem0 |
| **Recherche** | Brave Search, Feedly |
| **Stockage** | Notion, Google Sheets, Airtable |
| **Communication** | Slack, Email |

## Documentation

- [Installation](./docs/getting-started/installation.md) - Installer n8n
- [Configuration](./docs/getting-started/configuration.md) - Configurer les credentials
- [Guide AI Agent](./docs/guides/AI_AGENT_GUIDE_FR.md) - Créer des agents IA
- [Best Practices](./docs/guides/BEST_PRACTICES_FR.md) - Bonnes pratiques
- [Cheat Sheet](./docs/guides/N8N_CHEAT_SHEET_FR.md) - Aide-mémoire n8n

## Contribuer

Les contributions sont les bienvenues ! Voir [CONTRIBUTING.md](./CONTRIBUTING.md) pour les guidelines.

### Ajouter un workflow

1. Placer le fichier `.json` dans le bon dossier domaine
2. Créer un `README.md` décrivant le workflow
3. Mettre à jour le README du domaine
4. Soumettre une Pull Request

## Liens utiles

- [Documentation n8n](https://docs.n8n.io/)
- [API Anthropic](https://docs.anthropic.com/)
- [Communauté n8n](https://community.n8n.io/)

---

*Créé par Baptiste - MyWai*
