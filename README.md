# 🎵 Music Recommender Simulation

## Project Summary

This project simulates a simple content-based music recommender system. It compares a user's music preferences with the characteristics of each song in the dataset and assigns each song a score. The system recommends the songs with the highest scores based on matching genre, mood, and energy level. This project demonstrates how recommendation systems use user preferences and item features to make personalized suggestions.

---

## How The System Works

This recommender uses a content-based filtering approach. Each song is described using features such as genre, mood, energy, tempo, valence, danceability, and acousticness. The user's preferences are stored in a `UserProfile`, which includes a favorite genre, favorite mood, preferred energy level, and whether the user likes acoustic music.

Each song is compared to the user's preferences and receives a score. A matching genre is worth **3 points**, a matching mood is worth **2 points**, and the energy score is calculated based on how close the song's energy is to the user's preferred energy using the formula:

`Energy Score = 1 - |song_energy - user_energy|`

Songs with energy levels closer to the user's preference receive higher scores. After every song is scored, the recommender sorts the songs from highest score to lowest score and returns the top recommendations.

**Song Features**

* ID
* Title
* Artist
* Genre
* Mood
* Energy
* Tempo (BPM)
* Valence
* Danceability
* Acousticness

**UserProfile Features**

* Favorite Genre
* Favorite Mood
* Target Energy
* Likes Acoustic (True/False)


---

## Getting Started

### Setup

1. Create a virtual environment (optional but recommended):

   ```bash
   python -m venv .venv
   source .venv/bin/activate      # Mac or Linux
   .venv\Scripts\activate         # Windows

2. Install dependencies

```bash
pip install -r requirements.txt
```

3. Run the app:

```bash
python -m src.main
```

### Running Tests

Run the starter tests with:

```bash
pytest
```

You can add more tests in `tests/test_recommender.py`.

---

## Sample Recommendation Output

Loading songs from data/songs.csv...
Number of songs loaded: 10
Recommendations returned: [
  ({'id': 1, 'title': 'Sunrise City', 'artist': 'Neon Echo', 'genre': 'pop', 'mood': 'happy', 'energy': 0.82, 'tempo_bpm': 118, 'valence': 0.84, 'danceability': 0.79, 'acousticness': 0.18}, 5.98, 'Genre matches your preference, Mood matches your preference, Energy level is very close to your preference'), 
  
  ({'id': 10, 'title': 'Rooftop Lights', 'artist': 'Indigo Parade', 'genre': 'indie pop', 'mood': 'happy', 'energy': 0.76, 'tempo_bpm': 124, 'valence': 0.81, 'danceability': 0.82, 'acousticness': 0.35}, 5.96, 'Genre matches your preference, Mood matches your preference, Energy level is very close to your preference'), 
  
  ({'id': 5, 'title': 'Gym Hero', 'artist': 'Max Pulse', 'genre': 'pop', 'mood': 'intense', 'energy': 0.93, 'tempo_bpm': 132, 'valence': 0.77, 'danceability': 0.88, 'acousticness': 0.05}, 3.87, 'Genre matches your preference, Energy level is very close to your preference'), 
  
  ({'id': 8, 'title': 'Night Drive Loop', 'artist': 'Neon Echo', 'genre': 'synthwave', 'mood': 'moody', 'energy': 0.75, 'tempo_bpm': 110, 'valence': 0.49, 'danceability': 0.73, 'acousticness': 0.22}, 0.95, 'Energy level is very close to your preference'), 
  
  ({'id': 3, 'title': 'Storm Runner', 'artist': 'Voltline', 'genre': 'rock', 'mood': 'intense', 'energy': 0.91, 'tempo_bpm': 152, 'valence': 0.48, 'danceability': 0.66, 'acousticness': 0.1}, 0.89, 'Energy level is very close to your preference')
  ]

Number of recommendations returned: 5

Top recommendations:

Sunrise City - Score: 5.98
Because: Genre matches your preference, Mood matches your preference, Energy level is very close to your preference

Rooftop Lights - Score: 5.96
Because: Genre matches your preference, Mood matches your preference, Energy level is very close to your preference

Gym Hero - Score: 3.87
Because: Genre matches your preference, Energy level is very close to your preference

Night Drive Loop - Score: 0.95
Because: Energy level is very close to your preference

Storm Runner - Score: 0.89
Because: Energy level is very close to your preference




**Screenshot or video** *(optional)*: <!-- Insert a screenshot or demo video link here -->
<p align="center">
  <img src="assets/Demo.gif" width="800" alt="Demo">
</p>

---

## Experiments You Tried

- I tested the recommender using a user profile with the preferences: genre = pop, mood = happy, and energy = 0.8.
- The recommender correctly ranked songs that matched both the preferred genre and mood at the top of the list. "Sunrise City" and "Rooftop Lights" received the highest scores because they matched all three criteria: genre, mood, and a similar energy level.
- Songs that matched only the genre or only the energy received lower scores. For example, "Gym Hero" matched the preferred genre and had a similar energy level, but its mood did not match, so it ranked below the top two songs.
- Songs that only had a similar energy level but did not match the preferred genre or mood received the lowest scores. This confirmed that the genre and mood weights had a greater impact on the final ranking than energy alone.

---

## Limitations and Risks

This recommender has several limitations. It only uses a small dataset of ten songs, so its recommendations are limited. The system only compares song features and does not learn from user listening history, ratings, or feedback. It also does not consider lyrics, popularity, or context, such as the time of day or the user's activity. Because genre has the highest weight, the recommender may overlook songs from other genres that have similar moods or energy levels.

---

## Reflection

Read and complete `model_card.md`:

[**Model Card**](model_card.md)

This project helped me understand how recommendation systems compare user preferences with item features to make predictions. Even a simple scoring algorithm can produce personalized recommendations by assigning weights to important features and ranking the results based on their scores.

I also learned that recommendation systems can introduce bias depending on how they are designed. If certain features are weighted too heavily or the dataset is too small, the system may repeatedly recommend similar songs while ignoring other good options. Real-world recommendation systems reduce these problems by using much larger datasets, machine learning, and user feedback to improve recommendations over time.

