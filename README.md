
Student: Haotian Zhu

Instructor: Sam Lau

Date:11/17/2023

---

### Introduction
As a silver top player in League of Legends, I always wonder whether I should be more aggressive so that I can win more games. However, it's quite impossible to get all the data of rank games around the world. With that question, we will explore the dataset of records of all League of Legends **Professional** games in 2018 from oracleselixir.com instead.

In the first section, I will clean and explore the data, which involves in Univariateanalysis, Bivariate analysis and conditional distribution. 

Secondly, since most of the real world data contain missingness, we will analyze the missingness(specifically, finding **NMAR**) of some columns if there is any by performing a permutation test conditionally on "suspect" columns.

The final step, we will reach back to our "aggressiveness" question,then perform hypothesis test to make a summary to the question.


This dataframe has 80904 rows and 123 columns, each 12 rows is a group, 10 of the rows contain information about each of the 10 players in a single game. The rest 2 
rows contains information about the two teams in that game. Only some of the columns
relates to our question, which are:
- `result`: The result of that game, '0' means defeat, '1' means victory. 
- `kills`: Number of kills of a player in a game.
- `deaths`: Number of deaths of a player in a game.
- `assists`: Number of assists of a player in a game.
- `cspm`: Creep score per minute of a player in a game.
- `dpm`: Damage per minute of a player in a game.
- `teamname`(for missingness permutation test): The team's name of a player.



---

## Cleaning and EDA

### Data Cleaning
We only need columns that relates to "**aggresiveness**" , and are just interested in an overall performance of a player, which means we dont need to know who the 
opponents are. Also we need to create new columns to numerize "**aggressiveness**" and do some normalization to calculate columns with different means and standard deviations.
The steps are:
1. Select only the rows that represent top players.
2. Select only the columns we need: `result`, `kills`, `deaths`, `assists`, `cspm`,
`dpm`, `teamname`
3. Create a new column which is a indicator of participation of a player in team fights called `kda`. Calculated by `kills` + `deaths` + `assists`.
4. Change `result`'s data type to boolean.
5. Use mean normalization on cspm, dpm and kda to create new columns `cspm_normalized`, `dmp_normalized` and `kda_normalized`. Then drop `kills`, `deaths` and `assists`.
6. Make a new column for our statistic "agressiveness", using `dpm_normalized` - `cspm_normalized` + `kda_nomalized`


***Note1***: `kda` is **NOT** the traditional kda calculated by (k+a) / d. In our dataframe, `kda` is calculated by (k+d+a) since deaths is a positive factor in terms of "**aggressiveness**".

***Note2***: In terms of "**agressiveness**", a higher value of cspm_normalized is totally opposite to "**pure agressiveness**",since  a high cspm and a dpm value cannot singely prove that this player is more agressive, maybe this player is
just better than the others.Thats why we need to  subtract dpm_normalized by cspm_normalized.

Total rows and columns of cleaned dataframe: (13484, 9)

Here is the cleaned dataframe with first five rows:



|   cspm |     dpm |   kda |   cspm_normalized |   dpm_normalized |   kda_normalized | result   | teamname        |   agressiveness |
|-------:|--------:|------:|------------------:|-----------------:|-----------------:|:---------|:----------------|----------------:|
| 6.8848 | nan     |    19 |        -1.24423   |     nan          |         2.0578   | False    | JD Gaming       |      nan        |
| 8.8483 | nan     |    19 |         0.343248  |     nan          |         2.0578   | True     | Invictus Gaming |      nan        |
| 9.7349 | 380.458 |    14 |         1.06006   |      -0.236077   |         0.985075 | True     | Invictus Gaming |       -0.31106  |
| 8.3373 | 417.253 |    10 |        -0.0698915 |      -0.00923238 |         0.126891 | False    | JD Gaming       |        0.18755  |
| 8.7887 | 469.606 |     5 |         0.295062  |       0.313524   |        -0.945838 | False    | Bilibili Gaming |       -0.927375 |







---

### Assessment of Missingness

Here's what a Markdown table looks like. Note that the code for this table was generated _automatically_ from a DataFrame, using

<iframe src="assets/fig0.html" width=800 height=600 frameBorder=0></iframe>

---

## Hypothesis Testing


---