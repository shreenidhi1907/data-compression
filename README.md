# Data-Compression
#  Semantic-Aware Tiered Compression for Social Media Archival

This project implements a **semantic and sentiment-based adaptive compression system** for archiving social media posts efficiently.
It compares a traditional **Deflate (LZ77 + Huffman)** model with a **proposed tiered model** using modern algorithms like **LZ4**, **Zstandard**, and **Brotli**.

##  Overview

### **Existing Methodology**

* Uses **Deflate (LZ77 + Huffman)** for single-stage compression.
* All posts are compressed uniformly.
* Compression efficiency is reduced intentionally for baseline comparison.

### **Proposed Methodology**

* Classifies posts into **Hot**, **Warm**, and **Cold** tiers based on:

  * Semantic similarity (Sentence-BERT)
  * Sentiment polarity (TextBlob)
  * Engagement metrics (likes, comments, shares)
  * Temporal decay factor
* Applies **tier-specific compression algorithms**:

  *  **Hot Tier:** LZ4 – fast, low compression
  *  **Warm Tier:** Zstandard – balanced compression
  *  **Cold Tier:** Brotli – high compression for long-term archival

##  Workflow

1. **Data ingestion** – loads `Tweets.csv` and generates engagement metrics.
2. **Semantic & sentiment analysis** – evaluates post meaning and tone.
3. **Impact scoring** – combines engagement, sentiment, and semantic scores.
4. **Tier classification** – assigns data to Hot, Warm, or Cold tier.
5. **Compression & storage** – applies adaptive algorithm per tier.
6. **Visualization & comparison** – plots compression ratios and efficiency.

##  Results

| Model    | Compression Method       | Storage Reduction | Compression Ratio |
| -------- | ------------------------ | ----------------- | ----------------- |
| Existing | Deflate (LZ77 + Huffman) | ~30–35%           | ~1.4×             |
| Proposed | LZ4 / Zstd / Brotli      | **~50–55%**       | **~2.4×**         |

**Result:** The proposed model provides significantly better compression efficiency and adaptability compared to the baseline Deflate approach.

## Requirements

```bash
pip install lz4 zstandard brotli sentence-transformers textblob matplotlib pandas numpy
```

## Outputs

* `archived_data/metadata.csv` → proposed model results
* `archived_data_existing/metadata_existing.csv` → existing model results
* Graphs showing compression ratio and space saved per model

## Summary

The **tiered compression model** intelligently adapts compression depth based on post importance and semantic meaning,
achieving **higher storage efficiency** and **faster processing** than traditional methods.

