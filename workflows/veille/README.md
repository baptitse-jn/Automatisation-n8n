# Veille

Workflows de veille stratégique et intelligence économique.

## Catégories

| Dossier | Description | Cas d'usage |
|---------|-------------|-------------|
| `tech/` | Veille technologique | Nouvelles technos, IA, dev |
| `market/` | Veille marché | Tendances, opportunités |
| `competitive/` | Veille concurrentielle | Analyse concurrents, benchmarks |

## Workflows disponibles

| Workflow | Description | Trigger | Intégrations |
|----------|-------------|---------|--------------|
| [Agent Veille IA](./tech/agent-veille-ia.json) | Veille technologique IA quotidienne | Schedule (9h) | Feedly, Brave Search, Claude, Notion |

## Sources de données

### Flux RSS / Agrégateurs
- Feedly, Inoreader
- Google Alerts

### Recherche Web
- Brave Search API
- Google Custom Search
- Tavily

### Social / News
- Twitter/X API
- LinkedIn
- Reddit API

## Comment ajouter un workflow

1. Placer le fichier `.json` dans le sous-dossier approprié
2. Créer un `README.md` dans le même dossier avec la documentation
3. Mettre à jour ce fichier avec les infos du workflow
