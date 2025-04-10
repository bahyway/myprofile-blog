# README.md

Welcome to the Portfolio and Blog documentation. This GitBook outlines the full setup, multilingual support, chatbot integration, deployment, and security model.

**Suggested Content:**
- Project purpose and vision
- Technologies used (Astro, LangChain, OpenAI, Docker, GitHub Actions)
- Structure of the documentation
- How to contribute
- Link to GitHub repository
. This GitBook outlines the full setup, multilingual support, chatbot integration, deployment, and security model.

---

# portfolio.md

## Portfolio Overview

This section describes the structure, goals, and selected public projects.

**Suggested Content:**
- Goals of the portfolio
- Modules included and their categories
- How projects are selected (e.g., public vs private)
- Visual layout and navigation strategy
- Integration with Astro and GitHub Pages


This section describes the structure, goals, and selected public projects.

---

# projects/veterinary-microbial-diseases.md

## Veterinary Microbial Diseases

Knowledge Graph project visualizing microbial relationships with Dash + LangChain.

**Suggested Content:**
- Objective of the project
- Tools used (Python, Dash, Cytoscape, PostgreSQL Graph, FAISS)
- Sample dataset and graph explanation
- Screenshots or diagrams
- Link to code/demo if public


Knowledge Graph project visualizing microbial relationships with Dash + LangChain.

---

# blog/index.md

## Blog Overview

This section collects multilingual blog posts related to projects and reflections.

**Suggested Content:**
- Purpose of the blog section
- How posts are organized by language
- Feed structure (if using Astro or RSS)
- Guidelines for submitting a post


This section collects multilingual blog posts related to projects and reflections.

---

# blog/2025-04-10-veterinary-microbial-diseases.md

## Blog: Veterinary Microbial Diseases

Behind the scenes of building the Veterinary KG using Markdown and Dash Cytoscape.

**Suggested Content:**
- Personal insights or lessons learned
- Design and development flow
- Challenges and how they were solved
- Graph modeling techniques


Behind the scenes of building the Veterinary KG using Markdown and Dash Cytoscape.

---

# i18n.md

## Multilingual Setup

**Suggested Content:**
- Supported languages and structure: `en/`, `nl/`, `ar/`
- How to translate and localize content
- Language detection or routing logic (in Astro or JavaScript)
- Tools for translation (e.g., i18next, MD files)


Overview of the multilingual structure (English, Dutch, Arabic).

---

# i18n/en/index.md

## English Home

**Suggested Content:**
- Welcome message
- Explanation of site features in English
- How to switch language
- Links to blog and portfolio


Welcome to the English homepage.

---

# i18n/nl/index.md

## Nederlandse Startpagina

**Suggested Content:**
- Welkomstbericht
- Beschrijving van de functies van de site
- Uitleg over taalkeuze
- Links naar blog en projecten


Welkom op de Nederlandstalige startpagina.

---

# i18n/ar/index.md

## الصفحة الرئيسية العربية

**Suggested Content:**
- رسالة ترحيبية
- شرح لأقسام الموقع باللغة العربية
- طريقة تغيير اللغة
- روابط للمدونة والمشاريع


مرحبًا بك في الصفحة العربية.

---

# chatbot/index.md

## Chatbot Integration

**Suggested Content:**
- Overview of multilingual chatbot structure
- Technologies used (JS, HTML, LangChain, FAISS, OpenAI)
- Per-language routing and fallback logic
- Admin-only access rules and escalation triggers


Overview of the chatbot stack, UI, APIs, and knowledge routing.

---

# chatbot/ui.md

## Chatbot UI

**Suggested Content:**
- UI for `en.html`, `nl.html`, `ar.html`
- Input + chat display design per language
- iFrame and language toggle strategies
- Styling tips (RTL for Arabic)


Multilingual chatbot HTML and JS components.

---

# chatbot/api.md

## Chatbot API

**Suggested Content:**
- API endpoints: `/api/chat/{lang}`
- Implementations in FastAPI, Flask, Node.js
- How to secure the API
- Examples with OpenAI + FAISS vector search


Python (FastAPI/Flask) and Node.js endpoints for multilingual responses.

---

# chatbot/langchain-index.md

## LangChain Vector Index

**Suggested Content:**
- Markdown folder parsing with DirectoryLoader
- Splitting text and creating embeddings
- Saving and loading FAISS indexes per language
- Scripts (`build_index.py`) and `Makefile` integration


How Markdown content is parsed and indexed with LangChain + FAISS.

---

# chatbot/escalation.md

## Escalation to Human

**Suggested Content:**
- Confidence threshold logic (e.g., cosine similarity < 0.6)
- Language fallback or unsupported input handling
- Admin topics: security, restricted endpoints, private logic
- Human notification options (email, Slack, redirect)


Bot logic to forward low-confidence questions or admin-level topics.

---

# deployment/index.md

## Deployment Overview

**Suggested Content:**
- Deployment architecture
- Astro + API backends + Docker + GitHub Actions
- Hosting (GitHub Pages, Docker Hub, Vercel, etc.)

---

### 🧪 Preview GitBook Locally

To preview this GitBook locally before publishing:

1. **Install GitBook CLI**
   ```bash
   npm install -g gitbook-cli
   ```

2. **Navigate to your `/docs` folder**
   ```bash
   cd docs
   ```

3. **Install required plugins (if needed)**
   ```bash
   gitbook install
   ```

4. **Start local preview server**
   ```bash
   gitbook serve
   ```

This will build and serve your GitBook locally at:
📍 `http://localhost:4000`


**Suggested Content:**
- Deployment architecture
- Astro + API backends + Docker + GitHub Actions
- Hosting (GitHub Pages, Docker Hub, Vercel, etc.)


Overview of Docker and CI/CD setup for Astro and Chatbot services.

---

# deployment/docker.md

## Docker Setup

**Suggested Content:**
- Dockerfiles for each backend
- Volume mapping for markdown + FAISS indexes
- `docker-compose.yml` breakdown
- How to scale with networks or services


Dockerfiles for FastAPI, Flask, Node.js + `docker-compose.yml` with LangChain volumes.

---

# deployment/github-actions.md

## GitHub Actions

**Suggested Content:**
- Triggering index rebuilds on markdown change
- Slack + email notification integration
- Using GitHub secrets for API keys and credentials
- Sample YAML workflow

### 📦 Publishing to GitBook using GitHub Actions

To auto-publish this GitBook using GitHub Actions:

1. Ensure your repo has the `/docs` folder containing all the `.md` files and `SUMMARY.md`.
2. Commit a `.gitbook.yaml` file.
3. Use this GitHub Actions workflow:

```yaml
name: Deploy GitBook

on:
  push:
    paths:
      - 'docs/**'
      - '.github/workflows/gitbook.yml'

jobs:
  deploy:
    runs-on: ubuntu-latest
    steps:
      - name: Checkout code
        uses: actions/checkout@v3

      - name: Install Node.js
        uses: actions/setup-node@v3
        with:
          node-version: 18

      - name: Install GitBook CLI
        run: |
          npm install -g gitbook-cli
          gitbook install ./docs

      - name: Build GitBook
        run: |
          cd docs
          gitbook build

      - name: Deploy to GitHub Pages
        uses: peaceiris/actions-gh-pages@v3
        with:
          github_token: ${{ secrets.GITHUB_TOKEN }}
          publish_dir: docs/_book
```

---

### 🛠️ `.gitbook.yaml` Template
```yaml
root: ./docs
structure:
  readme: README.md
  summary: SUMMARY.md
```

This will help GitBook CLI recognize and structure your GitBook properly.
You can commit it to the root of your repository alongside the `/docs` folder.


**Suggested Content:**
- Triggering index rebuilds on markdown change
- Slack + email notification integration
- Using GitHub secrets for API keys and credentials
- Sample YAML workflow

### 📦 Publishing to GitBook using GitHub Actions

To auto-publish this GitBook using GitHub Actions:

1. Ensure your repo has the `/docs` folder containing all the `.md` files and `SUMMARY.md`.
2. Commit a `.gitbook.yaml` file (or use GitBook.io to configure).
3. Add this GitHub Actions workflow:

```yaml
name: Deploy GitBook

on:
  push:
    paths:
      - 'docs/**'
      - '.github/workflows/gitbook.yml'

jobs:
  deploy:
    runs-on: ubuntu-latest
    steps:
      - name: Checkout code
        uses: actions/checkout@v3

      - name: Install Node.js
        uses: actions/setup-node@v3
        with:
          node-version: 18

      - name: Install GitBook CLI
        run: |
          npm install -g gitbook-cli
          gitbook install ./docs

      - name: Build GitBook
        run: |
          cd docs
          gitbook build

      - name: Deploy to GitHub Pages
        uses: peaceiris/actions-gh-pages@v3
        with:
          github_token: ${{ secrets.GITHUB_TOKEN }}
          publish_dir: docs/_book
```

This builds the GitBook from `/docs` and publishes the HTML to GitHub Pages.
Make sure `GitHub Pages` is set to serve from `gh-pages` branch in repo settings.


**Suggested Content:**
- Triggering index rebuilds on markdown change
- Slack + email notification integration
- Using GitHub secrets for API keys and credentials
- Sample YAML workflow


CI automation for deploying Astro and indexing chat documents.

---

# deployment/notifications.md

## Notifications

**Suggested Content:**
- Slack webhook setup
- SMTP configuration for email
- Message templates
- `.env` secrets for alerts


Slack + Email notification integration for indexing job status.

---

# env.md

## .env and Secrets

**Suggested Content:**
- `.env.example` with all variables used
- GitHub Secrets equivalents
- How to avoid committing sensitive data
- Environment variable use in Docker and scripts


Environment variables and GitHub Secrets configuration instructions.

