# 🎵 Spotify Data Analysis with Python

> Uncovering insights about song attributes, artist trends, and listener behavior through comprehensive exploratory data analysis of Spotify's music catalog.

---

## 📋 Table of Contents

- [Project Overview](#-project-overview)
- [Dataset](#-dataset)
- [Tech Stack](#-tech-stack)
- [Project Structure](#-project-structure)
- [Analysis Workflow](#-analysis-workflow)
- [Key Insights](#-key-insights)
- [Visualizations](#-visualizations)
- [Recommendations](#-recommendations)
- [How to Run](#-how-to-run)
- [License](#-license)

---

## 🎯 Project Overview

This project performs an end-to-end exploratory data analysis (EDA) on Spotify music data to answer questions like:

- **What makes a song popular?** — Which audio features correlate with higher popularity?
- **How has music evolved?** — How have features like energy, loudness, and acousticness changed over the decades?
- **What genres dominate?** — Which genres are growing, and which are declining?
- **What defines a great playlist?** — What audio feature profiles work best for Party, Chill, Workout, and Coffee Shop playlists?

The ultimate goal is to provide **actionable insights** for music labels, playlist curators, artists, and the platform itself.

---

## 📊 Dataset

| File            | Rows      | Columns | Description                                |
| --------------- | --------- | ------- | ------------------------------------------ |
| `tracks.csv`  | 586,672   | 20      | Song metadata + Spotify audio features     |
| `artists.csv` | 1,104,349 | 5       | Artist name, followers, genres, popularity |

### Key Features (Tracks)

| Feature              | Description                              | Range      |
| -------------------- | ---------------------------------------- | ---------- |
| `popularity`       | How popular the song is based on streams | 0–100     |
| `danceability`     | How suitable a song is for dancing       | 0–1       |
| `energy`           | Intensity and activity level of the song | 0–1       |
| `loudness`         | Overall loudness in decibels (dB)        | −60 to ~5 |
| `speechiness`      | Presence of spoken words                 | 0–1       |
| `acousticness`     | Confidence that the track is acoustic    | 0–1       |
| `instrumentalness` | Likelihood the track has no vocals       | 0–1       |
| `liveness`         | Presence of a live audience              | 0–1       |
| `valence`          | Musical positiveness (happy vs. sad)     | 0–1       |
| `tempo`            | Speed of the song in BPM                 | 0–246     |

**Data Source:** Spotify Web API / publicly available repositories.

---

## 🛠️ Tech Stack

| Tool                       | Purpose                                        |
| -------------------------- | ---------------------------------------------- |
| **Python 3**         | Core programming language                      |
| **Pandas**           | Data loading, cleaning, manipulation           |
| **NumPy**            | Numerical computations                         |
| **Matplotlib**       | Static charts (histograms, boxplots, heatmaps) |
| **Seaborn**          | Statistical visualizations                     |
| **Plotly**           | Interactive charts and dashboards              |
| **Jupyter Notebook** | Development & presentation environment         |

---

## 📁 Project Structure

```
spotify/
├── spotify_data/
│   ├── tracks.csv          # Tracks dataset
│   └── artists.csv         # Artists dataset
├── spotify_data_analysis.ipynb   # Main analysis notebook
└── README.md               # This file
```

---

## 🔄 Analysis Workflow

### 1. Data Preparation

- Loaded two datasets (tracks + artists).
- Identified and handled missing values:
  - 71 missing track names → filled with `'Unknown Track'`.
  - 13 missing artist follower counts → filled with `0`.
  - 3 missing artist names → filled with `'Unknown Artist'`.
- Checked for duplicates — **0 duplicates** found in tracks.
- **Feature Engineering:**
  - Extracted `release_year` from date strings (range: 1900–2021).
  - Created `decade` column for trend analysis.
  - Converted `duration_ms` → `duration_min`.
  - Categorized popularity into `Low / Medium / High / Very High`.
  - Extracted `primary_artist` from artist lists.
  - Computed `energy_dance_ratio`.
  - Parsed genre lists → `primary_genre` and `genre_count`.

### 2. Exploratory Data Analysis (EDA)

- **Descriptive Statistics:** Mean, median, std, skewness, kurtosis for all audio features.
- **Correlation Analysis:** Heatmap revealing feature relationships.
- **Univariate Analysis:** Histograms showing distribution of each feature.
- **Bivariate Analysis:** Scatter plots exploring feature-pair relationships.
- **Outlier Detection:** Boxplots identifying anomalies in loudness, tempo, and duration.

### 3. Data Visualization

- Top artists and songs by track count and popularity.
- Audio feature distributions grouped by popularity category (violin/box plots).
- Explicit vs. non-explicit content analysis.

### 4. Musical Trend Analysis

- **Time Series:** How danceability, energy, loudness, acousticness, and duration evolved across decades.
- **Genre Trends:** Growth of hip-hop and electronic genres since 2000.
- **Artist Trends:** Prolific artists vs. popular artists — quality vs. quantity.

### 5. Insights Extraction & Interactive Exploration

- Popularity prediction features analysis.
- Ideal playlist feature profiles.
- Interactive Plotly-based feature explorer.
- Musical key and mode (Major vs. Minor) analysis.

---

## 💡 Key Insights

| # | Insight                                                                                                                                                                     |
| - | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| 1 | **Popularity Drivers:** Loudness (+0.33) and energy (+0.30) positively correlate with popularity; acousticness (−0.37) negatively correlates.                        |
| 2 | **Music Evolution:** Over the decades, music has become louder, more danceable, and less acoustic — reflecting the shift from live recordings to digital production. |
| 3 | **Genre Landscape:** Pop, rock, and hip-hop dominate. Hip-hop and electronic genres have grown dramatically since 2000.                                               |
| 4 | **Duration Trends:** Average song duration has decreased in recent years — streaming-era listeners prefer ~2.5–3.5 minute tracks.                                   |
| 5 | **Explicit Content:** Explicit tracks tend to have higher energy, higher danceability, and slightly higher average popularity.                                        |

### Top Feature Correlations

| Feature Pair               | Correlation       |
| -------------------------- | ----------------- |
| Energy ↔ Loudness         | **+0.765**  |
| Energy ↔ Acousticness     | **−0.715** |
| Danceability ↔ Valence    | **+0.528**  |
| Loudness ↔ Acousticness   | **−0.519** |
| Acousticness ↔ Popularity | **−0.371** |

---

## 📊 Visualizations

The notebook includes the following visualizations:

- 📈 **Correlation Heatmap** — Relationships between all audio features and popularity
- 📊 **Histograms** — Distribution of danceability, energy, loudness, tempo, valence, etc.
- 📦 **Boxplots** — Outlier detection across features
- 📉 **Line/Area Charts** — Feature evolution across decades (1920s–2020s)
- 🎤 **Bar Charts** — Top artists by track count and popularity
- 🎵 **Violin Plots** — Audio features grouped by popularity category
- 🔑 **Key & Mode Analysis** — Track distribution by musical key (C, D, E...) and Major vs. Minor
- 🎛️ **Interactive Plotly Charts** — Explorable scatter plots and dashboards

---

## 📌 Recommendations

### Playlist Feature Profiles

| Playlist Type    | Danceability | Energy | Tempo (BPM) | Valence  |
| ---------------- | ------------ | ------ | ----------- | -------- |
| 🎉 Party / Club  | > 0.7        | > 0.7  | 120–130    | > 0.6    |
| 📚 Chill / Study | < 0.5        | < 0.4  | 80–100     | 0.3–0.5 |
| 🏋️ Workout     | > 0.6        | > 0.8  | 130–150    | > 0.5    |
| ☕ Coffee Shop   | < 0.5        | < 0.3  | 90–110     | 0.4–0.6 |

### Business Recommendations

1. **For Labels:** Focus on high-energy, danceable tracks with moderate tempo for maximum streaming potential.
2. **For Playlist Curators:** Use the audio feature profiles above to create targeted, mood-based playlists.
3. **For Artists:** Songs in Major keys with higher loudness and energy tend to perform better on the platform.
4. **For Spotify:** The growing trend toward shorter songs suggests optimizing recommendations for playlist-friendly track lengths (2.5–3.5 min).

---

## 🚀 How to Run

### Prerequisites

- Python 3.8+
- Jupyter Notebook or JupyterLab


### Dataset Setup

Place the dataset files inside the `spotify_data/` directory:

```
spotify_data/
├── tracks.csv
└── artists.csv
```
