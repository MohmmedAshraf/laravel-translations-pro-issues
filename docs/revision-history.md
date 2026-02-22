# Revision History

Every translation change is tracked automatically, giving you a full audit trail with diff support and rollback capabilities.

## What's Tracked

Every time a translation value changes, Pro records:

- Old value and new value
- Who made the change
- Change type: Manual, Import, AI Translation, Rollback, or Bulk Operation
- Timestamp and metadata

## Viewing History

**Per-translation:** In the translation editor, view the full revision history for any key with paginated entries.

**Global history:** The **History** page shows all revisions across all translations, filterable by language, change type, and contributor.

## Diff View

Compare any two revisions with character-level diffing. Shows exactly what changed, with character count deltas.

## Rollback

**Single rollback:** Roll back any translation to a previous revision value directly from the editor.

**Bulk rollback by contributor:** Undo all changes made by a specific contributor between two dates. Useful when a batch of translations needs to be reverted.

**Bulk rollback by date:** Undo all changes after a given date, optionally filtered by language and change type.

**Rollback preview:** Before executing a bulk rollback, preview exactly which translations will be affected.

## Retention

Revisions are retained for a configurable number of days (default 90). The cleanup command always preserves the most recent revision per translation, regardless of age.

```bash
php artisan translations:cleanup-revisions
```

## Configuration

```php
// config/translations-pro.php

'revision_history' => [
    'enabled'        => true,
    'retention_days' => 90,    // 0 = keep forever
],
```
