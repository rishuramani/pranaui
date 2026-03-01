# PranaOS Prototype — Memory

## Project Structure

- `/index.html` — Prototype hub with 40 screen cards grouped by persona
- `/Screens/` — 40 standalone HTML files (capital S)
- `/brand.html` — Brand guide (colors, typography, accessibility)
- `/vercel.json` — Vercel static deployment config

## Screen Inventory (40 total)

### Marketing & Sales (10)
| ID | File | Description |
|----|------|-------------|
| S-01 | S-01-marketing-site.html | Landing page with hero, agent showcase |
| S-01b | S-01b-partners.html | Partner agency directory |
| S-02 | S-02-interactive-demo.html | Live agent playground |
| S-03 | S-03-pricing.html | Three-tier pricing |
| S-04 | S-04-signup-checkout.html | Sign-up with payment |
| S-05 | S-05-login.html | Email/password + SSO login |
| S-06 | S-06-forgot-password.html | Password reset flow |
| S-07 | S-07-accept-invite.html | User invitation acceptance |
| S-08 | S-08-email-templates.html | 4 transactional email previews |
| S-09 | S-09-404.html | 404 error page |

### Agency (18)
| ID | File | Description |
|----|------|-------------|
| A-01 | A-01-onboarding-survey.html | Agency profile survey |
| A-02 | A-02-agency-self-setup.html | Connectors + branding setup |
| A-03 | A-03-command-center.html | **Canonical agency sidebar source** |
| A-04 | A-04-agent-marketplace.html | Browse/deploy agents |
| A-05 | A-05-client-setup.html | New client wizard |
| A-06 | A-06-agent-config-integrations.html | Agent config + data sources |
| A-07 | A-07-users-teams.html | Client user management |
| A-08 | A-08-agency-admin-view.html | View client site as admin |
| A-09 | A-09-client-billing.html | Per-client billing config |
| A-10 | A-10-client-management.html | All clients table |
| A-11 | A-11-decision-inbox-agency.html | Cross-client decision queue |
| A-12 | A-12-billing-management.html | Agency-wide billing/MRR |
| A-13 | A-13-agent-builder.html | Visual agent IDE |
| A-14 | A-14-agent-clone.html | Fork marketplace agents |
| A-15 | A-15-publish-agent.html | Agent library + publish |
| A-16 | A-16-analytics.html | Cross-client analytics |
| A-17 | A-17-team-management.html | Agency team roster |
| A-18 | A-18-audit-log.html | Filterable activity log |

### Client (11)
| ID | File | Description |
|----|------|-------------|
| C-01 | C-01-client-welcome.html | First-time welcome |
| C-02 | C-02-integration-auth.html | OAuth/API key setup |
| C-03 | C-03-guided-walkthrough.html | Onboarding tour |
| C-04 | C-04-client-dashboard.html | **Canonical client sidebar source** |
| C-05 | C-05-agent-gui.html | Individual agent interface |
| C-06 | C-06-universal-chat.html | Cross-agent chat |
| C-07 | C-07-decision-inbox.html | Approve/reject decisions |
| C-08 | C-08-user-walkthrough.html | Invited user onboarding |
| C-09 | C-09-department-setup.html | Department config |
| C-10 | C-10-user-management.html | Team + invite management |
| C-11 | C-11-settings.html | Org settings |

### System (1)
| ID | File | Description |
|----|------|-------------|
| S-10 | S-10-maintenance.html | Maintenance page |

## Navigation Architecture

- **Per-file `navTo()` functions** — each screen has its own route map (no shared JS)
- **Agency sidebar:** 9 items in 3 sections (Main, Manage, System)
- **Client sidebar:** 8 items (Dashboard, Agents, Chat, Decisions, Departments, Team, Settings, Knowledge)
- **Standalone screens** (no sidebar): S-series, A-01, A-02, A-08, A-13, A-14

## Dummy Data (AMC Theatres)

- **Agency org:** Prana IQ, owner Rishabh K.
- **Client org:** AMC Theatres, admin Jessica Miller (JM)
- **9 users**, 3 departments (Concessions, Operations, Marketing)
- **6 agents:** Final Sale Agent, Paid Ads Manager, Knowledge Q&A, Revenue Reporter, Email Drafter, Churn Predictor

## Design Tokens

- Background: `#faf6f0` / Card: `#fffdf9` / Elevated: `#f0e8dc`
- Text: `#2a1f10` / Muted: `#7a6348` / Dim: `#a89880`
- Accent: `#18856a` (AA on light bg) / Bright: `#2dd4a0` (icons only, not text)
- Fonts: Plus Jakarta Sans (UI), IBM Plex Mono (code/data)
- Radii: 14px / 10px / 8px

## Key Flows

1. **Agency onboarding:** S-01 → S-03 → S-04 → A-01 → A-02 → A-03
2. **Client onboarding:** C-01 → C-02 → C-03 → C-04
3. **User onboarding:** S-07 → C-08 → C-04
4. **Agent deploy:** A-04 → A-06 → A-15 → C-05
5. **Decision flow:** C-04 → C-07 → C-05
