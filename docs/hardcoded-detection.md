# Hardcoded String Detection

Scan your codebase for user-facing strings that should be translated but are hardcoded directly in templates and source files.

## Supported File Types

- **Blade** templates (`.blade.php`)
- **PHP** files (`.php`) — including controller flash messages, validation messages, etc.
- **Vue** components (`.vue`)
- **React/JSX** components (`.tsx`, `.jsx`)

## Scanning

Run a scan from the **Hardcoded Text** page in the UI, or from the command line:

```bash
php artisan translations:detect-hardcoded
```

The scanner finds strings that match configurable criteria (minimum word count, minimum character length) and stores them with their file path, line number, element type, and surrounding context.

## Converting Strings

Once detected, you can convert hardcoded strings to translation keys:

1. Select a detected string
2. Pro suggests a key name based on the file path and text content
3. Preview exactly how the file will look after conversion
4. Confirm — Pro replaces the string in your source file and creates the translation key

**Batch convert** is supported for converting multiple strings at once.

**Parameter detection:** If a hardcoded string contains dynamic variables, Pro detects them and converts them to translation parameters (e.g., `:name`, `{count}`).

## Ignoring Strings

Not every detected string needs translation. You can:

- **Ignore a single string** — by its content hash (won't be flagged again in any file)
- **Ignore an entire file** — all strings in that file are ignored
- **Bulk ignore** — ignore multiple selected strings at once
- **Unignore** — remove ignore rules when needed

## Statuses

- **Pending** — detected and awaiting action
- **Converted** — string has been replaced with a translation key
- **Resolved** — string no longer found in the codebase (removed or changed)

## Configuration

```php
// config/translations-pro.php

'detect_hardcoded' => [
    'paths' => [
        'resources/views',
        'resources/js',
        'app',
    ],
    'extensions' => ['php', 'blade.php', 'tsx', 'jsx', 'vue'],
    'patterns' => [
        'min_word_count'  => 2,   // minimum words to flag a string
        'min_char_length' => 5,   // minimum characters to flag a string
    ],
],
```

Add or remove paths and extensions to control what gets scanned.
