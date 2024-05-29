[![Review Assignment Due Date](https://classroom.github.com/assets/deadline-readme-button-24ddc0f5d75046c5622901739e7c5dd533143b0c8e959d652212380cedb1ea36.svg)](https://classroom.github.com/a/1lXY_Wlg)

# Spotify Stats & Insights
## Problem description
So, there are a lot of dashboards about Spotify statistics/insights. Even Spotify itself will display customized dashboard of your most recently played tracks, artists, podcasts, trending charts, etc.
This project is slightly different. In this project, I aim to uncover and help visualize a lot of interesting data points that Spotify provides about various entities (Artists, tracks, podcasts) that will:
1. Give you an interesting view of your user level metrics (Dashboard)
2. Give you an interesting view of global level metrics (Dashboard)

Some interesting data points to be displayed by this project 
(Filtering feature TBD. I'd probably allow filtering by country, artist, genre):
1. Top 10 most acoustic tracks
2. Top 10 most acoustic artists
3. Top 10 most dance-able tracks
4. Top 10 most artists with most dance-able tracks
5. Few more for: 
   1. Most energetic, instrumental, live in a concert, etc.
6. Audio analysis for a track
   1. Tempo, beats, etc.
7. More to come

## Use cases:
1. Dashboard
2. OLAP database in a data warehouse (Most likely BigQuery)
3. Publish the data to Kaggle for community usage

## Data sources
1. Batch data:
   1. Huggingface - https://huggingface.co/datasets/maharshipandya/spotify-tracks-dataset
   2. Kaggle - https://www.kaggle.com/datasets/asaniczka/top-spotify-songs-in-73-countries-daily-updated
2. Spotify API - https://developer.spotify.com/documentation/web-api/reference/

## High level overview diagram
![overview-diagram]

## Schemas
1. Batch data - Spotify track dataset
- dim_tracks_dataset
  - track_id: The Spotify ID for the track
  - artists: The artists' names who performed the track.
  - album_name: The album name in which the track appears
  - track_name: Name of the track
  - popularity: The popularity of a track is a value between 0 and 100, with 100 being the most popular. 
  - duration_ms: The track length in milliseconds
  - acousticness: A confidence measure from 0.0 to 1.0 of whether the track is acoustic. 1.0 represents high confidence the track is acoustic
  - danceability: Danceability describes how suitable a track is for dancing based on a combination of musical elements including tempo, rhythm stability, beat strength, and overall regularity. A value of 0.0 is least danceable and 1.0 is most danceable
  - energy: Energy is a measure from 0.0 to 1.0 and represents a perceptual measure of intensity and activity. Typically, energetic tracks feel fast, loud, and noisy. For example, death metal has high energy, while a Bach prelude scores low on the scale

2. Live streamed API data
- dim_tracks_audio_features
- dim_tracks_audio_analysis

3. Analytics tables
   1. fct_most_acoustic_tracks
      - track_id
      - country_code
      - acousticness_score (aggregated by track_id)
   2. fct_most_danceable_tracks
      - track_id
      - country_code
      - acousticness_score (aggregated by track_id)
   3. fct_most_acoustic_artist
      - country_code
      - artist_id
      - acousticness_score (aggregated by artist_id)
   4. TBD

## Data storage
1. Raw data will be stored in Google cloud storage
2. Data warehouse will be Google BigQuery

## Visualization
Deciding between Streamlit OR Metabase

## Author
Contact `Akshay Jain` on [LinkedIn][linkedin]

[linkedin]: https://www.linkedin.com/in/akshayrjain/
[overview-diagram]: ./images/Spotify%20stats.drawio.svg