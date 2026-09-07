---
name: ancient-culture-research
description: 搜图：收集和整理古代文献、碑铭、文物与高清图片。用户以“搜图”简称调用本技能，或提出古代资料及文物图片采集研究任务时使用；按任务难度分级处理以控制成本。
---

# Ancient Culture Research

Collect useful ancient materials and artifact images efficiently. Optimize cost through staged processing and keep the result easy to review and reuse.

## Model routing

When the environment permits model selection or delegation:

- Use the cheapest capable vision-and-text model for bulk discovery, OCR drafts, metadata extraction, deduplication, classification, and formatting. In the current GPT-5.6 family, prefer Luna.
- Escalate only flagged records to a balanced model for source comparison, dating, attribution, translation, and final verification. In the current GPT-5.6 family, prefer Terra.
- Reserve the strongest model for genuinely difficult cases such as damaged inscriptions, conflicting chronologies, disputed provenance, ambiguous iconography, or multi-source historical reasoning. In the current GPT-5.6 family, use Sol.
- If those models are unavailable, preserve the same cheap/balanced/strong routing by capability. Do not claim that a requested model was used unless it actually was.
- Model routing is an efficiency preference, not permission to create tasks, spend API credits, or contact external services. Use only tools and models already authorized for the request.

For small jobs, use the current model rather than adding routing overhead. When one pass reveals uncertainty, perform a focused second pass on the uncertain fields instead of repeating the whole collection.

## Research workflow

1. Clarify or infer the collection scope: culture or dynasty, date range, object type, geography, languages, intended use, and desired output. State consequential assumptions.
2. Search museums, archaeological publications, digital archives, academic resources, and useful image collections. Prefer clearer and more complete material.
3. Capture records in a consistent, user-friendly structure.
4. Deduplicate by title, period, object characteristics, page identity, and image similarity when available. Do not merge uncertain matches.
5. Flag incomplete, contradictory, low-resolution, or difficult-to-read items for focused review.
6. Deliver the requested artifact plus a short limitations note. Never imply exhaustive coverage unless the search was demonstrably exhaustive.

## Required record fields

Adapt the format to the user's requested table, database, JSON, or prose, but retain these concepts whenever available:

- `title_original` and `title_normalized`
- `object_type`
- `culture_or_dynasty`
- `date_as_stated` and `date_normalized`
- `creator_or_workshop`
- `material_technique`
- `dimensions`
- `findspot`
- `current_repository`
- `description`
- `inscription_original`, `transcription`, and `translation`
- `source_name` when useful
- `image_reference` and resolution when useful
- `notes`

Use null or “未提供” for missing data. Do not invent values to complete the schema.

## Accuracy rules

- Preserve the institution's wording for uncertain dates such as “约”“可能”“公元前3世纪末”. Normalization must not erase that uncertainty.
- Treat OCR and visual identification cautiously, especially when text or details are unclear.
- Do not infer authenticity, market value, legal ownership, excavation legitimacy, or cultural affiliation from appearance alone.
- Report obvious disagreements rather than silently choosing one version.
- Never present generated, restored, colorized, or reconstructed imagery as an original artifact photograph.

## Image handling

Distinguish whether an image shows the full object, a detail, reverse, inscription, excavation context, restoration, or reconstruction when that matters to the request.

- Downloaded images must be at least 1K resolution: the longest edge must be 1024 pixels or greater. Reject smaller images instead of upscaling them.
- Prefer images whose shortest edge is also at least 1024 pixels when a higher-resolution alternative exists.
- Do not count thumbnails, logos, navigation graphics, banners, QR codes, or unrelated page illustrations as collected artifact images.
- Verify the pixel dimensions and that the artifact or garment is the main subject before accepting each image.

Use lower-detail image analysis for broad triage when legibility is sufficient. Reinspect only relevant images or crops at higher detail for inscriptions, seals, tool marks, damage, or fine iconography. Avoid repeatedly sending identical full-resolution images.

## Token discipline

- Search and process in bounded batches.
- Extract structured fields rather than retaining entire pages in context.
- Cache and reuse stable source summaries and identifiers when supported.
- Pass only the disputed record and its evidence into verification, not the whole corpus.
- Keep final prose concise unless the user asks for an essay; attach or save large datasets in a structured file.
- Do not reduce accuracy by dropping important uncertainty notes.

## Output quality check

Before finishing, check for obvious duplicates, broken images, images below 1K, non-artifact page graphics, missing key fields, and contradictions. Summarize counts for collected, duplicate, rejected-below-1K, reviewed, and unresolved records when producing a dataset.
