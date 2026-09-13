# oliverpadilla.com

Personal portfolio site for Oliver Padilla, YouTube Strategist. Single static
HTML file, no build step, no dependencies, deployed to Cloudflare Pages.

## Owner context

Oliver is running an active job search for YouTube and video strategy
leadership roles. This site is a live job-search asset, not a side project.
Copy accuracy matters more than features. Every line was reviewed and
approved by him block by block; do not rewrite copy without asking.

## Stack

- One file: `index.html`. All CSS is inline in a `<style>` block.
- Fonts from Google Fonts: Big Shoulders Display (display, condensed, uppercase), Spline Sans (body).
- No JS. No framework. No package.json. Nothing to install.
- Host: Cloudflare Pages, connected to a GitHub repo.
- Domain: oliverpadilla.com, registered and DNS-managed in Cloudflare.
- Email: Proton Mail on the domain. `oliver@oliverpadilla.com` is live.

## Deploy

1. Push to the connected GitHub repo's default branch.
2. Cloudflare Pages builds automatically. Build command: none. Output directory: `/`.
3. Custom domains `oliverpadilla.com` and `www.oliverpadilla.com` are attached
   in the Pages project.

To set up from scratch: Cloudflare dashboard → Workers & Pages → Create →
Pages → Connect to Git → select repo → leave build command blank → output
directory `/` → Save and Deploy → Custom domains → add both hostnames.

## Structure

The page is twelve reviewed blocks, marked with HTML comments matching the
numbering used during copy review. Keep the comments; they are how Oliver and
Claude refer to sections.

| Block | Section |
|-------|---------|
| 1 | `<title>` and meta description |
| 2 | Hero: callsign, headline, lede, jump nav |
| 3 | Thesis pull quote and paragraph |
| 4 | Attribution note above Work |
| 5 | Work 01, McLaren / Lando Norris |
| 6 | Work 02, channel architecture |
| 7 | *(removed — see below)* |
| 8 | Work 03, CNET |
| 9 | How I work, three blurbs |
| 10 | About |
| 11 | Contact |
| 12 | Footer |

Work entries render as a two-column schedule (slot number + format label
and headline on the left, body and role line on the right), not a card
grid. Slot numbers are hardcoded in `.slot` paragraphs and must be
renumbered by hand if an entry is added or removed.

The design is "Direction E: Daylight" from the Claude Design exploration
(bundle: `Portfolio design directions-handoff.zip`, Sept 2026). The earlier
navy/SMPTE-bar build is retired; `DESIGN-BRIEF.md` describes that earlier
build and the exploration brief, and is kept for the constraints section.

## Design system

    --ground     #F4F2ED   page background, warm off-white
    --ink        #121417   primary text; also the thesis band background
    --ink-soft   #2B2F35   body copy in Work and About
    --ink-dim    #5C6169   metadata, attribution note, role lines, footer
    --green      #0F6B4F   accent: headline word, hero bar, slot labels, CTA, contact band
    --mint       #8FE3B6   quote accent on the dark thesis band
    --rule       rgba(18,20,23,.18)  hairlines between work entries

Structure: sticky top bar (callsign + "Get in touch." CTA), hero with the
10px green wipe bar, dark thesis band, Work, How I work, About, green
Contact band, footer. Section heads are uppercase condensed type with a
2px rule running out to the right.

Motion is CSS only: `rise` / `wipeX` on the hero at load, and
scroll-driven `animation-timeline: view()` reveals on the work entries,
thesis quote, How I work grid, and About. Browsers without scroll
timelines just play the keyframes once on load. `prefers-reduced-motion`
disables all of it. Do not add JS for motion.

Type scale is fluid via `clamp()`. Display type is uppercase Big Shoulders
Display at tight line height; body is Spline Sans at 300/400. Focus rings
are 2px green with 3px offset (off-white inside the contact band).

## Copy rules — read before editing any text

These were set by Oliver during review and are not stylistic suggestions.

1. **No em dashes in visible copy.** He considers them an AI tell. Use a
   period, colon, or comma instead. The two in `<title>` and `og:title` are
   approved name/title separators and stay.
2. **Nothing negative about Hilton, CNET, colleagues, or former employers.**
   Critique of industry practice in general is fine and appears
   intentionally in the hero and thesis. Critique of a specific prior
   employer's state, decisions, or output is not.
3. **No specific internal metrics.** Directional and order-of-magnitude
   claims only, and only things inferable from public video pages. "Millions
   of organic views" is fine. Channel-level analytics are not.

   The McLaren line in Block 5 is deliberately loose. The verified underlying
   figures are 8.1M views and 1.2M watch hours, and Oliver chose to state
   them as "millions of organic views and over a million watch hours." Views
   are publicly countable; watch hours only exist in YouTube Studio. Do not
   "correct" this line to the precise numbers — the imprecision is the
   decision. The real figures are for interviews.
4. **Honest attribution.** Role lines state strategy ownership only. Do not
   add verbs implying he produced, directed, or edited the Hilton work.
5. **No self-deprecation and no stated limitations.** An earlier draft said
   he doesn't want to produce day-to-day; it was cut because it narrows him
   out of smaller roles he would take.
6. **Present tense for Hilton.** He is currently employed there.
7. **No location.** He is targeting remote roles and does not want to be
   geo-filtered.

## Deliberately absent

Do not add these back without Oliver asking:

- **Video embeds.** An earlier version had eleven lite-embed slots. He has
  not supplied IDs. Empty slots look worse than no slots.
- **The SMPTE color bars and CH 01/02/03 section markers.** Part of the
  retired navy build; Direction E dropped them deliberately.
- **The travel slate case study.** Pulled during review: he found
  inconsistencies in the underlying data and does not want to defend it.
- **The Python attribution framework.** Built by him after the fact for his
  own analysis. It was never a Hilton deliverable and must not be presented
  as one. This was a correction he made explicitly.
- **AdPipe by name.** The AI video tool in the About section is deliberately
  unnamed. He has an active vendor relationship with them on Hilton's behalf.
- **Subscriber counts.** A standing decision across all his job-search
  materials.
- **Target role titles beyond the Contact line.** The list there is
  approved; do not repeat it elsewhere.

## Known open items

- **Work section balance.** Three case studies, two of them Hilton platform
  strategy. The identified candidate for a fourth is the "Off the Menu" food
  documentary series: strong hit rate, clean attribution (optimization
  leadership, not creation), and it adds series and format range. Not
  drafted. Only add if Oliver asks.
- **No analytics.** Nothing is tracking visits. If he wants this, Cloudflare
  Web Analytics is the privacy-preserving option and needs one script tag.
- **No favicon.**
- **No `robots.txt` or sitemap.** Fine at one page.

## If asked to add pages

The original plan was multi-page with separate portfolio categories. That was
descoped to ship fast. If expanding: keep the single-file-per-page pattern,
duplicate the `<style>` block or extract it to `style.css` and link it, and
keep the jump nav in sync across pages. Cloudflare Pages serves `/about.html`
at `/about` automatically.
