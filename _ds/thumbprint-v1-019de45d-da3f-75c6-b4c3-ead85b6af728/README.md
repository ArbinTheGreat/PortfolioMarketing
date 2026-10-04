# Thumbprint — Thumbtack's Design System

This project packages **Thumbprint**, the design language used across all of Thumbtack's surfaces, into a reusable kit for Claude. Use it whenever you're designing for Thumbtack — consumer search, the Pro app, marketing pages, internal tools.

> Thumbtack helps people care for and improve their homes by matching them with skilled local pros. Thumbprint exists so every one of those touchpoints feels like the same product, made by the same team, in service of the same outcome.

---

## How to use

1. Link the two stylesheets:
   ```html
   <link rel="stylesheet" href="colors_and_type.css">
   <link rel="stylesheet" href="components.css">
   ```
2. Put any artboards, app screens, or marketing modules inside an element using the body font (`font-family: var(--font-family-body)`).
3. Use the class names documented in `components.css` (`.tp-btn`, `.tp-input`, `.tp-pill`, `.tp-card`, etc.). Reach for the CSS variables before writing new values — most design decisions are already in `colors_and_type.css`.
4. Icons live in `assets/icons/` as raw SVG. Drop them in with `<img>` or inline.

---

## Brand voice & content fundamentals

Thumbtack's voice is **confident, plainspoken, and warm**. We write like a knowledgeable neighbor who's done this a hundred times before — never a salesperson, never a robot, never overly clever.

**Voice principles**
- **Helpful, not pushy.** Tell people what they need to know to make a decision. If a price varies, say so. If a step is optional, say so.
- **Specific over generic.** "House cleaning, $120 avg." beats "Affordable services." Real numbers, real names, real outcomes.
- **Calm under pressure.** Errors and edge cases get the same warmth as happy paths. No exclamation points in error states.
- **Short.** Aim for the shortest sentence that's still warm. Cut adjectives first.

**Tone in components**
- Buttons: verb-led, ≤3 words. "Get started," "See pros," "Send message."
- Empty states: one sentence of context, one sentence of what to do next.
- Errors: name the problem, then offer the fix. "We couldn't load your inbox. Try refreshing."
- Confirmation: past tense, lowercase status pills. "Booked," "Sent," "Confirmed."

**Capitalization**
- Sentence case for headings, buttons, labels — **not** Title Case.
- Title case is reserved for proper nouns and product names ("Thumbtack," "Pro Plus").

**Numbers, currency, dates**
- US format by default: `$120`, `Mar 14`, `2:30 PM`.
- Always show currency for prices. Round honest averages to whole dollars.
- Star ratings use one decimal: `4.8`.

---

## Visual foundations

### Color
Thumbprint's palette is anchored on **Thumbtack Blue (`#009fd9`)**, used for primary action and brand accent. The palette is structured as 6-step ramps (`100`–`600`) for blue, indigo, purple, green, yellow, and red, plus a neutral ramp (`gray-200`, `gray-300`, `gray`, `black-300`, `black`).

- **Primary action / links:** `--tp-color-blue`
- **Success:** `--tp-color-green` family
- **Warning (yellow):** `--tp-color-yellow` family — use sparingly
- **Caution / destructive:** `--tp-color-red` family
- **Surfaces:** white on neutral; emphasis surfaces use `--tp-color-black`

Don't introduce new hues. If you need a new tint, pick one from the existing ramp.

### Type
The brand typeface is **Rise**, a custom variable sans (weights 100–900) loaded from `fonts/ThumbtackRiseVF.woff2`. It's already wired up via `--font-family-body`.

The type scale is **Title 1–8** (display + headings) and **Body 1–3** (paragraph). Use semantic classes (`.tp-title-2`, `.tp-body-1`) — don't pick raw sizes.

| Style | Size / Line | Use |
|---|---|---|
| Title 1 | 28 / 32 | Page lead |
| Title 2 | 24 / 28 | Section header |
| Title 3 | 22 / 28 | Card title |
| Title 4 | 20 / 28 | Subsection |
| Title 5 | 18 / 24 | Strong list item |
| Title 6 | 16 / 24 | Subheading |
| Title 7 | 14 / 20 | Form labels, micro |
| Title 8 | 12 / 18 (caps) | Eyebrows, tags |
| Body 1 | 16 / 24 | Default body |
| Body 2 | 14 / 20 | Secondary body |
| Body 3 | 12 / 18 | Captions, fine print |

### Spacing & radii
The spacing scale is the standard 4-baseline ramp: **4, 8, 16, 24, 32, 48, 64**. Stick to it.

Radii: `--radius-xs` (4) for inputs/buttons, `--radius-s` (6) for inputs, `--radius-m` (8), `--radius-l` (12) for cards, `--radius-xl/xxl` for hero surfaces, `--radius-pill` for chips and pills.

### Elevation
Four shadow steps (`--shadow-100` through `--shadow-400`). Cards use `--shadow-300` on hover. Modals use `--shadow-400`. Default surfaces are flat.

---

## Iconography

Thumbprint icons are **outlined, 2px stroke, 24×24 base** with optional small (18) and tiny (14) sizes. They live in `assets/icons/`. Common categories:

- **Navigation:** `arrow-left`, `arrow-right`, `caret-down`, `caret-right`, `close`, `search`, `hamburger`, `home`, `more-horizontal`, `settings`
- **Content actions:** `add`, `check`, `edit`, `filter`, `share`, `trash`, `phone-call`, `image`, `folder`, `preview`
- **Feature:** `bookmark`, `chat`, `camera`, `explore`, `inbox`, `messages`, `portrait`, `star`
- **Notification:** `info`, `warning`, `notification-bell`, `help`

Use them as `<img class="tp-icon" src="assets/icons/search.svg" alt="">` (decorative — empty alt) or inline the SVG when you need to recolor via `currentColor`.

When a needed icon isn't in the kit, use the closest match or a placeholder square — don't invent a new icon style.

---

## Components

`components.css` exports the building blocks. Highlights:

- **Button** (`.tp-btn` + `--primary` / `--secondary` / `--tertiary` / `--caution` / `--solid`, plus `--small` / `--large` / `--full`)
- **Text input** (`.tp-input`, `.tp-input-row`, `.tp-textarea`) + `.tp-label` + `.tp-form-note`
- **Checkbox / Radio** (`.tp-check`, `.tp-radio`)
- **Pill / Chip** (`.tp-pill` + color modifiers, `.tp-chip` + `--selected`)
- **Avatar** (`.tp-avatar` + `--xs/s/m/l/xl`)
- **Card** (`.tp-card`, `.tp-card--elevated`, `.tp-service-card`)
- **Alert banner** (`.tp-banner` + `--info/success/caution/warning`)
- **Modal** (`.tp-modal-scrim`, `.tp-modal`, header / body / footer)
- **Tooltip, Tabs, Stars, Loader dots, HR**

See the visual previews under the **Design System** tab or open the previews directly:
- `previews/colors.html`
- `previews/type.html`
- `previews/spacing.html`
- `previews/buttons.html`
- `previews/forms.html`
- `previews/cards-and-banners.html`
- `previews/modals.html`
- `previews/icons.html`

A live mockup of a Thumbtack consumer search results screen lives at `examples/search-results.html` — a good reference for how the system composes.

---

## Don'ts

- Don't introduce new fonts. Rise + system fallback only.
- Don't introduce new colors outside the ramp. New tints come from existing ramps.
- Don't use Title Case in product UI.
- Don't use emoji in production UI.
- Don't put gradients on backgrounds. Brand surfaces are flat.
- Don't reach for shadow as decoration — it signals elevation, not style.
