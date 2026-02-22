# Quality Validation

Pro runs 8 automated checks on every translation to catch common issues before they reach production.

## Built-in Checks

| Check | Severity | Auto-fixable | What it catches |
|-------|----------|--------------|-----------------|
| Missing Placeholder | Error | No | Translation is missing a `:name` or `{variable}` placeholder from the source |
| Extra Placeholder | Warning | No | Translation has placeholders not present in the source |
| HTML Tag Mismatch | Error | No | Opening/closing HTML tags don't match between source and translation |
| Length Ratio | Warning | No | Translation is suspiciously shorter or longer than the source |
| Whitespace | Info | Yes | Leading/trailing whitespace or double spaces |
| Casing | Info | Partial | First-letter capitalization doesn't match the source pattern |
| URL/Email Preservation | Error | No | URLs or email addresses in the source were altered in the translation |
| Glossary Compliance | Warning | No | Approved glossary translations weren't used |

## Automatic Validation

Validation runs automatically every time a translation is saved. Issues appear inline in the translation editor and in the Quality Report page.

## Quality Report

The Quality Report page shows all open validation issues across your project, sorted by severity (errors first). You can filter by language, check type, and severity.

**Bulk actions:**
- **Fix All** — auto-fix all fixable issues (whitespace)
- **Dismiss** — dismiss selected issues if they're intentional

## Batch Validation

Run validation across all translations at once using the UI or the CLI:

```bash
php artisan translations:validate
```

See [Artisan Commands](commands.md) for all options.

## Configuration

```php
// config/translations-pro.php

'validation' => [
    'checks' => [
        // Remove a class to disable that check
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
        'overrides' => [
            // Per-language overrides (some languages are naturally shorter/longer)
            // 'ja' => ['min' => 0.2, 'max' => 1.5],
            // 'de' => ['min' => 0.8, 'max' => 2.5],
        ],
    ],
],
```
