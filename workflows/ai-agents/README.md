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
