# oliverpadilla.com — Design Brief

Upload this alongside `index.html`. The HTML is self-contained: inline CSS,
Google Fonts, no assets, no build step. It renders as-is.

---

## The one rule

**Copy is locked.** Every line was reviewed and approved word by word. Do not
rewrite, shorten, tighten, or improve any text. If a layout idea requires a
copy change, ask first and propose the change rather than making it.

Two formatting rules that survive into design work:

- No em dashes in visible copy. The two in `<title>` and `og:title` are
  approved name/title separators.
- Keep the `<!-- BLOCK N -->` comments. They are how sections get referenced
  across sessions and into Claude Code.

---

## Who this is for

Oliver Padilla, YouTube strategist, running an active search for channel and
video strategy leadership roles at brands and publishers. Targeting remote.

The page will be read by hiring managers and recruiters, often on a phone,
often with his resume open in another tab, usually in under sixty seconds
before they decide whether to reply. It needs to survive a skim and reward a
read.

**Tone:** creative and energetic, YouTube-native. Not corporate, not a
resume with thumbnails. He works in video; the page should feel like someone
who does.

---

## Design language

Broadcast television. Established in an earlier build and worth keeping,
because it is the thing separating this from every other portfolio in the
pile.

- **SMPTE color bar strip** across the top of the page. Keep it.
- **Work section as a programming schedule** — slot number, format label,
  title, body, role line — rather than a card grid.
- **Section markers as channel numbers** (CH 01, CH 02, CH 03).
- **Role lines** set in mono with an amber left rule, styled like a slate or
  a lower third.

### Palette

    --ink       #0A1628   background, deep navy
    --paper     #F2F0EA   primary text
    --paper-dim #B9C2CE   secondary text, metadata
    --cyan      #4CC8E0   structure: section markers, links, primary CTA
    --amber     #E8A33D   accent: role labels, quote highlight, focus ring
    --rule      rgba(185,194,206,.22)   hairlines

Cyan is the analyst voice, amber is the audience voice. Consistent
throughout; worth preserving if the palette shifts.

### Type

- **Archivo** 500/600/700 — display, headings, section titles
- **Newsreader** 300 — body copy, serif, generous line height
- **IBM Plex Mono** 400/500 — metadata, slot numbers, role lines, nav

Body stays serif. The serif-on-navy contrast is doing real work against the
sans-serif sameness of most portfolio sites.

Scale is fluid via `clamp()` throughout.

---

## Page structure

| Block | Section | Notes |
|-------|---------|-------|
| 1 | Title / meta | Not visible |
| 2 | Hero | Callsign, headline, lede, jump nav |
| 3 | Thesis | Pull quote + paragraph, between hairlines |
| 4 | Attribution note | Mono, sits above Work |
| 5 | Work 01 | McLaren / Lando Norris — 2 paragraphs |
| 6 | Work 02 | Channel architecture — 2 paragraphs |
| 8 | Work 03 | CNET — 3 paragraphs |
| 9 | How I work | 3 blurbs in an auto-fit grid |
| 10 | About | Kicker + 2 paragraphs |
| 11 | Contact | Heading, role line, 2 buttons |
| 12 | Footer | Copyright |

Block 7 was removed during review. Numbering is intentionally non-contiguous.

Work slot numbers (01, 02, 03) are hardcoded and need manual renumbering if
entries are added or removed.

---

## What to explore

Ranked by leverage.

**1. The hero.** Currently text on navy. A recruiter's first three seconds
are entirely reading, and this is a video person's site. Highest-impact area
on the page. Motion, texture, a broadcast-inspired treatment, something that
signals the medium before a word is read.

**2. Mobile.** Recruiters open links on phones. Check the headline at 375px —
`clamp()` at 2.5rem against a 15ch max-width wraps awkwardly at some sizes.
The Work grid collapses to single column under 680px; verify the slot number
and format label still read as a unit.

**3. Work entry rhythm.** Three entries of uneven length — CNET runs three
paragraphs, the others two. The schedule layout may need help absorbing that
imbalance so the section doesn't feel bottom-heavy.

**4. Video slots.** No embeds yet; IDs aren't available. Worth designing the
slot now so the shape is settled and dropping them in later is mechanical.
Do not add empty placeholders to the live page.

**5. Section transitions.** Hairline rules do all the work currently. Fine,
possibly too quiet across a long scroll.

---

## Constraints

- **Single file.** Inline CSS, no build step, no framework, no npm. Deploys
  to Cloudflare Pages by pushing to a GitHub repo. If CSS gets extracted to
  `style.css`, that's fine, but keep it to plain files.
- **No JavaScript unless it earns its place.** The page currently has none
  and loads instantly. Motion via CSS is preferred.
- **Accessibility holds.** Focus rings are amber at 2px with 3px offset.
  `prefers-reduced-motion` is already respected; any new motion must respect
  it too. Contrast must stay AA on the navy.
- **Fonts stay on Google Fonts** with `preconnect`, unless self-hosting is
  proposed deliberately.

---

## Do not add

These were removed or withheld deliberately during review.

- **Video embeds** — no IDs supplied yet. Empty slots look worse than none.
- **A fourth case study** — one was pulled over data inconsistencies.
- **Metrics or analytics figures** — directional claims only. One figure
  appears in Work 01 and is deliberately rounded. Do not sharpen it into
  precise numbers, and do not pull it out into a stat block, callout, or
  counter.
- **A location** — targeting remote, does not want geo-filtering.
- **Photography of Oliver** — none supplied.
- **Subscriber counts** — standing decision across all his materials.
- **Testimonials, logos, or client walls** — not part of this build.

---

## Starter prompt

```
Attached is my portfolio site as a single self-contained HTML file,
plus a design brief.

COPY IS LOCKED — do not rewrite any text. Read the brief first;
it covers the design language, palette, type, and constraints.

I want to iterate on visuals only. Start with the hero: it's the
highest-leverage area and right now it's just text on navy. I'm a
video person and nothing on the page moves.

Show me 2-3 directions before building any of them out.
```

---

## After Design

Export the revised HTML, drop it in the repo next to `CLAUDE.md`, and Claude
Code picks up the maintenance rules automatically. Check that the
`<!-- BLOCK N -->` comments survived the round trip; restore them if not.
