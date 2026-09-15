# Let Me JW That For You

A "let me google that for you"-style gag page. Type a search term in, get a link.
Send the link to someone. When they open it, the page fake-types the term into
a jw.org-style search box, shows "See how easy that was?", then auto-redirects
them to the real jw.org search results for that term.

Single static file, no build step, no backend, no data stored anywhere. Works
as-is on GitHub Pages.

## Deploy

1. Create a new **public** repo on GitHub (any name, e.g. `lmgtfy-jw`).
2. Push these files to it:
   ```bash
   git init
   git add .
   git commit -m "Initial commit"
   git branch -M main
   git remote add origin https://github.com/YOUR-USERNAME/YOUR-REPO.git
   git push -u origin main
   ```
   (If this folder is already a git repo with a commit, skip straight to
   adding the remote and pushing.)
3. In the repo on GitHub: **Settings -> Pages -> Source -> Deploy from a
   branch -> `main` / `root`**. Save.
4. Your live URL will be `https://YOUR-USERNAME.github.io/YOUR-REPO/`
   (GitHub Pages usually takes 1-2 minutes to go live after the first push).

## Use it

- Open the live URL with no parameters -> you get the link generator.
- Type a term, click **Generate link**, copy the link it gives you.
- Send that link to someone. Opening it plays the gag, then sends them to
  the real jw.org search results for that term.

## Customize

Everything is in `index.html` (HTML/CSS/JS, no dependencies):

- `speed` (search for `var speed = 55;`) controls how fast the term
  "types" — lower is faster.
- The `2500` in `setTimeout(function () { window.location.href = resultUrl; }, 2500);`
  is how long "See how easy that was?" stays on screen before redirecting
  (in milliseconds).
- `buildResultUrl()` controls where it redirects — currently
  `https://www.jw.org/en/search/?q=TERM`. Swap this if you'd rather point at
  `wol.jw.org` or somewhere else.
