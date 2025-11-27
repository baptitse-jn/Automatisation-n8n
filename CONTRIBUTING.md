# Guide de contribution

Merci de contribuer à ce projet ! Voici les guidelines pour ajouter des workflows et de la documentation.

## Structure des contributions

### Ajouter un workflow

1. **Identifier le domaine** approprié dans `workflows/`
2. **Créer un sous-dossier** si le cas d'usage est nouveau
3. **Ajouter le fichier JSON** du workflow
4. **Créer un README.md** dans le même dossier

### Structure d'un README de workflow

```markdown
# Nom du Workflow

Description courte.

## Objectif

Quel problème ce workflow résout.

## Architecture

Description du flow et des nodes utilisés.

## Prérequis

- Credential 1
- Credential 2

## Configuration

1. Étape 1
2. Étape 2

## Trigger

- Type : Schedule / Webhook / Manuel
- Fréquence : ...

## Limitations

- Point d'attention 1
- Point d'attention 2
```

## Conventions de nommage

### Fichiers JSON
- Utiliser PascalCase : `Mon_Workflow_Name.json`
- Être descriptif : `Email_Welcome_Sequence.json`

### Dossiers
- Utiliser kebab-case : `email-automation/`
- Être concis : `crm/`, `social-media/`

## Bonnes pratiques

### Dans les workflows

1. **Documenter avec des Sticky Notes** - Ajouter des notes explicatives dans le workflow
2. **Nommer les nodes clairement** - `Fetch Feedly Articles` plutôt que `HTTP Request`
3. **Gérer les erreurs** - Ajouter des branches d'erreur
4. **Ne pas hardcoder les credentials** - Utiliser les credentials n8n

### Dans le code

1. **Pas de secrets** - Ne jamais commiter d'API keys ou tokens
2. **JSON valide** - Vérifier que le JSON est bien formaté
3. **Tester** - S'assurer que le workflow fonctionne

## Process de Pull Request

1. Fork le repo
2. Créer une branche : `feat/nom-du-workflow`
3. Ajouter le workflow et sa documentation
4. Mettre à jour le README du domaine
5. Soumettre la PR avec une description claire

## Questions ?

Ouvrir une issue sur GitHub pour toute question.
