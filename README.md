# Academic portfolio

Static personal site. Plain HTML and CSS, no build step, no framework, no
JavaScript. Every page is a standalone file; the only shared asset is
`assets/css/style.css`.

## Files

```
.
├── index.html          Homepage — about, interests, news, selected papers
├── publications.html   Full publication list
├── experience.html     Research, industrial, teaching, service
├── education.html      Degrees, coursework, training, awards
├── others.html         Projects, software, talks, outreach, contact
├── .nojekyll           Stops GitHub Pages running the files through Jekyll
├── assets/
│   ├── css/style.css   All styling. Design tokens are at the top.
│   ├── img/            portrait.jpg, favicon.png, preview.jpg
│   └── js/             (empty — add only if you need it)
└── resources/
    └── pdf/            cv.pdf, certificates, posters
```

## Deploying to GitHub Pages

1. Create a public repository named exactly `YOURUSERNAME.github.io`.
   The name must match your GitHub username for the site to serve from the
   root domain.
2. Push these files to the default branch.
3. Repository → Settings → Pages → Source: *Deploy from a branch*, branch
   `main`, folder `/ (root)`.
4. The site appears at `https://YOURUSERNAME.github.io/` within a few
   minutes. The first build is the slowest.

```bash
git init
git add .
git commit -m "Initial site"
git branch -M main
git remote add origin https://github.com/YOURUSERNAME/YOURUSERNAME.github.io.git
git push -u origin main
```

If you are pushing over HTTPS, GitHub no longer accepts account passwords.
Generate a personal access token (Settings → Developer settings → Personal
access tokens) and use it in place of the password, or configure SSH keys.

## Editing

Everything you need to change is marked `EDIT:` in the HTML. Search for that
string across all five files.

**To restyle the whole site**, change the custom properties in the `:root`
block at the top of `style.css` — colours, typefaces, and column width are all
defined there once.

**To change the fonts**, edit two places: the Google Fonts `<link>` in every
page's `<head>`, and the `--font-*` tokens in `style.css`.

**Dark mode** follows the operating system setting. To force light mode
permanently, delete the `@media (prefers-color-scheme: dark)` block.

**The navigation bar is duplicated** in all five files. That is the cost of
having no build step. When you add or rename a page, update it in each file,
and move the `aria-current="page"` attribute to the link for the current page.

## Previewing locally

```bash
python -m http.server 8000
```

Then open `http://localhost:8000`. Opening the files directly with `file://`
mostly works, but relative paths behave differently, so use the server.

## Images

- `assets/img/portrait.jpg` — square, at least 400×400 px.
- `assets/img/favicon.png` — 32×32 px.
- `assets/img/preview.jpg` — 1200×630 px, used for link previews on social
  media and messaging apps. Referenced from `index.html`'s Open Graph tags.

Convert photographs to WebP if you want smaller files; update the `src`
attribute accordingly.
