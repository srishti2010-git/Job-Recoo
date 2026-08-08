# Waypoint

A guided, single-page web app that helps a user figure out **which tech job roles they're closest to qualifying for**, based on the skills they already have — and gives them role-specific guidance to close the gap.

**Live demo:** _[add your GitHub Pages link here]_

---

## How it works

Waypoint walks the user through six steps:

1. **Sign in** — simple name/email registration (stored client-side for the session)
2. **Skills** — user adds their current skills and types a career goal (any role, free text — not limited to a preset list)
3. **Search** — kicks off the matching process
4. **Matches** — shows open roles for the user's goal field first, plus related roles in nearby fields, each with a live match percentage and matched/missing skill tags
5. **Guidance** — for whichever role the user picks, shows what's still needed to qualify, with role-category-specific advice (e.g. web dev roles emphasize a portfolio, security roles emphasize hands-on labs, etc.)
6. **Contact** — lets the user send a question, which arrives by email (via Formspree) along with their full registered profile (skills, goal, chosen role, match %)

## Tech stack

- Plain **HTML / CSS / JavaScript** — no build step, no framework, single file
- **[Formspree](https://formspree.io)** for the contact form → email delivery
- Hosted as a static site (e.g. GitHub Pages)

## Dataset

- **61 job roles** across 13 tech fields: Web Development, Data & Analytics, Cloud & Infrastructure, Product & Business, Mobile Development, QA & Testing, Cybersecurity, UI/UX Design, Database, AI & Machine Learning, Game Development, Blockchain, and Embedded & IoT
- **131 unique skills**, auto-derived from the role dataset and used to power the skill-search autocomplete

## Core logic

Matching works by comparing the user's entered skills against each role's required skills, scoring every role by percentage match, then ranking and grouping the results by field relative to the user's stated career goal.

## Running locally

This is a static single-file site — no install needed:

1. Clone the repo
2. Open `index.html` directly in a browser, **or** serve it locally for full functionality (some browsers restrict local file `fetch()` calls, which the contact form needs):
   ```bash
   python3 -m http.server 8000
   ```
   then visit `http://localhost:8000`

## Setting up the contact form

The contact form posts to a [Formspree](https://formspree.io) endpoint. To point it at your own inbox:

1. Create a form at [formspree.io](https://formspree.io) under your account
2. Copy its endpoint URL (`https://formspree.io/f/xxxxxxx`)
3. Replace the `FORMSPREE_ENDPOINT` constant near the top of the `<script>` block in `index.html`

## Deploying

Hosted via GitHub Pages:

1. Push `index.html` to the repo root
2. Repo → **Settings → Pages** → Source: **Deploy from a branch** → Branch: `main` / `root`
3. Your site goes live at `https://<username>.github.io/<repo-name>/`

## Project background

This project doubles as a Data Structures & Algorithms coursework submission. Its core matching feature (scoring, ranking, and grouping 61 roles against a user's skill set) is built on arrays, hashing (via `Set`), and search/sort operations. See `Waypoint_DSA_Project_Documentation.pdf` in this repo for a full breakdown of which DSA syllabus topics are represented in the code, and where.

## License

_Add a license if you'd like others to be able to reuse this (e.g. MIT)._
