# League of Handsomes

The league record. Static site, no build step, no dependencies.

## Adding a season

Open `index.html` and find the `SEASONS` array near the top of the `<script>` block at
the bottom of the file. Copy the last block, change the names, and paste it at the end:

```js
{ year: 2026,
  first:  { manager: "", team: "" },
  second: { manager: "", team: "" },
  third:  { manager: "", team: "" },
  rest: [ { title: "Best of the Rest", manager: "", team: "" } ] },
```

Leave `rest: []` if there was no consolation winner that year. A season can carry more
than one, the way 2022 does.

Directly below the array is `LIVE_SEASON`. Set it to the year being played so the top of
the wall shows a blank plate, or to `null` once the season is in the array.

Everything else on the page recalculates itself: the reigning champion, the all-time
ledger, the Bold and Brash annex, and every manager's file. Commit and it is live in
about a minute.

## Files

```
index.html              the whole site
CNAME                   the custom domain
.nojekyll               tells GitHub Pages to serve the files as-is
favicon.ico             browser tab icon
apple-touch-icon.png    iOS home screen icon
assets/
  handsome-face.png     logo
  handsome-figure.png   footer
  bold-and-brash.png    the painting
  og.png                link preview card
  icon-512.png          large icon
```

## Publishing

1. Create a repo and upload everything here at the root, not inside a folder.
2. Settings, then Pages. Under Build and deployment set Source to "Deploy from a branch",
   branch `main`, folder `/ (root)`. Save.
3. Still on that page, set Custom domain to `leagueofhandsomes.com` and save.
4. At the registrar, point the domain at GitHub:

   | Type | Name | Value |
   | ---- | ---- | ----- |
   | A    | @    | 185.199.108.153 |
   | A    | @    | 185.199.109.153 |
   | A    | @    | 185.199.110.153 |
   | A    | @    | 185.199.111.153 |
   | CNAME | www | `USERNAME.github.io.` |

   Optional IPv6, four AAAA records on `@`: `2606:50c0:8000::153`, `2606:50c0:8001::153`,
   `2606:50c0:8002::153`, `2606:50c0:8003::153`.

5. DNS takes anywhere from a few minutes to a few hours. Once GitHub reports the domain
   as verified, tick "Enforce HTTPS" on the same Pages screen. The certificate can take
   up to 24 hours to issue, so a warning before then is normal.
