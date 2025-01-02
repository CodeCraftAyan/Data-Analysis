# IPL Matches Analysis (2008-2024)

This project explores and analyzes the IPL Matches Dataset (2008-2024) to uncover key insights, trends, and statistics about the Indian Premier League (IPL). The analysis is performed using Python and Jupyter Notebook.

<div align="center">
  <img src="https://github.com/user-attachments/assets/bd43160e-bf1f-493e-83cc-a5701e6c51f8" alt="IPL Analysis Image" width="400"/>
</div>

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
![Total_Matches_Played](https://github.com/user-attachments/assets/a78f6dfe-b613-453a-8985-831cabd721f6)

### Most Match-Winning Teams (After Data Cleaning)
![No_of_matches_Win_by_each_team_after](https://github.com/user-attachments/assets/4eec0235-f5d6-4fbd-9276-3a5c3d97e475)

### Match Type and Team Wins (Heatmap)
![Win_by_match_type_and_team](https://github.com/user-attachments/assets/9a6a3968-446c-4aec-9a2d-b9dfe0ded10b)

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
