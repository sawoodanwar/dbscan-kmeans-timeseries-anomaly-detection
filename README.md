# Density-Based and Centroid-Based Clustering for Time Series Anomaly Detection

[![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/sawoodanwar/dbscan-kmeans-timeseries-anomaly-detection/blob/main/dbscan_kmeans_timeseries.ipynb)

**Author:** Sawood Anwar | [ORCID: 0009-0000-2819-9179](https://orcid.org/0009-0000-2819-9179)

---

## Overview

This notebook demonstrates two unsupervised clustering approaches for detecting anomalous and low-quality patterns in multivariate time series data:

| Method | Approach | Anomaly criterion |
|--------|----------|-------------------|
| **DBSCAN** | Density-based; no k required | Noise points (label = −1) |
| **K-Means** | Centroid-based; k selected by Silhouette + Davies-Bouldin | Distance to nearest centroid > 95th percentile |

The methods are then compared on anomaly agreement, temporal distribution, and interpretability — mirroring the comparative evaluation task in Euronext Clearing research position Ref. R28837.

---

## Dataset

[Air Quality UCI](https://archive.ics.uci.edu/ml/datasets/Air+Quality) — 9,358 hourly sensor readings from a metal oxide chemical sensor array in an Italian city (March 2004 – February 2005). Contains known missing values (−200) and sensor drift, making it a realistic proxy for industrial time series data quality challenges.

---

## Workflow

1. **Load & clean** — handle missing values (forward/back fill for short gaps)
2. **Feature engineering** — 24-hour rolling mean, std, and rate-of-change per sensor
3. **Standardise** — StandardScaler; PCA for visualisation
4. **DBSCAN** — k-distance elbow plot → eps selection → noise point extraction
5. **K-Means** — elbow + Silhouette + Davies-Bouldin → optimal k → centroid-distance anomaly score
6. **Comparative evaluation** — agreement matrix, monthly temporal distribution, summary table

---

## Requirements

Install dependencies:

```
pip install -r requirements.txt
```

Or run directly in the browser with no installation via the **Open In Colab** badge above.

---

## Key outputs

| File | Description |
|------|-------------|
| `k_distance_plot.png` | DBSCAN eps selection |
| `dbscan_pca.png` | DBSCAN clusters + anomalies in PCA space |
| `dbscan_timeseries.png` | Anomalies on original time axis |
| `kmeans_selection.png` | Elbow / Silhouette / Davies-Bouldin plots |
| `kmeans_pca.png` | K-Means clusters + anomaly overlay |
| `comparison_monthly.png` | Monthly anomaly counts by method |
| `anomaly_flags.csv` | All flagged records with method labels |

---

## License

This project is released under the [MIT License](LICENSE).

---

## Related work

This repository supports the methodological section of my doctoral thesis:

> Anwar, S. (2025). *"Facebook Reactions" as Emotional Indicators: A Multi-Method Approach to Analyzing User Engagement with COVID-19 News on Indian Media Platforms* [Doctoral dissertation, University of Urbino Carlo Bo]. https://ora.uniurb.it/handle/11576/2761691

Peer-reviewed publication:

> Anwar, S., & Giglietto, F. (2024). Facebook reactions in the context of politics and social issues: A systematic literature review. *Frontiers in Sociology*, 9. https://doi.org/10.3389/fsoc.2024.1379265
