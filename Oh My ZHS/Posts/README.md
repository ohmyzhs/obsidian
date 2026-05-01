# Oh My ZHS Posts

Obsidian editorial source for oh-my-zhs.com posts.

## Template source
- `00-System/Templates/Blog Draft Harness Template.md`
- `00-System/Templates/Posting Draft Template.md`

## Publishing flow
1. Draft and expand notes here by category.
2. Keep `status: draft` until the article is ready.
3. Copy approved Markdown into the repo under `content/posts/<category>/<slug>.md`.
4. Set repo copy to `status: published`.
5. Run `npm run lint && npm run build` in `agency-web`.
6. Commit and deploy.

## Categories
- `01-Guides`: evergreen tool-adjacent guides.
- `02-IT-News`: sourced IT/news/trend notes.
- `03-Daily`: site/build/daily notes.
- `04-Experiments`: typing, lab, tarot/saju-style experiments kept separate from core trust pages.

## Public URL policy
- Canonical: `/posts`, `/posts/[slug]`
- Friendly alias: `/blog` redirects to `/posts`
- `/guides` remains a filtered guide landing, not a separate article namespace.

Updated: 2026-05-01
