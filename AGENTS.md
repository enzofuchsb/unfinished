# AGENTS.md — UNFINISHED

Rules and context for any AI agent working in this repository. Read this file fully before suggesting, writing or changing anything.

## 1. What this project is

**UNFINISHED** is an individual college project (course: Research and Innovation). It is a personal website, a visual autobiographical blog in the format of an independent zine, built by a student who must be able to explain and defend every part of it.

- **Central theme:** skateboarding. It is the backbone of the story.
- **Supporting themes:** music and artists, personal style and looks, visual references and alternative culture, plus any other interests the author decides to include.
- **It is not** a store, a skate catalog, a news site, an encyclopedia or a conventional professional portfolio. Nothing is being sold.
- **Meaning of the name:** an identity and a trajectory still under construction. This is a conceptual reading, not a statement about the author's life.
- **Language of the site content:** Brazilian Portuguese (pt-BR).

## 2. Hard rules (never break these)

1. **No external APIs or third-party services without explicit authorization from the author.** The professor forbids them unless there is a strong justification and he approves. This includes music APIs, maps, third-party auth, game catalogs, stock image services, CDNs, hosted fonts (for example Google Fonts), analytics and hotlinked images. The project's own Node.js API is not an external API.
   - If an idea depends on an external service: say which service, why it would help, offer an alternative that does not need it, say the author must ask the professor, and wait for the decision. Do not implement anything in the meantime.
   - Free or easy does not mean allowed. When in doubt about a library or dependency, ask first.
2. **Never invent biographical content.** No events, dates, places, people, feelings, bands, brands or achievements. The author decides the story. Use clearly generic placeholder text when sample copy is needed, and say it is a placeholder.
3. **Work step by step.** Do not build the whole site at once. Do not generate code, create files or integrate services before the author asks for that specific step.
4. **Do not decide pending items for the author** (see section 9). Ask, or wait for the material.
5. **Be honest about status.** Never claim something works before it was actually checked. If you could not run or test something, say so. Point out problems directly.

## 3. How to work with the author

The author is learning and wants to **write most of the site by hand**.

- **Always reply to the author in Brazilian Portuguese (pt-BR)**, including explanations, summaries and questions.
- Prefer lean, simple, well-executed solutions over clever ones. Avoid unnecessary complexity.
- Explain what a relevant piece of code does, why it was chosen and how to test it.
- When there are several valid approaches, compare pros and cons and recommend one with a reason.
- When the author sends existing code, understand its structure first, then suggest changes and justify each one.
- When something fails, explain the cause and the fix, not only the corrected code.
- Skeleton and starter files must be minimal and **heavily commented**: what each part is, and what the author can change.
- Comments in code are written in Portuguese (pt-BR), in a teaching tone, matching the existing files.
- Do not rewrite a whole file when a small, targeted change is enough. The author edits files locally, so a full replacement can erase their changes. Prefer showing the exact lines to change.

## 4. Tech stack

| Layer | Technology | Notes |
| --- | --- | --- |
| Structure | HTML | semantic tags, accessible markup |
| Look | CSS | separate file, no frameworks unless approved |
| Behavior | JavaScript | front-end interaction, validation, data handling |
| Back end | Node.js | the project's own API |
| Database | MySQL | relational |
| Dashboard | WebDataViz | tool required by the professor; its exact role is **not defined yet** |

Do not assume WebDataViz replaces Node.js or MySQL.

## 5. Repository structure

```
README.md           project presentation (animated SVGs live in assets/)
AGENTS.md           this file
assets/             SVG files used only by the README
img/                site photos (author's own images)
pages/index.html    home page
styles/style.css    all site styles
```

- CSS stays in its own file, never inline in the HTML.
- Paths are relative to each file. From `pages/index.html`, the stylesheet is `../styles/style.css` and images are `../img/...`.
- Image file names: lowercase, no spaces, no accents (for example `hero.jpg`).
- The page structure is **provisional**. It will be defined after the author chooses the story to tell. Do not lock a final navigation architecture before that.

## 6. Visual identity

Underground, grunge, alternative and editorial. The reference is an independent magazine or a visual diary: collage, torn paper, print noise, oversized type, small text floating on dark areas. Deliberately imperfect, but never at the cost of readability, navigation or usability. It must not look like a corporate template.

**Palette (four colors, defined as CSS variables):**

| Name | Value | Use |
| --- | --- | --- |
| Black | `#080808` | page background |
| Paper (white) | `#f2f0eb` | text and cut-outs |
| Red | `#b52f2b` | highlights, strips, labels |
| Green | `#9bb34a` | **almost never**: tiny accents only (a dot, a small label) |

**Typography:** system fonts only (Arial for titles and UI, Georgia for body copy). A custom font is allowed only if the font file is stored in the repository.

**Signature details to preserve:**
- The home title is `UN` filled in paper color and `FINISHED` as outline only (`color: transparent` plus `-webkit-text-stroke`), with very tight letter spacing and line height.
- Photos are shown in black and white (CSS grayscale) so the author can keep original color files.
- Tilted frames with a hard, offset red shadow; red strip with spaced uppercase text; small red label on photos.
- Animations and interactions are subtle and must serve the content.

Keep the visual identity consistent across every page.

## 7. Functional requirements

- **Sign-up and login pages are mandatory** and must be real, not visual mockups:
  - registration form and login form with validation;
  - front end talks to the back end, which talks to MySQL;
  - passwords stored with a proper hash on the back end (never plain text);
  - credentials verified at login;
  - clear error handling and user feedback, with API errors handled properly.
- **Dashboard** is mandatory and must use real data from the source defined for the project, not decorative charts. What it shows is **undecided**: do not assume it will show user statistics, sign-ups or autobiographical content.
- **Loops and arrays** must be used in the code, in a legitimate way that fits real features (for example, rendering a list of cards from an array with a loop). Never add them artificially just to tick a requirement. Explain where and why they are used.
- Sessions, tokens and other auth decisions are not defined yet. Ask before choosing.

## 8. Code conventions

- Keep HTML semantic (`header`, `nav`, `main`, `section`, `article`, `figure`, `footer`) and give every `<img>` a meaningful `alt`.
- Keep the layout responsive. The current mobile breakpoint is `max-width: 760px`.
- Use the CSS variables from `:root` instead of hard-coded colors.
- Follow the naming style already present in the files. Do not rename classes or restructure files without being asked.
- Do not use `localStorage` to fake authentication or persistence of user data.
- Never commit secrets (database passwords, keys). Use environment variables and keep them out of the repository.
- SQL: do not use `BOOLEAN`, `CAST` or `ROUND` unless the author explicitly asks for them.
- Keep commits small and understandable. The project is published on GitHub and updated weekly, and the evolution must be demonstrable.

## 9. Still undefined (do not treat as decided)

- The personal story and which events, experiences and references will be shared.
- The final page structure and navigation.
- The professor's material on WebDataViz.
- The purpose and data of the dashboard.
- Technical details of the sign-up and login architecture, including form fields.
- Any grading or implementation rule not yet clarified.

## 10. Schedule (reference, not a rigid sequence)

| Week | Focus |
| --- | --- |
| 1 | Start: initial definition of project and theme |
| 2 | Theme and documentation, GitHub organization |
| 3 | Start of the site: initial structure, Home page, visual identity |
| 4 | Data: data features, database integration, backlog and code organization |
| 5 | Dashboard: development, integration, validation of charts and data |
| 6 | Presentation: slides, demo planning |

Final presentation: November 30 and December 4, about 10 minutes. It must show the visual result and the technical learning, including how the front end, back end, API and database communicate, and mastery of WebDataViz. Help build it truthfully, without inventing difficulties, achievements or lessons the author did not report.

## 11. Before you answer, check

- [ ] Does this need an external service? If yes, stop and ask.
- [ ] Am I inventing anything about the author's life? If yes, remove it.
- [ ] Was this step actually requested?
- [ ] Is it simple enough for the author to explain line by line?
- [ ] Did I claim something works without verifying it?