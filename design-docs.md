# Case Study Design System

## Design Tokens

### Color Palette

| Token | Value | Usage |
|-------|-------|-------|
| `--cs-text` | `#0a0a0a` | Headings, primary text |
| `--cs-body` | `#4e5a61` | Paragraph copy — slate grey-blue |
| `--cs-meta` | `#676a6c` | Navigation, captions, metadata |
| `--cs-muted` | `#ababab` | Eyebrow borders, quiet labels |
| `--cs-line` | `#e5e5e5` | Hairline dividers |
| `--cs-bg` | `#ffffff` | Page background |
| `--cs-slot-bg` | `#ffffff` | Empty media-slot fill |
| `--cs-slot-border` | `#d4d4d2` | Empty media-slot dashed border |
| `--cs-accent` | `#bb162c` | Brand accent (use sparingly — swap per project) |

### Typography

| Token | Font Stack |
|-------|-----------|
| `--cs-font-display` | Archivo, Helvetica Neue, Arial, sans-serif |
| `--cs-font-body` | Inter, -apple-system, Hiragino Sans, Noto Sans JP, sans-serif |

### Spacing & Layout

| Token | Value | Usage |
|-------|-------|-------|
| `--cs-measure` | 720px | Comfortable reading width for paragraphs |
| `--cs-page` | 1200px | Max width of page column |
| `--cs-gutter` | clamp(14px, 3vw, 38px) | Symmetrical side margin (reduced 40% from original) |
| `--cs-space-title-body` | 56px | Section header → paragraph spacing |
| `--cs-space-body-media` | 56px | Paragraph → image asset(s) spacing |

## Components

### Header

Sticky transparent header with brand mark and menu toggle.

```css
.cs-header {
  position: sticky;
  top: 0;
  z-index: 60;
  background: transparent;
}
```

- **Brand text**: Uppercase, Archivo 400, 15px, letter-spacing 0.04em
- **Menu toggle**: 14px, font-weight 500, hover color accent
- No border-bottom
- Padding: 22px on horizontal, gutter on sides

### Hero Section

Full-bleed image with title, subtitle, and eyebrow label.

```html
<header class="cs-container cs-hero">
  <span class="cs-eyebrow">Case Study</span>
  <h1 class="cs-title">Project Name</h1>
  <p class="cs-tagline">Subtitle</p>
</header>
<figure class="media-slot media-slot--bleed" style="--ar: 21/9;">
  <img src="..." alt="...">
</figure>
```

- **Title**: clamp(40px, 6vw, 64px), Archivo 400, line-height 1
- **Tagline**: 18px, max-width 720px (measure)
- **Eyebrow**: 11px, uppercase, 6px 12px padding, subtle border + light grey background

### Section

Standard content section with title, body text, and media assets.

```html
<section class="cs-section cs-container">
  <h2 class="cs-section-title">Section Title</h2>
  <div class="cs-section-body">
    <p>Body text...</p>
  </div>
  <figure class="media-slot" style="--ar: 21/9;">
    <img src="..." alt="...">
  </figure>
</section>
```

- **Section padding**: 64px top/bottom
- **Title**: clamp(24px, 3vw, 32px), Archivo 400, 56px margin-bottom
- **Body**: Max-width 720px (measure), line-height 1.65
- **Body → Title gap**: 56px
- **Body → Media gap**: 56px
- **Consecutive media**: 30px gap between each

### Media Slot

Flexible container for images with aspect ratio control.

```html
<figure class="media-slot" style="--ar: 16/10;">
  <img src="image.jpg" alt="Description">
  <figcaption>Caption (shown only if image missing)</figcaption>
</figure>
```

**CSS Variables:**
- `--ar`: aspect-ratio (default 16/10)

**Variants:**
- `.media-slot--bleed`: 21/9 aspect, full-width hero image
- `.media-slot--dark`: Black background (for phone rows, dark cards)
- `.media-slot--photo-bg`: Background image fill (used with `--bg` variable)
- `.is-empty`: Dashed border + centered caption when image fails to load

### Media Groups

Side-by-side media containers.

```html
<div class="media-group media-group--2">
  <figure class="media-slot" style="--ar: 4/3;">...</figure>
  <figure class="media-slot" style="--ar: 4/3;">...</figure>
</div>
```

**Variants:**
- `.media-group--2`: 1fr 1fr (50% / 50%)
- `.media-group--3`: repeat(3, 1fr) (33% / 33% / 33%)
- `.media-group--asym`: 1.3fr 1fr (56% / 44%)

**Responsive:** Collapses to single column at 720px

### Phone Row (Dark Box)

Three phone screens inside a black background slot.

```html
<figure class="media-slot media-slot--dark" style="--ar: 16/9;">
  <div class="phone-row phone-row--opportunity">
    <figure class="media-slot media-slot--phone">
      <img src="..." alt="...">
    </figure>
    <figure class="media-slot media-slot--phone">
      <img src="..." alt="...">
    </figure>
    <figure class="media-slot media-slot--phone">
      <img src="..." alt="...">
    </figure>
  </div>
</figure>
```

**Base Phone Specs:**
- Border: 6px solid #3a3a3a
- Border-radius: 20px
- Aspect-ratio: 9/16
- Min-height: 0 (allows flex items to respect aspect-ratio)
- Object-fit: cover

**Row Variants:**

**`.phone-row--opportunity`** (3 phones, 25.5% width each)
- Aspect-ratio: 720/1446 (narrower frame)
- 1st phone: scale(0.93)
- 3rd phone: scale(0.95)

**`.phone-row--solution`** (3 phones, equal width)
- All phones: aspect-ratio 9/16
- Scale(0.98) on all phones

**`.phone-row--platform`** (3 phones, height-driven, varying widths)
- 1st phone: aspect-ratio 1306/1022, no zoom
- 2nd phone: aspect-ratio 690/1258, no zoom
- 3rd phone: aspect-ratio 658/1252, no zoom
- Object-fit: contain (preserve full image)
- Height: 100%, width: auto

**Gap:** 24px between phones
**Padding:** 24px (around the entire row)

### Dark Grid (My Duties Section)

Card-based layout on dark background.

```html
<figure class="media-slot media-slot--dark media-slot--photo-bg" style="--ar: auto; --bg: url(...);">
  <div class="dark-grid">
    <div class="dark-card dark-card--full">
      <p class="dark-card-label">Card Title</p>
      <p class="dark-card-caption">One-sentence description</p>
      <img src="..." alt="...">
    </div>
    <div class="dark-card dark-card--wide">
      ...
    </div>
    <div class="dark-card dark-card--narrow">
      ...
    </div>
  </div>
</figure>
```

**Dark Card Specs:**
- Background: white
- Border: 6px solid #3a3a3a (matches phone frame)
- Border-radius: 20px
- Padding: 14px 12px 12px

**Card Layout Grid:**
- 12-column grid, 24px gap
- `.dark-card--full`: grid-column: span 12
- `.dark-card--wide`: grid-column: span 8
- `.dark-card--narrow`: grid-column: span 4

**Card Label:**
- Archivo 400, clamp(24px, 3vw, 32px)
- Black text, no margin-bottom

**Card Caption:**
- Inter 15px, max-width 720px
- 6px margin-top (light spacing under label)
- 32px margin-top when following an image (loose card)

**Card Images:**
- Object-fit: contain (preserve aspect)
- 16px margin-top
- Border-radius: 10px

**Card Pairs** (two images side-by-side):
- 45fr / 55fr grid split
- 16px gap
- Aligned to top

### Work List (Homepage)

Grid of case study cards.

```html
<div class="work-list">
  <a href="dior.html" class="work-item">
    <figure class="media-slot">...</figure>
    <div class="work-item-text">
      <h3>Dior</h3>
      <p>Boutique Booking Platform</p>
    </div>
  </a>
</div>
```

- Grid: 2 columns, 32px gap
- On hover: h3 text color becomes accent
- Responsive: 1 column below 640px

## Responsive Behavior

### Breakpoints

- **720px and below:** Media groups collapse to single column
- **640px and below:** Work list becomes 1 column

### Fluid Typography

Uses CSS `clamp()` for responsive scaling without media queries:

```css
font-size: clamp(MIN, PREFERRED, MAX);
```

Examples:
- Title: `clamp(40px, 6vw, 64px)`
- Section title: `clamp(24px, 3vw, 32px)`
- Gutter: `clamp(14px, 3vw, 38px)`

### Box Model

- `box-sizing: border-box` on all elements
- No left/right margins on sections (use padding via container)
- Reset browser defaults: `h1, h2, h3, p, figure { margin: 0; }`

## Key Principles

1. **Readable line length**: Body text capped at 720px (measure)
2. **Generous spacing**: 56px between sections, 30px between consecutive media
3. **Device frames preserved**: Phone bezels (6px borders) kept exact, images contained not cropped
4. **Dark backdrop contrast**: Black backgrounds (#000) with white cards (#fff) for visual hierarchy
5. **Typography hierarchy**: Archivo for headings (modern, geometric), Inter for body (friendly, readable)
6. **No bold font weights**: All text uses font-weight 400 or 500 only (600/700 removed for lighter aesthetic)
7. **Full-bleed hero**: Hero image extends edge-to-edge, establishes visual anchor

## Custom Properties Usage

Swappable tokens allow per-project theming without rewriting selectors:

```css
/* In the HTML, override at element level or globally: */
:root {
  --cs-accent: #your-brand-color;
  --cs-text: #your-text-color;
}

/* Or per-element: */
<div class="cs-section" style="--cs-accent: #new-color;">
```

This design system is derivative of Konrad Group's case study design.
