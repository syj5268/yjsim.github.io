# Shared Publications Design

## Goal

Use `_bibliography/papers.bib` as the single source of publication data for both the main Publications page and the CV Publications section.

## Current State

- The main Publications page renders `_bibliography/papers.bib` through Jekyll Scholar.
- The CV Publications section separately renders publication objects from `assets/json/resume.json`.
- Updating a publication therefore requires editing two data sources, which can leave the pages inconsistent.

## Design

The CV Publications include will invoke Jekyll Scholar directly with a CV-specific bibliography template. The template will render every BibTeX entry and show only bibliographic information appropriate for a CV: title, authors, venue, and year.

The main Publications page will continue using its existing `bib` template, including PDF and Code buttons. The CV-specific template will not render PDF, Code, or other action buttons and will not add links to publication titles.

The `publications` key in `assets/json/resume.json` will remain only as a structural marker so the existing generic CV layout preserves the Publications section's position. It will not contain duplicated paper metadata.

## Files

- `_bibliography/papers.bib`: canonical publication data; no structural change.
- `_includes/resume/publications.liquid`: render the bibliography instead of JSON publication objects.
- `_layouts/bib_cv.liquid`: new CV-only Jekyll Scholar entry template without links or action buttons.
- `assets/json/resume.json`: replace duplicated publication objects with a structural marker.

## Verification

- Build the Jekyll site successfully.
- Confirm every title in `_bibliography/papers.bib` appears on both `/publications/` and `/cv/`.
- Confirm the CV publication entries show title, authors, venue, and year.
- Confirm `/cv/` contains no PDF or Code controls in its Publications section.
- Confirm `/publications/` retains its existing PDF and Code controls.
