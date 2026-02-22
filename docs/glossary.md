# Glossary Management

The glossary ensures consistent terminology across all translations. Define approved terms once, and they're enforced during quality checks and injected into AI prompts.

## Creating Terms

In the Glossary page, add a term with:

- **Source text** — the term in your source language
- **Case-sensitive** — whether matching should respect casing
- **Exact match** — whole-word matching only (prevents matching substrings)
- **Context notes** — optional guidance for translators on when/how to use this term

## Per-Language Translations

Each glossary term can have approved translations for every target language. Set these individually or in bulk using the "Set translations" action.

## How Glossary Works

**In the editor:** When editing a translation, Pro highlights glossary terms found in the source text and shows their approved translations as inline suggestions.

**In AI translation:** Matching glossary terms and their approved translations are automatically included in the AI prompt, ensuring the AI uses your approved terminology.

**In quality checks:** The glossary compliance check verifies that approved translations are used in the translated text. Violations appear as warnings in the Quality Report.

## CSV Import/Export

**Export:** Download the full glossary as CSV, optionally filtered by language. Useful for sharing with external translators or archiving.

**Import:** Upload a CSV file to bulk-add terms and translations. Pro shows a preview before committing, so you can review what will be created or updated.

## Matching Behavior

- **Case-sensitive off (default):** "API" matches "api", "Api", etc.
- **Exact match on:** "test" only matches the word "test", not "testing" or "contest"
- **Exact match off:** "test" matches anywhere, including inside other words
