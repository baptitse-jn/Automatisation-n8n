# Commercial / Ventes

Workflows d'automatisation pour les équipes commerciales et ventes.

## Catégories

| Dossier | Description | Cas d'usage |
|---------|-------------|-------------|
| `crm/` | Automatisation CRM | Sync contacts, mise à jour deals |
| `lead-generation/` | Génération de leads | Scraping, enrichissement, qualification |
| `sales-pipeline/` | Pipeline de ventes | Suivi deals, alertes, reporting |
| `prospection/` | Prospection commerciale | Séquences, outreach, follow-up |

## Workflows disponibles

| Workflow | Description | Trigger | Intégrations |
|----------|-------------|---------|--------------|
| [Lead Enrichment Pipeline](./lead-generation/Lead_Enrichment_Pipeline.json) | Pipeline d'enrichissement et scoring de leads | Webhook | Apollo, Clearbit, HubSpot, Slack |
| [Follow Up Sequence Automation](./prospection/Follow_Up_Sequence_Automation.json) | Séquence de relance automatique | Schedule (quotidien) | HubSpot, Claude, Gmail, Slack |
| [Proposal Generator](./prospection/Proposal_Generator.json) | Génération automatique de propositions commerciales | Webhook | Notion, Claude, Google Docs, Gmail |
| [Meeting Scheduler Bot](./crm/Meeting_Scheduler_Bot.json) | Bot de prise de rendez-vous automatique | Webhook | HubSpot, Google Calendar, Gmail, Slack |
| [Deal Stage Notifier](./sales-pipeline/Deal_Stage_Notifier.json) | Notifications automatiques sur changement de pipeline | Schedule (horaire) | HubSpot, Claude, Slack, Notion |

## Intégrations courantes

- **CRM** : HubSpot, Salesforce, Pipedrive, Folk
- **Enrichissement** : Clearbit, Apollo, PhantomBuster
- **Email** : Lemlist, Instantly, Woodpecker
- **LinkedIn** : Sales Navigator, LinkedIn API

## Comment ajouter un workflow

1. Placer le fichier `.json` dans le sous-dossier approprié
2. Créer un `README.md` dans le même dossier avec la documentation
3. Mettre à jour ce fichier avec les infos du workflow
