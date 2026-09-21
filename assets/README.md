# Legacy media assets

Images referenced by the engineering case studies in [`../case-studies/`](../case-studies/). These are separate from the Astro site's own case content in [`../src/content/cases/`](../src/content/cases/), which has its own self-contained structure and README.

## Structure

Each project gets its own folder for cover/screenshot evidence:

```
assets/<project>/
  cover/          # a single hero/overview image representing the product
  screenshots/    # specific feature or UI screenshots
```

Testimonials are **not** nested under a project — see below.

Only create the subfolders a project actually has evidence for. Don't add empty placeholder folders.

## Testimonials are global, not per-project

All client reviews live in one place: [`testimonials/`](testimonials/), with a single [`testimonials.json`](testimonials/testimonials.json) array. A testimonial is social proof first — it doesn't have to be tied to a specific case study to be worth showing. `project` is **nullable**: set it to a project slug only when the review clearly names or obviously matches that product; otherwise leave it `null` rather than guessing. Never silently guess — a testimonial whose match is uncertain still gets included (it's still real social proof), just with `"projectConfirmed": false` and a `note` explaining the ambiguity.

Fields, transcribing only what's visibly readable in the image — never invent a quote, name, rating, or date that isn't shown:

| Field | Meaning |
|---|---|
| `id` | Unique slug |
| `project` | Project slug if confidently matched, else `null` |
| `projectConfirmed` | `true` only when the match is certain (named product, known client) |
| `source` | Platform the review came from (e.g. `Upwork`, `Google`, `Email`), else `null` |
| `sourceContext` | Job/project title as shown, if any |
| `rating` | Numeric rating if shown, else `null` |
| `dateRange` | As displayed, else `null` |
| `quote` | Transcribed text, exactly as visible |
| `quoteTruncated` | `true` if the visible text is cut off (e.g. "...See more") |
| `clientEndorsements` | Tag list if shown, else `[]` |
| `clientName` | Only if actually visible in the image, else `null` |
| `clientTitle` | Role/company as shown, if any, else omit |
| `hasClientPhoto` | `true` if the source image includes a real photo of the client |
| `verified` | `true`/`false` if the source shows a verification badge, else `null` |
| `image` | Filename within `testimonials/` |
| `featured` | `true` if this testimonial should be surfaced publicly |
| `featuredOrder` | Display order among featured testimonials (`1` = first), else `null` |

Marketplace pricing (rate, price type, job budget) is never captured in this metadata, even if visible in the source screenshot — it's not for public display.

## Sanitization policy

The default is to **use** the strongest available screenshot, not discard it for containing PII. Raw originals in `../incoming/` and `../testimonials/` (both gitignored, never published) are the only place unredacted material lives. Every file under `assets/` is a sanitized derivative, produced by masking or cropping — never just blurring — visible emails, phone numbers, physical addresses, usernames, workspace/tenant names, and unrelated third-party identities that aren't the product's own public-facing content (e.g. a platform's own listed coaches are fine to keep; a stranger's forum username in a sidebar is not).

**Exception — live credentials:** if a screenshot shows what looks like a real API key, token, or secret, it is never published in any form, blurred or not, because a blur can sometimes be reconstructed and the risk is asymmetric. The secret region is fully masked/cropped out of the derivative, and the finding is flagged separately for rotation — treat it as a live-credential incident, not just an image-editing task.

Redaction here is done with solid-fill rectangles (sampled from the surrounding background so the patch blends in) or hard crops that drop the offending region entirely — built with Pillow via a one-off script per batch, not a reusable tool in this repo.

## Referencing from case studies

Markdown case studies under `../case-studies/` link images with relative paths, e.g. `../assets/<project>/cover/<file>` for cover/screenshots, or `../assets/testimonials/<file>` for a testimonial. Update the reference in the same commit as any move or rename.

## Home featured order

[`projects.json`](projects.json) at the root of this folder is the single canonical source for which projects are featured on Home and in what order (`featured` + `featuredOrder`). It's a plain, hand-editable JSON array — reorder or toggle projects there, no code or prose changes needed. `README.md` and `case-studies/README.md` are kept in sync with it by hand for now (there's no build step that generates them from this file); if that ever changes, this file is the thing a generator should read.

## Websites (external-link cards)

[`websites.json`](websites.json) lists standalone websites that appear on the site's "Websites & Landing Pages" Work category page as their own cards linking straight to the live site (no internal case-study page). Add an entry to show another site; no code changes needed. Fields: `slug`, `name`, `url` (required, https — an entry without a real live URL is skipped with a warning, never guessed), `cover` (path to a repo image, ideally `assets/websites/<slug>/cover/cover.jpg`, 16:9), `description` (`en` required, `uk` optional), `visible` (default `true`), `order` (ascending).
