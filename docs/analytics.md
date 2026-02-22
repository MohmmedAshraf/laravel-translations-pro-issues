# Analytics

The analytics dashboard gives you a high-level view of your translation project's health and progress.

## Metrics

**Translation Coverage** — Percentage of translated keys per language, with an overall coverage average.

**Untranslated Counts** — How many keys are still untranslated for each language.

**Stale Translations** — Translations where the source text was updated after the translation was last saved. Shows per-language breakdown with days stale and the current values.

**Translation Velocity** — How many translations are completed per period. Includes monthly summaries and trend indicators (up/down).

**Contributor Leaderboard** — Top contributors ranked by translation output.

**Quality Scores** — Per-language quality scores based on validation results.

**Activity Feed** — Recent revisions, imports, and exports in a unified timeline.

## CSV Export

Export analytics data to CSV for reporting or external analysis.

## Filters

Filter the dashboard by language, date range, or contributor to focus on specific areas.

## Configuration

```php
// config/translations-pro.php

'analytics' => [
    'cache_ttl' => 3600,         // seconds to cache analytics data
    'velocity' => [
        'period_days' => 30,     // velocity calculation window
    ],
    'leaderboard' => [
        'limit' => 10,           // max contributors in leaderboard
    ],
],
```

Analytics data is cached to keep the dashboard fast. Adjust `cache_ttl` based on how frequently your translations change.
