# DMProject-2021

**Data Mining Project:** *Tennis Matches*

A **project** consists in data analysis based on the use of data mining tools. The project has to be performed by a team of 2/3 students. It has to be performed by using Python. The guidelines require to address specific tasks and results must be reported in a unique paper. The total length of this paper must be **max 25 pages** of text including figures. The students must deliver both: paper and  well commented Python notebooks.

**DATASET DESCRIPTION**

The dataset to be analyzed is composed of information about some tennis matches. Data are organized in .csv file:

- tennis\_matches.csv where each row represents a match
- male\_players.csv
- female\_players.csv

The dataset contains different features, with the following semantic meaning:

- **Tourney\_id**: a unique identifier for each tournament, such as 2020-888. The exact formats are borrowed from several different sources, so while the first four characters are always the year, the rest of the ID doesn't follow a predictable structure.
- **Tourney\_name**: the name of the tourney
- **Surface**: kind of surface for the match
- **Draw\_size**: number of players in the draw, often rounded up to the nearest power of
  - (For instance, a tournament with 28 players may be shown as 32.)
- **Tourney\_level**: they are split for men and women.
- **For men**: 'G' = Grand Slams, 'M' = Masters 1000s, 'A' = other tour-level events, 'C' = Challengers, 'S' = Satellites/ITFs, 'F' = Tour finals and other season-ending events, and 'D' = Davis Cup. F
- **For women**, there are several additional tourney\_level codes, including 'P' = Premier, 'PM' = Premier Mandatory, and 'I' = International. The various levels of ITFs are given by the prize money (in thousands), such as '15' = ITF $15,000. Other codes, such as 'T1' for Tier I (and so on) are used for older WTA tournament designations. 'D' is used for the Federation/Fed/Billie Jean King Cup, and also for the Wightman Cup and Bonne Bell Cup.
- There is also some competition which can be for both men and women: 'E' = exhibition (events not sanctioned by the tour, though the definitions can be ambiguous), 'J' = juniors, and 'T' = team tennis, which does yet appear anywhere in the dataset but will at some point.
- **Tourney\_date**: eight digits, YYYYMMDD, usually the Monday of the tournament week.
- **Match\_num**: a match-specific identifier. Often starting from 1, sometimes counting down from 300, and sometimes arbitrary.
- **Winner\_id**: the player\_id used in this repo for the winner of the match.
- **Winner\_entry**: 'WC' = wild card, 'Q' = qualifier, 'LL' = lucky loser, 'PR' = protected ranking, 'ITF' = ITF entry, and there are a few others that are occasionally used.
- **Winner\_hand**:R = right, L = left, U = unknown. For ambidextrous players, this is their serving hand.
- **Winner\_ht**: height in centimetres, where available
- **Winner\_ioc**: three-character country code
- **Winner\_age**: the age of the player, in years, depending on the date of the tournament
- **Best\_of**: '3' or '5', indicating the number of set for this match
- **Minutes**: match length, where available
- **W\_ace**: winner's number of aces
- **W\_df**: winner's number of doubles faults
- **W\_svpt**: winner's number of serve points
- **W\_1stln**: winner’s number of first serves made
- **W\_1stWon**: winner’s number of first-serve points won
- **W\_2stwon**: winner’s number of second-serve points won
- **W\_SvGms**: winner’s number of serve games
- **W\_bdSaved**: winner's number of breakpoints saved
- **W\_bdFaced**: winner's number of breakpoints faced
- **Winner\_rank**: winner's ATP or WTA rank, as of the tourney\_date, or the most recent ranking date before the tourney\_date
- **Winner\_rank\_points**: number of ranking points, where available.

We did not report the meaning of losers attribute because they are the same as the winners, but the feature names start with ‘loser’.

**Task 1 Data Understanding and Preparation (30 points):**

**Task 1.1: Data Understanding:** Explore the dataset with the analytical tools studied and write a concise “data understanding” report assessing data quality, the distribution of the variables and the pairwise correlations.

**Task 1.2: Data Preparation:** Improve the quality of your data and prepare it by extracting *new features* interesting for describing the player profile and his behavior derivable from matches. These indicators have to be extracted for each player. Examples of Indicators to be computed are:

- how many times did the player win during a given period
- how many matches the player played in a given period
- a ratio between the previous indicators
- percentage of aces related to the number of first serves made
- number of breakpoints numbers w.r.t. all games
- ….

Note that these examples are not mandatory. You can derive indicators that you prefer and that you consider interesting for describing the players.

It is MANDATORY that each team defines **indicators** and their description and when it is necessary also their mathematical formulation. The profile will be useful for the clustering analysis (i.e., the second project’s task).

Once the set of indicators is computed, the team has to explore the new features for a statistical analysis (distributions, outliers, visualizations, correlations).

**Subtasks of DU**

- Data semantics for each feature that is not described above and the new one defined by the team
- Distribution of the variables and statistics
- Assessing data quality (missing values, outliers, duplicated records, errors)
- Variables transformations
- Pairwise correlations and eventual elimination of redundant variables

**Task 2: Clustering analysis (30 POINTS - 32 with optional subtask)**

Based on the player’s profiles explore the dataset using various clustering techniques. Carefully describe your decisions for each algorithm and which are the advantages provided

by the different approaches.

**Subtasks**

- Clustering Analysis by K-means:
1. Identification of the best value of k
1. Characterization of the obtained clusters by using both analysis of the k centroids and comparison of the distribution of variables within the clusters and that in the whole dataset
1. Evaluation of the clustering results
- Analysis by density-based clustering**:**
1. Study of the clustering parameters
1. Characterization and interpretation of the obtained clusters
- Analysis by hierarchical clustering
1. Compare different clustering results got by using different merging strategies
1. Show and discuss different dendrograms using the different merging strategies
- Final evaluation of the best clustering approach and comparison of the clustering obtained
- **Optional (2 points):** Explore the opportunity to use alternative clustering techniques in the library: https://github.com/annoviko/pyclustering/

**Delivery of the first draft of the report with Task 1.1, Task 1.2 and Task 2: 5 November**

**Task 3: Predictive Analysis (30 POINTS)**

Consider the problem of predicting for each player a label that defines if s(he) is a *high ranked player* or a *low ranked player* (binary task) by exploiting the feature related to the rank of the players.

The student need to:

1. Define a player profile that enables the above player classification. For this task, you can exploit the profile created for the clustering task, by adding or removing features, depending on the results previously obtained.
1. Compute the label for any customer. The extraction of the label can take advantage of several features related to the rank, such as loser\_rank, winner\_rank, loser\_rank\_points, winner\_rank\_points, etc. An example of simple label can be derived by:
- computing the average rank per player by exploiting loser\_rank, winner\_rank
- select a threshold for discretizing in two categorical labels the class.

Note that you can define in different ways the labels.

3. Perform the predictive analysis comparing the performance of different models, discussing the results and discussing the possible preprocessing that you applied to the data for managing possible problems identified that can make the prediction hard. Note that the evaluation should be performed on both training and test set.

**Note:** The final report delivered within the end of December can also improve the already delivered tasks.

**Task 4: Address one of the two tasks (32 POINTS - Optional)**

**Task 4.1: Time series analysis**

Consider the dataset of time series CityGlobalTemperature2000-2009.csv containing for 100 cities the temperature measurements (mean and standard deviation over a month). The goal of the task is to find groups of similar cities with respect to the temperature trends.

**Task 4.2: Explanation Analysis**

Consider the non-interpretable models used in Task 3 (eg. SVM, ensemble methods, etc) and study the global explanation with SHAP and the local explanation with LIME and SHAP. Use the evaluation metrics presented during the XAI Laboratory (for using LORE, you can download the library at the link: <https://github.com/rinziv/XAI_lib_HAI-net_Tutorial> and follow the instructions contained in the notebook presented  during the XAI Laboratory).
