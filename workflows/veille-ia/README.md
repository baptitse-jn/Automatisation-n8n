# Agent Veille IA - Feedly to Notion

## Description
Cet agent N8N automatise votre veille technologique en :
1. Récupérant les articles du folder "VeilleArticleIA" sur Feedly tous les jours à 9h
2. Effectuant une recherche internet complémentaire pour chaque article
3. Générant un article de veille structuré avec Claude (Anthropic)
4. Sauvegardant l'article dans votre base Notion

## Architecture du Workflow
```
[Schedule 9h] → [Get Profile] → [Get Categories] → [Filter VeilleArticleIA]
                                                            ↓
[Save Notion] ← [AI Agent Claude] ← [Prepare Data] ← [Brave Search] ← [Get Articles] ← [Split]
       ↓
   [Loop] → retour au traitement du prochain article
```

## Prérequis

### 1. Feedly API Token
- Allez sur https://feedly.com/v3/auth/dev
- Générez un Developer Access Token
- Créez un credential "HTTP Header Auth" dans N8N :
  - Name: `Authorization`
  - Value: `Bearer VOTRE_TOKEN_FEEDLY`

### 2. Anthropic API Key
- Allez sur https://console.anthropic.com/
- Créez une API Key
- Créez un credential "Anthropic API" dans N8N

### 3. Notion Integration
- Allez sur https://www.notion.so/my-integrations
- Créez une nouvelle intégration
- Copiez l'Internal Integration Token
- Créez un credential "Notion API" dans N8N
- Partagez votre base de données avec l'intégration

### 4. Brave Search API (optionnel - peut être remplacé)
- Allez sur https://api.search.brave.com/
- Créez un compte et obtenez une API Key
- Créez un credential "HTTP Header Auth" dans N8N :
  - Name: `X-Subscription-Token`
  - Value: `VOTRE_CLE_BRAVE`

## Configuration de la Base Notion

Créez une base de données Notion avec les propriétés suivantes :
| Propriété | Type | Description |
|-----------|------|-------------|
| Titre | Title | Titre de l'article |
| Résumé | Text | Résumé de l'article |
| Source Originale | URL | Lien vers l'article source |
| Date | Date | Date de création |
| Statut | Select | Options: Nouveau, Lu, Archivé |


## Installation

### Méthode 1: Import direct
1. Ouvrez N8N
2. Allez dans **Workflows** → **Import from File**
3. Sélectionnez `agent-veille-ia.json`
4. Configurez les credentials (voir section Prérequis)
5. Modifiez les IDs suivants dans le workflow :
   - `NOTION_DATABASE_ID` : L'ID de votre base Notion
   - Vérifiez que le nom du folder Feedly correspond ("VeilleArticleIA")

### Méthode 2: Import via URL (si hébergé sur GitHub)
1. Ouvrez N8N
2. Allez dans **Workflows** → **Import from URL**
3. Collez l'URL raw du fichier JSON

## Configuration Mem0 (Mémoire Partagée)

Pour utiliser Mem0 comme mémoire partagée entre vos agents :

### Installation du node Mem0
```bash
# Dans votre instance N8N, installez le community node
npm install n8n-nodes-mem0
```

### Configuration
1. Créez un compte sur https://mem0.ai ou déployez votre propre instance
2. Obtenez votre API Key
3. Ajoutez un node Mem0 dans vos workflows pour :
   - Stocker le contexte des articles traités
   - Récupérer les préférences et l'historique
   - Partager des informations entre agents

### Exemple d'utilisation Mem0
```json
{
  "parameters": {
    "operation": "add",
    "messages": "={{ $json.output.titre + ': ' + $json.output.resume }}",
    "userId": "veille-agent",
    "metadata": {
      "source": "feedly",
      "folder": "VeilleArticleIA",
      "date": "={{ $now.toISODate() }}"
    }
  },
  "name": "Store in Mem0",
  "type": "n8n-nodes-mem0.mem0"
}
```

## Personnalisation

### Changer la fréquence
Modifiez le node "Trigger 9h Quotidien" :
- `triggerAtHour`: Heure (0-23)
- `triggerAtMinute`: Minute (0-59)

### Changer le folder Feedly
Modifiez le node "Filter VeilleArticleIA" :
- `rightValue`: Nom de votre folder

### Modifier le prompt AI
Modifiez le node "AI Agent - Rédaction Article" :
- `text`: Votre prompt personnalisé
- `systemMessage`: Les instructions système

### Utiliser un autre modèle Anthropic
Modifiez le node "Anthropic Claude" :
- `model`: `claude-sonnet-4-20250514` ou `claude-3-haiku-20240307`

## Dépannage

### Erreur "API handler not found" sur Feedly
- Vérifiez que votre token est valide
- Assurez-vous d'utiliser `cloud.feedly.com` et non `api.feedly.com`

### Articles non récupérés
- Vérifiez le nom exact du folder dans Feedly
- Le paramètre `newerThan` filtre les articles des dernières 24h

### Erreur Notion "Could not find database"
- Vérifiez que l'intégration a accès à la base
- L'ID de la base doit être correct (32 caractères)

## Maintenance

- **Logs** : Consultez les exécutions dans N8N pour déboguer
- **Limites API** : Attention aux quotas Feedly (250 requêtes/jour en free)
- **Coûts** : L'API Anthropic est facturée à l'usage

---
*Créé par Claude pour MyWai - Agent de Veille IA*
