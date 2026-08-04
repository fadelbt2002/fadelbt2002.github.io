# fadelbatal-site

Personal academic site. Plain HTML + one CSS file, no build step, no dependencies.

## Files

- `index.html` — the whole site (one page)
- `style.css` — all styling; the variables at the top control colors, fonts, and the left strip
- `assets/` — portrait, figures, CV PDF

## Preview locally

```
python3 -m http.server -d . 8000
```

Then open http://localhost:8000

## Before publishing — replace these

1. `assets/portrait.jpg` — drop in a photo (portrait orientation, ~600×750 or larger).
   Until it exists the page falls back to `assets/portrait-placeholder.svg`.
2. `assets/Batal_Fadel_CV.pdf` — export the CV to PDF and put it here.
3. Google Scholar link in the nav — `YOUR_ID` is a placeholder.
4. LinkedIn / GitHub URLs in the nav — confirm the handles are right.
5. The Arabic spelling of the name in `index.html` (`فاضل بطل`) — verify.
6. `assets/work-*.svg` — abstract placeholder figures. Swap in real figures from
   the papers (PNG or SVG, roughly 3:2) whenever you have ones you can share.

## Deploying to GitHub Pages

```
git init && git add -A && git commit -m "Personal site"
gh repo create fadelbatal.github.io --public --source=. --push
```

Pages serves `fadelbatal.github.io` from the default branch automatically. For a
custom domain, add a `CNAME` file containing the domain and point a DNS ALIAS/A
record at GitHub Pages.
