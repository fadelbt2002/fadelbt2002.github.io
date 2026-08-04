# fadelbatal-site

Personal academic site. Plain HTML + one CSS file + ~15 lines of JS. No build step, no
dependencies, nothing loaded from a CDN, so it works offline and will still work in five years.

## Files

- `index.html`: the whole site (single page)
- `style.css`: all styling. The `:root` block at the top holds every color, font, and
  radius; change `--cyan` / `--violet` and the whole page re-themes.
- `assets/`: portrait, figures, CV PDF

## Preview locally

```bash
python3 -m http.server -d . 8000
```

Then open http://localhost:8000

## Before publishing, replace these

1. `assets/portrait.png`: drop in a photo (portrait orientation, ~600×750 or larger).
   Until that file exists the page falls back to `assets/portrait-placeholder.svg`.
2. `assets/Batal_Fadel_CV.pdf`: export the CV to PDF and put it here.
3. Google Scholar link in the nav: `YOUR_ID` is a placeholder.
4. LinkedIn / GitHub URLs in the nav: confirm the handles are right.
5. `assets/work-*.svg`: schematic placeholder figures drawn to match the site's palette.
   Swap in real figures from the papers whenever you have ones you can share (any image
   format, roughly 3:2, dark background reads best).

## Design notes

- Dark base with two blurred gradient orbs, a faint 64px grid that fades out downward, and a
  very light SVG-generated grain. All three are fixed layers behind `main`.
- The accent gradient (cyan to violet) is reused for the surname and the section numbers, so
  the page reads as one system.
- Sections fade in on scroll via `IntersectionObserver`. That is disabled under
  `prefers-reduced-motion`, and a `<noscript>` block makes everything visible if JS is off.
- The nav is sticky and masked so content fades out beneath it; on mobile it collapses to a
  single horizontally-scrollable row.
- A `@media print` block flattens the page to black-on-white.

## Deploying to GitHub Pages

```bash
gh repo create fadelbatal.github.io --public --source=. --push
```

Pages serves `fadelbatal.github.io` from the default branch automatically. For a custom
domain, add a `CNAME` file containing the domain and point a DNS ALIAS/A record at GitHub
Pages.
