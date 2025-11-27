# Opérations

Workflows d'automatisation pour les opérations et la gestion de projet.

## Catégories

| Dossier | Description | Cas d'usage |
|---------|-------------|-------------|
| `project-management/` | Gestion de projet | Sync tâches, notifications, reporting |
| `task-automation/` | Automatisation tâches | Calendrier, rappels, routines |
| `reporting/` | Reporting opérationnel | Dashboards, KPIs, alertes |
| `data-sync/` | Synchronisation données | ETL, migrations, backups |

## Workflows disponibles

| Workflow | Description | Trigger | Intégrations |
|----------|-------------|---------|--------------|
| [Google Calendar AI Agent](./task-automation/Google_Calendar_AI_Agent.json) | Agent IA pour gestion calendrier | Manuel | Google Calendar, Claude |
| [Project Status Sync](./data-sync/Project_Status_Sync.json) | Synchronisation de statut de projets entre outils | Schedule (15 min) | Notion, Asana, Slack |
| [Daily Standup Bot](./reporting/Daily_Standup_Bot.json) | Bot de standup quotidien automatique | Schedule (9h) | Slack, Notion, Claude |
| [Inventory Alert System](./reporting/Inventory_Alert_System.json) | Système d'alertes sur les niveaux de stock | Schedule (horaire) | Airtable, Claude, Slack, Email |
| [Document Approval Flow](./task-automation/Document_Approval_Flow.json) | Workflow d'approbation de documents | Webhook | Notion, Slack, Email |
| [Meeting Notes Processor](./task-automation/Meeting_Notes_Processor.json) | Traitement automatique des notes de réunion | Webhook | Claude, Notion, Slack, Asana |

## Intégrations courantes

- **Project Management** : Notion, Asana, Monday, Linear
- **Calendrier** : Google Calendar, Outlook Calendar
- **Storage** : Google Drive, Dropbox, OneDrive
- **Database** : Airtable, Supabase, PostgreSQL

## Comment ajouter un workflow

1. Placer le fichier `.json` dans le sous-dossier approprié
2. Créer un `README.md` dans le même dossier avec la documentation
3. Mettre à jour ce fichier avec les infos du workflow
