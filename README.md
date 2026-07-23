# kranthiboggula.com

Personal site and portfolio. Plain HTML and CSS — no build step, no dependencies,
no `npm install`. Edit a file, push, it's live.

```
.
├── index.html                    home — profile, operations board, timeline
├── work.html                     case studies
├── 404.html                      not-found page (Cloudflare serves this automatically)
├── assets/
│   └── css/site.css              every design decision lives here
├── projects/
│   └── flight-log/index.html     self-contained flight log dashboard
└── README.md
```

## Why no framework

Astro, Eleventy and Hugo are all good, and one of them may be right later. Right now
they'd add a build step that can fail, a `node_modules` folder to download over a
satellite link, and a layer of abstraction between me and the HTML I'm still learning.
Plain files remove every one of those failure modes. Revisit this once there are
enough pages that repeating the nav by hand is genuinely annoying — that's the real
signal, not fashion.

## Working routine

```bash
# 1. see what's changed
git status

# 2. preview locally before pushing (http://localhost:8000)
python3 -m http.server 8000

# 3. stage, commit, push
git add .
git commit -m "Add case study on asset reconciliation"
git push
```

Cloudflare Pages watches the `main` branch and redeploys within about a minute.
Every commit gets its own preview URL, so a mistake is never more than one
`git revert` away.

Write commit messages as *what changed and why*, not "update". In two years the
history is the only record of how the site got here.

## Editing conventions

- **Colours and type** are CSS variables at the top of `site.css`. Change them there
  and the whole site follows. Don't hard-code a hex value in a page.
- **New page?** Copy `work.html`, strip the body, keep the `<head>` and `<nav>`.
  Update the `<title>`, the meta description, and `aria-current="page"` on the nav link.
- **Every image** needs an `alt` attribute. Every page needs a unique `<title>`.

## Publishing rules I hold myself to

This site is public and my employer is identifiable from it. Before anything goes live:

1. No operational data. Figures describe system architecture — how many lists, how many
   locations — never records, never content.
2. No named field offices in relation to security posture, closures or drawdown activity.
3. No colleague names, no internal URLs, no tenant or site names, no ticket numbers.
4. Screenshots use generated sample data only.
5. Anything describing my employer's work gets a second read before it's pushed —
   and if there's doubt, I ask my supervisor first. Easier before publishing than after.

The footer disclaimer stays on every page.

## Still to do

- [ ] Fill the `TODO` placeholders in `index.html` — career timeline, education, contact links
- [ ] Register the domain and attach it to the Cloudflare Pages project
- [ ] First field-notes post
- [ ] Sanitised screenshots for the case studies
