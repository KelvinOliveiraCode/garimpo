# garimpo

[![HTML/CSS/JS](https://img.shields.io/badge/HTML-CSS-JS-orange)](https://developer.mozilla.org/)   ![status: done](https://img.shields.io/badge/status-done-green)   ![license: MIT](https://img.shields.io/badge/license-MIT-blue)

## Summary

Curadoria de 131 ofertas Shopee: filtros, wishlist e SEO ,  100% client-side | Curated Shopee deals site, 100% client-side
## Problem / Why it exists

The project addresses a practical scope and automates a task that, done manually, is repetitive and error-prone. The focus is on turning data or processes into reliable output, with readable, testable, and extensible code.
## Architecture

Code files (2):
- `index.html`
- `produtos.json`
## Design Patterns and Techniques Identified

- Client-side data fetching
- JSON data catalog
- Single-page HTML entry
- localStorage theme persistence
## What it does

Curadoria de 131 ofertas Shopee: filtros, wishlist e SEO ,  100% client-side | Curated Shopee deals site, 100% client-side
## How to run

Open `index.html` directly in the browser, or serve locally:

```bash
python -m http.server 8080
# access http://localhost:8080
```
## Project Structure

- `index.html`
- `produtos.json`
## Trade-offs and Technical Decisions

- Single file (or few): easy to host on any static server (GitHub Pages, Netlify, Vercel) and audit line by line.
- No build, no server, no database.
- Data in snapshot (when applicable), not real-time ,  user confirms on official linked source.
- Light/dark theme persisted in `localStorage` with no external JS.
## Known Limitations

- No backend; functionality limited to the browser.
- Static data or snapshot; confirm values in official sources.
- No authentication or multi-user support.
## Tests

No automated tests detected (documentation/guide project).
## License

Distributed under the MIT License. See the `LICENSE` file in this repository.
## Author

Kelvin Oliveira ,  https://github.com/KelvinOliveiraCode
Portfolio: https://kelvinoliveiracode.github.io/portfolio/
