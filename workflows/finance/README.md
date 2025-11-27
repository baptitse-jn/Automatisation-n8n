# Finance

Workflows d'automatisation pour la gestion financière.

## Catégories

| Dossier | Description | Cas d'usage |
|---------|-------------|-------------|
| `invoicing/` | Facturation | Génération factures, relances, paiements |
| `expense-tracking/` | Suivi des dépenses | Notes de frais, catégorisation |
| `reporting/` | Reporting financier | Tableaux de bord, prévisions |

## Workflows disponibles

| Workflow | Description | Trigger | Intégrations |
|----------|-------------|---------|--------------|
| [Expense Tracker AI Agent](./expense-tracking/Expense_Tracker_AI_Agent.json) | Agent IA pour suivi des dépenses | Manuel | Claude |
| [Invoice Generator](./invoicing/Invoice_Generator.json) | Génération automatique de factures | Webhook | Notion, Claude, Google Docs, Email |
| [Payment Reminder Sequence](./invoicing/Payment_Reminder_Sequence.json) | Séquence de relance de paiement | Schedule (quotidien) | Notion, Claude, Email, Slack |
| [Expense Categorizer](./expense-tracking/Expense_Categorizer.json) | Catégorisation automatique des dépenses | Webhook | Claude, Notion, Slack |
| [Monthly Financial Report](./reporting/Monthly_Financial_Report.json) | Rapport financier mensuel automatisé | Schedule (1er du mois) | Notion, Claude, Google Sheets, Slack |
| [Budget Alert Monitor](./reporting/Budget_Alert_Monitor.json) | Surveillance et alertes budgétaires | Schedule (quotidien) | Notion, Claude, Slack, Email |

## Intégrations courantes

- **Comptabilité** : QuickBooks, Xero, Pennylane
- **Facturation** : Stripe, PayPal, Mollie
- **Banque** : Plaid, Bridge API
- **Expense** : Spendesk, Expensify

## Comment ajouter un workflow

1. Placer le fichier `.json` dans le sous-dossier approprié
2. Créer un `README.md` dans le même dossier avec la documentation
3. Mettre à jour ce fichier avec les infos du workflow
