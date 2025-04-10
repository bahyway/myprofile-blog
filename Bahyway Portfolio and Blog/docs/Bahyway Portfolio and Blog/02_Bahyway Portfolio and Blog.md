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

## Security Tips
- Keep `.env` files out of Git using `.gitignore`
- Use GitHub private repos for sensitive work
- Consider GitHub Secrets if deploying via Actions
- Do not expose database or API credentials

## Next Steps
1. Select which projects you want public.
2. List which modules/scripts are private.
3. Choose whether to use Jekyll or another static generator (e.g., Hugo, Astro).
4. We can build the structure and automate deployment together.

Let me know when you're ready to start step-by-step!

