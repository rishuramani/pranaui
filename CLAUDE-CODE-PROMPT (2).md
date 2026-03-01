# PranaOS — Claude Code Build Prompt

## What This Is

You are finishing the UI mockup suite for **PranaOS**, a multi-tenant AI agent platform for agencies/consultants/MSPs. There are 31 completed HTML screen mockups and a master build plan. Your job is to:

1. Audit and fix the existing screens
2. Build the remaining 8 screens
3. Stitch all 39 screens into a navigable clickthrough prototype
4. Fix any inconsistencies as you go

### THIS IS A UI WALKTHROUGH ONLY

This is **not** a real app. There is no backend, no database, no API. Every screen is a standalone HTML file with dummy data and vanilla JS for interactivity (modals, tabs, approve buttons, etc). 

The build plan (`pranaos-build-plan.html`) contains detailed specs including backend tasks, database schemas, and API references — **ignore all of that**. Only use the build plan for:
- Screen names and descriptions
- Feature lists (what should be visible on screen)
- UI component specs
- User flows and navigation between screens

When building new screens, use realistic dummy data that's consistent with what's already in the existing screens. Don't build any real functionality — just make it look and feel right.

### WATCH FOR MISSING CONNECTORS & MISALIGNED SCREENS

These screens were built across 15+ sessions and batch-converted multiple times. Things got shifted, duplicated, and mangled along the way. **Be paranoid.** Specifically watch for:

- **Missing connectors:** Screen A has a button that should go to Screen B, but there's no obvious path. Example: a "View Details" link that alerts instead of linking, or a flow that dead-ends with no way to get to the next logical screen.
- **Misaligned content:** A file named C-05 that actually contains C-06's content. Screen IDs that don't match filenames. Titles that don't match the screen ID badge.
- **Broken flows:** The user journey should make sense. If you're clicking through and something feels wrong — a screen appears out of context, nav doesn't match, data references something that doesn't exist elsewhere — **stop and ask.**
- **Orphaned screens:** Screens that nothing links to, or screens that link to nothing.
- **Data conflicts:** One screen says 9 users, another says 8. One screen calls it "Operations" another calls it "Ops." One screen has an agent called "Maintenance Bot" and another doesn't mention it.

**When you find these issues:**
- Obvious bugs (wrong screen ID, broken div) → just fix them
- Ambiguous design decisions → stop and ask
- Missing screens in a flow → stop and ask
- Data conflicts you're not sure how to resolve → stop and ask

Don't silently paper over problems. If something looks off, say so.

---

## Brand & Design System

### Colors
```
--bg: #faf6f0 (warm linen)
--bg-card: #fffdf9 (warm white)
--bg-elevated: #f0e8dc (sand)
--border: #e2d5c4
--text: #2a1f10 (espresso)
--text-muted: #7a6348
--text-dim: #a89880
--accent: #18856a (emerald green — PranaOS system color)
--accent-bright: #2dd4a0
```

### Client Branding (AMC Theatres as demo client)
```
--client-primary: #c41e3a (AMC red)
--client-primary-light: rgba(196,30,58,0.08)
--client-primary-border: rgba(196,30,58,0.18)
```

### Typography
- **Font:** Plus Jakarta Sans (weights 300-800)
- **Mono:** IBM Plex Mono
- Import: `https://fonts.googleapis.com/css2?family=Plus+Jakarta+Sans:wght@300;400;500;600;700;800&family=IBM+Plex+Mono:wght@400;500;600&display=swap`

### Layout Patterns

**Agency screens (A-01 through A-17):** Left sidebar with PranaOS logo, emerald green accent, agency nav:
```
📊 Command Center
👥 Clients
🤖 Marketplace
🔧 Builder
📊 Analytics
💰 Billing
👥 Team
⚙️ Settings
```

**Client screens (C-04 through C-09+):** Left sidebar with PranaOS logo, AMC Theatres branding, client-primary red accents:
```
📊 Dashboard
🤖 Agents
💬 Chat
📥 Decisions [4]
─────────────
📚 Knowledge
🏢 Departments
👥 Team
⚙️ Settings
```

**Onboarding/Marketing screens (S-01 through S-04, C-01 through C-03, C-08):** No persistent nav — standalone flows.

### Screen ID Badge
Every screen has a fixed-position badge bottom-right:
```html
<div class="screen-id"><strong>X-##</strong> Screen Name</div>
```

---

## Completed Screens (31 files in `/screens/`)

### Marketing/Sales (5)
| File | Screen | Description |
|------|--------|-------------|
| S-01-marketing-site.html | S-01 | Marketing homepage |
| S-01b-partners.html | S-01b | Agency partner page |
| S-02-interactive-demo.html | S-02 | Interactive product demo |
| S-03-pricing.html | S-03 | Pricing page (3 tiers) |
| S-04-signup-checkout.html | S-04 | Signup + Stripe checkout |

### Agency (17)
| File | Screen | Description |
|------|--------|-------------|
| A-01-onboarding-survey.html | A-01 | 3-question onboarding survey |
| A-02-agency-self-setup.html | A-02 | 7-step guided setup wizard |
| A-03-command-center.html | A-03 | Agency command center dashboard |
| A-04-agent-marketplace.html | A-04 | Agent marketplace with deploy flow |
| A-05-client-setup.html | A-05 | Client partition creation wizard |
| A-06-agent-config-integrations.html | A-06 | 5-tab agent config (integrations, KB, behavior, prompt, test) |
| A-07-users-teams.html | A-07 | Department + user management |
| A-08-agency-admin-view.html | A-08 | Agency admin bar on client site |
| A-09-client-billing.html | A-09 | Per-client billing setup |
| A-10-client-management.html | A-10 | Client list/management |
| A-11-decision-inbox-agency.html | A-11 | Cross-client decision inbox |
| A-12-billing-management.html | A-12 | Agency billing dashboard |
| A-13-agent-builder.html | A-13 | Agent builder IDE |
| A-14-agent-clone.html | A-14 | Clone + edit agent |
| A-15-publish-agent.html | A-15 | Publish to marketplace |
| A-16-analytics.html | A-16 | Analytics dashboard |
| A-17-team-management.html | A-17 | Agency team management |

### Client (9)
| File | Screen | Description |
|------|--------|-------------|
| C-01-client-welcome.html | C-01 | Branded welcome screen |
| C-02-integration-auth.html | C-02 | OAuth consent requests |
| C-03-guided-walkthrough.html | C-03 | Client guided walkthrough |
| C-04-client-dashboard.html | C-04 | Client home — agent grid, stats, activity, decisions |
| C-05-agent-gui.html | C-05 | Agent GUI — Final Sale Agent with scan, results table, approve/reject |
| C-06-universal-chat.html | C-06 | Universal chat interface |
| C-07-decision-inbox.html | C-07 | Client decision inbox |
| C-08-user-walkthrough.html | C-08 | User-role walkthrough |
| C-09-department-setup.html | C-09 | Department setup (client admin) |

---

## Remaining Screens to Build (8)

### P1 Screens
| ID | Name | Persona | Notes |
|----|------|---------|-------|
| C-10 | User Management (Client Admin) | Client Admin | Users table, invite modal, edit modal, department assignment. Use AMC data: 9 users across 3 depts (Concessions, Operations, Marketing). Sidebar nav with 👥 Team active. |
| C-11 | Settings (Client Admin) | Client Admin | General settings: company info, notification prefs, connected integrations overview, danger zone (leave org). Sidebar nav with ⚙️ Settings active. |
| S-05 | Login | All | Email/password + SSO options. Clean centered card on warm bg. |
| S-06 | Forgot Password | All | Email input → confirmation message. |
| S-07 | Accept Invite | Client/User | Invite landing page — shows who invited, org name, set password. |
| S-08 | Email Templates | System | Preview of transactional emails: invite, welcome, password reset, decision notification. Show as rendered email previews. |

### P2 Screens
| ID | Name | Persona | Notes |
|----|------|---------|-------|
| A-18 | Audit Log | Agency | Filterable activity log: timestamps, actors, actions, targets. Agency sidebar nav. |
| S-09 | 404 Page | All | Branded 404 with navigation back. |
| S-10 | Maintenance/Error | All | System down page. |

---

## Stitching — Clickthrough Prototype

After all 39 screens exist, create an `index.html` that serves as the prototype hub:

### Requirements
1. **Navigation index** — Grid of all screens grouped by persona (Sales → Agency → Client → System), each linking to the HTML file
2. **In-screen navigation** — Update all `onclick` handlers and `navTo()` functions in existing screens to actually link between files instead of showing `alert()` dialogs
3. **Sidebar links** — Wire sidebar nav items to their corresponding screens:
   - Agency sidebar: Command Center → A-03, Clients → A-10, Marketplace → A-04, Builder → A-13, Analytics → A-16, Billing → A-12, Team → A-17, Settings → (new or alert)
   - Client sidebar: Dashboard → C-04, Agents → C-05, Chat → C-06, Decisions → C-07, Knowledge → (alert), Departments → C-09, Team → C-10, Settings → C-11
4. **Flow continuity** — Key user flows should be clickable end-to-end:
   - **Agency onboarding:** S-01 → S-03 → S-04 → A-01 → A-02 → A-03
   - **Client onboarding:** (invite) → C-01 → C-02 → C-03 → C-04
   - **User onboarding:** (invite) → S-07 → C-08 → C-04
   - **Agent deploy:** A-04 (deploy) → A-06 (config) → C-05 (client sees it)
   - **Decision flow:** C-04 (pending) → C-07 (inbox) → C-05 (in-agent review)
5. **Back navigation** — All back buttons and breadcrumbs should work

### Index Page Design
- Same warm brand (faf6f0 bg, Plus Jakarta Sans)
- PranaOS logo top center
- "PranaOS Clickthrough Prototype" as title
- Screen cards in a grid, grouped by persona
- Each card shows: screen ID, name, description, priority badge
- Click → opens the screen
- Progress indicator: X/39 screens complete

---

## Technical Notes

- Every screen is a **standalone HTML file** — all CSS inline in `<style>`, all JS inline in `<script>`, no external dependencies except Google Fonts
- Keep this pattern for new screens
- All screens should work when opened directly in a browser
- For the stitching, use relative links (`href="C-04-client-dashboard.html"`)
- Mobile responsive: sidebar hides at 600px breakpoint
- Interactive elements (modals, toggles, approve buttons) should work with vanilla JS

---

## CRITICAL: Track Everything As You Go

### Use MEMORY.md as Your Brain
Create and continuously update a `MEMORY.md` file in the project root. Write to it **after every meaningful action** — don't batch it up, don't wait until the end. This is your persistent memory across sessions. Include:

- **Decisions made** — any design, layout, content, or naming decision you make, write it down
- **Issues found and fixed** — what was broken, what you did about it
- **Issues found and NOT fixed** — things that need human input
- **Screen status** — which screens are audited, built, wired, tested
- **Data consistency notes** — user names, department names, agent names, counts — anything that needs to stay in sync across screens
- **Navigation map** — which screen links to which, so you don't break flows when editing
- **Open questions** — anything you need answered before continuing

### Check Off Progress in This File
As you complete work, **edit this prompt file directly** to mark progress. Use checkboxes:

```
- [x] C-10 — Built and tested
- [ ] C-11 — Not started
```

Update the status after every screen is audited, built, or wired. This file is the source of truth for what's done and what isn't. If you pick up work in a new session, read this file first to know where you left off.

### When In Doubt, Write It Down
If you notice something weird — a pattern that doesn't match, data that conflicts, a screen that looks auto-generated — write it in MEMORY.md even if you fix it. Future sessions need to know what happened.

---

## CRITICAL: Audit First, Build Second

Before building anything new, **read and test every existing screen**. Open each HTML file, inspect it, and fix problems before moving forward. This codebase was built across many sessions and has accumulated some inconsistencies.

### Step 0: Full Audit
- [ ] Read every HTML file and verify structure
- [ ] Fix all broken screen IDs, titles, active states
- [ ] Fix all encoding/unicode issues
- [ ] Verify all agency screens have identical sidebar nav
- [ ] Verify all client screens have identical sidebar nav
- [ ] Verify AMC data consistency (users, depts, agents)
- [ ] Test all modals and interactive JS
- [ ] Create AUDIT-LOG.md with findings
1. **Open every HTML file** and verify:
   - Screen ID badge matches filename
   - Title tag matches screen identity
   - Correct nav pattern (agency sidebar / client sidebar / standalone)
   - Active nav state matches the screen's purpose
   - Content is present and complete (not just a nav shell)
   - CSS variables are consistent across same-persona screens
   - No broken unicode, escaped characters, or encoding issues
   - Modals, buttons, and interactive JS actually work
   - Div structure is balanced (opens = closes)

2. **Flag and fix anything broken** — don't ask, just fix obvious issues like:
   - Wrong screen IDs
   - Missing content
   - Broken active states
   - Inconsistent nav items between screens of the same persona
   - Dead JS functions
   - CSS that doesn't match the design system

3. **Check cross-screen consistency:**
   - All agency screens should have identical sidebar nav items and structure
   - All client screens should have identical sidebar nav items and structure
   - Color variables should be consistent within each persona group
   - User avatars, names, and roles should be consistent (Jessica Miller = Admin for client screens, etc.)
   - AMC Theatres branding consistent across all client screens
   - Department names consistent: Concessions, Operations, Marketing (3 AMC depts)
   - User roster consistent: 9 users across those 3 depts

4. **Document what you find** — create an `AUDIT-LOG.md` with every issue found and whether you fixed it or need input

### Step 1: Ask Questions
After the audit, if anything is ambiguous or requires a design decision, **stop and ask**. Examples:
- "C-06 and C-07 have sidebar nav but the content areas look like they were auto-generated from a batch script — should I rebuild the content from the build plan specs?"
- "A-08 agency admin view is pretty minimal — want me to flesh it out?"
- "The pricing on S-03 says $497/seat — is that still current?"

Don't guess on product decisions. Do fix obvious bugs without asking.

### Step 2: Build Remaining Screens
- [ ] C-10 User Management (Client Admin)
- [ ] C-11 Settings (Client Admin)
- [ ] S-05 Login
- [ ] S-06 Forgot Password
- [ ] S-07 Accept Invite
- [ ] S-08 Email Templates
- [ ] A-18 Audit Log
- [ ] S-09 404 Page
- [ ] S-10 Maintenance/Error Page

### Step 3: Stitch & Wire Navigation
- [ ] Create index.html prototype hub
- [ ] Wire all agency sidebar links across A-screens
- [ ] Wire all client sidebar links across C-screens
- [ ] Wire onboarding flows (S-01→S-04→A-01→A-02→A-03)
- [ ] Wire client onboarding (C-01→C-02→C-03→C-04)
- [ ] Wire user onboarding (S-07→C-08→C-04)
- [ ] Wire agent deploy flow (A-04→A-06→C-05)
- [ ] Wire decision flow (C-04→C-07→C-05)
- [ ] Replace all remaining alert() navTo calls with real links

### Step 4: Final Smoke Test
- [ ] Click through agency onboarding flow end-to-end
- [ ] Click through client onboarding flow end-to-end
- [ ] Click through user onboarding flow end-to-end
- [ ] Click through agent deploy flow end-to-end
- [ ] Click through decision flow end-to-end
- [ ] Verify every sidebar link on every screen
- [ ] Verify every back button
- [ ] Verify every modal open/close
- [ ] Create TEST-RESULTS.md

### Step 5: Prepare for Vercel Deploy
- [ ] Ensure index.html is at project root
- [ ] All screen files in a flat `/screens/` directory (no nested folders)
- [ ] All links use relative paths that work from Vercel's static hosting
- [ ] No absolute paths, no localhost references, no file:// links
- [ ] Add a `vercel.json` with rewrites so `/` serves index.html and `/screens/*` serves screen files
- [ ] Test that opening index.html locally and clicking through works identically to how it will on Vercel
- [ ] Final check: no external dependencies except Google Fonts CDN (which works everywhere)

We are deploying this to **Vercel** as a static site when done. Keep that in mind throughout — everything needs to work as flat static HTML files served from a CDN. No server-side anything.

---

## Reference

- **Build plan:** `pranaos-build-plan.html` — has feature specs for every screen. **Use only the Features sections for UI guidance. Ignore all "Developer Tasks" sections** — those are backend/database tasks for a future real build, not relevant here.
- **Existing screens:** Study C-04 and A-03 as reference for layout patterns, CSS variables, and component styles
- **Client sidebar pattern:** Copy from C-04 or C-09 for any new client screen
- **Agency sidebar pattern:** Copy from A-03 or A-16 for any new agency screen
- **All data is fake** — use realistic dummy data consistent with what's already in the screens. The AMC Theatres demo has: 9 users, 3 departments (Concessions, Operations, Marketing), 6 agents (Final Sale Agent, Paid Ads Manager, Knowledge Q&A, Revenue Reporter, Email Drafter, Churn Predictor). Keep it consistent.
