# AI Agents

Agents IA transversaux utilisables dans différents contextes métier.

## Catégories

| Dossier | Description | Cas d'usage |
|---------|-------------|-------------|
| `multi-tools/` | Agents multi-outils | Agents avec plusieurs capacités |
| `research/` | Agents de recherche | Recherche web, analyse documents |
| `content-generation/` | Génération de contenu | Rédaction, résumé, traduction |

## Workflows disponibles

| Workflow | Description | Trigger | Intégrations |
|----------|-------------|---------|--------------|
| [AI Agent Multi Tools FR](./multi-tools/AI_Agent_Multi_Tools_FR.json) | Agent multi-outils en français | Manuel | Claude, Multiple tools |
| [Research Assistant Agent](./research/Research_Assistant_Agent.json) | Agent de recherche web avancé | Webhook | Brave Search, Claude, Notion |
| [Data Analyst Agent](./research/Data_Analyst_Agent.json) | Agent d'analyse de données | Webhook | Claude, Google Sheets, Notion, Slack |
| [Code Review Agent](./research/Code_Review_Agent.json) | Agent de revue de code automatisée | Webhook | GitHub, Claude, Notion, Slack |
| [Meeting Prep Agent](./research/Meeting_Prep_Agent.json) | Agent de préparation de réunion | Webhook | Google Calendar, Claude, Notion, Slack |
| [Content Repurposer](./content-generation/Content_Repurposer.json) | Agent de transformation de contenu multi-format | Webhook | Claude, Notion, Buffer |

## Stack IA recommandée

- **LLM Principal** : Claude (Anthropic) - claude-sonnet-4-20250514
- **Mémoire** : Mem0, Pinecone, Supabase Vector
- **Search** : Brave Search, Tavily, Perplexity
- **Vision** : Claude Vision, GPT-4V

## Patterns d'agents

### Agent de base
```
Trigger → Pre-processing → LLM → Post-processing → Output
```

### Agent avec mémoire
```
Trigger → Recall Memory → LLM → Store Memory → Output
```

### Agent multi-outils (ReAct)
```
Trigger → LLM → Tool Selection → Tool Execution → LLM → Output
```

## Comment ajouter un workflow

1. Placer le fichier `.json` dans le sous-dossier approprié
2. Créer un `README.md` dans le même dossier avec la documentation
3. Mettre à jour ce fichier avec les infos du workflow
