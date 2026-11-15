# Lax Society

Source for [laxsociety.github.io](https://laxsociety.github.io): open-source apps, built in public by [JKL404](https://github.com/JKL404).

- GitHub: https://github.com/LaxSociety
- YouTube: https://www.youtube.com/@laxsociety

## How it works

The whole site is one static `index.html` with inline CSS and a little JavaScript: the hero typing effect, the category flags, and the small interactive shell (`help`, `ls`, `open <project>`, `whoami`, `github`, `youtube`, `clear`). Animations are skipped when the visitor prefers reduced motion. There is no framework and no build step. GitHub Pages serves it from the `main` branch.

```
index.html        the page
assets/           logo, favicons, og.png, project logos, org avatars
robots.txt        crawler rules
sitemap.xml       sitemap
.nojekyll         serve files as-is
```

## Run locally

```sh
python3 -m http.server 8823
# open http://localhost:8823
```

## Adding a project

Each project appears twice in `index.html`. Featured projects get an `article.fcard` in the Featured window. Every project also gets an `li.row` in the All projects list, which is a `<details>` element whose `<summary>` is the `ls -la` line. Copy an existing entry and change the text and links. Set `data-cat` on the row to one of the filter values (`tv`, `mac`, `ai`, `web`, `games`, `classic`) and update the counts on the flag buttons. Add the logo to `assets/logos/`. Add the project to the `PROJECTS` map in the script at the bottom so the shell's `open` command can find it, and to the `ItemList` in the JSON-LD block in `<head>`.

## Swapping the logo

The nav, footer and SVG favicon all use `assets/logo.svg`. To change the logo, replace that file, then regenerate the PNG sizes from an 800×800 PNG export:

```sh
for s in 32:favicon-32 180:apple-touch-icon 96:logo-96 512:logo-512; do
  sips -z ${s%%:*} ${s%%:*} logo-800.png --out assets/${s##*:}.png
done
```

`logo-512.png` is the Organization logo in the JSON-LD.
