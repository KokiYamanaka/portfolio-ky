# Portfolio – Change Tasks

Local preview: `python3 -m http.server 3000` → http://localhost:3000

## Tasks

### 1. Update hero tagline text
- **File:** `index.html` (hero, `.home-hero-tagline`, line ~44)
- **Current:** "I **manage** and **build** digital marketing products for enterprises."
- **Change to:** "manage and build digital products for enterprises"
- **Open question:** the narration didn't name the exact element. Assumed this is the hero tagline (drop "marketing"); confirm before implementing. Keep the bold on "manage" and "build".

### 2. Section "01 Project Management" – change card layout
- **File:** `index.html` (section starting at line ~86) and its styles (`style.css`)
- **Current:** four cards stacked vertically, each one a tall, narrow, short-form-video-style (portrait) card.
- **Change to:**
  - Make each card wider (landscape-style) instead of narrow portrait.
  - Reduce card height by about 40%.
  - Keep the cards stacked vertically (one per row); do not switch to a horizontal row.
  - The company name and the title must stay clearly visible on every card after the resize.
- **Open question:** the narration was ambiguous about stacked vs. side-by-side ("convert it horizontally, but ... show it vertically"). Interpreted as: wider cards, still stacked vertically. Confirm.
- **Done when:** all four cards are wide and ~40% shorter, with company name and title readable, on desktop and mobile.

### 3. Add a result line (impact numbers) under each card in "01 Project Management"
- **File:** `index.html` (the four `.work-item` cards, inside `.work-item-text`, below the brand `<h3>` and project `<p>`) and `style.css`
- **Change:** under the existing brand name and project name, add a third line showing the result in numbers. It uses a different, simple font style from the brand and project lines so it reads as a highlight.
- **Section label:** "4 selected case studies + impact (PM)"
- **Copy, per card:**

| # | Card | Result line |
|---|------|-------------|
| 1 | Dior – Boutique Booking Systems | Onboarded from 3 to 24 branches on renewed boutique reservation system |
| 2 | Tumi – In-Store CRM Platform | Piloted 3 main Tokyo branches |
| 3 | Dior Addict – Event Management and CRM System for Global Pop-Up (event) | 300+ fans attended and 5 global and domestic Dior ambassadors |
| 4 | Cyberfight – O2O Gamified Campaign | 300+ fans joined campaign before the event |

- **Assumption:** the cards were matched to the results by the order the cards appear on the page and the "(tumi)", "(event)" and "(cyberfight)" hints. Wording is lightly cleaned up from the narration (e.g. "ambassadors", "before the event"); confirm the final copy.
- **Done when:** each of the four cards shows brand, project name, then the result line in the distinct font, and the layout from task 2 still fits on desktop and mobile.

### 4. Section "02 Marketing" – apply the same card layout change as task 2
- **File:** `index.html` (the `.work-col` block with the "02 Marketing" label and the Novatrade card, lines ~141-154) and its styles (`style.css`). The work is mainly restructuring the `index.html` markup.
- **Current:** the Marketing card is a narrow, portrait-style card. It sits side by side with "03 Education" in one row (`.work-list--labeled`), so each column is narrow.
- **Change to:** same treatment as task 2:
  - Make the card wider (landscape-style) and about 40% shorter.
  - Show the card in a vertical stack (one per row) rather than side by side.
  - Keep the title and description (currently "IT Consultancy Firm" / "Create content for awareness") clearly visible.
- **Open questions:**
  - The narration said "the section of all marketing", assumed to mean "02 Marketing" only. Should "03 Education" (Technical School card, same row) get the same change?
  - The Novatrade image uses `media-slot--fit`; confirm it still looks right at the new wider, shorter size.
  - Should the impact-number line from task 3 also be added here? It was not mentioned, so it is not planned.
- **Done when:** the Marketing card matches the new wide, short, stacked style of the Project Management cards, on desktop and mobile.

### 5. Add a result section to the IT Consultancy Firm (Novatrade) card
- **File:** `index.html` ("02 Marketing" card, `href="novatrade.html"`, inside `.work-item-text`) and, if the case study page should show it too, `novatrade.html`. Style it like the result lines from task 3 (`.work-item-result`).
- **Change:** add a result section to the IT consultancy card showing the outcome in numbers.
- **Copy (from narration):**
  - In one month: 8 short-form reels posted, 5.65k average views per reel, 19k views on the top reel, 200 new followers
  - (Do not mention "Tech Founder Hub"; the card refers to the account generally.)
- **Open questions:**
  - "average 5.65k" and "19k max views" are assumed to be views per reel, so "5.65k average views". Confirm.
  - Show as one result line (e.g. "8 reels in a month · 5.65k avg views · 19k max views · 200 followers") or as a short list/stat row on the card? Task 3 used a single line per card.
  - Add it on the homepage card only, or also on the Novatrade case study page?
- **Done when:** the Marketing card shows the result in the same style as the Project Management cards, and the figures match the copy above.

### 6. Reword the IT Consultancy Firm (Novatrade) card description
- **File:** `index.html` ("02 Marketing" card, `href="novatrade.html"`, the `<p>` under the `<h3>IT Consultancy Firm</h3>`)
- **Current:** "Create content for awareness"
- **Change to:** "Instagram account growth for awareness" (replaces "Create content for awareness"; it should name Instagram instead of the vague "content").
- **Alternative wordings, pick one:**
  - "Instagram short-form growth for brand awareness"
  - "Growing an Instagram account through short-form video"
- **Keep:** the title "IT Consultancy Firm" unchanged, and the result section from task 5 below the description.
- **Done when:** the card description names Instagram and reads clearly on desktop and mobile.

### 7. Add a result line to the Education (Technical School) card
- **File:** `index.html` ("03 Education" card, `href="technical-school.html"`, inside `.work-item-text`, below "Lecturing for IT Technicals"). Style it like the other result lines (`.work-item-result`).
- **Copy (from narration):** "Course understanding 4.0/5 across 12 sessions"
- **Open question:** "course understanding" is assumed to be the average student rating, so the line may read "4.0/5 average course understanding across 12 sessions". Confirm the wording.
- **Done when:** the Education card shows the result line in the same style as the Project Management and Marketing cards.

### 8. Add a short intro (1-2 sentences) under each Past Work section label
- **File:** `index.html` (under each `.work-group-label`: "01 Project Management", "02 Marketing", "03 Education") and `case-study.css` for a small body-text style (existing body font and colour, with spacing between the label and the cards).
- **Change:** under each section label, add one to two clear sentences describing what I do in that area and in what domain.
- **Copy (polished from narration, past tense):**
  - **01 Project Management:** "I managed the delivery of digital customer engagement products."
  - **02 Marketing:** "I grew awareness for tech companies with Instagram short-form content."
  - **03 Education:** *not yet narrated.* Placeholder draft: "I lecture IT fundamentals at a technical school, teaching AI and software basics to students." Confirm or replace.
- **Open questions:**
  - Education wording and whether "Ideas" should get an intro too.
- **Done when:** each section shows its intro under the label, readable on desktop and mobile, and the cards below keep the layout from tasks 2 and 4.
