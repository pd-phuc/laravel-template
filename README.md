# Laravel Template

> Production-ready Laravel template with professional workflow, AI agent integration, and dual-mode auth (Session + Sanctum API).

## ⚡ Quick Start

```bash
# 1. Clone the template
git clone <repo-url> my-project
cd my-project

# 2. Install dependencies and setup
composer setup

# 3. Configure database
# Edit .env → set DB_DATABASE, DB_USERNAME, DB_PASSWORD

# 4. Run migrations
php artisan migrate

# 5. Start development
composer dev
```

## 🛠️ Commands

| Command | Description |
|---------|-------------|
| `composer setup` | Install all deps, generate key, migrate, build assets |
| `composer dev` | Run server + queue + logs + Vite concurrently |
| `composer test` | Run test suite |
| `composer lint` | Check code style (Pint, no changes) |
| `composer format` | Auto-fix code style (Pint + Prettier) |
| `npm run dev` | Vite dev server only |
| `npm run build` | Build production assets |

## 🏗️ Architecture

### Request Flow

```
Web:  routes/web.php  → Controllers/     → Models → views/
API:  routes/api.php  → Controllers/Api/ → Models → JSON
```

### Authentication

| Mode | Guard | Controller | Use Case |
|------|-------|-----------|----------|
| Session | `web` | `Auth\LoginController` | Browser, Blade views |
| Token | `sanctum` | `Api\AuthController` | Mobile app, SPA, 3rd party |

### Folder Structure

```
app/
├── Http/
│   ├── Controllers/
│   │   ├── Auth/           # Web session auth
│   │   ├── Api/            # API token auth (Sanctum)
│   │   └── Admin/          # Admin panel (create as needed)
│   └── Middleware/
│       └── EnsureIsAdmin.php
├── Models/
└── Providers/

routes/
├── web.php                  # Session-based routes
├── api.php                  # Sanctum-guarded API routes
└── console.php

resources/
├── views/                   # Blade templates
├── css/app.css              # Tailwind CSS entry
└── js/app.js                # JavaScript entry
```

## 🔧 Code Quality

| Tool | Purpose | Config |
|------|---------|--------|
| **Pint** | PHP code style | `pint.json` |
| **Prettier** | Blade/JS/CSS formatting | `.prettierrc` |
| **Husky** | Git hooks | `.husky/` |
| **Commitlint** | Commit message format | `commitlint.config.cjs` |
| **Lint-staged** | Pre-commit auto-format | `package.json` |
| **EditorConfig** | Editor consistency | `.editorconfig` |

### Commit Convention

```
<type>(<scope>): <subject>

# Types: feat, fix, docs, style, refactor, perf, test, chore, revert, ci
# Examples:
feat(auth): add google oauth login
fix(search): normalize phone number format
docs: update api documentation
```

## 🤖 AI Agent Integration

This template includes pre-configured instructions for AI coding assistants:

| File | Agent |
|------|-------|
| `CLAUDE.md` | Claude Code |
| `AGENTS.md` | Gemini / Antigravity |
| `.agent/` | 20 specialist agents, 49 skills, 11 workflows |
| `.claude/` | 75 Claude-specific skills |

## 📋 Tech Stack

- **PHP** 8.3+ / **Laravel** 13
- **Vite** 8 + **Tailwind CSS** 4
- **MySQL** (configurable via `.env`)
- **Laravel Sanctum** (API token auth)
- **PHPUnit** (testing)
- **Laravel Pint** (PHP code style)
