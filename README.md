# Periodic Table → BigQuery
This project fetches periodic table element data from the ptable.com JSON API, cleans it into a pandas **DataFrame**, and uploads it into **Google BigQuery** for querying and analysis.

**Sample Output**

| **Atomic Number**  | **Symbol**  | **Atomic Weight**  |  **Series**   | **Melting Point (K)**
| -------------------|  ---------   ------------------- |  -----------  | ------------------ |
|         1          |     H       |         1.008      |   Nonmetal    |         14.01      |
|         2          |     He      |         4.002      |   Noble       |         ------     |
|         3          |     Li      |         6.94       |   Alkali      |         453.69     |
|         4          |     Be      |         9.012      |   Alkaline    |          1560      | 

 **Key Questions Answered**
1. What are the Top 5 PPR scores regardless of season for a given position (RB, QB, WR)?
Filtered the dataset by position.

****Sorted by PPR in descending order.

****Dropped duplicate players to avoid repeat appearances from dominant players like Patrick Mahomes.

****Extracted the top 5 unique performances for each position.

2. What are the Top 5 average PPR scores for players who’ve played at least 3 seasons?
Filtered players by position.

****Grouped by player name and filtered for those appearing 3 or more times in the dataset.

****Calculated average PPR and sorted in descending order.

****Reset the index for clean presentation.

**Tools Used**

Python 

Pandas 

JupyterLab

CSV dataset (2017–2023 Fantasy Football stats)

**Sample Code Snippet**
# Top 5 PPR for RBs (unique players)
df_rb = df[df["FantPos"] == "RB"].sort_values(by = "PPR", ascending = False).drop_duplicates("Player").head()
df_rb[["Player", "PPR", "Year"]]

Sample Output (RBs)
| Player              | PPR   | Year |
| ------------------- | ----- | ---- |
| Christian McCaffrey | 471.2 | 2019 |
| Saquon Barkley      | 385.8 | 2018 |
| Todd Gurley         | 383.3 | 2017 |
| Alvin Kamara        | 377.8 | 2020 |
| Jonathan Taylor     | 373.1 | 2021 |


**What You’ll Learn**

How to filter and sort real-world data with pandas.

Use of groupby(), filter(), and lambda functions for conditional aggregation.



DATA SOURCE:https://www.kaggle.com/datasets/gbolduc/fantasy-football-data-2017-2023
