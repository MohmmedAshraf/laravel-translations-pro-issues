# Artisan Commands

Pro adds four CLI commands for scanning, validation, and maintenance.

## translations:detect-hardcoded

Scan your project files for hardcoded user-facing strings.

```bash
php artisan translations:detect-hardcoded
```

**Options:**

| Option | Description |
|--------|-------------|
| `--path=` | Scan a specific directory instead of configured paths |
| `--type=` | Limit to a scanner type: `blade`, `vue`, `react`, `php` |
| `--min-words=` | Override minimum word count (default from config) |
| `--fix` | Launch interactive mode to convert or ignore detected strings |

**Exit codes:** `0` if no pending strings found, `1` if pending strings exist.

## translations:scan-context

Scan your codebase to find where translation keys are used and build usage context.

```bash
php artisan translations:scan-context
```

**Options:**

| Option | Description |
|--------|-------------|
| `--path=` | Scan a specific directory instead of configured paths |

Context is also scanned automatically after every import.

## translations:validate

Run quality validation checks on all translations.

```bash
php artisan translations:validate
```

**Options:**

| Option | Description |
|--------|-------------|
| `--language=` | Validate only a specific locale (e.g., `fr`, `de`) |
| `--check=` | Run only a specific check class |
| `--fix` | Auto-fix all fixable issues (whitespace) |

**Exit codes:** `0` if no errors found, `1` if validation errors exist.

## translations:cleanup-revisions

Delete old revision history entries beyond the retention period.

```bash
php artisan translations:cleanup-revisions
```

**Options:**

| Option | Description |
|--------|-------------|
| `--days=` | Override the retention period from config |
| `--dry-run` | Preview what would be deleted without actually deleting |

The most recent revision per translation is always preserved regardless of age.
