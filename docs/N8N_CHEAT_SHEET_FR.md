# 📘 Guide Complet n8n - Cheat Sheet

## Table des Matières
1. [Structure des Données n8n](#structure-des-données-n8n)
2. [AI & LLM Intégrations](#ai--llm-intégrations)
3. [API & Webhook](#api--webhook)
4. [Traitement de Données](#traitement-de-données)
5. [Automatisation de Workflow](#automatisation-de-workflow)
6. [Intégrations Notables](#intégrations-notables)

---

## Structure des Données n8n

n8n passe les données entre les nœuds sous forme d'un tableau d'objets:

```json
[
  {
    "json": {
      "property1": "value1",
      "property2": "value2"
    },
    "binary": {}
  }
]
```

### Expressions Utiles

```javascript
// Accéder aux données du nœud précédent
{{ $json.property1 }}

// Accéder à une propriété imbriquée
{{ $json.parent.child.property }}

// Accéder aux données d'un nœud spécifique
{{ $node["NodeName"].json.property }}

// Date et heure actuelles
{{ DateTime.local().toFormat('cccc d LLLL yyyy') }}
```

---

## AI & LLM Intégrations

### OpenAI Chat Model (GPT-4)

```json
{
  "name": "ChatGPT",
  "type": "@n8n/n8n-nodes-langchain.lmChatOpenAi",
  "typeVersion": 1,
  "parameters": {
    "model": "gpt-4o",
    "temperature": 0.7,
    "maxTokens": 4096,
    "options": {}
  },
  "credentials": {
    "openAiApi": {
      "id": "YOUR_CRED_ID",
      "name": "OpenAI API"
    }
  }
}
```

### AI Agent avec Outils

```json
{
  "name": "AI Agent",
  "type": "@n8n/n8n-nodes-langchain.agent",
  "typeVersion": 1.7,
  "parameters": {
    "text": "={{ $json.chatInput }}",
    "options": {
      "systemMessage": "Tu es un assistant IA serviable.",
      "maxIterations": 10
    },
    "promptType": "define"
  }
}
```

### Mémoire de Conversation

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

### Outil Code pour Agent

```json
{
  "name": "Custom Tool",
  "type": "@n8n/n8n-nodes-langchain.toolCode",
  "typeVersion": 1.1,
  "parameters": {
    "name": "my_tool",
    "description": "Description de l'outil pour l'IA",
    "jsCode": "try {\n  const result = $input?.param || 'default';\n  return { success: true, data: result };\n} catch (error) {\n  return { error: true, message: error.message };\n}"
  }
}
```

---

## API & Webhook

### Requête HTTP GET

```json
{
  "name": "HTTP GET",
  "type": "n8n-nodes-base.httpRequest",
  "typeVersion": 4.2,
  "parameters": {
    "url": "https://api.example.com/data",
    "method": "GET",
    "responseFormat": "json",
    "options": {}
  }
}
```

### Requête HTTP POST

```json
{
  "name": "HTTP POST",
  "type": "n8n-nodes-base.httpRequest",
  "typeVersion": 4.2,
  "parameters": {
    "url": "https://api.example.com/posts",
    "method": "POST",
    "responseFormat": "json",
    "sendBody": true,
    "specifyBody": "json",
    "jsonBody": {
      "title": "Hello World",
      "content": "Contenu du post"
    }
  }
}
```

### Webhook Trigger

```json
{
  "name": "Webhook Trigger",
  "type": "n8n-nodes-base.webhook",
  "typeVersion": 2,
  "parameters": {
    "path": "incoming-data",
    "httpMethod": "POST",
    "options": {}
  }
}
```

---

## Traitement de Données

### Nœud Set (Edit Fields)

```json
{
  "name": "Set Fields",
  "type": "n8n-nodes-base.set",
  "typeVersion": 3.4,
  "parameters": {
    "options": {},
    "assignments": {
      "assignments": [
        {
          "name": "newField",
          "type": "string",
          "value": "={{ $json.existingField }}"
        }
      ]
    }
  }
}
```

### Nœud IF (Conditionnel)

```json
{
  "name": "Check Status",
  "type": "n8n-nodes-base.if",
  "typeVersion": 2,
  "parameters": {
    "conditions": {
      "conditions": [
        {
          "leftValue": "={{ $json.status }}",
          "rightValue": "success",
          "operator": {
            "type": "string",
            "operation": "equals"
          }
        }
      ],
      "combinator": "and"
    }
  }
}
```

### Nœud Switch

```json
{
  "name": "Route by Category",
  "type": "n8n-nodes-base.switch",
  "typeVersion": 3.2,
  "parameters": {
    "rules": {
      "values": [
        {
          "outputKey": "support",
          "conditions": {
            "conditions": [
              {
                "leftValue": "={{ $json.category }}",
                "rightValue": "support",
                "operator": { "type": "string", "operation": "equals" }
              }
            ]
          }
        }
      ]
    },
    "options": { "fallbackOutput": "extra" }
  }
}
```

### Nœud Code (JavaScript)

```json
{
  "name": "Process Data",
  "type": "n8n-nodes-base.code",
  "typeVersion": 2,
  "parameters": {
    "jsCode": "const results = [];\nfor (const item of items) {\n  const processed = {\n    ...item.json,\n    processed: true,\n    timestamp: new Date().toISOString()\n  };\n  results.push({ json: processed });\n}\nreturn results;"
  }
}
```

---

## Automatisation de Workflow

### Cron Trigger (Planification)

```json
{
  "name": "Daily Schedule",
  "type": "n8n-nodes-base.scheduleTrigger",
  "typeVersion": 1.2,
  "parameters": {
    "rule": {
      "interval": [
        {
          "field": "hours",
          "hoursInterval": 24
        }
      ]
    }
  }
}
```

### Exécuter un Sous-Workflow

```json
{
  "name": "Run Sub-workflow",
  "type": "n8n-nodes-base.executeWorkflow",
  "typeVersion": 1,
  "parameters": {
    "workflowId": "123",
    "waitForCompletion": true
  }
}
```

---

## Intégrations Notables

### Slack

```json
{
  "name": "Send Slack Message",
  "type": "n8n-nodes-base.slack",
  "typeVersion": 2,
  "parameters": {
    "resource": "message",
    "operation": "send",
    "channel": "#general",
    "text": "Message depuis n8n"
  }
}
```

### Google Sheets

```json
{
  "name": "Append to Sheet",
  "type": "n8n-nodes-base.googleSheets",
  "typeVersion": 4.5,
  "parameters": {
    "operation": "append",
    "documentId": { "value": "SHEET_ID" },
    "sheetName": { "value": "Sheet1" }
  }
}
```

---

## Bonnes Pratiques

1. **Gestion des erreurs**: Toujours utiliser `try/catch` dans les nœuds Code
2. **Mémoire**: Utiliser `sessionKey` unique pour chaque utilisateur
3. **Credentials**: Ne jamais hardcoder les clés API
4. **Expressions**: Utiliser `={{ }}` pour les valeurs dynamiques
5. **Documentation**: Ajouter des Sticky Notes pour expliquer le workflow

---

## Connexions entre Nœuds

```json
"connections": {
  "Node1": {
    "main": [[
      { "node": "Node2", "type": "main", "index": 0 }
    ]]
  },
  "AI Model": {
    "ai_languageModel": [[
      { "node": "AI Agent", "type": "ai_languageModel", "index": 0 }
    ]]
  },
  "Memory": {
    "ai_memory": [[
      { "node": "AI Agent", "type": "ai_memory", "index": 0 }
    ]]
  },
  "Tool": {
    "ai_tool": [[
      { "node": "AI Agent", "type": "ai_tool", "index": 0 }
    ]]
  }
}
```