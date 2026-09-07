# Silly String site

A tiny static page: headline, photo, tagline. No build step, no dependencies.

## Files
- `index.html` — the page
- `style.css` — styles
- `images/silly-string.jpg` — the photo

## 1. Push this to GitHub

```bash
cd site
git init
git add .
git commit -m "Initial site"
gh repo create silly-string-site --public --source=. --push
```
(Or create the repo on github.com first, then `git remote add origin <url>` and `git push -u origin main`.)

## 2. Connect it to Cloudflare Pages

1. In the Cloudflare dashboard, go to **Workers & Pages → Create → Pages → Connect to Git**.
2. Pick the repo you just pushed.
3. Build settings: leave the **build command** empty and set the **output directory** to `/` (this is a static site with no build step).
4. Click **Save and Deploy**.

That's it — Cloudflare Pages now watches the repo. Every push to `main` triggers a new deploy automatically (that's the CI/CD part), and pull requests get their own preview URLs.

## 3. Point your domain at it

In the Pages project, go to **Custom domains → Set up a custom domain** and add your Cloudflare-managed domain. DNS gets configured automatically since it's already on Cloudflare.

## Making changes later

Edit the files, then:
```bash
git add .
git commit -m "Update copy"
git push
```
Cloudflare picks it up and redeploys within a minute or two — no dashboard steps needed.
