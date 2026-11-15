# Lax Society

Source for [laxsociety.github.io](https://laxsociety.github.io): open-source apps, built in public by [JKL404](https://github.com/JKL404).

- GitHub: https://github.com/LaxSociety
- YouTube: https://www.youtube.com/@laxsociety

## How it works

The whole site is one static `index.html` with inline CSS and a little JavaScript: the hero typing effect, the category flags, and the small interactive shell (`help`, `ls`, `products`, `open <project>`, `whoami`, `github`, `youtube`, `clear`). Animations are skipped when the visitor prefers reduced motion. There is no framework and no build step. GitHub Pages serves it from the `main` branch.

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

Each project appears twice in `index.html`. Featured projects get an `article.fcard` in the Featured window. Every project also gets an `li.row` in the All projects list, which is a `<details>` element whose `<summary>` is the `ls -la` line. Copy an existing entry and change the text and links. Set `data-cat` on the row to one of the filter values (`ai`, `robotics`, `tv`, `mac`, `web`, `games`, `classic`) and update the counts on the flag buttons. Add the logo to `assets/logos/`. Add the project to the `PROJECTS` map in the script at the bottom so the shell's `open` command can find it, and to the `ItemList` in the JSON-LD block in `<head>`.

## Project order

Newest and earning first: mkTV, JobCairn, Gymnom, XOtale, Keepwatch, Agentic Skill Deck, VisaRadar, Ludo Raja, then the earlier 2019 to 2024 projects. Keep the JSON-LD `ItemList` in the same order.

- Gymnom and XOtale are paid products with a free option. They get their own `./products --paid` window above Featured and are never labelled open source.
- Featured shows mkTV, JobCairn, Keepwatch and Agentic Skill Deck.
- The `./coming-up` window lists the LLM, AI agent and robotics pillars as coming soon. Add real projects to All projects when they ship (`data-cat="ai"` or `"robotics"`), and don't list anything that hasn't shipped.

## Logo

The logo files come from the brand exports in `youtube-channel/logo-final/`:

- `assets/lockup.svg`: hood + LAX SOCIETY lockup in the nav
- `assets/logo.svg`: hood with LS eyes, used in the footer and og.png
- `assets/favicon.svg`, `favicon-32.png`, `apple-touch-icon.png`: favicons
- `assets/logo-96.png`, `logo-512.png`: made from the 800px avatar with `sips -z`. `logo-512.png` is the Organization logo in the JSON-LD.

To swap the logo, copy the new exports over these files.
