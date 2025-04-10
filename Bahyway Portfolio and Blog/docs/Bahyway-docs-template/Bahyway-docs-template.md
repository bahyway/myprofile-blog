# 📁 bahyway-docs-template

[![Deploy to GitHub Pages](https://github.com/bahyway/bahyway-docs-template/actions/workflows/gitbook.yml/badge.svg)](https://github.com/bahyway/bahyway-docs-template/actions)

A multilingual, AI-powered portfolio and documentation site powered by **Astro**, **GitBook**, **LangChain**, **Chatbots**, and **Docker**. Ideal for publishing personal or professional projects with multilingual chatbot support (English 🇬🇧, Dutch 🇳🇱, Arabic 🇸🇦).

---

This is a GitHub project template for deploying a multilingual portfolio and blog site using Astro, LangChain, Chatbots, and GitBook.

## 🗂 Folder Structure

```bash
bahyway-docs-template/
├── .github/
│   └── workflows/
│       └── gitbook.yml
├── .gitbook.yaml
├── .env.example
├── Makefile
├── build_index.py
├── docs/
│   ├── README.md
│   ├── SUMMARY.md
│   ├── portfolio.md
│   ├── blog/
│   │   ├── index.md
│   │   └── 2025-04-10-veterinary-microbial-diseases.md
│   ├── projects/
│   │   └── veterinary-microbial-diseases.md
│   ├── i18n/
│   │   ├── ar/index.md
│   │   ├── en/index.md
│   │   └── nl/index.md
│   ├── chatbot/
│   │   ├── index.md
│   │   ├── ui.md
│   │   ├── api.md
│   │   ├── langchain-index.md
│   │   └── escalation.md
│   ├── deployment/
│   │   ├── index.md
│   │   ├── docker.md
│   │   ├── github-actions.md
│   │   └── notifications.md
│   └── env.md
```

## ✅ Setup Instructions

1. Clone this repo
2. Customize content in `docs/`
3. Add secrets to GitHub:
   - `GITHUB_TOKEN`
   - `OPENAI_API_KEY`
   - `SLACK_WEBHOOK_URL`
   - `EMAIL_SERVER`, `EMAIL_USER`, etc.
4. Run `make build-indexes` to build LangChain FAISS indexes
5. Commit and push — GitHub Actions will publish to GitHub Pages automatically

---

## 🚀 Create and Push to GitHub

1. Go to [https://github.com/new](https://github.com/new)
2. Name the repository:
   ```
   bahyway-docs-template
   ```
3. Optional: check ✅ "Initialize with a README.md"
4. Click **Create repository**

### 🔁 Push Template from Local to GitHub
```bash
git init
git remote add origin https://github.com/bahyway/bahyway-docs-template.git
git add .
git commit -m "Initial commit with GitBook structure"
git branch -M main
git push -u origin main
```

---

1. Clone this repo
2. Customize content in `docs/`
3. Add secrets to GitHub:
   - `GITHUB_TOKEN`
   - `OPENAI_API_KEY`
   - `SLACK_WEBHOOK_URL`
   - `EMAIL_SERVER`, `EMAIL_USER`, etc.
4. Run `make build-indexes` to build LangChain FAISS indexes
5. Commit and push — GitHub Actions will publish to GitHub Pages automatically

---

## 🔧 build_index.py
```python
import os
from langchain.document_loaders import DirectoryLoader, TextLoader
from langchain.text_splitter import MarkdownTextSplitter
from langchain.embeddings import OpenAIEmbeddings
from langchain.vectorstores import FAISS

LANGUAGES = ['en', 'nl', 'ar']
MARKDOWN_BASE = os.environ.get('MARKDOWN_SOURCE_DIR', './markdown')
INDEX_BASE = os.environ.get('LANGCHAIN_INDEX_DIR', './indexes')

for lang in LANGUAGES:
    md_path = os.path.join(MARKDOWN_BASE, lang)
    index_path = os.path.join(INDEX_BASE, lang)

    print(f"Processing {lang.upper()} Markdown from {md_path}...")

    loader = DirectoryLoader(md_path, glob="**/*.md", loader_cls=TextLoader)
    documents = loader.load()

    splitter = MarkdownTextSplitter(chunk_size=512, chunk_overlap=64)
    texts = splitter.split_documents(documents)

    embeddings = OpenAIEmbeddings()
    vectorstore = FAISS.from_documents(texts, embeddings)
    vectorstore.save_local(index_path)

    print(f"✅ {lang.upper()} index saved to {index_path}")
```

---

## 🛠️ Makefile
```makefile
.PHONY: build-indexes

build-indexes:
	@echo "🔄 Building indexes for all languages..."
	python build_index.py
```

---

## 📄 .env.example
```env
# OpenAI API Key
OPENAI_API_KEY=your-openai-api-key

# LangChain Path Configuration
LANGCHAIN_INDEX_DIR=./indexes
MARKDOWN_SOURCE_DIR=./markdown

# Slack Notifications
SLACK_WEBHOOK_URL=https://hooks.slack.com/services/your/webhook/url

# Email Notifications (SMTP)
EMAIL_SERVER=smtp.example.com
EMAIL_PORT=587
EMAIL_USER=bot@example.com
EMAIL_PASSWORD=your-email-password
EMAIL_TO=your@email.com
```

---

## ⚙️ .github/workflows/gitbook.yml
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

## 📘 .gitbook.yaml
```yaml
root: ./docs
structure:
  readme: README.md
  summary: SUMMARY.md
```

Now everything needed to run, test, and deploy your GitBook portfolio and chatbot site is inside one place!

---

## 🎨 Customize GitHub Pages Settings for an Awesome Site

To make your GitBook site live under GitHub Pages:

1. Go to your repository settings → **Pages**
2. Under "Source", choose:
   - **Branch**: `gh-pages`
   - **Folder**: `/ (root)`
3. Save the settings
4. Your site will be available at:
   ```
   https://bahyway.github.io/bahyway-docs-template/
   ```

### 🧪 Optional Enhancements

- Add a `CNAME` file to link to a custom domain
- Add `favicon.ico` and `logo.png` under `docs/` for branding
- Use GitHub Project Settings > Custom Domain if hosting with your own domain name
- Add a `robots.txt` or `sitemap.xml` if you want SEO support

Let me know if you’d like to auto-generate those enhancements too! ✅

---

## 🖼 Auto-Generated Site Enhancements

### ✅ `CNAME`
If using a custom domain (e.g., `docs.bahyway.net`), add this file to your project root:
```txt
www.bahyway.net
```

GitHub will pick this up and route the Pages deployment to your custom domain.

### ✅ `favicon.ico` and `logo.png`
Place these branding files in `docs/`:

- `docs/favicon.ico`: your custom site icon
- `docs/logo.png`: logo for chatbot UI or GitBook header

Use `<link rel="icon" href="favicon.ico">` in your Astro layout or inject it in GitBook theme overrides.

### ✅ `robots.txt`
Allow search engines to index your GitBook:
```txt
User-agent: *
Allow: /
Sitemap: https://bahyway.github.io/bahyway-docs-template/sitemap.xml
```

### ✅ `sitemap.xml`
Basic sample for SEO indexing:
```xml
<?xml version="1.0" encoding="UTF-8"?>
<urlset xmlns="http://www.sitemaps.org/schemas/sitemap/0.9">
  <url>
    <loc>https://bahyway.github.io/bahyway-docs-template/</loc>
    <changefreq>weekly</changefreq>
    <priority>1.0</priority>
  </url>
</urlset>
```

These help bots crawl and index your documentation.

1. Clone this repo
2. Customize content in `docs/`
3. Add secrets to GitHub:
   - `GITHUB_TOKEN`
   - `OPENAI_API_KEY`
   - `SLACK_WEBHOOK_URL`
   - `EMAIL_SERVER`, `EMAIL_USER`, etc.
4. Run `make build-indexes` to build LangChain FAISS indexes
5. Commit and push — GitHub Actions will publish to GitHub Pages automatically

This template is fully aligned with the GitBook Placeholders you’ve authored.

Let me know if you'd like this zipped or pushed to a GitHub repository!

```python
from PIL import Image, ImageDraw, ImageFont
import os
import zipfile

# Create placeholder logo.png
logo = Image.new('RGB', (400, 120), color='navy')
draw = ImageDraw.Draw(logo)
draw.text((20, 40), "bahyway logo", fill='white')
logo_path = "/mnt/data/logo.png"
logo.save(logo_path)

# Create placeholder favicon.ico
favicon = Image.new('RGB', (32, 32), color='darkgreen')
draw = ImageDraw.Draw(favicon)
draw.text((3, 8), "B", fill='white')
favicon_path = "/mnt/data/favicon.ico"
favicon.save(favicon_path)

# Create ZIP archive
zip_path = "/mnt/data/bahyway-docs-assets.zip"
with zipfile.ZipFile(zip_path, 'w') as zipf:
    zipf.write(logo_path, arcname='docs/logo.png')
    zipf.write(favicon_path, arcname='docs/favicon.ico')

zip_path

```