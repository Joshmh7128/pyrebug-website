# Pyrebug Studios website

Static site (plain HTML + CSS, no build step) for Pyrebug Studios, hosted on GitHub Pages.

```
index.html          Landing page: hero, "Our work" (newest Steam release first), About
games.html          Wide game blocks linking to each Steam page
team.html           Team member cards
404.html            GitHub Pages "not found" page
assets/css/style.css
assets/img/favicon.svg
.nojekyll           Tells GitHub Pages to serve files as-is (skip Jekyll)
```

## Preview locally

```bash
python -m http.server 8080
```

Then open http://localhost:8080.

## Deploy to GitHub Pages

1. Create a GitHub repository (e.g. `pyrebug-studios`) and push this folder to the `main` branch.
2. In the repository, go to **Settings → Pages**.
3. Under **Build and deployment**, choose **Deploy from a branch**, select `main` and `/ (root)`, and save.
4. The site will be live at `https://<username>.github.io/pyrebug-studios/` within a minute or two.

All links are relative, so the site works from a project subpath or a custom domain. The one exception is `404.html`, whose "Back" button points to `/` — change it to `/pyrebug-studios/` if you are not using a custom domain.

### Custom domain (e.g. pyrebug.com)

1. In **Settings → Pages → Custom domain**, enter `pyrebug.com` and save (GitHub adds a `CNAME` file to the repo).
2. At your DNS provider, add `A` records for the apex domain pointing to
   `185.199.108.153`, `185.199.109.153`, `185.199.110.153`, `185.199.111.153`,
   and a `CNAME` record for `www` pointing to `<username>.github.io`.
3. Once the certificate is issued, tick **Enforce HTTPS**.

## Editing content

- **Team:** each person is one `<li>` card in `team.html`. Empty roles/bios are hidden automatically. To create a category, copy a `<div class="team-group">` block and rename its `<h2>`.
- **Games:** add a new `<li class="game">` block at the top of the list in `games.html` and a matching card at the top of the "Our work" grid in `index.html` (both are sorted newest first).
- **Images:** game images are loaded from Steam's CDN (`.../steam/apps/<appid>/header.jpg`). To self-host, save them into `assets/img/` and update the `src` attributes.
- **Monochrome images:** images are grayscale until hovered. To show full colour at all times, delete the `.mono` rule in `style.css`.
