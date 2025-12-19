# Movie Ratings & Recommendation Project

## Overview

I have been keeping track of all the movies I have watched and rated on Letterboxd. Currently, I have logged over **700 movies** and rated **688** of them. Visualizing this data was my first goal after learning I could export it from the site.

I then realized I could build a **predictive model** using this data (and supplemental data from The Movie Database) to forecast what I would rate a movie. One motivator is the desire to avoid being caught saying, *"I can't believe you haven't seen that one"* in conversation. By predicting ratings, the model can suggest high-rated movies I haven’t seen yet that I’m likely to enjoy.

---

## Dataset

**Letterboxd:** Exported data of all movies I watched and rated, including titles and my ratings.  

<img width="731" height="394" alt="Letterboxd Data" src="https://github.com/user-attachments/assets/52b73313-8cab-4b01-875a-dc086f656f36" />

**The Movie Database (TMDB):** Two datasets exported using their API:  
1. Attributes of movies I already rated (for model training).  
2. Top 500 rated movies (excluding movies I’ve seen) to feed into the model for recommendations.  

---

## Results

A **Neural Network model** predicted 15 movies I should watch next, with estimated ratings (0–5):

| Rank | Movie | Year | Predicted Rating |
|------|-------|------|-----------------|
| 1 | Frankenstein | 2025 | 4.92 |
| 2 | Raging Bull | 1980 | 4.10 |
| 3 | Gladiator | 2000 | 4.09 |
| 4 | Kill Bill: The Whole Bloody Affair | 2011 | 4.05 |
| 5 | The Prestige | 2006 | 4.04 |
| 6 | Casino | 1995 | 4.01 |
| 7 | Transformers One | 2024 | 3.96 |
| 8 | The Wild Robot | 2024 | 3.95 |
| 9 | Just Mercy | 2019 | 3.92 |
| 10 | Memories of Murder | 2003 | 3.88 |
| 11 | Blade Runner | 1982 | 3.88 |
| 12 | Alien | 1979 | 3.87 |
| 13 | Kill Bill: Vol. 2 | 2004 | 3.85 |
| 14 | The Sting | 1973 | 3.78 |
| 15 | No Country for Old Men | 2007 | 3.77 |

> **Note:** #4 is the combination of parts 1 and 2 of *Kill Bill*. I have already seen part 1, and part 2 is #13 on the recommendation list.

---

## Methods

**Neural Network:**  
Using a 20% test set, the network with 2 hidden layers achieved:  
- **RMSE:** 0.86  
- **MAE:** 0.68  

<img width="676" height="539" alt="Neural Network Performance" src="https://github.com/user-attachments/assets/d9a79c0d-d58f-4aab-816d-ca9c0e689be7" />

**Additional Validation Methods:**  
- **K-Fold Cross Validation:** 5 folds × 10 repeats = 50 total; **Mean MAE:** 0.25, **Std MAE:** 0.018  
- **Bootstrapping:** 50 bootstraps; **Mean MAE:** 0.25, **Std MAE:** 0.017  

<img width="560" height="446" alt="K-Fold & Bootstrapping" src="https://github.com/user-attachments/assets/ce5c7cef-0e6b-4ace-a0ca-21512da2928f" />  
<img width="477" height="373" alt="K-Fold & Bootstrapping 2" src="https://github.com/user-attachments/assets/beb207c4-bb65-44cb-a2ca-3a1509add4a1" />

---

## Additional Charts

**Time Trend of Ratings:**  
Shows spikes when I logged older movies all at once, likely leading to nostalgia-driven higher ratings.  

<img width="707" height="407" alt="Time Trend" src="https://github.com/user-attachments/assets/ce0046ee-0f2a-4a99-8953-6481c41a51e3" />

**Correlation with TMDB Ratings:**  
Scaled correlation between my ratings and TMDB ratings: 0.47  

<img width="707" height="473" alt="Correlation" src="https://github.com/user-attachments/assets/f8a9be7c-0142-4f98-9315-02ba0dd03909" />

**Genre Analysis:**  
Despite frequently watching horror movies, my ratings indicate I do not particularly enjoy them.  

<img width="760" height="459" alt="Genre Analysis" src="https://github.com/user-attachments/assets/585641ec-e5cc-445e-a480-779281f672b2" />

> **Note:** More exploratory analyses are included in the full code file.
