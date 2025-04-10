# Portfolio and Blog bahyway

## Objective
Create a personal Portfolio and Blog website based on your existing and future projects, with:
- GitHub Pages deployment
- Selective visibility of projects
- Exclusive admin access to specific modules/scripts

## Requirements
- Use GitHub Pages for hosting
- Use Jekyll or a static site generator compatible with GitHub Pages
- Implement access control for private modules/scripts
- Structure content to showcase selected public projects
- Allow Markdown-based blogging

## Visibility Strategy
### Public Projects
- Select a curated list of projects to publish
- Highlight project goals, features, technologies, and screenshots

#### ✅ Demo Project: Veterinary Microbial Diseases
- **Domain**: Veterinary / Microbiology / Knowledge Graphs
- **Stack**: Python, Cytoscape Dash, Markdown, SQL Server (Docker), Confluence Docs
- **Features**:
  - Knowledge graph to visualize microbial diseases
  - Node/Edge design documented in GitBook
  - Future plans for AI-enhanced data processing

### Hidden/Private Projects
- Do **not** push these projects to the public GitHub repo
- Maintain in a private repository or folder ignored by Git
- Use a separate private GitHub repo or local-only content for sensitive scripts

#### 🔐 Private Modules and Scripts
All modules related to **Graph Theory** or **Knowledge Graphs** are private. This includes (but is not limited to):
- PostgreSQL Graph
- DGraph
- GraphQL
- Apache TinkerPop
- Gremlin
- Python-based graph tools
- C++ graph libraries
- Any custom logic or visualization components tied to graph data structures

## Admin Access Strategy
- For blog and site management:
  - Use Jekyll admin plugin (e.g., `jekyll-admin`) for local editing
  - Or maintain `.md` blog files in a private folder, then push when needed

- For access-controlled modules/scripts:
  - Keep them in a private repo
  - Add a `README.md` reference in the public repo without exposing the code
  - Optionally use Git submodules for private content (readable only by you)
  - Consider GitHub Actions to sync content without exposing secrets

## Folder Structure (Example)
```
.
├── _config.yml
├── index.md              # Home page (About you, etc.)
├── _projects/            # Markdown for public projects
│   ├── veterinary-microbial-diseases.md
├── _blog/                # Blog posts
│   ├── 2025-04-10-first-post.md
├── _includes/
├── _layouts/
├── assets/
│   ├── images/
│   └── css/
├── scripts/              # Public scripts only
├── README.md
└── .gitignore
```

## Static Site Generator - Selected: Astro (Modern JS Framework)

Astro is a modern, fast static site builder optimized for Markdown and JavaScript frameworks. You’ve chosen Astro as the engine for your portfolio and blog.

### ✅ Create Astro Site with Markdown Support:
```bash
npm create astro@latest
# Choose "blog" template
cd your-astro-project
npm install
npm run dev
```

### ✅ Folder Structure (for Astro + Blog Template)
```
.
├── public/
│   └── favicon.ico
├── src/
│   ├── content/
│   │   ├── blog/
│   │   │   └── 2025-04-10-veterinary-microbial-diseases.md
│   │   └── projects/
│   │       └── veterinary-microbial-diseases.md
│   ├── components/
│   └── pages/
│       ├── index.astro
│       └── about.astro
├── astro.config.mjs
├── package.json
├── tsconfig.json
└── .gitignore
```

### ✅ Deploy Astro to GitHub Pages:
1. Install deploy dependencies:
```bash
npm install --save-dev @astrojs/github
```
2. Update `astro.config.mjs`:
```js
import { defineConfig } from 'astro/config';
import github from '@astrojs/github';

export default defineConfig({
  site: 'https://yourusername.github.io',
  outDir: 'dist',
  integrations: [github()],
});
```
3. Add GitHub Actions workflow in `.github/workflows/deploy.yml`:
```yaml
name: Deploy to GitHub Pages

on:
  push:
    branches: [main]

jobs:
  deploy:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v3
      - uses: withastro/action@v0
        with:
          deploy-branch: gh-pages
```
4. Commit & push to GitHub. Site will be deployed to GitHub Pages.
 (Modern JS Framework)
**Create Astro Site with Markdown Support:**
```bash
npm create astro@latest
# Choose "blog" template
npm install
npm run dev
```

**Deploy to GitHub Pages (via Actions):**
```bash
# astro.config.mjs
export default {
  site: 'https://yourusername.github.io',
  outDir: 'dist'
}
```

## Security Tips
- Keep `.env` files out of Git using `.gitignore`
- Use GitHub private repos for sensitive work
- Consider GitHub Secrets if deploying via Actions
- Do not expose database or API credentials

## Project Setup: Astro Scaffold

### 🛠️ Step-by-Step to Scaffold Your Astro Site Locally
1. Open your terminal.
2. Run the following to scaffold your site:
```bash
npm create astro@latest
# Name your project: bahyway-portfolio
cd bahyway-portfolio
npm install
npm run dev
```
3. Visit `http://localhost:4321` to see your site in development mode.

### 📁 Structure to Follow for Public Content
- `src/content/projects/` → contains your project markdowns
- `src/content/blog/` → contains blog post markdowns
- `src/pages/` → Astro components like homepage, about, contact

We will place your first project and blog post like so:
```
src/content/projects/veterinary-microbial-diseases.md
src/content/blog/2025-04-10-veterinary-microbial-diseases.md
```

---

## 📝 Example Content: Veterinary Microbial Diseases

### 📂 `src/content/projects/veterinary-microbial-diseases.md`
```md
---
title: Veterinary Microbial Diseases
description: A Knowledge Graph demo for veterinary microbiology.
date: 2025-04-10
tags: [Knowledge Graph, Veterinary, Python, Cytoscape]
image: /images/vet-micrograph.png
---

This project visualizes microbial diseases using a custom-built knowledge graph. It integrates data from structured and unstructured sources, offers an interactive dashboard, and supports further AI enhancements.
```

### 📰 `src/content/blog/2025-04-10-veterinary-microbial-diseases.md`
```md
---
title: Behind the Graph – Veterinary Microbial Diseases
description: Design walkthrough, tools used, and lessons learned.
date: 2025-04-10
tags: [blog, project-insights, VeterinaryKG]
---

In this post, I dive into the inner workings of my Veterinary Microbial Diseases knowledge graph project. From choosing node hierarchies to integrating Dash Cytoscape, this is how it all came together.
```

---

## 🧾 Markdown Files Created for Astro Content

Two Markdown files have been automatically created and placed in your Astro project structure:

- ✅ `bahyway-portfolio/src/content/projects/veterinary-microbial-diseases.md`
- ✅ `bahyway-portfolio/src/content/blog/2025-04-10-veterinary-microbial-diseases.md`

These files are now ready to display your first project and blog entry inside the Astro-powered site.

## 🏠 Example Astro Homepage – `src/pages/index.astro`

Here’s a simple homepage layout for your Astro site, introducing you and linking to the blog and projects:

```astro
---
import Layout from '../layouts/Layout.astro';
---

<Layout title="bahyway – Portfolio & Blog">
  <section>
    <h1>👋 Welcome to bahyway</h1>
    <p>This site showcases selected public projects and blog posts. For exclusive tools and modules, admin access is required.</p>
    <h2>🔗 Explore</h2>
    <ul>
      <li><a href="/projects">🧪 View Projects</a></li>
      <li><a href="/blog">📝 Read the Blog</a></li>
    </ul>
  </section>
</Layout>
```

You can customize this further with Astro components or Tailwind CSS.

## Next Steps
1. Select which projects you want public.
2. List which modules/scripts are private.
3. Choose whether to use Jekyll or another static generator (e.g., Hugo, Astro).
4. We can build the structure and automate deployment together.

Let me know when you're ready to start step-by-step!

