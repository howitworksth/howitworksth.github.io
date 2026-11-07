# How It Works TH — link-in-bio page

Static page. Every episode card (cover + title) links to its Shopee affiliate URL. Spec: `../web.md`.

## Add an episode
1. Product photo: keep the original as `..\product\epN-name\publish\product.webp`, then make the small copy:
   `magick ..\product\epN-name\publish\product.webp -resize 360x400 -quality 75 covers\epN.webp`
2. Add an entry to `episodes.json` (any order, the page sorts newest first):
   ```json
   { "ep": 3, "title": "…", "hook": "…", "product_url": "https://s.shopee.co.th/…", "cover": "covers/ep3.webp", "youtube_url": "", "date": "YYYY-MM-DD" }
   ```
   Empty `product_url` = card shows "เร็ว ๆ นี้" and isn't clickable. Paste the affiliate link exactly as Shopee gives it.
3. Commit + push → the host redeploys.

## Preview locally
`python -m http.server 8000` in this folder, open http://localhost:8000 (opening the file directly won't load `episodes.json`).

## Deploy
Any static host; serve this folder as-is, no build step.
