# Moosic Playlist Segmentation

## Project Overview

How can thousands of songs be automatically organized into playlists that are both musically meaningful and practical for a real music platform?

This project uses unsupervised machine learning to segment **5,235 songs** according to their Spotify audio characteristics. The goal was not only to find similar songs, but to create playlists that satisfy a real-world business constraint:

> Every playlist must contain between **50 and 250 songs**.

The final solution produced **32 named playlists**, with every playlist containing between **65 and 232 songs**.

---

## Business Objective

A mathematically valid clustering solution does not necessarily produce a useful playlist system.

For Moosic, playlists need to provide enough variety while maintaining a meaningful musical identity.

| Objective | Requirement |
|---|---|
| Musical segmentation | Group songs with similar audio characteristics |
| Business constraint | Every playlist must contain 50–250 songs |

The final solution needed to satisfy both objectives.

---

## Dataset

The dataset contains Spotify-style audio features describing the musical characteristics of each song.

| Feature | Description |
|---|---|
| `danceability` | How suitable a track is for dancing |
| `energy` | Perceptual intensity and activity |
| `key` | Musical key |
| `loudness` | Overall loudness |
| `mode` | Major/minor modality |
| `speechiness` | Presence of spoken words |
| `acousticness` | Likelihood that a track is acoustic |
| `instrumentalness` | Likelihood that a track contains no vocals |
| `liveness` | Live-performance characteristics |
| `valence` | Musical positivity or mood |
| `tempo` | Estimated beats per minute |
| `duration_ms` | Track duration |
| `time_signature` | Estimated time signature |

The numerical features were standardized before clustering so that features with different scales would contribute appropriately to the distance calculations.

---

## Methodology

The project followed a staged machine-learning workflow:

```text
Spotify Audio Features
        |
        v
Data Preparation
        |
        v
Feature Scaling
        |
        v
Principal Component Analysis
        |
        v
K-Means Clustering
        |
        v
Business Constraint Check
        |
        v
Selective Cluster Splitting
        |
        v
Silhouette / Coherence Analysis
        |
        v
Playlist Profiling
        |
        v
Human-Readable Playlist Names
        |
        v
Final Playlist Assignment
```

---

## Results

The final clustering solution transformed **5,235 songs into 32 practical playlists** while satisfying Moosic's business constraint.

| Metric | Result |
|---|---:|
| Total songs | 5,235 |
| Final playlists | 32 |
| Smallest playlist | 65 songs |
| Largest playlist | 232 songs |
| Required playlist size | 50–250 songs |
| All playlists within requirement | Yes |
| PCA components | 6 |
| Variance retained | 92.7% |
| Final silhouette score | 0.224 |
| Unassigned songs | 0 |

### Initial vs. Final Clustering

The initial K-Means solution produced 23 clusters, but some exceeded the 250-song limit.

| Metric | Initial K-Means | Final Solution |
|---|---:|---:|
| Number of clusters | 23 | 32 |
| Smallest cluster | 81 | 65 |
| Largest cluster | 508 | 232 |
| All within 50–250 songs | No | Yes |

Rather than removing songs or repeatedly changing the initial number of clusters, oversized clusters were selectively split. This preserved the complete dataset while satisfying the business requirement.

---

## Key Insights

### Business Constraint and Clustering Quality

The project demonstrates that the best machine-learning solution is not always the most useful business solution.

The initial K-Means model identified musical similarities, but several clusters were too large to function as practical playlists. Selective splitting allowed the clustering structure to be refined without losing any songs.

### Musical Profiles

The final clusters showed recognizable differences across the main Spotify audio features.

| Playlist Profile | Typical Characteristics |
|---|---|
| Acoustic Chill | Higher acousticness and lower energy |
| Acoustic Instrumentals | High acousticness and instrumentalness |
| High-Energy Instrumentals | High energy and instrumentalness |
| High-Energy Mix | High energy and relatively high tempo |
| Mellow Acoustic | Higher acousticness with moderate danceability |
| Upbeat Grooves | Higher danceability and energy |
| Feel-Good Dance | High danceability and valence |
| Happy Grooves | High valence with moderate-to-high danceability |
| Balanced Mix | More balanced musical characteristics |

These numerical clusters were translated into human-readable playlist names to make the final output more interpretable.

---

## Cluster Coherence

Silhouette analysis was used to evaluate how well songs fit within their assigned clusters compared with neighboring clusters.

The final overall silhouette score was **0.224**, indicating moderate separation between clusters.

| Coherence Measure | Silhouette Score |
|---|---:|
| Overall final solution | 0.224 |
| Strongest playlist | 0.456 |
| Second strongest | 0.407 |
| Third strongest | 0.365 |
| Lowest examples | 0.062–0.116 |

Some overlap is expected because musical styles can naturally share similar characteristics.

---

## Final Playlist Structure

The final 32 playlists were given descriptive names based on their dominant musical characteristics.

| Playlist | Songs |
|---|---:|
| Balanced Mix | 126 |
| Acoustic Instrumentals | 172 |
| Acoustic Instrumentals 2 | 194 |
| Acoustic Instrumentals 3 | 225 |
| Acoustic Chill | 141 |
| Acoustic Chill 2 | 81 |
| Acoustic Chill 3 | 166 |
| Mellow Acoustic | 97 |
| Mellow Acoustic 2 | 232 |
| Mellow Acoustic 3 | 115 |
| High-Energy Mix | 172 |
| High-Energy Mix 2 | 164 |
| High-Energy Mix 3 | 203 |
| High-Energy Mix 4 | 212 |
| High-Energy Mix 5 | 195 |
| Feel-Good Dance | 182 |
| Feel-Good Dance 2 | 223 |
| Feel-Good Dance 3 | 113 |
| Feel-Good Dance 4 | 156 |
| Happy Grooves | 215 |

Numbered variants represent different clusters with similar musical profiles.

---

## Visualizations

The analysis includes visualizations covering:

- PCA explained variance
- PCA feature loadings
- Cluster evaluation
- Final playlist sizes
- Musical profiles
- Playlist-level silhouette scores

These visualizations provide both a technical view of the clustering process and a practical view of the resulting playlist structure.

---

## Final Deliverable

The final output is provided in:

`final_playlist.csv`

| Column | Description |
|---|---|
| `name` | Song title |
| `artist` | Artist name |
| `playlist_id` | Final cluster identifier |
| `playlist_name` | Human-readable playlist name |

The final export contains all **5,235 songs**.

### Final Validation

```text
Original dataset: 5,235
Final export:     5,235
Difference:           0
```

Every song has a valid playlist assignment, and every playlist satisfies the 50–250 song requirement.

---

## Tools

**Python · Pandas · NumPy · Scikit-learn · PCA · K-Means · Matplotlib · Jupyter Notebook**

---

## Conclusion

This project demonstrates how unsupervised machine learning can be adapted to a real-world business problem rather than used purely for statistical clustering.

Starting with **5,235 songs**, the final approach produced **32 interpretable playlists**, with every playlist containing **65–232 songs** and every song successfully assigned.

The key result was balancing three competing objectives:

**Musical similarity + cluster coherence + business usability**

Rather than discarding songs or repeatedly changing the global clustering structure, oversized clusters were selectively split. This preserved the complete dataset while meeting Moosic's playlist-size requirement.

The final result is therefore not just a clustering model, but a **practical playlist segmentation system** that converts raw audio features into interpretable, usable music categories.
