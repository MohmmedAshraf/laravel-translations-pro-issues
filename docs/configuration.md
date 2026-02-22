# Configuration Reference

All Pro configuration lives in `config/translations-pro.php`. Publish it with:

```bash
php artisan vendor:publish --tag=translations-pro-config
```

## AI Settings

```php
'ai' => [
    'provider' => env('TRANSLATIONS_AI_PROVIDER', 'openai'),
    'api_key'  => env('TRANSLATIONS_AI_API_KEY'),
    'model'    => env('TRANSLATIONS_AI_MODEL', 'gpt-4o-mini'),
    'batch' => [
        'chunk_size'     => 20,
        'max_concurrent' => 3,
    ],
    'cost_rates' => [
        'gpt-4o-mini'                => ['input' => 0.15,  'output' => 0.60],
        'gpt-4o'                     => ['input' => 2.50,  'output' => 10.00],
        'claude-sonnet-4-5-20250929' => ['input' => 3.00,  'output' => 15.00],
    ],
],
```

| Key | Description | Default |
|-----|-------------|---------|
| `provider` | Default AI provider | `openai` |
| `api_key` | API key for the default provider | — |
| `model` | Model to use with the default provider | `gpt-4o-mini` |
| `batch.chunk_size` | Keys per chunk in batch translation | `20` |
| `batch.max_concurrent` | Maximum parallel requests | `3` |
| `cost_rates` | Cost per 1,000 characters (USD) by model | See defaults |

## Validation

```php
'validation' => [
    'checks' => [
        MissingPlaceholderCheck::class,
        ExtraPlaceholderCheck::class,
        HtmlTagMismatchCheck::class,
        LengthRatioCheck::class,
        WhitespaceCheck::class,
        CasingCheck::class,
        UrlEmailPreservationCheck::class,
    ],
    'length_ratio' => [
        'min' => 0.5,
        'max' => 2.0,
        'overrides' => [],
    ],
],
```

| Key | Description | Default |
|-----|-------------|---------|
| `checks` | Array of check classes to run. Remove a class to disable it. | All 7 checks |
| `length_ratio.min` | Minimum acceptable target/source length ratio | `0.5` |
| `length_ratio.max` | Maximum acceptable target/source length ratio | `2.0` |
| `length_ratio.overrides` | Per-language ratio overrides (e.g., `'ja' => ['min' => 0.2]`) | `[]` |

## Hardcoded Detection

```php
'detect_hardcoded' => [
    'paths' => [
        'resources/views',
        'resources/js',
        'app',
    ],
    'extensions' => ['php', 'blade.php', 'tsx', 'jsx', 'vue'],
    'patterns' => [
        'min_word_count'  => 2,
        'min_char_length' => 5,
    ],
],
```

| Key | Description | Default |
|-----|-------------|---------|
| `paths` | Directories to scan | Views, JS, App |
| `extensions` | File extensions to scan | php, blade.php, tsx, jsx, vue |
| `patterns.min_word_count` | Minimum words for a string to be flagged | `2` |
| `patterns.min_char_length` | Minimum characters for a string to be flagged | `5` |

## Context Scanning

```php
'context_scanning' => [
    'paths' => [
        'resources/views',
        'resources/js',
        'app',
    ],
],
```

| Key | Description | Default |
|-----|-------------|---------|
| `paths` | Directories to scan for translation key usage | Views, JS, App |

## Revision History

```php
'revision_history' => [
    'enabled'        => true,
    'retention_days' => 90,
],
```

| Key | Description | Default |
|-----|-------------|---------|
| `enabled` | Whether to record revision history | `true` |
| `retention_days` | Days to retain revisions (0 = forever) | `90` |

## Analytics

```php
'analytics' => [
    'cache_ttl' => 3600,
    'velocity' => [
        'period_days' => 30,
    ],
    'leaderboard' => [
        'limit' => 10,
    ],
],
```

| Key | Description | Default |
|-----|-------------|---------|
| `cache_ttl` | Seconds to cache analytics data | `3600` |
| `velocity.period_days` | Window for velocity calculations | `30` |
| `leaderboard.limit` | Maximum contributors in leaderboard | `10` |

## Approval Workflow

```php
'approval_workflow' => [
    'enabled'            => true,
    'require_review_for' => ['published'],
],
```

| Key | Description | Default |
|-----|-------------|---------|
| `enabled` | Enable/disable approval workflow | `true` |
| `require_review_for` | Statuses that require review | `['published']` |

## Environment Variables

| Variable | Description | Default |
|----------|-------------|---------|
| `TRANSLATIONS_AI_PROVIDER` | Default AI provider | `openai` |
| `TRANSLATIONS_AI_API_KEY` | API key for the default provider | — |
| `TRANSLATIONS_AI_MODEL` | Model for the default provider | `gpt-4o-mini` |

Additional AI provider keys (for multi-provider support) are configured via `config/ai.php` from the [Laravel AI](https://github.com/laravel/ai) package.
