# Agent Skills & Automation Workspace

A comprehensive workspace equipped with a library of **140 specialized agent skills** spanning frontend design, full-stack development, AI/LLM engineering, cybersecurity, data architecture, and browser automation.

---

## Quick Start

### 1. Prerequisites
- **Node.js**: `v20.0.0` or later (detected `v22.21.0`)
- **npm**: `v10.0.0` or later (detected `v11.11.1`)

### 2. Setup Playwright (Browser Automation)
To initialize Playwright and install required browser binaries (Chromium):

```bash
# Run setup directly from the workspace root:
npm run setup

# Or alternatively, run within the skill directory:
cd .agents/skills/playwright-skill
npm run setup
```

To install all browsers (Chromium, Firefox, and WebKit):
```bash
npm run setup:playwright:all
```

---

## Playwright Browser Automation Usage

The [`playwright-skill`](.agents/skills/playwright-skill) provides complete browser automation, dev-server auto-detection, screenshots, and UX validation.

### Run an Inline Automation Task
```bash
node .agents/skills/playwright-skill/run.js -e "const browser = await chromium.launch({headless: true}); try { const page = await browser.newPage(); await page.goto('https://example.com'); console.log('Page Title:', await page.title()); } finally { await browser.close(); }"
```

### Run a Playwright Script
Create a script (e.g. `test.js`):
```javascript
const { chromium } = require('playwright');

(async () => {
  const browser = await chromium.launch({ headless: false });
  try {
    const page = await browser.newPage();
    await page.goto('http://localhost:3000');
    console.log('Page loaded:', await page.title());
    await page.screenshot({ path: 'screenshot.png', fullPage: true });
  } finally {
    await browser.close();
  }
})();
```

Execute it using the runner:
```bash
node .agents/skills/playwright-skill/run.js test.js
```

---

## Skills Catalog Overview

This environment contains **140 active skills** organized in [`.agents/skills/`](.agents/skills/):

### Core Categories

| Domain | Key Skills |
| :--- | :--- |
| **Testing & Automation** | `playwright-skill`, `test-driven-development`, `e2e-testing-patterns`, `test-fixing`, `systematic-debugging` |
| **Frontend & UI/UX** | `react-best-practices`, `nextjs-app-router-patterns`, `ui-styling`, `ui-ux-pro-max`, `3d-web-experience`, `tailwind-patterns`, `mobile-design` |
| **Backend & APIs** | `fastapi-pro`, `fastapi-templates`, `django-pro`, `golang-pro`, `python-pro`, `api-patterns`, `nodejs-best-practices`, `auth-implementation-patterns` |
| **AI, LLM & RAG** | `langgraph`, `langfuse`, `rag-engineer`, `rag-implementation`, `ai-agents-architect`, `prompt-engineering`, `vector-database-engineer`, `build-with-exa` |
| **Security & Pentesting** | `ethical-hacking-methodology`, `burp-suite-testing`, `cloud-penetration-testing`, `top-web-vulnerabilities`, `api-security-best-practices`, `security-auditor` |
| **Cloud & DevOps** | `docker-expert`, `kubernetes-architect`, `aws-serverless`, `terraform-specialist`, `distributed-tracing`, `slo-implementation` |
| **Data & Databases** | `database-architect`, `postgres-best-practices`, `data-engineer`, `dbt-transformation-patterns`, `airflow-dag-patterns` |
| **Product & Marketing** | `product-manager-toolkit`, `seo-audit`, `programmatic-seo`, `copywriting`, `kpi-dashboard-design`, `app-store-optimization` |

---

## Managing Skills

Each skill is self-contained in its own directory containing:
- `SKILL.md`: Skill definition, frontmatter triggers, instructions, and workflows.
- `scripts/` or `lib/`: Helper utilities and execution runners (where applicable).

Skills can be audited or updated via [`skills-lock.json`](skills-lock.json).
