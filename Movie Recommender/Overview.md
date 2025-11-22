**Overview**:

  I have been keeping track of all the movies I have watched and rated on the Letterboxd site. Currently I have logged over 700 movies and rated 688 of them. Being able to visualize with data the movies I watched was my first goal after learning I could export the data from the site.

  I then realized I could build a model using this data (and data I was able to attech from a movie database) to predict what I would rate a movie on Letterboxd. One of my main motivators in countinuing to watch new movies and log them is the idea that I want to see all any movie that would prevent someone saying "I can't believe you haven't seen that one" in a conversation. Yes, this and other movie references I did not understand occured on a regular basis. In an attempt to help me continue to check off movies from this list, I plan on using my model to tell me which highly rated movies I should see next based off of what it predicts I would rate it.

*Dataset*
- Letterboxd: I outputted all movies I have watched and rated on Letterboxd, which includes the title and my rating
- The Movie Database (TMDB): I outputted two different sets of data using an API for this database. The first dataset included relevant attributes of the movies I had rated on letterboxd, so I could use them to train my model. The second dataset included the top 500 rated movies on the site (which i removed movies I had seen from) to be used to put into the model and reccomend movies for me to watch next.

*Results*:

  A Neural Network Model predicted that I should watch the following 15 movies next, and provided the estimated ranking I would give on a scale of 0-5:

  1.   Frankenstein  (2025) -          4.92
  
  2.  Raging Bull  (1980) -          4.10
  
  3.   Gladiator  (2000) -          4.09
  
  4. Kill Bill: The Whole Bloody Affair  (2011)         - 4.05

  5.    The Prestige  (2006) -          4.04
    
  6. Casino  (1995) -          4.01
     
  7. Transformers One  (2024) -          3.96
     
  8. The Wild Robot  (2024) -          3.95
      
  9.  Just Mercy  (2019)          - 3.92
      
  10.  Memories of Murder  (2003) -          3.88

  11.   Blade Runner  (1982)          - 3.88

  12.   Alien  (1979) -          3.87
  
  13.    Kill Bill: Vol. 2  (2004) -         3.85
  
  14. The Sting  (1973) -          3.78
      
  15.   No Country for Old Men  (2007)          - 3.77

      *A note that #4 is the combo of parts 1 and 2 of a movie I have already seen part 1 of, and part 2 is the #13 reccomended)*

  
*Methods*

- Neural Network: Using a 20% test set of the data, my network with 2 hidden layers produced an RMSE of 0.86 and MAE of 0.68. In an attempt to se how accurate I could get the model I also attempted two more firther methods.
<img width="676" height="539" alt="image" src="https://github.com/user-attachments/assets/d9a79c0d-d58f-4aab-816d-ca9c0e689be7" />

-    K-Fold: I used 5 folds, 10 repeats (50 total) with this method which produced a Mean MAE of 0.25 and Standard Deviation of MAE at 0.018.
-   Bootstrapping: I used 50 bootstraps in this method which produced a Mean MAE of 0.25 and Standard Deviation of MAE at 0.017.
<img width="560" height="446" alt="image" src="https://github.com/user-attachments/assets/ce5c7cef-0e6b-4ace-a0ca-21512da2928f" />
<img width="477" height="373" alt="image" src="https://github.com/user-attachments/assets/beb207c4-bb65-44cb-a2ca-3a1509add4a1" />













