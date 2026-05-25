# Skills — Erovoutika CMS OJT Project

A living record of skills, tools, and competencies developed during this OJT.
Update this file regularly — it doubles as a portfolio and a study log.

---

## Technical Skills

### Programming Languages

| Language | Level (1–5) | Where Used |
|----------|-------------|------------|
| HTML5 | 4 | `index4(1).html`, `admin.html` — semantic markup, forms, media |
| CSS3 | 4 | Inline styles in both HTML files — custom properties, light/dark themes, responsive layout, animations |
| JavaScript (ES Modules) | 4 | `erovoutika-cms.js`, inline `<script>` in `admin.html` — async/await, DOM manipulation, Firebase SDK |

### Frameworks, SDKs & Libraries

| Technology | Level (1–5) | Where Used |
|------------|-------------|------------|
| Firebase Auth (Google OAuth) | 3 | `admin.html` — `signInWithPopup`, `onAuthStateChanged`, sign-out flow |
| Cloud Firestore | 4 | Both files — `setDoc`, `getDoc`, `updateDoc`, `deleteDoc`, `getDocs`, `collection` |
| Firebase Storage | 3 | `admin.html` — `uploadBytesResumable`, `getDownloadURL` for image uploads |
| Firebase Web SDK v12.12.1 | 4 | CDN ES-module imports across all JS |

### Browser APIs & Patterns

| API / Pattern | Level (1–5) | Where Used |
|---------------|-------------|------------|
| BroadcastChannel | 3 | Cross-tab live updates — admin publishes, public site re-hydrates |
| ES Modules (`import` / `export`) | 4 | `erovoutika-cms.js` imports Firebase SDK from CDN |
| DOM manipulation (querySelector, innerHTML, createElement) | 4 | All hydrator functions rebuild sections dynamically |
| CSS Custom Properties (design tokens) | 4 | Light/dark theme switching via `data-theme` attribute |
| Responsive Design (media queries, flexbox, grid) | 3 | Both HTML files adapt to mobile/desktop viewports |

### Tools & Platforms

| Tool | Purpose | Notes |
|------|---------|-------|
| Git | Version control | Branching, commits, pull requests |
| GitHub | Hosting & collaboration | Issues, PRs, code review |
| Firebase Console | BaaS management | Auth config, Firestore rules, Storage buckets |
| VS Code / Editor | Development | Live Server extension for local testing |
| Chrome DevTools | Debugging | Network tab, Console, Application (Firestore viewer) |

### Databases

| Database | Level (1–5) | Notes |
|----------|-------------|-------|
| Cloud Firestore (NoSQL) | 4 | Document model: `sections/{about,services,portfolio,awards,partners}` — nested objects, arrays of image URLs |

---

## Concepts & Patterns Demonstrated

| Concept | Evidence in Codebase |
|---------|---------------------|
| NoSQL document modelling | Firestore `sections/{name}` with flexible schema per section |
| OAuth authentication flow | Google sign-in gating the admin UI |
| Image upload pipeline | Firebase Storage → public URL → stored in Firestore field → rendered on public site |
| Cross-tab real-time UX (without WebSockets) | `BroadcastChannel` pattern for instant live-site refresh |
| Separation of concerns | Editor (`admin.html`) ↔ Data (Firestore) ↔ Presenter (`index4(1).html` + `erovoutika-cms.js`) |
| Hydration pattern | JS reads server data post-load and injects into static HTML shell |
| Theme system (light/dark) | CSS custom properties toggled via `data-theme` attribute on `<html>` |
| Progressive enhancement | Site renders a static shell; JS hydrates dynamic content on top |

---

## Soft Skills

- **Communication** — Coordinated Firebase project sharing and section ownership across group members.
- **Time management** — Balanced multiple deliverables (admin panel, public site, hydration script) within OJT timeline.
- **Problem solving** — Debugged cross-origin issues with Firebase CDN imports; solved BroadcastChannel timing edge cases.
- **Teamwork / collaboration** — Group project with shared Firebase project; used PRs for code review.
- **Adaptability** — Learned Firebase SDK v12 (modular) which differs significantly from older v8/v9 compat mode.

---

## Projects & Contributions

| Project | Role | Skills Used | Outcome |
|---------|------|-------------|---------|
| Erovoutika Public Site (`index4(1).html`) | Front-end developer | HTML, CSS (dark theme, animations), responsive design | Polished marketing page with multiple sections |
| Erovoutika Admin Console (`admin.html`) | Full-stack (client-side) | Firebase Auth, Firestore CRUD, Storage uploads, form UX | Functional CMS for non-technical content editors |
| Hydration Script (`erovoutika-cms.js`) | Front-end / integration | ES modules, Firestore reads, DOM injection, BroadcastChannel | Live-updating public site without page reload |

---

## Weekly Progress Log

### Week 1 — _YYYY-MM-DD to YYYY-MM-DD_
- **Tasks:** Project setup, Firebase project creation, initial HTML structure
- **Learned:** Firebase console setup, Firestore data model planning
- **Blockers:** —
- **Next:** Build admin auth screen

### Week 2 — _YYYY-MM-DD to YYYY-MM-DD_
- **Tasks:** Admin authentication, About section editor
- **Learned:** Google OAuth with Firebase Auth, `setDoc` / `getDoc` patterns
- **Blockers:** —
- **Next:** Add remaining section editors

### Week 3 — _YYYY-MM-DD to YYYY-MM-DD_
- **Tasks:** Services, Portfolio, Awards, Partners editors in admin panel
- **Learned:** Image upload to Firebase Storage, dynamic form rows
- **Blockers:** —
- **Next:** Build hydration script for public site

### Week 4 — _YYYY-MM-DD to YYYY-MM-DD_
- **Tasks:** `erovoutika-cms.js` hydration, BroadcastChannel integration, testing
- **Learned:** ES module imports from CDN, BroadcastChannel API, DOM rebuild strategies
- **Blockers:** —
- **Next:** Polish UI, documentation, final submission

> Copy the block above for each additional week.

---

## Certifications & Training

| Title | Provider | Date | Link |
|-------|----------|------|------|
| _e.g. Firebase Fundamentals_ | _Google_ | _YYYY-MM_ | _link_ |

---

## Goals

### Short-term (next 2 weeks)
- [ ] Rename `index4(1).html` → `index.html`
- [ ] Add `.gitignore` and remove `File3.zip` from repo
- [ ] Extract inline CSS to external stylesheets

### Medium-term (this OJT period)
- [ ] Add Firestore security rules to the repository
- [ ] Deploy to Firebase Hosting with custom domain
- [ ] Add a "Contact" or "Team" section with its own hydrator

### Long-term (career)
- [ ] Learn a front-end framework (React / Vue / Svelte) and rebuild with components
- [ ] Explore server-side rendering or static-site generation (Next.js / Astro)
- [ ] Obtain Firebase / GCP certification

---

## Self-Assessment Legend

| Level | Meaning |
|-------|---------|
| 1 | Aware — heard of it, no hands-on use |
| 2 | Beginner — guided exercises, simple tasks |
| 3 | Intermediate — independent on common tasks |
| 4 | Advanced — handles complex tasks, mentors others |
| 5 | Expert — deep knowledge, designs solutions |
