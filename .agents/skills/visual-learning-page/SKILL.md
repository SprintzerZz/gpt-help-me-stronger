---
name: visual-learning-page
description: 'Create or maintain interactive algorithm visualizations and technical interview learning pages. Use for algorithm problems, SQL/database tutorials, interview concepts, standalone HTML demos, shared vintage styling, searchable catalogs, or publishing learning pages.'
argument-hint: 'Algorithm problem ID and title, or interview-learning topic and goal, with any supplied HTML or source material'
user-invocable: true
---

# Visual Learning Pages

Use this workflow for algorithm visualizations and technical interview learning content. Both page types share the same visual identity and catalog conventions, but use different directory naming rules.

## 1. Classify the request

Choose the page type before editing:

- **Algorithm problem:** a named programming/algorithm challenge with a problem ID, examples, and an algorithm to demonstrate.
- **Interview learning content:** a concept lesson, such as SQL/MySQL, database behavior, or interview knowledge, without a problem ID.

If a request combines both, create separate pages using each type's directory convention, unless the user asks for one combined lesson.

## 2. Inspect the repository

- Identify the repository root, supplied HTML/source, requested page type, title, and expected destination.
- Read the root index and relevant neighboring pages. Follow the repository's existing category, link, tags, description, and layout conventions.
- Check `git status`, current branch, and configured remotes before editing. Preserve unrelated work.
- Check whether the requested topic already exists. Update an existing page rather than creating a duplicate.
- For algorithm problems, identify the problem platform/source and exact problem ID. For interview content, identify the learning objective and intended audience.
- Ask before proceeding if the page type, problem ID, English slug, or destination is materially ambiguous. Never invent a GitHub remote or publish to a different host.

## 3. Use the correct directory convention

- **Algorithm problem:** use a directory containing the problem ID followed by an English title, then `index.html`. Follow any existing platform/category parent directory:
  - `codefun2000/P5507-Reorder-List/index.html`
  - `<platform>/<problem-id>-<English-Problem-Title>/index.html`
- **Interview learning content:** use an English-topic directory without a problem ID, then `index.html`:
  - `MySQL/count/index.html`
  - `<topic>/<english-topic-slug>/index.html`
- Keep slugs concise, lowercase where neighboring directories do so, and separated with hyphens. Do not use Chinese directory names. Do not put an interview lesson under a problem ID.
- Keep each page self-contained and directly openable unless the repository already has a shared site architecture or stylesheet.

## 4. Preserve and teach the content

- Preserve the supplied problem statement, examples, constraints, algorithm, and interaction behavior for algorithm pages. Do not invent missing problem details; ask or clearly identify assumptions.
- For interview lessons, preserve supplied requirements and examples. Ensure example data, SQL/code, displayed results, and explanations agree. Distinguish database-specific behavior from general language or SQL behavior.
- Do not rewrite working demo logic as a side effect of styling. Preserve IDs, DOM hooks, handlers, and public page behavior. Only change logic when the user asks or a verified defect requires it.
- Build interactions that directly teach the requested concept: stepping through algorithm states, changing inputs, switching query forms, toggling NULL values, or comparing results.
- Use semantic headings, buttons, tables, and labels. Keep focus visible, keyboard operation usable, content responsive, and honor reduced-motion preferences when animations are used.
- Safely handle user-controlled text. Prefer `textContent` for plain text and escape values when constructing HTML.

## 5. Shared visual language

Use the established Claude-inspired vintage palette and editorial feel consistently across the index and every learning page:

```css
:root {
  color-scheme: light;
  --paper: #f3eee4;
  --paper-light: #fbf8f1;
  --paper-deep: #ebe3d5;
  --ink: #292923;
  --muted: #777267;
  --line: #ded5c7;
  --terracotta: #c76c4e;
  --terracotta-dark: #a74e37;
  --olive: #65745c;
  --olive-soft: #e8ecdf;
  --shadow: 0 18px 42px #382a1712;
}
```

- Use warm paper backgrounds, ink-colored text, restrained terracotta highlights, olive state colors, fine warm borders, and soft low-contrast shadows.
- Use serif display headings and readable sans-serif body text and controls. Keep cards and sections comfortably spaced with softly rounded corners.
- Use terracotta for primary actions and current-step emphasis; use warm neutral surfaces for secondary controls.
- Keep code panels dark charcoal/ink with warm off-white monospace text. Highlight active algorithm lines with muted olive and a terracotta edge.
- Keep semantic states distinguishable with labels, outlines, or shapes as well as color.
- Keep gradients and decorative texture subtle. Avoid blue/purple neon, heavy hard-edged shadows, repeated noisy textures, and external font dependencies.
- Keep styles local to standalone pages unless the repository has an established shared stylesheet.
- When a visual refresh is requested, inspect all repository HTML pages, including the root index and every demo, and correct visible drift without changing page-specific layouts unnecessarily.
- Never describe a page or the website as a "lab" or "laboratory". Do not use "实验室", "交互式实验室", "lab", or "laboratory" in visible page text, document titles, navigation, headings, or descriptions. Prefer "交互演示", "学习资料", or "学习索引".

## 6. Update the main index

- Add a card to the appropriate section using a relative URL that resolves to the new `index.html`.
- For an algorithm problem, include its problem ID, requested title, concise description, and accurate algorithm tags.
- For interview learning content, include a concise topic title, description, and useful search terms (including common acronyms and alternate spellings).
- Preserve the existing card structure, categories, accessible link/focus behavior, and search implementation. Do not remove or reorder unrelated entries.
- Update the displayed problem/page count only as the index convention requires. If the count is computed from visible cards, do not add a separate hard-coded total.
- Verify that the ID, title, description, or tags are included in searchable card text.

## 7. Validate

- Review the complete diff and run `git diff --check`.
- Verify the directory and `index.html` path match the selected page type, the catalog link resolves, and search finds the card by ID/title/topic.
- Check inline JavaScript syntax without altering demo logic. Confirm supplied behavior and examples are preserved.
- When browser tools are available, open the catalog and page. Check the card navigation, search, primary interaction, and desktop/narrow layouts; check for horizontal overflow.
- For a site-wide theme request, inspect all HTML pages and correct visual inconsistencies.
- Search all HTML pages for prohibited lab/laboratory wording and confirm none remain in user-facing content.
- Fix issues caused by the change; avoid broad unrelated repairs.

## 8. Commit and publish

- Inspect the repository's actual GitHub Pages configuration and URL before publishing. Use the existing configured publishing source; do not assume a repository, branch, or host.
- After validation, commit and push to the verified publishing branch by default unless the user asks not to. Stage only files related to the requested page, index, or theme change.
- Inspect the staged diff and run `git diff --cached --check` before committing. Use a concise commit message and include any repository-required trailers.
- Never create or configure a separate server or hosting project. If Pages configuration is absent or publishing fails, report that blocker instead of switching hosts.
- After pushing, verify the remote branch contains the commit. When Pages is configured, open the existing homepage and new page URL and confirm they serve the actual HTML and the index card reaches the page. Distinguish a pushed commit from a verified live deployment.
- Check the final working-tree status and preserve unrelated user changes.

## 9. Report

Summarize the page type and path, index update, validation, and commit/publishing status. Link workspace files using absolute paths and provide live Pages URLs only when verified.
