<h1 align="center">Hi 👋, We're Group 6</h1>

<h3 align="left">Connect with me:</h3>
<p align="left">
<a href="https://linkedin.com/in/anthony-odhiambo-47167a15b/" target="blank"><img align="center" src="https://raw.githubusercontent.com/rahuldkjain/github-profile-readme-generator/master/src/images/icons/Social/linked-in-alt.svg" alt="anthony-odhiambo-47167a15b/" height="30" width="40" /></a>
</p>

Github Repository: [Click to Open the Project Github Repository](https://github.com/odhinto/dsc-phase-1-project-v3)

Tableau Dashboard: [Click to Open the Tableau Dashboard](https://public.tableau.com/views/Phase1_EDA/Dashboard2?:language=en-US&publish=yes&:sid=&:redirect=auth&:display_count=n&:origin=viz_share_link)


# **Problem Definition**

A recent profitable trend across most big companies is creation of original video content. Our company's expansion and diversification plans include getting in on this fun by creating a new movie studio. 
An analysis of box office performance is critical to identify a profitable formula for operating a profitable studio.

## Business Understanding

The primary objective of this exercise is to generate an accurate model for predicting box office success as a blueprint for running our proposed new movie studio

*   The highest rated movies with respect to attributes such as Genre, Region, Writers, Directors, Actors etc.
*   The most watched/voted movies with respect to attributes such as Genre, Region, Writers, Directors, Actors etc.
*   The highest grossing movies with respect to attributes such as Genre, Region, Writers, Directors, Actors etc.

The insights from this analysis will determine the kind of movies our studio focuses on and the people we approach to partner with us to ensure our studio is successful and profitable.

# **Data Preprocessing**

This section prepare the provided movie data for analysis. We intend to do the following:

*   Dataset Overview - Load and understand the data
*   Handling Missing Values using derived domain knowledge and imputation
*   Data Cleaning e.g. standardizing categorical values, deriving useful date data, removing duplicates etc

## **Dataset Overview**

It is imperative for us to understand the movie database first i.e.:

*   The data structure e.g. available tables, their columns, data types and presence of missing values
*   Establish the relevance of the data to our study
*   Identify useful columns to focus on

Data Understanding will prescribe subsequent cleaning steps to be done in the **Data Cleaning** subsection

### Python Libraries Initialization
First, we initialize common libraries we project to utilize in this exercise:

*   pandas to create and manipulate dataframes
*   seaborn and matplotlib to facilitate any requisite visualizations within the notebook
*   numpy for mathematical calculations
*   sqlite3 to navigate the movie database
*   etc

### Data Loading
We then load the dataset into python as a dataframe and embark on a data understanding exercise.

### Data Understanding

The movie database contains the following tables with shown columns

*   **principals**: insert description and data summary
*   **persons**: insert description and data summary
*   **known_for**: insert description and data summary
*   **directors**: insert description and data summary
*   **writers**: insert description and data summary
*   **movie_basics**: insert description and data summary
*   **dmovie_ratings**: insert description and data summary
*   **movie_akas**: insert description and data summary

<div align="center">
    <img src="pictures/movie_data_erd.jpeg" alt="Database Schema" width="800">
    <p><em>Dirty Makers - Needs Cleaning with Fuzzy Logic</em></p>
</div>


## **Data Cleaning**

To ensure reliable analysis, the following data cleaning steps were implemented:

1. **Handling Missing Values:**
   - Replaced missing values in categorical fields (e.g., genre, director) with "Unknown" to retain as much data as possible.
   - Imputed missing numerical values with the mean or median based on the data distribution.

2. **Standardization:**
   - Normalized categorical data to ensure consistent capitalization and formatting.
   - Removed duplicate rows to avoid skewed insights.

3. **Date Formatting:**
   - Converted date fields to a uniform datetime format for proper chronological analysis.

4. **Outlier Detection and Removal:**
   - Identified and addressed outliers in box office revenue and ratings to enhance prediction accuracy.

5. **Feature Engineering:**
   - Derived new columns (e.g., "profit margin") to facilitate deeper analysis.
     
# **Exploratory Data Analysis**

Using the Tableau dashboard, the following insights were derived:

1. **Highest Rated Genres and Regions:**
   - **Drama** and **Action** movies dominate in terms of ratings across all regions.
   - North America contributes the highest revenue, making it a key focus for studio operations.

2. **Directors and Writers:**
   - Collaborations involving well-established directors and writers correlate strongly with high box office revenue.
   - Analyzing director-writer pairings further refined this insight.

3. **Revenue Trends:**
   - Movies released during holiday seasons (summer and Christmas) consistently outperform those released in off-peak periods.
   - High-budget films tend to yield higher returns, but a significant portion of mid-budget films also shows profitability.

4. **Casting Insights:**
   - A-list actors consistently attract larger audiences, but the story quality (as reflected by user reviews) remains a critical factor.

# **Recommendations and Conclusions**

1. **Genre Focus:**
   - Prioritize creating **Drama** and **Action** films targeting North American audiences, as they show the strongest performance metrics.

2. **Seasonal Releases:**
   - Schedule movie releases during high-demand periods (e.g., summer and holidays) to capitalize on peak audience interest.

3. **Director and Writer Partnerships:**
   - Invest in partnerships with proven directors and writers to enhance the likelihood of success.

4. **Casting Strategy:**
   - Include at least one A-list actor in high-budget projects while ensuring strong scripts and storytelling to retain audience satisfaction.

5. **Budget Allocation:**
   - Focus on mid- to high-budget films with a clear emphasis on maximizing profit margins.

6. **Long-Term Strategy:**
   - Continuously analyze audience preferences and emerging trends to adapt to shifting market demands.

These recommendations provide a roadmap for achieving consistent profitability and success in the competitive movie industry.
