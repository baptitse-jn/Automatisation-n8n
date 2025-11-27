# ✅ Bonnes Pratiques n8n

## 1. Structure du Workflow

### Organisation
- Utiliser des **Sticky Notes** pour documenter chaque section
- Grouper les nœuds par fonctionnalité
- Nommer clairement chaque nœud en français

### Conventions de Nommage
```
✔️ Bon:  "Réception Message Chat"
✔️ Bon:  "Traitement Données Utilisateur"
❌ Mauvais: "Node1"
❌ Mauvais: "HTTP Request"
```

## 2. Gestion des Erreurs

### Pattern Try/Catch
```javascript
try {
  const result = await process($input);
  return { success: true, data: result };
} catch (error) {
  return {
    success: false,
    error: error.message,
    timestamp: new Date().toISOString()
  };
}
```

### Utiliser onError
```json
{
  "onError": "continueRegularOutput"
}
```

## 3. Sécurité

### Credentials
- **JAMAIS** de clés API en dur dans le code
- Utiliser les credentials n8n
- Rotation régulière des clés

### Validation des Entrées
```javascript
if (!$input?.required_field) {
  return { error: 'Champ requis manquant' };
}
```

## 4. Performance

### Optimisations
- Limiter les appels API inutiles
- Utiliser le batch processing
- Activer le cache quand possible

### Mémoire AI Agent
- `contextWindowLength: 20` maximum recommandé
- Utiliser `sessionKey` unique par utilisateur

## 5. Documentation

### Sticky Notes Obligatoires
- Note d'introduction du workflow
- Note par section fonctionnelle
- Note de configuration/setup

### Commentaires dans le Code
```javascript
// Traitement des données utilisateur
// Entrée: { name, email, data }
// Sortie: { processed: true, result }
```

## 6. Tests

### Avant Déploiement
- [ ] Tester avec des données réelles
- [ ] Vérifier la gestion des erreurs
- [ ] Valider les timeouts
- [ ] Tester les cas limites

## 7. Maintenance

### Versionnement
- Utiliser `versionId` dans les workflows
- Documenter les changements majeurs
- Garder des backups
