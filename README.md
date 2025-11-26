# 🤖 Automatisation N8N - MyWai

Collection de workflows N8N pour l'automatisation des processus métier.

## 📁 Structure du repo

```
Automatisation-n8n/
├── workflows/
│   └── veille-ia/           # Agent de veille technologique
│       ├── agent-veille-ia.json
│       └── README.md
├── config/                   # Fichiers de configuration partagés
└── docs/                     # Documentation générale
```

## 🚀 Workflows disponibles

| Workflow | Description | Trigger |
|----------|-------------|---------|
| [Veille IA](./workflows/veille-ia/) | Extraction Feedly → Recherche web → Rédaction Claude → Notion | Quotidien 9h |

## ⚙️ Configuration globale

### Stack technique
- **IA** : Anthropic Claude (claude-sonnet-4-20250514)
- **Mémoire partagée** : Mem0
- **Sources** : Feedly (RSS), Brave Search
- **Stockage** : Notion

### Credentials requis
1. **Anthropic API Key** - Pour les agents IA
2. **Feedly Developer Token** - Pour l'extraction RSS
3. **Notion Integration** - Pour la sauvegarde
4. **Brave Search API** (optionnel) - Pour la recherche web

## 📖 Comment utiliser

1. Cloner ce repo
2. Ouvrir N8N
3. Importer le fichier JSON du workflow souhaité
4. Configurer les credentials
5. Activer le workflow

## 🔗 Liens utiles

- [Documentation N8N](https://docs.n8n.io/)
- [API Feedly](https://developer.feedly.com/)
- [API Anthropic](https://docs.anthropic.com/)

---
*Créé par Baptiste - MyWai*
