# Moosic Playlist Segmentation

## Project Overview

How can thousands of songs be automatically organized into playlists that are
both musically meaningful and practical for a real music platform?

This project uses unsupervised machine learning to segment **5,235 songs**
according to their Spotify audio characteristics. The objective was not only
to find similar songs, but to create playlists that satisfy a real-world
business constraint:

> Every playlist must contain between **50 and 250 songs**.

The final solution produced **32 named playlists**, with every playlist
containing between **65 and 232 songs**.

---

## Business Objective

A purely mathematical clustering solution does not necessarily produce a
useful playlist system.

For Moosic, a playlist that is too small may not provide enough variety, while
a playlist that is too large may be difficult to manage or too broad in its
musical identity.

The project therefore had two objectives:

| Objective | Requirement |
|---|---|
| Musical segmentation | Group songs with similar audio characteristics |
| Business constraint | Every playlist must contain 50–250 songs |

The final solution needed to satisfy both.

---

## Dataset

The dataset contains Spotify-style audio features describing the musical
characteristics of each song.

The features used for dimensionality reduction and clustering included:

| Feature | Description |
|---|---|
| `danceability` | How suitable a track is for dancing |
| `energy` | Perceptual intensity and activity |
| `key` | Musical key |
| `loudness` | Overall loudness of the track |
| `mode` | Major/minor modality |
| `speechiness` | Presence of spoken words |
| `acousticness` | Confidence that a track is acoustic |
| `instrumentalness` | Likelihood that a track contains no vocals |
| `liveness` | Presence of an audience or live-performance characteristics |
| `valence` | Musical positivity or mood |
| `tempo` | Estimated beats per minute |
| `duration_ms` | Track duration |
| `time_signature` | Estimated time signature |

Before clustering, the numerical features were standardized so that features
with larger scales would not dominate the distance calculations.

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

---

