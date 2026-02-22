# Approval Workflow

Route translations through a review process before they go live. Translators submit their work, and reviewers approve or reject with feedback.

## How It Works

When enabled, translations saved by translators are automatically set to **Needs Review** status instead of **Translated**. A reviewer must then approve them before they're considered final.

## Roles

The approval workflow uses the same role system as the free package:

- **Owner / Admin** — full access, can approve and reject
- **Reviewer** — can approve and reject translations in the review queue
- **Translator** — can translate, but translations go through review when the workflow is enabled

## Review Queue

Reviewers see a dedicated **Review Queue** page listing all translations pending review. The queue can be filtered by:

- Language
- Translation group
- Translator

## Approve / Reject

- **Approve** — marks the translation as approved and adds an automatic approval comment
- **Reject** — marks the translation as rejected, stores the reviewer's feedback, and adds a rejection comment visible to the translator
- **Bulk approve** — approve multiple translations at once

## Configuration

```php
// config/translations-pro.php

'approval_workflow' => [
    'enabled'            => true,   // set to false to disable entirely
    'require_review_for' => ['published'],
],
```

When `enabled` is `false`, translations are saved directly without going through review.
