# Elysian theme adaptation

The garden loads the Elysian Obsidian theme from the URL configured by `THEME` in `.env`. `src/site/get-theme.js` downloads that CSS at build time and writes a hash-named stylesheet under `src/site/styles/`; generated theme files are ignored by Git and refreshed during the build.

Elysian includes embedded font and artwork data. Obsidian-specific `data:@file/...` MIME labels are not standard browser data-URL media types, so `get-theme.js` normalizes embedded WOFF2, TTF, and PNG MIME labels before writing the stylesheet. This preserves the bundled fonts and textures for the browser without copying the base64 payloads into a second file.

The site adaptation lives in `src/site/styles/custom-style.scss`. It applies Elysian's palette and font families to the rendered garden, uses its static artwork plus side markers and scratch texture as the page background, and adapts supported note elements (titles, links, lists, code, callouts, tables, embeds) and garden navigation. Obsidian-only editor/workspace components have no equivalent in the published site and are intentionally not reproduced.

The theme is fetched from the upstream `master` URL at build time. A future upstream URL or branch change should be reviewed for font/data-URL changes and checked with `npm run build`.
