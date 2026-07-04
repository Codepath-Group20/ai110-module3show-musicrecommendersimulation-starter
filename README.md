# 🎵 Music Recommender Simulation

## Project Summary

In this project you will build and explain a small music recommender system.

Your goal is to:

- Represent songs and a user "taste profile" as data
- Design a scoring rule that turns that data into recommendations
- Evaluate what your system gets right and wrong
- Reflect on how this mirrors real world AI recommenders

Replace this paragraph with your own summary of what your version does.

---

## How The System Works

Explain your design in plain language.

Some prompts to answer:

- What features does each `Song` use in your system
  - For example: genre, mood, energy, tempo
- What information does your `UserProfile` store
- How does your `Recommender` compute a score for each song
- How do you choose which songs to recommend

You can include a simple diagram or bullet list if helpful.

---
Overview of Real-World Systems
Modern music platforms rely on two primary recommendation frameworks:
Collaborative Filtering: Analyzes user behavior patterns (likes, shares, skips) to group similar users together and recommend music based on collective listening habits.
Content-Based Filtering: Analyzes the intrinsic qualities of individual tracks (such as tempo, genre, and acousticness) to recommend music with matching mathematical and categorical profiles.
Our Simulation Approach
This simulation prioritizes a Content-Based Filtering approach using a weighted-score scoring rule. Instead of blindly favoring high-energy or high-valence tracks, the algorithm calculates the absolute distance between a song's attributes ($F$) and a user's specified ideal preferences ($P$). The individual feature alignment is calculated using the formula:
Feature Score = 1.0 - |Fsong - Puser|
The system then aggregates these continuous feature scores along with categorical bonuses (like exact genre and mood matches) using customizable user-profile weights to compute an overall compatibility score for each track. Finally, a ranking rule sorts the full catalog to generate a clean, top-$N$ list of personalized suggestions.
Data Structures
Song Object Attributes
id (int): Unique identifier for the track.
title (string): Title of the song.
artist (string): Performing artist.
genre (string): Categorical genre (e.g., pop, lofi, rock).
mood (string): Categorical vibe indicator (e.g., happy, chill, intense).
energy (float): Numerical value from 0.0 to 1.0 representing intensity.
tempo_bpm (int): Beats per minute.
valence (float): Numerical value from 0.0 to 1.0 describing musical positivity.
danceability (float): Numerical value from 0.0 to 1.0 representing rhythmic stability.
acousticness (float): Numerical value from 0.0 to 1.0 tracking acoustic vs electronic presence.
UserProfile Object Attributes
user_id (int/string): Unique identification for the user.
preferred_genres (list of strings): Target categories for hard matching or bonuses.preferred_moods (list of strings): Target moods for contextual affinity.
target_features (dict): Ideal baseline float values for continuous metrics (energy, valence, danceability, acousticness).
feature_weights (dict): Importance scaling metrics assigned to individual features, ensuring heavily weighted preferences exert a greater influence over final song calculation scores.

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

Paste a sample of your recommender's output here as a text block so a reader can see what it produces:

```
# e.g.:
# User profile: genre=indie, mood=chill, energy=low
# Recommendations:
#   1. ...
#   2. ...
#   3. ...
```

**Screenshot or video** *(optional)*: <!-- Insert a screenshot or demo video link here -->

---

## Experiments You Tried

Use this section to document the experiments you ran. For example:

- What happened when you changed the weight on genre from 2.0 to 0.5
- What happened when you added tempo or valence to the score
- How did your system behave for different types of users

---

## Limitations and Risks

Summarize some limitations of your recommender.

Examples:

- It only works on a tiny catalog
- It does not understand lyrics or language
- It might over favor one genre or mood

You will go deeper on this in your model card.

---

## Reflection

Read and complete `model_card.md`:

[**Model Card**](model_card.md)

Write 1 to 2 paragraphs here about what you learned:

- about how recommenders turn data into predictions
- about where bias or unfairness could show up in systems like this



