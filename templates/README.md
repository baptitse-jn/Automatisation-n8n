# Templates

Templates et snippets réutilisables pour accélérer la création de workflows.

## Structure

| Dossier/Fichier | Description |
|-----------------|-------------|
| `workflow-template.json` | Template de base pour un nouveau workflow |
| `node-snippets/` | Snippets de nodes réutilisables |

## Utilisation

### Workflow Template

Le fichier `workflow-template.json` contient une structure de base avec :
- Configuration des métadonnées
- Node de démarrage (trigger)
- Commentaires et documentation intégrés

### Node Snippets

Les snippets dans `node-snippets/` sont des configurations de nodes pré-configurées :
- HTTP Request avec retry
- Claude AI Agent
- Error handling pattern
- Data transformation

## Comment contribuer

1. Créer un nouveau fichier dans le dossier approprié
2. Documenter le snippet avec des commentaires
3. Ajouter une entrée dans ce README
