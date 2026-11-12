# Abtal Science (أبطال العلوم)

Arabic RTL science practice app for grade 2 (Saudi curriculum, semester 1, 1446). One file, `index.html`, published by GitHub Pages from `main` at https://mafia3001.github.io/abtal-science/. Sister project: `abtal-math`.

## Publishing rule
Every change goes live right away: commit and push straight to `main` (no branch, no pull request) unless the owner asks otherwise.

## Source book
Page images are in the owner's Google Drive folder "SCIN conv" (folder id `1Wv61dpLufwzOIjKO2ap_1KvKQHdssWH-`), files `SCIN conv N.png`; book page number = N + 1. Drive's `search_files` with `snippetVerbosity` returns OCR text for many pages at once, which is much faster than reading one by one. Contents: intro skills (pp. 6-25), Unit 1 plants and animals (ch. 1-2), Unit 2 habitats (ch. 3-4), Unit 3 our Earth (ch. 5-6), student references (body, health, safety, glossary pp. 159-175).

## Adding a lesson
1. Add an entry to `LEVELS`: `id`, `g` (index into `GROUPS`), `tag` (book pages, e.g. `'ص ٣٠–٣٧'`), `name`, `sub`, `ex` (emoji), and `qs: () => [...]` returning question objects (a function so generators give new values each time).
2. Question builders: `MC(q, answer, wrongs[], why, showHTML)`, `TF(statement, bool, why, showHTML)`, `OR(q, [[emoji, text], ...in correct order], why)`. Use `EM('🌱')` for big emoji and `.emrow` for rows. Choices and ordering are shuffled automatically.
3. Generators (`classifyQ`, `habQ`, `seedsMath`, `frogMath`, `termQ`, `foodQ`) draw from tables at the top; use `REP(n, fn)` inside `qs` or `gen(fn, n)` to repeat them.
4. A round has up to 10 questions; keep at least 10 per lesson so rounds vary. The `mix` lesson samples 3 from every lesson automatically.
5. Update the contents list in `README.md`.

## Conventions
- Arabic text only, simple wording like the book; numbers in Arabic-Indic digits via `ar()`.
- Facts must come from the book (cite page in `tag`). Don't invent facts that contradict it.
- Images: use emoji or small inline SVG (see `PUPA`). Colours use the CSS tokens so light and dark themes work.
- Points: 10 per correct answer, +5 every 3 in a row. Don't change scoring unless asked.

## Before pushing
Open the page in headless Chromium at about 400px width, play each changed lesson once wrong and once right, and confirm there are no console errors.
