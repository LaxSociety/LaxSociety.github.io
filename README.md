# Lax Society

Source for [laxsociety.github.io](https://laxsociety.github.io): open-source apps, built in public by Laxman Khatri (Hacker Laxu).

- GitHub: https://github.com/LaxSociety
- YouTube: https://www.youtube.com/@laxsociety

## How it works

The whole site is one static `index.html` with inline CSS and a few lines of JavaScript for the category filter. There is no framework and no build step. GitHub Pages serves it from the `main` branch.

```
index.html        the page
assets/           avatar, favicon, og.png, project logos, org avatars
robots.txt        crawler rules
sitemap.xml       sitemap
.nojekyll         serve files as-is
```

## Run locally

```sh
python3 -m http.server 8822
# open http://localhost:8822
```

## Adding a project

Copy an existing card in `index.html` (a featured `article.fcard` or an `li.card` in the All projects grid), change the text and links, and add the logo to `assets/logos/`. Set `data-cat` to one of the filter values. Add the project to the `ItemList` in the JSON-LD block in `<head>` as well.
