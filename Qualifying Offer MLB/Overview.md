**Qualifying Offer Analysis Inspired by 2025 Trent Grisham**

Scott Lehrfeld

To begin, I would like to acknoledge I have no problem with Trent Grisham. I would say indifferent is the strongest word I would use. My friend however does not feel this way. As a Yankees fan he was dissapointed Grisham was offered the qualifying offer (QO), and irate that he accepted it. 

His passion peaked my interest, as I was not sure if there was a fair way to judge a team for their judgement on when to offer this special deal. It has only existed since 2012, and the book is not out on how to proceed perfectly for both player and front office. In fact, 2025 marked the most ever acceptances in one season. My question is, did the Yankees make a mistake, or can my friend feel better about this front office decision?

As I continued to look into the history of the qualifying offer, which has only existed since 2012, the scope of my interest expanded. The topics I covered in this project included:  
1. History of qualifying offer summary
2. Summary of year-to-year performance changed based on QO decision (including charts)
3. Accept or Reject QO prediction model (Is Grisham expected to accept, and why)
4. Grisham stat comparison to other hitters who accepted the QO
5. QO offered player performance by team
6. Team player retention based on QO

## Results

Players who accepted the Qualifying Offer experienced the largest average declines in offensive production, particularly in home runs (−5.75), OPS (−0.120), and wOBA (−0.044), compared to players who rejected the offer. A random forest model predicted that Trent Grisham would reject the QO, driven primarily by his strong underlying indicators—most notably a top-quartile xwOBA (83rd percentile) relative to historical QO acceptors. His decision to accept the offer therefore represents an atypical case that may provide the Yankees with surplus value compared to the historical performance of QO acceptances. 

Translation, my friend can feel better about the Yankees' front office decision in this case, and have some hope for this one year deal!


## Data Sources

- [Qualifying Offer History](https://www.mlb.com/news/history-of-mlb-qualifying-offer-decisions-c300602464)
- [Player Statistics](https://baseballsavant.mlb.com/) 2015-2024
- [Player IDs](https://www.smartfantasybaseball.com/tools/)

<details>
<summary>Click for Data Dictionary </summary>

# Data Dictionary 

Qualifying Offer Dataset
| Column       | Description                                                                        |
| ------------ | ---------------------------------------------------------------------------------- |
| `Player`     | Player name                                                                        |
| `Year`       | Season in which the Qualifying Offer was made                                      |
| `Team1`      | Team that extended the Qualifying Offer                                            |
| `Team2`      | Team the player signed with if they rejected and left (NaN if stayed)              |
| `Decision`   | Player decision on the QO (`Accepted`, `Rejected and Stayed`, `Rejected and Left`) |
| `Offer`      | Dollar value of the Qualifying Offer                                               |
| `Name_Clean` | Cleaned player name used for merging datasets                                      |
| `MLBID`      | Unique MLB player identifier                                                       |


Player Performance Statistics

| Column             | Description                            |
| ------------------ | -------------------------------------- |
| `home_run`         | Home runs hit during the season        |
| `k_percent`        | Strikeout percentage                   |
| `bb_percent`       | Walk percentage                        |
| `on_base_plus_slg` | On-base plus slugging percentage (OPS) |
| `woba`             | Weighted On-Base Average               |
| `xwoba`            | Expected Weighted On-Base Average      |
| `home_run_next_year`         | Home runs in the season following the QO     |
| `k_percent_next_year`        | Strikeout percentage in the following season |
| `bb_percent_next_year`       | Walk percentage in the following season      |
| `on_base_plus_slg_next_year` | OPS in the following season                  |
| `woba_next_year`             | wOBA in the following season                 |
| `xwoba_next_year`            | xwOBA in the following season                |


Derived Features
| Column                   | Description                                     |
| ------------------------ | ----------------------------------------------- |
| `delta_home_run`         | Change in home runs from QO year to next season |
| `delta_k_percent`        | Change in strikeout rate                        |
| `delta_bb_percent`       | Change in walk rate                             |
| `delta_on_base_plus_slg` | Change in OPS                                   |
| `delta_woba`             | Change in wOBA                                  |
| `delta_xwoba`            | Change in xwOBA                                 |


Machine Learning Features
| Column            | Description                                             |
| ----------------- | ------------------------------------------------------- |
| `Offer_numeric`   | Numeric version of QO value used for modeling           |
| `Decision_binary` | Binary target variable (`1 = Accepted`, `0 = Rejected`) |

</details>

1. **History of qualifying offer summary**

The history of the qualifying offer starts in 2012, but i started my research with 2015 where I could get Statcast data. As it can be seen, the acceptance rate is low, as teams almost always offer the deal to players who will make much more as free agents, anticipating a rejection and compensatory draft pick in return (did the Yankees think this would happen with Grisham?).
<img width="984" height="584" alt="image" src="https://github.com/user-attachments/assets/b2c80dd8-7c77-4f82-b8ec-0f8074bf51e4" />


3. **Summary of year-to-year performance changed based on QO decision (including charts)**

  
### Performance Change After QO by Decision
| Decision | Δ HR (Mean) | Δ K% (Mean) | Δ BB% (Mean) | Δ OPS (Mean) | Δ wOBA (Mean) | Δ xwOBA (Mean) | Count |
|--------|------------|------------|-------------|-------------|--------------|---------------|-------|
| Accepted | -5.75 | +1.78 | +0.63 | -0.120 | -0.044 | -0.027 | 12 |
| Rejected – Left | -2.37 | +1.76 | -0.43 | -0.064 | -0.023 | -0.020 | 75 |
| Rejected – Stayed | -4.58 | +1.06 | +0.18 | -0.064 | -0.026 | -0.014 | 24 |
> **Insight:** Players who accepted the Qualifying Offer experienced the largest average declines in offensive performance, particularly in home runs and OPS. This suggests that acceptance may be associated with lower expected market value or declining performance at the time of the offer.



<img width="1383" height="1184" alt="image" src="https://github.com/user-attachments/assets/400347cc-17c3-429d-a4d5-6cd40fe0fedf" />


4. **Accept or Reject QO prediction model (Is Grisham expected to accept, and why)**

I used a random forest classifier as a model to predict acceptance or rejection. The model predicted that he would reject the offer (only 4% likely to accept).

### Model Performance (Random Forest)

| Class | Precision | Recall | F1-score | Support |
|------|-----------|--------|----------|---------|
| Rejected (0) | 0.95 | 0.95 | 0.95 | 22 |
| Accepted (1) | 0.00 | 0.00 | 0.00 | 1 |
| **Accuracy** |  |  | **0.91** | 23 |

> **Note:** The model performs well overall but struggles to identify QO acceptances due to class imbalance, as relatively few players accept the offer. This limitation is expected given the small sample size of accepted cases.

4. **Grisham stat comparison to other hitters who accepted the QO**

In terms of performance in the season previous to accepting the qualifying offer Grisham did show that he was among the top performers in some key areas among hitters.
- 67th percentile in wOBA
- 83rd percentile in xwOBA
- 33rd percentile in OPS
- 50th percentile in Strikeout rate

The key indicator here is in the xwOBA, which is a predictive statistic that uses Statcast measurements. The fact his percentile is much higher than his actual wOBA, shows that he was actually expected to perform better, and may even improve after accepting the qualifying offer. This shows me that the model selected Grisham to reject the offer due to his likelihood of vbeing able to make more money in a contract as a free agent. If anything, the Yankees are getting Griasham at a lower price than expected for a player put in this scenario.

<img width="1484" height="784" alt="image" src="https://github.com/user-attachments/assets/c74f22c2-00c9-45f2-a221-5ba6d57a8449" />


5. **Team player retention based on QO**
<img width="774" height="858" alt="image" src="https://github.com/user-attachments/assets/cb286e55-d7b1-4b55-9774-e8df4ef7c029" />


6. **QO offered player performance by team**
Due to the high rejection rate in general, it is hard to blame any team for having a low retention rate with the QO. Interestingly, 50% by the Twins and White Sox is the highest, with many teams never having an offer accepted (Grisham was the Yankees first!). 
### Team-Level Offensive Change After Qualifying Offers

*Average change in performance for players who accepted the Qualifying Offer, grouped by team.*

| Team | Δ wOBA (Mean) | Δ OPS (Mean) | QO Count |
|------|---------------|--------------|----------|
| Angels | -0.068 | -0.195 | 9 |
| Reds | -0.057 | -0.150 | 3 |
| Twins | -0.057 | -0.151 | 2 |
| Yankees | -0.056 | -0.143 | 4 |
| Giants | -0.048 | -0.134 | 7 |
| Dodgers | -0.045 | -0.111 | 11 |
| Mariners | -0.041 | -0.103 | 1 |
| Rays | -0.041 | -0.105 | 1 |
| Orioles | -0.040 | -0.106 | 6 |
| Rangers | -0.035 | -0.098 | 3 |
| Rockies | -0.032 | -0.069 | 2 |
| Royals | -0.030 | -0.083 | 4 |
| Diamondbacks | -0.027 | -0.073 | 2 |
| Phillies | -0.022 | -0.055 | 3 |
| Blue Jays | -0.022 | -0.052 | 6 |
| Brewers | -0.021 | -0.054 | 1 |
| Guardians | -0.017 | -0.052 | 1 |
| Red Sox | -0.017 | -0.048 | 5 |
| Astros | -0.015 | -0.040 | 7 |
| Nationals | -0.006 | -0.025 | 4 |
| Cubs | -0.006 | -0.008 | 6 |
| Braves | -0.003 | -0.018 | 4 |
| Mets | +0.004 | +0.012 | 12 |
| Padres | +0.007 | +0.012 | 4 |
| Cardinals | +0.009 | +0.024 | 4 |
| White Sox | +0.047 | +0.105 | 2 |
> **Insight:** Most teams see a decline in offensive production from players who accept the Qualifying Offer, particularly in wOBA and OPS. However, a small number of teams (e.g., Mets, Padres, Cardinals, White Sox) show neutral or positive average changes, suggesting that team context or player selection may influence post-QO outcomes.


