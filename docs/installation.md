# Installation

## Prerequisites

- PHP 8.2 or higher
- Laravel 11 or higher
- [Laravel Translations UI](https://github.com/MohmmedAshraf/laravel-translations) ^2.0 installed and configured
- [Laravel AI](https://github.com/laravel/ai) ^0.1 (required for AI translation features)

## Step 1: Install the Package

Add the private Composer repository and authenticate with your license key:

```bash
composer config repositories.outhebox.dev composer https://outhebox.dev/composer
composer config http-basic.outhebox.dev your-email@example.com your-license-key
```

Then install the package:

```bash
composer require outhebox/laravel-translations-pro
```

Your email and license key are available from your [account page](https://dub.sh/transuipro). The service provider registers automatically via Laravel's package discovery.

## Step 2: Run the Install Command

The free package's install command automatically detects Pro and handles everything — config, assets, migrations, and seeding:

```bash
php artisan translations:install
```

This will:
- Publish both free and Pro configuration files
- Publish both free and Pro frontend assets
- Run all migrations (including Pro's tables)
- Seed default languages
- Create the first contributor (if using the contributors auth driver)

### Pro Tables Created

| Table | Purpose |
|-------|---------|
| `ltu_key_contexts` | File/line usage context for translation keys |
| `ltu_ai_usage_logs` | AI provider call logs (cost, characters, success) |
| `ltu_revisions` | Translation change history |
| `ltu_activity_logs` | User action audit trail |
| `ltu_glossary_terms` | Glossary source terms |
| `ltu_glossary_translations` | Per-language approved glossary translations |
| `ltu_translation_comments` | Comments on translations |
| `ltu_hardcoded_strings` | Detected hardcoded strings |
| `ltu_hardcoded_ignores` | Ignore rules for hardcoded detection |
| `ltu_validation_issues` | Persisted quality validation issues |

Pro also adds a `reviewer_feedback` column and an index on `ai_generated` to the free package's `ltu_translations` table.

## Step 3: Configure AI Providers

Pro uses [Laravel AI](https://github.com/laravel/ai) for all AI functionality. Add your provider credentials to `.env`:

```env
TRANSLATIONS_AI_PROVIDER=openai
TRANSLATIONS_AI_API_KEY=sk-your-key-here
TRANSLATIONS_AI_MODEL=gpt-4o-mini
```

To use multiple providers (selectable in the UI), configure them in `config/ai.php`:

```env
OPENAI_API_KEY=sk-...
ANTHROPIC_API_KEY=sk-ant-...
GEMINI_API_KEY=...
```

Any provider with a configured API key will appear as an option in the AI Settings page.

**Supported providers:** OpenAI, Anthropic, Gemini, DeepSeek, Groq, Mistral, xAI, OpenRouter, Ollama, Cohere, Jina, VoyageAI, ElevenLabs.

## Verify Installation

Visit `/translations` in your browser. You should see the Pro navigation items in the sidebar: Analytics, AI Settings, Glossary, Hardcoded Text, Quality Report, History, Review Queue, and Activity Log.

## Updating

```bash
composer update outhebox/laravel-translations-pro
php artisan translations:update
```

The update command handles both free and Pro automatically — re-publishes assets and runs any new migrations.

This re-publishes assets for both packages and runs any new migrations.

You can automate this in your `composer.json`:

```json
{
    "scripts": {
        "post-update-cmd": ["@php artisan translations:update --ansi"]
    }
}
```
