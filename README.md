# Visual Product Matcher (Offline-Ready)

This is a lightweight Flask app for **visual product matching** that works fully offline using **local images**.
It supports image upload or URL input (when online), shows the query image, and lists similar products from a 50-item catalog.
Results can be filtered by similarity score.

## Why this version?
- Uses **local images** in `static/images/` so there are **no broken external links**.
- Caches features in **CSV** (no PyArrow/fastparquet needed).
- Simple features (pHash + RGB histogram) for explainable similarity.

## Run locally
```bash
python -m venv .venv
# Windows: .venv\Scripts\activate
# macOS/Linux: source .venv/bin/activate
pip install -r requirements.txt
python app.py
```
Open http://127.0.0.1:5000

## Catalog
- Edit `data/products.csv` (already contains 50 items).
- Each row: `id,name,category,image_url,price`
- For local images, `image_url` points to `static/images/*.jpg`.

## Notes
- If you change `data/products.csv`, **delete** `data/index.csv` so it rebuilds the feature index.
- For stronger results later, swap features with CLIP embeddings and a vector DB.
