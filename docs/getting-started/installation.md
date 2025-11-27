# Installation

Guide d'installation de n8n et configuration de l'environnement.

## Prérequis

- Node.js 18+ ou Docker
- Un compte n8n Cloud (optionnel)

## Options d'installation

### Option 1 : n8n Cloud (Recommandé pour débuter)

1. Créer un compte sur [n8n.io](https://n8n.io)
2. Accéder à votre instance cloud
3. Importer les workflows depuis ce repo

### Option 2 : Docker (Recommandé pour production)

```bash
docker run -it --rm \
  --name n8n \
  -p 5678:5678 \
  -v ~/.n8n:/home/node/.n8n \
  n8nio/n8n
```

### Option 3 : npm

```bash
npm install n8n -g
n8n start
```

## Configuration post-installation

1. Accéder à `http://localhost:5678`
2. Créer un compte admin
3. Configurer les credentials (voir [Configuration](./configuration.md))

## Importer un workflow

1. Ouvrir n8n
2. Aller dans **Workflows** > **Import from File**
3. Sélectionner le fichier `.json` du workflow
4. Configurer les credentials manquants
5. Activer le workflow

## Ressources

- [Documentation officielle n8n](https://docs.n8n.io/)
- [Forum communautaire](https://community.n8n.io/)
