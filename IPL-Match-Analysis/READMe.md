# IPL Matches Analysis (2008-2024)

This project explores and analyzes the IPL Matches Dataset (2008-2024) to uncover key insights, trends, and statistics about the Indian Premier League (IPL). The analysis is performed using Python and Jupyter Notebook.

## Table of Contents
- [Dataset Overview](#dataset-overview)
- [Steps for Analysis](#steps-for-analysis)
- [Key Insights](#key-insights)
  - [Total Matches Played Per Season](#total-matches-played-per-season)
  - [Number of Matches Won by Each Team](#number-of-matches-won-by-each-team)
  - [Match Type vs. Winners Analysis](#match-type-vs-winners-analysis)
- [Visualization Examples](#visualization-examples)
- [Usage](#usage)

## Dataset Overview

The dataset contains information about IPL matches from 2008 to 2024. Key features include:
- Match details: `season`, `date`, `city`, `venue`
- Teams and results: `team1`, `team2`, `winner`, `result`, `result_margin`
- Additional details: `player_of_match`, `toss_winner`, `toss_decision`, `umpires`

### File Structure
- `matches.csv`: Contains match-level data.

## Steps for Analysis

1. **Warnings Filtering**
   - Suppress irrelevant warnings using `warnings.simplefilter()`.
   ```python
   import warnings
   warnings.simplefilter("ignore", FutureWarning)
   warnings.simplefilter("ignore", UserWarning)
   ```

2. **Load Dataset**
   - Use pandas to load and inspect the dataset.
   ```python
   import pandas as pd
   df = pd.read_csv('archive/matches.csv')
   df.head()
   ```

3. **Explore Dataset**
   - Inspect structure using `df.info()` and column names with `df.columns`.

4. **Data Cleaning**
   - Standardize team names for consistent analysis.
   ```python
   team_name_mapping = {
       'Delhi Daredevils': 'Delhi Capitals',
       'Rising Pune Supergiant': 'Rising Pune Supergiants',
       'Royal Challengers Bengaluru': 'Royal Challengers Bangalore',
       'Kings XI Punjab': 'Punjab Kings',
       'Gujarat Lions': 'Gujarat Titans'
   }
   df['team1'] = df['team1'].replace(team_name_mapping)
   df['team2'] = df['team2'].replace(team_name_mapping)
   df['winner'] = df['winner'].replace(team_name_mapping)
   ```

5. **Generate Insights**
   - Analyze matches played per season, team performance, and match type statistics.

6. **Visualizations**
   - Create insightful visualizations using Matplotlib and Seaborn.

## Key Insights

### Total Matches Played Per Season
- Calculate and visualize the total matches played in each season.
```python
match_count = df.groupby('season')['id'].count()
match_count.plot(kind='bar', figsize=(10, 5))
```

### Number of Matches Won by Each Team
#### Before Data Cleaning
- Analyze the performance of teams based on raw data.
#### After Data Cleaning
- Analyze the performance of teams with standardized franchise names.

### Match Type vs. Winners Analysis
- Explore the performance of teams across different match types (league, playoffs, finals).

## Visualization Examples

### Total Matches Played by Season
![Bar Chart](examples/matches_per_season.png)

### Most Match-Winning Teams (After Data Cleaning)
![Horizontal Bar Chart](examples/team_wins.png)

### Match Type and Team Wins (Heatmap)
![Heatmap](examples/match_type_analysis.png)

## Usage

1. Clone the repository:
   ```bash
   git clone https://github.com/CodeCraftAyan/Data-Analysis/IPL-Match-Analysis.git
   ```
2. Install required libraries:
   ```bash
   pip install pandas matplotlib seaborn
   ```
3. Open the Jupyter Notebook:
   ```bash
   jupyter notebook
   ```
4. Load and run the analysis notebook to explore insights.

## Contributing
Contributions are welcome! Feel free to open issues or submit pull requests to improve this analysis.

## License
This project is licensed under the MIT License. See the `LICENSE` file for more details.
