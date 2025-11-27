# Configuration

Fichiers de configuration partagés et templates de credentials.

## Fichiers

| Fichier | Description |
|---------|-------------|
| `credentials-template.md` | Template pour documenter les credentials |
| `.env.example` | Exemple de variables d'environnement |

## Variables d'environnement

Créer un fichier `.env` à la racine de votre installation n8n :

```bash
# Copier le template
cp .env.example .env

# Éditer avec vos valeurs
nano .env
```

## Credentials partagés

Les credentials ne doivent **jamais** être committés dans le repo.

Pour partager une configuration :
1. Documenter les credentials nécessaires dans le README du workflow
2. Utiliser des noms de credentials cohérents dans l'équipe
3. Partager les credentials via un gestionnaire de secrets (1Password, Vault, etc.)
