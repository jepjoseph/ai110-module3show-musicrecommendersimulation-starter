# 🎧 Model Card: Music Recommender Simulation

## 1. Model Name  

Give your model a short, descriptive name.  
Example: **MyRec 1.0**  

---

## 2. Intended Use  

This recommender is designed to recommend songs based on a user's musical preferences. It generates recommendations by comparing the user's favorite genre, mood, and preferred energy level with the characteristics of each song in the catalog. The model assumes that users enjoy songs with similar features to the ones they prefer. This project is intended for classroom learning and demonstrates the basic concepts behind content-based recommendation systems rather than serving as a production music recommendation service.

---

## 3. How the Model Works  

The recommender compares each song with the user's preferences and assigns it a score. Songs earn the most points when their genre matches the user's favorite genre, followed by matching the user's preferred mood. The system also compares the song's energy level with the user's preferred energy level. Songs whose energy is closer to the user's preference receive higher scores. After every song has been scored, the recommender sorts them from highest to lowest score and returns the top recommendations. Compared to the starter code, I implemented a scoring algorithm that ranks songs instead of simply returning the first few songs in the dataset.

---

## 4. Data  

The dataset contains 10 songs with information including title, artist, genre, mood, energy, tempo, valence, danceability, and acousticness. The catalog includes genres such as pop, rock, lofi, jazz, ambient, synthwave, and indie pop, along with moods like happy, chill, focused, relaxed, intense, and moody. I used the provided dataset without adding or removing songs. Because the dataset is small, it does not represent the wide variety of music or listening preferences found in real-world streaming services.

---

## 5. Strengths  

The recommender performs well when a user's preferences closely match the available song features. It successfully identifies songs with the same genre and mood while also recommending songs whose energy level is similar to the user's preferred energy. For example, a user who prefers pop, happy music with high energy receives recommendations that closely match those preferences, which aligns with my expectations.

---

## 6. Limitations and Bias 

The recommender only considers a few song features and ignores many aspects of musical taste, such as lyrics, language, popularity, listening history, favorite artists, or user feedback. The small dataset also means that some genres and moods are represented by only one or two songs, which can bias recommendations toward the more common categories. Since genre receives the highest weight, the system may overlook songs from other genres that have similar moods or energy levels.

---

## 7. Evaluation  

I tested the recommender using the sample user profile with a preference for pop music, a happy mood, and an energy level of 0.8. I checked whether the songs with matching genres and moods appeared at the top of the recommendations and whether the scores matched my scoring rules. The results were consistent with the algorithm, and the highest-ranked songs matched my expectations based on their features.

---

## 8. Future Work  

I would improve the recommender by including additional features such as favorite artists, tempo preferences, and listening history. I would also use user ratings or feedback so the recommendations could improve over time. Another improvement would be increasing the diversity of recommendations so users are occasionally introduced to songs outside their usual preferences while still matching their overall musical taste.

---

## 9. Personal Reflection  

This project helped me understand how recommendation systems transform user preferences and item features into numerical scores that can be used to rank recommendations. Before completing this project, I knew music apps recommended songs, but I did not realize how much the recommendation depends on carefully choosing and weighting features.

I also learned that even a simple recommendation system can introduce bias if the dataset is small or if some features receive much higher weights than others. This project gave me a better appreciation for the complexity of the recommendation systems used by music streaming platforms and other online services.
