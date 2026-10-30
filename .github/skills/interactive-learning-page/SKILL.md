---
name: interactive-learning-page
description: 'Create or maintain standalone interactive learning pages in this repository. Use for MySQL/database tutorials, visual explanations, quizzes, simulations, adding learning resources to the searchable home catalog, applying the Claude-inspired vintage HTML theme, or removing lab terminology while preserving existing behavior.'
argument-hint: 'Topic and learning goal, with any supplied examples or source material'
user-invocable: true
---

# Interactive Learning Pages

Create accurate, approachable, offline-friendly teaching pages for this repository and keep them discoverable from the root catalog. All HTML pages must follow the shared Claude-inspired vintage theme, and page copy must not describe the site or a lesson as a "lab" or "laboratory".

## 1. Inspect the repository

- Read the root `index.html` and the relevant topic pages before making changes.
- Check `git status`, the current branch, and configured remotes. Preserve unrelated work.
- Follow the existing topic and slug conventions. Current MySQL pages live under `MySQL/<topic>/index.html`.
- Check whether the requested topic already exists. Update it rather than creating duplicate lessons; ask if the intended topic or destination is unclear.

## 2. Design the lesson

- Identify the target learner, learning goal, key concept, and the misconception or question the page should resolve.
- Organize the explanation around concrete examples. For database lessons, keep sample tables, SQL, and displayed results consistent with one another.
- Preserve supplied wording, examples, and requirements unless the user asks for editorial changes. Do not invent unsupported product behavior; distinguish MySQL syntax and limitations from general SQL concepts.
- Choose interactions that directly teach the concept, such as comparing before/after states, switching JOIN types, stepping through a process, or answering a short quiz. Explain the result and why it occurs.

## 3. Implement the page

- Put a new MySQL lesson at `MySQL/<short-kebab-case-topic>/index.html`, following neighboring pages. Use an existing category when one fits; do not create a new top-level structure without a clear need.
- Keep each lesson self-contained and usable by opening its HTML file directly. Prefer inline CSS and JavaScript; do not add frameworks, remote scripts, external fonts, build steps, or network-dependent content just for a lesson.
- Preserve existing DOM hooks and interactions when editing. Keep rendering, controls, examples, and explanations aligned; do not change lesson logic as a side effect of visual work.
- Use semantic headings, buttons and tables; provide accessible labels for interactive controls and visualizations. Keep keyboard focus visible, layouts usable on narrow screens, and honor reduced-motion preferences when transitions are used.
- Escape or otherwise safely handle user-controlled text before inserting it into HTML. Use `textContent` for plain text where practical.

## 4. Visual language

Use the root catalog and [algorithm visualization reference](https://sprintzerzz.github.io/algorithm-visualization/) as the reference identity: a warm paper palette, editorial serif headings, olive-green accents, and restrained terracotta highlights.

```css
:root {
  color-scheme: light;
  --bg: #f3eee4;
  --surface: #fbf8f1;
  --surface-soft: #eee8dc;
  --line: #ded5c7;
  --text: #292923;
  --muted: #777267;
  --green: #65745c;
  --green-dark: #4a5842;
  --coral: #c76c4e;
  --shadow: 0 18px 42px #382a1712;
}
```

- Use warm paper backgrounds, ink-colored text, fine warm borders, muted olive algorithm states, and terracotta actions or highlights. Keep code panels dark charcoal with warm off-white monospace text.
- Use serif display headings and readable sans-serif body text. Keep cards and sections softly rounded with low-contrast shadows.
- Maintain readable contrast; use labels or shapes as well as color to distinguish states.
- Keep gradients and decorative texture subtle. Avoid neon colors, heavy shadows, or requiring an external font to match the site.
- Preserve page-specific layouts where useful, but make new pages visually compatible with the catalog and existing learning pages.
- Keep styles local to each standalone HTML page unless the repository gains an established shared stylesheet.
- If the user requests a site-wide visual refresh, inspect and update every HTML page, including the root index and all lessons; do not leave pages on mixed themes.
- This vintage visual language is the default for every HTML page, not an optional theme. New pages, edited pages, and the root index must all use it.
- Never use "实验室", "交互式实验室", "lab", or "laboratory" in visible page text, document titles, navigation, headings, or descriptions. Prefer "交互演示", "学习资料", or "学习索引". Before finishing, search every HTML page for these terms and remove any remaining occurrences.

## 5. Update the root catalog

- Add one card inside the appropriate `.resource-section` in the root `index.html`, linking to the new lesson with a correct relative URL.
- Include a concise title and description, a category label consistent with neighboring cards, and accurate keywords in `data-search`. Include likely search terms, acronyms, and alternate spellings.
- Retain the existing card structure and accessible link/focus behavior. Do not rewrite the search implementation unless the current behavior cannot support the requested entry.
- The result count is calculated from visible cards; do not add or manually maintain a separate total.
- Do not remove or reorder unrelated entries.

## 6. Validate

- Review the full diff and run `git diff --check`.
- Confirm the new page exists at the intended path, the catalog link resolves, and its title/keywords are searchable.
- Check that the page works offline, all controls perform the stated action, and rendered examples agree with their explanations.
- Check inline JavaScript syntax with an available runtime or browser. When browser tools are available, inspect the catalog and lesson at desktop and narrow widths, search by a topic keyword, follow the card, and exercise the main interaction.
- For a theme-only request, compare all HTML pages and correct visual drift. Avoid unrelated fixes.
- Search all HTML pages for lab/laboratory wording and confirm no prohibited terms remain in user-facing content.

## 7. Commit and publish

- After validation, create a local commit and push by default unless the user asks not to.
- Stage only files related to the requested lesson, catalog, or theme changes. Inspect the staged diff and run `git diff --cached --check` before committing.
- Use a concise commit message describing the lesson or site change. Include the repository's required commit trailers.
- Push only to a verified configured remote and the intended branch. Never invent or silently change either. If Git metadata, authentication, or a remote update blocks publishing, report the exact blocker.
- Verify the resulting commit and final working-tree status.

## 8. Report

Summarize the lesson path, catalog changes, validation, and commit/publish status. Link workspace files using absolute paths.
