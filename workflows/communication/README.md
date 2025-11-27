# Communication

Workflows d'automatisation pour la communication interne et externe.

## Catégories

| Dossier | Description | Cas d'usage |
|---------|-------------|-------------|
| `internal/` | Communication interne | Notifications équipe, onboarding |
| `external/` | Communication externe | Newsletters, annonces, press release |
| `social-listening/` | Écoute sociale | Monitoring mentions, sentiment analysis |
| `pr-relations/` | Relations presse/publiques | Suivi médias, contacts journalistes |

## Workflows disponibles

| Workflow | Description | Trigger | Intégrations |
|----------|-------------|---------|--------------|
| [Internal Announcement Broadcaster](./internal/Internal_Announcement_Broadcaster.json) | Diffusion d'annonces internes multi-canaux | Webhook | Notion, Claude, Slack, Email |
| [Employee Onboarding Comms](./internal/Employee_Onboarding_Comms.json) | Communication automatique pour l'onboarding | Webhook | Notion, Gmail, Slack, Google Calendar |
| [Crisis Communication Alert](./internal/Crisis_Communication_Alert.json) | Système d'alerte de communication de crise | Webhook | Claude, Slack, Email, SMS |
| [Social Listening Alert](./social-listening/Social_Listening_Alert.json) | Alertes de monitoring des réseaux sociaux | Schedule (horaire) | Twitter, Brave Search, Claude, Notion, Slack |
| [Press Release Distributor](./external/Press_Release_Distributor.json) | Distribution automatique de communiqués de presse | Webhook | Notion, Claude, Email, Slack |

## Intégrations courantes

- **Messaging** : Slack, Teams, Discord
- **Email** : Gmail, Outlook
- **Monitoring** : Mention, Brand24, Google Alerts
- **PR** : Cision, Muck Rack

## Comment ajouter un workflow

1. Placer le fichier `.json` dans le sous-dossier approprié
2. Créer un `README.md` dans le même dossier avec la documentation
3. Mettre à jour ce fichier avec les infos du workflow
