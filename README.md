
Student: Haotian Zhu

Instructor: Sam Lau

Date:11/17/2023

---

## Introduction
As a silver top player in League of Legends, I always wonder whether I should be more aggressive so that I can win more games. However, it's quite impossible to get all the data ofrank games around the world. With that question, we will explore the dataset of records of all League Of Legends professional games in 2018 from oracleselixir.com instead.

In the first section, I will clean and explore the data, which involves in Univariateanalysis, Bivariate analysis and conditional distribution. 

Secondly, since most of the real world data contain missingness, we will analyze the missingness(specifically, finding NMAR) of some columns if there is any by performing a permutation test conditionally on "suspect" columns

The final step, we will reach back to our "aggressiveness" question,then perform hypothesis test to make a summary to the question.


This dataframe has 80904 rows and 123 columns, each 12 rows is a group, 10 of the rows contain information about each of the 10 players in a single game. The rest 2 
rows contains information about the two teams in that game. Only some of the columns
relates to our question, which are:
- 'result': The result of that game, '0' means defeat, '1' means victory. 
- 'kills': Number of kills of a player in a game.
- 'deaths': Number of deaths of a player in a game.
- 'assists': Number of assists of a player in a game.
- 'cspm': Creep score per minute of a player in a game.
- 'dpm': Damage per minute of a player in a game.
- 'teamname'(for missingness permutation test): The team's name of a player.





***Note***: If you choose a repo name and title as uninspired as the ones here, I will be quite sad.

---

## Cleaning and EDA

<iframe src="assets/10-80-enrollment.html" width=800 height=600 frameBorder=0></iframe>

---

## Assessment of Missingness

Here's what a Markdown table looks like. Note that the code for this table was generated _automatically_ from a DataFrame, using

```py
print(counts[['Quarter', 'Count']].head().to_markdown(index=False))
```

| Quarter     |   Count |
|:------------|--------:|
| Fall 2020   |       3 |
| Winter 2021 |       2 |
| Spring 2021 |       6 |
| Summer 2021 |       4 |
| Fall 2021   |      55 |

---

## Hypothesis Testing


---