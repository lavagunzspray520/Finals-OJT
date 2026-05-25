# Agent Guide — Erovoutika CMS

This file tells AI coding agents (Kiro, Codex, Cursor, Claude, etc.) how to work
effectively in this repository. Keep it short, specific, and up to date.

## Project Overview

- **Name:** Erovoutika CMS
- **Purpose:** A lightweight, Firebase-backed content management system for the Erovoutika Automation & Robotics marketing site. Built as a Finals OJT group project.
- **Owner:** [@lavagunzspray520](https://github.com/lavagunzspray520)
- **Status:** Work in progress

## Architecture

```
┌──────────────┐       setDoc / updateDoc       ┌─────────────────────────────────────────┐
│  admin.html  │ ─────────────────────────────► │  Firestore: sections/{name}             │
│  (Admin UI)  │                                 │  name ∈ {about, services, portfolio,    │
└──────┬───────┘                                 │           awards, partners}             │
       │                                         └────────────────────┬────────────────────┘
       │  BroadcastChannel('erovoutika-cms')                          │ getDoc
       ▼                                                              ▼
┌──────────────────┐         imports         ┌────────────────────────────┐
│  index4(1).html  │ ◄───────────────────── │  erovoutika-cms.js          │
│  (Public site)   │                         │  (Hydration / live-update)  │
└──────────────────┘                         └────────────────────────────┘
```

**Data flow:**
1. Admin signs in via Google OAuth → edits a section → saves to Firestore.
2. Admin broadcasts a `{ section, at }` message via `BroadcastChannel`.
3. `erovoutika-cms.js` (loaded by the public page) listens and re-hydrates only the changed section from Firestore — no full-page reload needed.

## Repository Structure

```
Finals-OJT/
├── README.md            # Project overview
├── agent.md             # This file — guidance for AI agents
├── skills.md            # OJT skills, technologies, and progress log
├── admin.html           # Admin console (auth + section editors)
├── erovoutika-cms.js    # Live-site hydration script (ES module)
├── index4(1).html       # Public marketing site
└── File3.zip            # Original archive (should be removed)
```

## Tech Stack

| Layer | Technology |
|-------|-----------|
| Languages | HTML5, CSS3 (custom properties, light/dark themes), Vanilla JavaScript (ES Modules) |
| Backend-as-a-Service | Firebase v12.12.1 — Auth, Firestore, Storage |
| Auth | Google OAuth via `signInWithPopup` |
| Database | Cloud Firestore (NoSQL document store) |
| File Storage | Firebase Storage (image uploads) |
| Cross-tab sync | `BroadcastChannel` API |
| Fonts | Google Fonts (Space Grotesk, DM Sans, Inter), CDN Fonts (ICA Rubrik, Poppins) |

## Run Locally

```bash
# Any static file server works — the site is pure client-side
python3 -m http.server 8080
# or
npx serve .

# Then open:
#   Public site  → http://localhost:8080/index4(1).html
#   Admin panel  → http://localhost:8080/admin.html
```

No build step, no bundler, no `npm install` required.

## Common Commands

| Task | Command |
|------|---------|
| Serve locally | `python3 -m http.server 8080` |
| Lint HTML | `npx htmlhint "*.html"` *(optional, not yet configured)* |
| Deploy | Upload files to any static host (Firebase Hosting, Netlify, Vercel, GitHub Pages) |

## Key Contracts (do NOT break these without updating both sides)

### 1. Section-name contract
The following names are used as:
- Firestore document IDs (`sections/{name}`)
- `HYDRATORS` object keys in `erovoutika-cms.js`
- `BroadcastChannel` message payloads from `admin.html`

```
about | services | portfolio | awards | partners
```

Renaming any section requires changes in **both** `admin.html` and `erovoutika-cms.js`.

### 2. DOM selector contract
Hydrators in `erovoutika-cms.js` target specific selectors in `index4(1).html`:

| Hydrator | Target selectors |
|----------|-----------------|
| `hydrateAbout` | `#aboutImg`, text containers inside the About section |
| `hydrateServices` | `#stackRight` |
| `hydratePortfolio` | `.gallery-grid` |
| `hydrateAwards` | `.awards-grid` |
| `hydratePartners` | `.marquee-track` |

Do **not** rename or remove these IDs/classes without updating the hydrator functions.

### 3. Firebase config
Both `admin.html` and `erovoutika-cms.js` contain an identical `firebaseConfig` object pointing to project `erovoutika-cms-b2f23`. If one changes, the other must too.

## Coding Conventions

- Pure vanilla JS — no frameworks, no bundlers.
- ES module imports via CDN (`https://www.gstatic.com/firebasejs/...`).
- CSS lives inside `<style>` tags in the HTML files (no external stylesheets yet).
- Use clear, descriptive names; prefer readability over cleverness.
- Add comments only where intent is non-obvious.

## Git Workflow

- `main` is the default branch — do **not** force-push or rewrite history.
- Create feature branches: `git checkout -b feature/<short-name>`.
- Commit messages: short imperative subject, e.g. `Add awards hydrator`.
- Open a Pull Request and request review before merging.

## Instructions for AI Agents

When working in this repo, agents should:

1. **Read `README.md`, `agent.md`, and `skills.md` first** to gather context.
2. **Never push directly to `main`.** Always use a branch + PR.
3. **Respect the contracts above** — section names, DOM selectors, Firebase config must stay in sync across files.
4. **Don't rotate or remove `firebaseConfig` keys** without coordinating; security depends on Firestore rules (not in this repo yet).
5. **Keep changes scoped.** Don't refactor unrelated code in the same PR.
6. **Update documentation** when behavior or structure changes.
7. **Ask before destructive operations** (force-push, history rewrite, deleting files).
8. **Match existing code style** — inline CSS, ES modules, no build tools.

## Known Issues / Technical Debt

- [ ] `index4(1).html` has parentheses in the filename — fragile in URLs and CLI tooling. Should be renamed to `index.html`.
- [ ] `File3.zip` is committed alongside its extracted contents — redundant; should be removed from git history.
- [ ] No `.gitignore` — should ignore OS files, editor configs, etc.
- [ ] Firestore security rules are not in the repo — should be added for auditability.
- [ ] All CSS is inline — extracting to external `.css` files would improve maintainability.

## Out of Scope

- Production credentials, secrets, or `.env` files must never be committed.
- Do not add large binary assets without discussion.
- Firestore security rules are managed in the Firebase console (not yet version-controlled here).

## Contact

- Repository owner: [@lavagunzspray520](https://github.com/lavagunzspray520)
