# My Profile: Technical Resume & Blog for Databases and Graph Technologies

## 🧑‍💻 About Me
I'm a Data Engineer and Graph Architect passionate about designing scalable database solutions and exploring the power of graph technologies. With deep knowledge of SQL Server, PostgreSQL, Neo4j, and Gremlin (Apache TinkerPop), I combine traditional RDBMS with modern graph data models to solve complex problems. I'm also a strong advocate of open-source and automation using Docker, GitHub Actions, and CI/CD pipelines.

---

## 💼 Technical Resume

### 🔧 Skills & Technologies
- **Databases**: SQL Server, PostgreSQL, MongoDB, Redis, Neo4j, GraphQL
- **Graph Tech**: Gremlin (TinkerPop), Cypher, RDF, SPARQL, Property Graphs, NetworkX
- **Programming**: Python, C#, Golang, Bash, T-SQL, PowerShell
- **Data Modeling**: ER Diagrams, Graph Models, Star & Snowflake Schemas
- **Tools**: Docker, VSCode, GitHub, GitBook, pgAdmin, Azure Data Studio
- **Visualization**: Python Dash, Streamlit, D3.js, Cytoscape.js, Leaflet.js
- **DevOps**: GitHub Actions, Ansible, Docker Compose, CI/CD

### 🏗️ Architecture
- Domain-Driven Design (DDD)
- Event-Driven Architecture (EDA)
- Microservices using gRPC, REST, and Pub/Sub patterns
- Clean Architecture & Factory Design Pattern

### 🧪 Testing & Automation
- PyTest, unittest, T4 templates, YAML pipelines
- Documentation with DocFX, GitBook, and Markdown

### 📈 Projects & Labs
- **Mortgages DWH Lab** (EDA + CQRS + SQL Server + SSIS)
- **PetroGraphAI** (Graph + Defect Prediction + ML)
- **Cemetery Knowledgebase** (Geo + Graph + Leaflet.js)
- **Genealogy Tree System** (Dash Cytoscape + Graph DB + Redis)
- **Blog/Portfolio Website** (Gatsby + GitHub Pages + PostgreSQL)

---

## 📝 My Blog (Gatsby + GitHub Pages)
### Purpose
To share, teach, and document real-world experiences in Data Engineering, Graph Systems, and Automation with bilingual support (English/Arabic).

### Concept Pages Strategy
Instead of filtering by date, isolate your blog content by concept-specific pages:
- `src/pages/knowledge-graph.js`
- `src/pages/rules-engine.js`
- `src/pages/data-cleansing.js`
- `src/pages/data-mining.js`
- `src/pages/datawarehouse.js`

Each page uses GraphQL to filter posts with a matching frontmatter field (e.g., `concept: knowledge-graph`). This enhances topic navigation, improves SEO, and offers readers focused learning paths.

---

## 🚀 Let's Build It Step-by-Step

### ✅ Step 1: Initialize Gatsby Blog Project
**What**: Use Gatsby CLI to scaffold your project.  
**Why**: Creates the structure to support plugins, React, and Markdown/MDX posts.
```bash
npm init gatsby@latest myprofile-blog
```
Choose:
- Blog starter
- `myprofile-blog` as folder
- TypeScript support: No (optional)
- CMS: No (manual Markdown)

### 🔧 Step 2: Basic File Creation
Inside `myprofile-blog`, add these:

**src/pages/about.js**
```jsx
import React from "react"
export default () => <div><h1>About Me</h1><p>This blog focuses on graph & data engineering.</p></div>
```

**src/pages/contact.js**
```jsx
import React from "react"
export default () => <div><h1>Contact</h1><p>Email me: your_email@example.com</p></div>
```

**src/pages/concepts/knowledge-graph.js**
```jsx
import React from "react"
import { graphql } from 'gatsby'
import PostList from '../../components/PostList'
export default ({ data }) => (
  <PostList title="Knowledge Graph Articles" posts={data.allMdx.nodes} />
)
export const query = graphql`
  query {
    allMdx(filter: { frontmatter: { concept: { eq: "knowledge-graph" } } }) {
      nodes {
        frontmatter { title date slug }
        excerpt
      }
    }
  }
`
```

**src/components/PostList.js**
```jsx
import React from 'react'
import { Link } from 'gatsby'
const PostList = ({ title, posts }) => (
  <div>
    <h1>{title}</h1>
    <ul>
      {posts.map(post => (
        <li key={post.frontmatter.slug}>
          <Link to={`/${post.frontmatter.slug}`}>{post.frontmatter.title}</Link>
          <p>{post.excerpt}</p>
        </li>
      ))}
    </ul>
  </div>
)
export default PostList
```

### 📂 Step 3: First Blog Post with Concept Tagging
`content/2025-03-27-knowledge-graphs.mdx`
```mdx
---
title: "Why Knowledge Graphs Matter"
date: "2025-03-27"
slug: "why-knowledge-graphs-matter"
concept: "knowledge-graph"
---

In this post, we explore how knowledge graphs model real-world domains...
```

### 🧱 Step 4: Setup gatsby-config.js
```js
module.exports = {
  siteMetadata: {
    title: `MyProfile Blog`,
    siteUrl: `https://yourusername.github.io/myprofile-blog`,
  },
  plugins: [
    `gatsby-plugin-image`,
    `gatsby-plugin-sharp`,
    `gatsby-transformer-sharp`,
    `gatsby-plugin-mdx`,
    `gatsby-plugin-react-helmet`,
    {
      resolve: `gatsby-source-filesystem`,
      options: { name: `content`, path: `${__dirname}/content` },
    },
  ]
}
```

### 🌐 Step 5: Setup GitHub Actions for CI/CD
Create `.github/workflows/deploy.yml`
```yaml
name: Deploy Gatsby
on:
  push:
    branches:
      - main
jobs:
  build-and-deploy:
    runs-on: ubuntu-latest
    steps:
    - uses: actions/checkout@v3
    - uses: actions/setup-node@v3
      with:
        node-version: '20'
    - run: npm install
    - run: npm run build
    - uses: JamesIves/github-pages-deploy-action@v4
      with:
        branch: gh-pages
        folder: public
```
Enable GitHub Pages: Settings > Pages > Source: `gh-pages` branch.

### 💬 Step 6: Create Concept Pages
Repeat the earlier `knowledge-graph.js` structure for:
- `rules-engine.js`
- `data-cleansing.js`
- `data-mining.js`
- `datawarehouse.js`

Each with a GraphQL query filtering on `concept` field.

### 🎨 Step 7: Bilingual Layout Support
Install:
```bash
npm install react-i18next i18next gatsby-plugin-react-i18next
```
Configure bilingual routing in `gatsby-config.js` and add translations to `/locales/en/` and `/locales/ar/`.

### 💼 Step 8: Add Advertising (Optional)
Create `src/components/SidebarAds.js`
```jsx
import React from 'react'
export default () => (
  <aside>
    <h3>Sponsored</h3>
    <a href="https://neo4j.com">
      <img src="/images/neo4j-banner.png" alt="Neo4j Graph DB"/>
    </a>
  </aside>
)
```
Use on any layout: `<SidebarAds />`

---

## 📬 Contact
- GitHub: [github.com/BahaaFadam](https://github.com/BahaaFadam)
- Email: your_email@example.com
- LinkedIn: [linkedin.com/in/yourprofile](https://linkedin.com/in/yourprofile)

> “Sharing knowledge builds legacy.”

