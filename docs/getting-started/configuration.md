# Configuration

Guide de configuration des credentials et paramètres globaux.

## Credentials essentiels

### Anthropic (Claude AI)

1. Créer un compte sur [console.anthropic.com](https://console.anthropic.com)
2. Générer une API Key
3. Dans n8n : **Credentials** > **New** > **Anthropic API**
4. Coller l'API Key

**Modèles recommandés :**
- `claude-sonnet-4-20250514` - Meilleur rapport qualité/prix
- `claude-opus-4-20250514` - Plus puissant, plus lent

### Notion

1. Créer une intégration sur [notion.so/my-integrations](https://www.notion.so/my-integrations)
2. Récupérer le token d'intégration
3. Partager les pages/databases avec l'intégration
4. Dans n8n : **Credentials** > **New** > **Notion API**

### Google (Calendar, Drive, Sheets)

1. Créer un projet sur [Google Cloud Console](https://console.cloud.google.com)
2. Activer les APIs nécessaires
3. Créer des credentials OAuth 2.0
4. Dans n8n : **Credentials** > **New** > **Google OAuth2 API**

### Feedly

1. Obtenir un Developer Token sur [developer.feedly.com](https://developer.feedly.com)
2. Dans n8n : utiliser un node HTTP Request avec header Authorization

### Brave Search

1. Créer un compte sur [brave.com/search/api](https://brave.com/search/api)
2. Générer une API Key
3. Dans n8n : utiliser un node HTTP Request

## Variables d'environnement

Pour une configuration centralisée, utiliser les variables d'environnement n8n :

```bash
# .env ou variables d'environnement
N8N_ENCRYPTION_KEY=votre-cle-secrete
ANTHROPIC_API_KEY=sk-ant-xxx
NOTION_TOKEN=secret_xxx
```

## Bonnes pratiques

1. **Ne jamais commiter les credentials** dans le repo
2. Utiliser des **variables d'environnement** pour les secrets
3. **Rotation régulière** des API keys
4. **Limiter les scopes** au minimum nécessaire
