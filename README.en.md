# Garimpo

[![HTML](https://img.shields.io/badge/HTML5-E34F26?style=flat-square&logo=html5&logoColor=white)](index.html)
[![CSS](https://img.shields.io/badge/CSS3-1572B6?style=flat-square&logo=css3&logoColor=white)](index.html)
[![SEO](https://img.shields.io/badge/SEO-JSON--LD%2Fsitemap-green?style=flat-square)](sitemap.xml)

Static product curation site for Shopee with 131 items in 8 categories, search, category filters, in-browser wishlist, and direct offer links — no server and no registration.

## Problem / Why it exists

Navigating the Shopee catalog means going through thousands of listings to find products worth the price. Garimpo filters that catalog and gathers products people actually buy, organizes them by category, and sends the visitor directly to the official Shopee page, where payment and delivery are handled by the store. The visitor does not create an account and does not enter payment details on Garimpo.

## What it does

- Displays 131 products in 8 categories (Home & Kitchen, Christmas, Fashion, Beauty, Technology, Tools, Pets and Fitness), with data in produtos.json.
- Filters by category via fixed chips at the top of the product list; each category count comes from the JSON itself.
- Keyword search with highlighting of terms found in titles.
- Sorts by relevance, bestsellers, lowest price, highest price, and name A to Z.
- Loads products 24 at a time with a "Load more" button, without reloading the page.
- Keeps a saved items list (wishlist) in the browser's localStorage, without a user account.
- Shows a featured carousel on the home page and a daily offer countdown.
- Opens Shopee affiliate links (`rel="nofollow sponsored"`) when clicking "View offer"; Garimpo does not process payment nor see the customer's card.
- SEO with meta tags, Open Graph, Twitter cards, canonical URL, JSON-LD (Organization, WebSite, ItemList), sitemap.xml and robots.txt.

## Stack

- Semantic HTML5 (`nav`, `section`, `main`, `footer`, `article`) with inline CSS in `index.html` itself.
- CSS3 with CSS variables, responsive grid (3, 2 or 1 columns), sticky filters and search at the top, transitions and animations.
- Vanilla JavaScript, no frameworks: `fetch` of `produtos.json`, grid rendering, filters, search, wishlist, carousel and analytics placeholders.
- Data: `produtos.json` with 131 products.
- Static hosting: Vercel (`.vercel/project.json`).

Prices observed in `produtos.json` range from R$ 15,99 to R$ 843,60.

## How it works

1. `index.html` loads `produtos.json` via `fetch`.
2. JavaScript renders the grid, category chips with counts, search bar, and sorting.
3. The visitor filters, searches, and sorts without reloading the page (client-side rendering).
4. Clicking "View offer", the link takes to the official product page on Shopee (affiliate). Garimpo does not see card, does not do checkout and does not calculate shipping.
5. Saved items are stored only in the browser (localStorage).

## How to run

- Open `index.html` directly in the browser (static file).
- For behavior closer to production (fetch of `produtos.json` without local file restrictions), serve the folder with any static server, for example `python -m http.server`, `npx serve` or Vercel.
- No dependencies to install and no backend. Keep `produtos.json` next to `index.html`.

## Project structure

```
Garimpo/
├── index.html                 # HTML, inline CSS, JavaScript and SEO in a single file
├── produtos.json              # 131 products (price, category, badge, image, Shopee link)
├── sitemap.xml                # sitemap for indexing by search engines
├── robots.txt                 # crawling rules
├── .gitignore                 # ignores WhatsApp*, .vercel, videos and reports; keeps img/
├── .vercel/project.json       # project identification on Vercel
├── logo.png / logo.jpg / logo-icon.png / favicon.jpg / apple-touch-icon.jpg
└── img/                       # product images (webp/jpeg)
```

## Trade-offs and decisions

- Everything in a single file (`index.html` with HTML, CSS and JS) simplifies deployment on static hosting, but does not scale for large teams; CSS is not modularized.
- No backend: wishlist persists only in the browser (`localStorage`). When clearing data or switching devices, saved items disappear.
- Shopee affiliate links: revenue depends on external clicks; price and stock come from Shopee and can change at any moment.
- When a product image fails, there is a fallback via Unsplash (`onerror` on the `img` tag).
- Analytics placeholders (Meta Pixel, gtag) need real IDs to work.
- No server, therefore no login, cart or checkout inside Garimpo.

## Known limitations

- Products and prices are static in `produtos.json` and updated manually; they may be outdated compared to Shopee.
- The daily offer countdown depends on the visitor's browser clock.
- The wishlist persists only locally (`localStorage`).
- The `sendBeacon` for `/api/track` has no corresponding backend in the repository.
- The Meta Pixel and gtag IDs are placeholders (`REPLACE_PIXEL_ID`).
- No PWA, cart, checkout nor user account.

## License

This repository does not include a `LICENSE` file. Consult the author before reusing the code or contents.

## Author

Garimpo (garimpo-oficial.vercel.app). Networks: Instagram @garimpo0132, TikTok @garimpo0176, YouTube @Garimpoprodutos. The repository does not declare an individual author name.
