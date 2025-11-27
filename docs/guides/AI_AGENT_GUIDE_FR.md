# 🤖 Guide Complet des AI Agents n8n

## Introduction

Les AI Agents dans n8n permettent de créer des assistants IA intelligents capables d'utiliser des outils pour accomplir des tâches complexes.

---

## Architecture d'un AI Agent

```
┌─────────────────┐
│  Chat Trigger   │
└────────┬────────┘
        │
        ▼
┌─────────────────┐
│   AI Agent      │◄─────┐
└────────┬────────┘     │
        │               │
   ┌────┴────┐          │
   │         │          │
   ▼         ▼          │
┌──────┐  ┌──────┐  ┌─────┴──┐
│ LLM  │  │Memory│  │ Tools  │
└──────┘  └──────┘  └────────┘
```

---

## Types d'Agents Disponibles

### 1. Tools Agent (Par défaut)
Utilise des outils externes pour accomplir des tâches.

```json
{
  "name": "AI Agent",
  "type": "@n8n/n8n-nodes-langchain.agent",
  "typeVersion": 1.7,
  "parameters": {
    "text": "={{ $json.chatInput }}",
    "options": {
      "systemMessage": "Tu es un assistant...",
      "maxIterations": 10
    },
    "promptType": "define"
  }
}
```

### 2. Conversational Agent
Idéal pour les chatbots et assistants virtuels.

### 3. ReAct Agent
Utilise la stratégie Reasoning + Acting pour des tâches complexes.

---

## Composants Essentiels

### 1. Modèle de Langage (LLM)

```json
{
  "name": "OpenAI Chat Model",
  "type": "@n8n/n8n-nodes-langchain.lmChatOpenAi",
  "typeVersion": 1.1,
  "parameters": {
    "model": "gpt-4o",
    "options": {
      "temperature": 0.7,
      "maxTokens": 4096
    }
  }
}
```

**Modèles recommandés:**
- `gpt-4o` - Meilleure qualité
- `gpt-4o-mini` - Plus économique
- `claude-3-5-sonnet` - Alternative Anthropic

### 2. Mémoire

```json
{
  "name": "Window Buffer Memory",
  "type": "@n8n/n8n-nodes-langchain.memoryBufferWindow",
  "typeVersion": 1.3,
  "parameters": {
    "sessionKey": "={{ $json.sessionId }}",
    "sessionIdType": "customKey",
    "contextWindowLength": 20
  }
}
```

**Types de mémoire:**
- `memoryBufferWindow` - Mémoire à fenêtre glissante
- `memoryPostgresChat` - Mémoire persistante PostgreSQL
- `memoryRedisChat` - Mémoire Redis

### 3. Outils (Tools)

#### Outil Code
```json
{
  "name": "Outil Personnalisé",
  "type": "@n8n/n8n-nodes-langchain.toolCode",
  "typeVersion": 1.1,
  "parameters": {
    "name": "mon_outil",
    "description": "Description pour l'IA",
    "jsCode": "try {\n  return { success: true };\n} catch (error) {\n  return { error: error.message };\n}"
  }
}
```

#### Outil HTTP
```json
{
  "name": "API Request",
  "type": "@n8n/n8n-nodes-langchain.toolHttpRequest",
  "typeVersion": 1.1,
  "parameters": {
    "method": "GET",
    "url": "={{ $fromAI('url') }}",
    "toolDescription": "Appelle une API externe"
  }
}
```

#### Outil Workflow
```json
{
  "name": "Sous-Workflow",
  "type": "@n8n/n8n-nodes-langchain.toolWorkflow",
  "typeVersion": 1.3,
  "parameters": {
    "name": "execute_task",
    "workflowId": { "value": "workflow-id" },
    "description": "Exécute un sous-workflow"
  }
}
```

---

## Meilleures Pratiques

### 1. Prompt Système

```
Tu es un assistant IA spécialisé en [domaine].

## Tes Capacités:
1. [Outil 1] - Description
2. [Outil 2] - Description

## Règles:
- Réponds dans la langue de l'utilisateur
- Utilise les outils quand nécessaire
- Ne jamais inventer de données

## Format:
- Utilise des listes pour la clarté
- Mets en gras les infos importantes
```

### 2. Gestion des Erreurs

```javascript
try {
  // Code principal
  const result = await processData($input);
  return { success: true, data: result };
} catch (error) {
  return {
    success: false,
    error: error.message,
    suggestion: "Essayez avec d'autres paramètres"
  };
}
```

### 3. Variables $fromAI

Permet à l'IA de fournir dynamiquement des valeurs:

```javascript
{{ $fromAI('parameter_name', 'Description pour l\'IA') }}
```

Exemples:
- `{{ $fromAI('date', 'Date au format YYYY-MM-DD') }}`
- `{{ $fromAI('query', 'Requête de recherche') }}`

---

## Connexions entre Nœuds

```json
"connections": {
  "Chat Trigger": {
    "main": [[{ "node": "AI Agent", "type": "main", "index": 0 }]]
  },
  "OpenAI Model": {
    "ai_languageModel": [[{ "node": "AI Agent", "type": "ai_languageModel", "index": 0 }]]
  },
  "Memory": {
    "ai_memory": [[{ "node": "AI Agent", "type": "ai_memory", "index": 0 }]]
  },
  "Tool 1": {
    "ai_tool": [[{ "node": "AI Agent", "type": "ai_tool", "index": 0 }]]
  },
  "Tool 2": {
    "ai_tool": [[{ "node": "AI Agent", "type": "ai_tool", "index": 0 }]]
  }
}
```

---

## Exemples de Cas d'Usage

### 1. Assistant Calendrier
- Outils: Google Calendar (get, create)
- Mémoire: Window Buffer
- Prompt: Gestion de rendez-vous

### 2. Suivi de Dépenses
- Outils: Information Extractor, Google Sheets
- Mémoire: Window Buffer
- Prompt: Parsing de messages en JSON

### 3. Support Client
- Outils: Vector Store, HTTP Request
- Mémoire: PostgreSQL
- Prompt: Réponse aux questions FAQ

### 4. Automatisation CRM
- Outils: Notion, Slack, Email
- Mémoire: Redis
- Prompt: Gestion de leads

---

## Dépannage

### Erreurs Courantes

1. **"Tool not found"**
   - Vérifier les connexions ai_tool
   - Vérifier le nom de l'outil

2. **"Memory session error"**
   - Vérifier sessionKey unique
   - Vérifier la connexion ai_memory

3. **"LLM timeout"**
   - Augmenter timeout dans options
   - Réduire maxTokens

### Conseils de Performance

- Limiter `maxIterations` à 10
- Utiliser `gpt-4o-mini` pour les tâches simples
- Activer le cache quand possible
- Utiliser des descriptions d'outils précises
