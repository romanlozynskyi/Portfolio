# Legacy media assets

Images referenced by the engineering case studies in [`../case-studies/`](../case-studies/). These are separate from the Astro site's own case content in [`../src/content/cases/`](../src/content/cases/), which has its own self-contained structure and README.

## Structure

Each project gets its own folder, split by evidence type:

```
assets/<project>/
  cover/          # a single hero/overview image representing the product
  screenshots/    # specific feature or UI screenshots
  testimonials/   # client review screenshots + testimonials.json metadata
```

Only create the subfolders a project actually has evidence for. Don't add empty placeholder folders.

## Testimonial metadata

When a `testimonials/` folder contains a review screenshot, add a matching entry to a `testimonials.json` array in that same folder, transcribing only what's visibly readable in the image — never invent a quote, name, rating, or date that isn't shown. Fields:

| Field | Meaning |
|---|---|
| `id` | Unique slug, `<project>-<source>-<n>` |
| `project` | Matches the parent folder name |
| `source` | Platform the review came from (e.g. `Upwork`, `Google`, `Email`) |
| `sourceContext` | Job/project title as shown, if any |
| `rating` | Numeric rating if shown, else `null` |
| `dateRange` | As displayed, else `null` |
| `quote` | Transcribed text, exactly as visible |
| `quoteTruncated` | `true` if the visible text is cut off (e.g. "...See more") |
| `clientEndorsements` | Tag list if shown, else `[]` |
| `clientName` | Only if actually visible in the image, else `null` |
| `image` | Filename within the same `testimonials/` folder |
| `featured` | `true` if this testimonial should be surfaced publicly |
| `featuredOrder` | Display order among featured testimonials (`1` = first), else `null` |

Marketplace pricing (rate, price type, job budget) is never captured in this metadata, even if visible in the source screenshot — it's not for public display.

## Referencing from case studies

Markdown case studies under `../case-studies/` link images with relative paths, e.g. `../assets/<project>/cover/<file>`. Update the reference in the same commit as any move or rename.
