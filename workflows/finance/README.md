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

## Intégrations courantes

- **Comptabilité** : QuickBooks, Xero, Pennylane
- **Facturation** : Stripe, PayPal, Mollie
- **Banque** : Plaid, Bridge API
- **Expense** : Spendesk, Expensify

## Comment ajouter un workflow

1. Placer le fichier `.json` dans le sous-dossier approprié
2. Créer un `README.md` dans le même dossier avec la documentation
3. Mettre à jour ce fichier avec les infos du workflow
