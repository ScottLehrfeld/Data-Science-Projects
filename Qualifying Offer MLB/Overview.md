**Qualifying Offer Analysis Inspired by 2025 Trent Grisham**

Scott Lehrfeld

To begin, I would like to acknoledge I have no problem with Trent Grisham. I would say indifferent is the strongest word I would use. My friend however does not feel this way. As a Yankees fan he was dissapointed Grisham was offered the qualifying offer (QO), and irate that he accepted it. 

His passion peaked my interest, as I was not sure if there was a fair way to judge a team for their judgement on when to offer this special deal. It has only existed since 2012, and the book is not out on how to proceed perfectly for both player and front office. In fact, 2025 marked the most ever acceptances in one season. My question is, did the Yankees make a mistake, or can my friend feel better about this front office decision?

As I continued to look into the history of the qualifying offer, which has only existed since 2012, the scope of my interest expanded. The topics I covered in this project included:  
1. History of qualifying offer summary
2. Summary of year-to-year performance changed based on QO decision (including charts)
3. Accept or Reject QO prediction model (Is Grisham expected to accept, and why)
4. QO offered player performance by team
5. Team player retention based on QO
6. Grisham stat comparison to other hitters who accepted the QO

The data sources I used in the reasearch were:

- [Qualifying Offer History](https://www.mlb.com/news/history-of-mlb-qualifying-offer-decisions-c300602464)
- [Player Statistics](https://baseballsavant.mlb.com/)
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
<img width="984" height="584" alt="image" src="https://github.com/user-attachments/assets/b2c80dd8-7c77-4f82-b8ec-0f8074bf51e4" />


2. **Summary of year-to-year performance changed based on QO decision (including charts)**
<img width="1383" height="1184" alt="image" src="https://github.com/user-attachments/assets/400347cc-17c3-429d-a4d5-6cd40fe0fedf" />


3. **Accept or Reject QO prediction model (Is Grisham expected to accept, and why)**


4. **QO offered player performance by team**


5. **Team player retention based on QO**
<img width="774" height="858" alt="image" src="https://github.com/user-attachments/assets/cb286e55-d7b1-4b55-9774-e8df4ef7c029" />


6. **Grisham stat comparison to other hitters who accepted the QO**
<img width="1484" height="784" alt="image" src="https://github.com/user-attachments/assets/c74f22c2-00c9-45f2-a221-5ba6d57a8449" />



