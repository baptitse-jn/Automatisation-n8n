# Marketing

Workflows d'automatisation pour les opérations marketing.

## Catégories

| Dossier | Description | Cas d'usage |
|---------|-------------|-------------|
| `email-automation/` | Automatisation des campagnes email | Newsletters, séquences, drip campaigns |
| `social-media/` | Gestion des réseaux sociaux | Publication, planification, analytics |
| `seo/` | Optimisation SEO | Audit, suivi positions, analyse |
| `content-creation/` | Création de contenu | Génération, repurposing, traduction |
| `analytics/` | Analyse marketing | Dashboards, reporting, KPIs |

## Workflows disponibles

| Workflow | Description | Trigger | Intégrations |
|----------|-------------|---------|--------------|
| [Newsletter Weekly Automation](./email-automation/Newsletter_Weekly_Automation.json) | Génération automatique de newsletter hebdomadaire | Schedule (Lundi 8h) | Feedly, Claude, Mailchimp, Slack |
| [Lead Magnet Delivery](./email-automation/Lead_Magnet_Delivery.json) | Livraison automatique de lead magnets | Webhook | Notion, Gmail, Slack |
| [Social Media Post Scheduler](./social-media/Social_Media_Post_Scheduler.json) | Planification et publication sur les réseaux sociaux | Schedule (quotidien) | Claude, Buffer, Notion, Slack |
| [SEO Content Generator](./seo/SEO_Content_Generator.json) | Génération de contenu optimisé SEO | Schedule (hebdo) | Google Search Console, Brave Search, Claude, Notion |
| [Campaign Performance Report](./analytics/Campaign_Performance_Report.json) | Rapport de performance des campagnes marketing | Schedule (Lundi 9h) | Google Analytics, HubSpot, Claude, Notion, Slack |

## Intégrations courantes

- **Email** : Mailchimp, Brevo, SendGrid
- **Social** : LinkedIn, Twitter/X, Instagram, Buffer
- **Analytics** : Google Analytics, Plausible
- **CMS** : WordPress, Webflow, Notion

## Comment ajouter un workflow

1. Placer le fichier `.json` dans le sous-dossier approprié
2. Créer un `README.md` dans le même dossier avec la documentation
3. Mettre à jour ce fichier avec les infos du workflow
