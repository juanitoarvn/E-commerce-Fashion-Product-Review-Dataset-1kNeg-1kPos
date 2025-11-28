# E-commerce-Fashion-Product-Review-Dataset-1kNeg-1kPos

This repository includes `combined_text_1k_pos_1k_neg.csv`, a **balanced sentiment dataset** of **2,000 Indonesian fashion e-commerce reviews** designed for text (and optionally multimodal) sentiment classification.

## Quick Stats
- **Total samples:** 2,000
- **Class balance:** 1,000 **Positive** + 1,000 **Negative**
- **Labeling rule (rating-based):**
  - **Positive** if `rating` ∈ {4, 5}
  - **Negative** if `rating` ∈ {1, 2}
  - *(Rating 3 is not included in this subset)*
- **Image availability (optional multimodal fields):**
  - 1,255 rows include an image URL/filename
  - 745 rows are text-only (`"Tidak ada gambar"`)
- **Dates:**
  - Some rows contain `tanggal` (range: **2024-01-01** to **2025-08-30**)
  - Others use `"Tidak ada tanggal"`

## File
- `combined_text_1k_pos_1k_neg.csv`

## Columns (Schema)

| Column | Type | Description |
|---|---|---|
| `review_id` | string | Unique ID per review (e.g., `A000044`) |
| `tanggal` | string | Review date (`YYYY-MM-DD`) or `"Tidak ada tanggal"` |
| `username` | string / nullable | Username (may be masked or empty) |
| `review` | string | Raw review text (Indonesian), may include emojis |
| `clean_text` | string | Preprocessed/normalized version of `review` for modeling |
| `nama_produk` | string | Product name/title |
| `variasi_produk` | string / nullable | Variant information (may be missing) |
| `link_gambar` | string | Image URL or `"Tidak ada gambar"` |
| `file_gambar` | string | Image filename (e.g., `A000044.jpg`) or `"Tidak ada gambar"` |
| `rating` | int | Star rating (1, 2, 4, or 5) |
| `sentiment` | string | Sentiment label: `Positive` / `Negative` |
| `sentiment_numeric` | int | Numeric label (`1` = Positive, `0` = Negative) |

## Notes
- `clean_text` is included to support reproducible NLP pipelines.
- Image-related columns (`link_gambar`, `file_gambar`) allow multimodal workflows, but many samples are text-only.
- This dataset is intended for research/educational purposes (sentiment modeling, benchmarking, and preprocessing experiments).

## Example Usage (Python)

```python
import pandas as pd

df = pd.read_csv("combined_text_1k_pos_1k_neg.csv")
print(df.shape)
print(df["sentiment"].value_counts())
