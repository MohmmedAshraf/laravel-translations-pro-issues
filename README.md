<h1 align="center">Laravel Translations UI Pro</h1>

<p align="center">
The professional add-on for <a href="https://github.com/MohmmedAshraf/laravel-translations">Laravel Translations UI</a>.<br>
Ship high-quality, AI-powered translations with built-in review workflows, quality checks, and full audit trails.
</p>

<p align="center">
<a href="https://dub.sh/transuipro">Get Pro</a> · <a href="docs/">Documentation</a> · <a href="../../issues/new?template=bug_report.yml">Report a Bug</a> · <a href="../../issues/new?template=feature_request.yml">Request a Feature</a>
</p>

---

## Features

**AI & Translation**
- Multi-provider translation (OpenAI, Anthropic, Gemini, and more)
- 5 variants per key with confidence scores
- Batch translate entire languages with cost estimation
- Glossary-aware prompts with per-language tone
- Context-aware: knows where each key is used

**Quality & Validation**
- 8 automatic checks on every save
- Glossary compliance enforcement
- Hardcoded string detection across Blade, PHP, Vue, React
- One-click convert to translation keys

**Workflow & Tracking**
- Approval workflow with review queue
- Revision history with character-level diffs and rollback
- Analytics dashboard with coverage, velocity, and leaderboard
- Activity log and threaded comments

---

## Quick Start

```bash
composer config repositories.outhebox.dev composer https://outhebox.dev/composer
composer config http-basic.outhebox.dev your-email@example.com your-license-key
composer require outhebox/laravel-translations-pro

php artisan translations:install
```

Add the private Composer repository and authenticate with your license key, then install. The install command handles everything — config, assets, migrations, and seeding for both the free and Pro packages. See the [Installation Guide](docs/installation.md) for detailed setup including AI provider configuration.

### Requirements

- PHP 8.2+
- Laravel 11+
- [Laravel Translations UI](https://github.com/MohmmedAshraf/laravel-translations) ^2.0
- [Laravel AI](https://github.com/laravel/ai) ^0.1 (for AI features)

---

## Documentation

| Topic | |
|-------|-|
| [Installation](docs/installation.md) | Setup, configuration, and prerequisites |
| [AI Translation](docs/ai-translation.md) | Providers, batch translation, cost estimation |
| [Glossary](docs/glossary.md) | Term management, CSV import/export |
| [Quality Validation](docs/quality-validation.md) | Checks, auto-fix, configuration |
| [Approval Workflow](docs/approval-workflow.md) | Review queue, roles, configuration |
| [Analytics](docs/analytics.md) | Dashboard, metrics, CSV export |
| [Hardcoded Detection](docs/hardcoded-detection.md) | Scanning, converting, ignoring |
| [Revision History](docs/revision-history.md) | Tracking, diffing, rollback |
| [Artisan Commands](docs/commands.md) | CLI tools for scanning, validation, cleanup |
| [Configuration](docs/configuration.md) | Full config reference |

---

## Issue Tracker

This repository is the issue tracker for Laravel Translations UI Pro.

- [Report a Bug](../../issues/new?template=bug_report.yml) — for unexpected behavior or errors
- [Request a Feature](../../issues/new?template=feature_request.yml) — for new features or enhancements

> Blank issues are disabled. Please use a template so your report includes all necessary info.

---

[Purchase Pro](https://dub.sh/transuipro) · [Free Package](https://github.com/MohmmedAshraf/laravel-translations) · [Discussions](../../discussions)
