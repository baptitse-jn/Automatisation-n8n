# Customer Service

Workflows d'automatisation pour le service client.

## Catégories

| Dossier | Description | Cas d'usage |
|---------|-------------|-------------|
| `support-tickets/` | Gestion tickets | Triage, routage, escalade |
| `chatbots/` | Chatbots & IA | Réponses automatiques, FAQ |
| `feedback/` | Retours clients | NPS, avis, satisfaction |

## Workflows disponibles

| Workflow | Description | Trigger | Intégrations |
|----------|-------------|---------|--------------|
| [Ticket Triage AI](./support-tickets/Ticket_Triage_AI.json) | Triage automatique des tickets avec IA | Webhook | Claude, Zendesk, Notion, Slack |
| [Refund Processor](./support-tickets/Refund_Processor.json) | Traitement automatique des demandes de remboursement | Webhook | Claude, Stripe, Notion, Email, Slack |
| [Auto Response Bot](./chatbots/Auto_Response_Bot.json) | Bot de réponse automatique intelligent | Webhook | Claude, Notion, Email |
| [NPS Survey Automation](./feedback/NPS_Survey_Automation.json) | Envoi automatique de sondages NPS | Schedule (quotidien) | Notion, Claude, Typeform, Email, Slack |
| [Customer Health Score](./feedback/Customer_Health_Score.json) | Calcul automatique du score de santé client | Schedule (quotidien) | Notion, Claude, HubSpot, Slack |

## Intégrations courantes

- **Helpdesk** : Zendesk, Intercom, Freshdesk, Crisp
- **Chat** : Tidio, LiveChat, Drift
- **Feedback** : Typeform, SurveyMonkey, Hotjar
- **IA** : Claude, OpenAI, Custom LLM

## Comment ajouter un workflow

1. Placer le fichier `.json` dans le sous-dossier approprié
2. Créer un `README.md` dans le même dossier avec la documentation
3. Mettre à jour ce fichier avec les infos du workflow
