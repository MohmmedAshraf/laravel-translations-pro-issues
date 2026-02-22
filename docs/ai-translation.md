# AI Translation

Pro integrates with multiple AI providers to translate your keys with context-aware, high-quality results.

## How It Works

When you translate a key, Pro builds a rich prompt that includes:

- The source text and target language
- File/line usage context from your codebase (where the key is used, what HTML element it's in)
- Glossary terms that appear in the source text, with their approved translations
- Per-language tone/formality settings
- Sibling keys from the same group for consistency
- Quality rules (preserve placeholders, HTML, URLs, match casing)

## Single Key Translation

In the translation editor, click the AI translate button on any key. Pro returns **5 variant suggestions**, each with:

- The translated text
- A confidence score
- Style notes explaining the translation choice

Choose the variant that best fits your context.

## Batch Translation

Translate many keys at once:

1. Navigate to a language
2. Use the batch translate action
3. Pro splits keys into chunks (configurable, default 20 per chunk) and processes them via a queued job
4. Track progress in real-time via the UI

You can cancel a batch translation mid-job.

## Translate Entire Language

One-click translation of all untranslated keys for a given language. This dispatches a batch job behind the scenes.

## Cost Estimation

Before committing to a batch or full-language translation, Pro estimates the cost based on:

- Character count of source texts
- Provider and model rates (configurable in `config/translations-pro.php`)
- Breakdown by input/output tokens

## Provider Comparison

Send a single key to multiple providers simultaneously and compare results side-by-side. Useful for evaluating translation quality across providers before committing to one.

## AI Review

After translating, send key pairs to the AI review agent for quality assessment. The review checks for issues like meaning shifts, formality mismatches, and placeholder handling.

## Per-Language Tone

Set a tone/formality level for each target language in the AI Settings page. This is applied to every AI translation for that language. Options like formal, informal, technical, or casual help maintain consistency.

## Usage Tracking

Every AI call is logged to `ltu_ai_usage_logs` with:

- Provider and model used
- Input/output character counts
- Estimated cost in USD
- Success/failure status

View aggregated usage stats in the AI Settings page, broken down by provider and time period.

## Configuration

```php
// config/translations-pro.php

'ai' => [
    'provider' => env('TRANSLATIONS_AI_PROVIDER', 'openai'),
    'api_key'  => env('TRANSLATIONS_AI_API_KEY'),
    'model'    => env('TRANSLATIONS_AI_MODEL', 'gpt-4o-mini'),
    'batch' => [
        'chunk_size'     => 20,   // keys per chunk in batch translate
        'max_concurrent' => 3,
    ],
    'cost_rates' => [
        // cost per 1,000 characters (USD)
        'gpt-4o-mini'                => ['input' => 0.15,  'output' => 0.60],
        'gpt-4o'                     => ['input' => 2.50,  'output' => 10.00],
        'claude-sonnet-4-5-20250929' => ['input' => 3.00,  'output' => 15.00],
    ],
],
```

Add entries to `cost_rates` for any models you use to get accurate cost estimates.
