# Brainrot Data Analysis

## Project Overview

This project explores short-form video consumption patterns and their relationships with sleep, attention, and cognitive-performance indicators. Using Python, the notebook combines exploratory data analysis (EDA), data preprocessing, statistical correlation analysis, and visualizations to investigate patterns across short-form video platforms.

> **Note:** The analysis explores associations in the dataset. It does not establish that short-form video usage causes cognitive decline.

## Objectives

- Explore the structure, data types, and distributions of the dataset.
- Compare daily short-form video usage across platforms.
- Prepare data by handling duplicates, missing values, and an age outlier.
- Examine relationships among screen time, bedtime scrolling, sleep, and sustained attention.
- Visualize numerical correlations and prepare features for further analysis.

## Dataset

**File:** `short_form_brain_rot_cognitive_decay.csv`

The notebook examines fields including:

| Category | Example columns |
| --- | --- |
| Demographics and platform | `age`, `gender`, `primary_platform` |
| Video consumption | `daily_short_form_hours`, `avg_clip_duration_sec`, `swipes_per_minute`, `scroll_sessions_day` |
| Sleep and screen use | `bedtime_scroll_min`, `total_sleep_hours`, `total_screen_time_hours` |
| Cognitive indicators | `sustained_attention_span_sec`, `working_memory_score`, `task_switch_latency_sec`, `brain_fog_score`, `attention_retention_pct` |
| Other indicators | `multitasking_score`, `dopamine_burnout_index` |

## Workflow

### 1. Data exploration

Inspect the dataset's shape, first and last records, data types, and summary information using Pandas.

### 2. Data cleaning and preprocessing

The notebook creates a working copy of the dataset and deliberately introduces some missing values for preprocessing practice. It then:

- Removes duplicate rows.
- Fills missing numeric values with each column's median.
- Fills missing categorical values with each column's mode.
- Checks for remaining missing values and duplicates.
- Uses box plots to inspect age outliers and replaces ages above 100 with a median calculated from ages of 100 or below.

### 3. Exploratory analysis and visualization

The notebook includes:

- **Bar chart:** Average daily short-form video hours by primary platform.
- **Histogram:** Distribution of daily short-form video hours.
- **Box plot:** Video usage distributions across platforms.
- **Scatter plot with trendline:** Daily short-form hours versus total sleep hours.
- **Scatter plot with trendline:** Bedtime scrolling versus sustained attention span, colored by dopamine burnout index.
- **Correlation heatmap:** Relationships among numerical features.
- **Correlation ranking:** Strongest feature-pair correlations.

Platform-specific colors are used for TikTok, Instagram Reels, YouTube Shorts, and Snapchat Spotlight.

### 4. Feature preparation

- Applies one-hot encoding with `pandas.get_dummies()`.
- Applies min-max normalization to numeric columns using `MinMaxScaler` from scikit-learn.
- Includes a feature-selection visualization section intended to display mutual-information scores; this section requires a defined `feature_scores` DataFrame before it can run.

## Technologies

- **Python**
- **Pandas** and **NumPy** — data manipulation and numerical analysis
- **Plotly Express** — interactive visualizations
- **Matplotlib** and **Seaborn** — statistical plots
- **scikit-learn** — min-max feature scaling
- **Jupyter Notebook / Google Colab** — notebook environment

## Repository Structure

```text
Brainrot-Data-Analysis/
├── brainrot_(67).ipynb
├── short_form_brain_rot_cognitive_decay.csv
├── README.md
└── .gitignore
```

## How to Run

1. Clone the repository or download its files.
2. Open `brainrot_(67).ipynb` in Jupyter Notebook or Google Colab.
3. Install the required packages:

   ```bash
   pip install numpy pandas matplotlib seaborn plotly scikit-learn statsmodels
   ```

4. Ensure the CSV dataset is available in the notebook's runtime. In Google Colab, upload the CSV to `/content/` to match the current notebook path:

   ```python
   data = pd.read_csv('/content/short_form_brain_rot_cognitive_decay.csv')
   ```

   For local Jupyter use, replace the path with:

   ```python
   data = pd.read_csv('short_form_brain_rot_cognitive_decay.csv')
   ```

5. Run the notebook cells in order. **Note:** The mutual-information feature-selection chart currently references `feature_scores`, which is not defined in the supplied notebook; define or revise that section before running all cells uninterrupted.

## Scope and Limitations

This is an exploratory analysis and preprocessing project, **not a trained predictive machine-learning model**. Correlations describe relationships in the data, not causation. Some charts use the original dataset (`data`), while other analyses use the processed copy (`data_dirty`); keep this distinction in mind when interpreting results.

## Author

**Ahmed Mostafa**  
GitHub: [@a7mad-69](https://github.com/a7mad-69)
