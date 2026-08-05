# AGENTS.md — Laravel Template

> Project-level rules for AI agents working in this repository.

## Stack

- **Backend**: Laravel 13, PHP 8.3+, Eloquent ORM, MySQL
- **Frontend**: Vite + Tailwind CSS 4, Blade templates
- **Auth**: Laravel Sanctum (API tokens) + Session (web)
- **Testing**: PHPUnit / Pest
- **Code Style**: Laravel Pint, Prettier (Blade), EditorConfig

## Commands

| Task | Command |
|------|---------|
| Dev server | `composer dev` |
| Setup | `composer setup` |
| Test | `composer test` |
| Lint (check) | `composer lint` |
| Format (fix) | `composer format` |

## Conventions

### Code Style
- Follow Laravel Pint conventions (`pint.json` preset)
- Blade templates formatted by Prettier
- Commits follow **Conventional Commits** format (enforced by commitlint)

### Eloquent
- Use `casts()` method, not `$casts` property
- Explicit return types on relationships (`BelongsTo`, `HasMany`, etc.)
- Always include `HasFactory` trait + corresponding factory
- Use scopes for custom queries, avoid raw `DB::` calls

### Controllers
- Web controllers return Blade views
- API controllers return JSON responses
- Admin routes use `EnsureIsAdmin` middleware

### File Structure
```
app/
├── Http/
│   ├── Controllers/
│   │   ├── Auth/           # Session-based web auth
│   │   ├── Api/            # Sanctum token-based API auth
│   │   └── Admin/          # Admin panel controllers
│   └── Middleware/
├── Models/                  # Eloquent models
└── Providers/

routes/
├── web.php                  # Web routes (session auth)
├── api.php                  # API routes (Sanctum guard)
└── console.php              # Artisan commands

resources/
├── views/                   # Blade templates
├── css/app.css              # Tailwind entry
└── js/app.js                # JS entry
```

## Agent Skills

This project includes `.agent/` and `.claude/` skill directories with 49+ skills covering:
- Frontend, backend, database, testing, security, deployment
- Code review, debugging, performance, SEO
- See `.agent/ARCHITECTURE.md` for the full skill catalog

## Rules

1. **Read before write**: Always understand existing code patterns before making changes
2. **Test your changes**: Run `composer test` after any logic change
3. **Format your code**: Run `composer format` before committing
4. **Small commits**: One logical change per commit, conventional format
5. **No business logic in template**: Keep this repo framework-agnostic
