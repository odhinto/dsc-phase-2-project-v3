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

The movie database contains the following tables with shown columns:

*   **principals**:

#Explore principal table
principals_query = """
                      SELECT *
                      FROM principals"""
principals_df = pd.read_sql(principals_query, conn)
principals_df.to_csv('principals.csv')   #create a principals csv file to facilitate EDA on Tableau
principals_df.head()

![image](https://github.com/user-attachments/assets/ffd68c86-7102-4032-860d-85dd3800fab2)

The principals table details main people (using their person_id)that were involved with different movies (using the movie_id) and the capacities in which they were involved e.g. director, actor, producer etc. There could be a relationship between these people and the success of the movie in the box office.

*   **persons**:
  
#Explore persons table
persons_query = """
                      SELECT *
                      FROM persons"""
persons_df = pd.read_sql(persons_query, conn)
persons_df.to_csv('persons.csv')   #create a persons csv file to facilitate EDA on Tableau
persons_df.head()

![image](https://github.com/user-attachments/assets/66ac232a-c0fb-4b79-a8da-59e75efc6ced)

The persons table details the name, birth year, death year and primary professions of the various people using their person_id. There could be a relationship between the people involved in a movie and the success of the movie in the box office.
 
*   **known_for**:
  
#Explore known_for table
known_for_query = """
                      SELECT *
                      FROM known_for"""
known_for_df = pd.read_sql(known_for_query, conn)
known_for_df.to_csv('known_for.csv')   #create a known_for csv file to facilitate EDA on Tableau
known_for_df.head()

![image](https://github.com/user-attachments/assets/5bebda41-1b18-483f-ac93-8002a63c8226)

Known_for table details the various movies different people are known for by person_id and movie_id.

*   **directors**:

#Explore directors table
directors_query = """
                      SELECT *
                      FROM directors"""
directors_df = pd.read_sql(directors_query, conn)
directors_df.to_csv('directors.csv')   #create a directors csv file to facilitate EDA on Tableau
directors_df.head()

![image](https://github.com/user-attachments/assets/a30f8dde-24ef-44b3-89a5-9a6da837a707)

Directors table details the various movies and the people they are known for by movie_id and person_id. There could be a relationship between the directors of a movie and the success of the movie in the box office.

*   **writers**:

#Explore writers table
writers_query = """
                      SELECT *
                      FROM writers"""
writers_df = pd.read_sql(writers_query, conn)
writers_df.to_csv('writers.csv')   #create a writers csv file to facilitate EDA on Tableau
writers_df.head()

![image](https://github.com/user-attachments/assets/49ace174-b171-4182-83b1-e8b2e8244d5a)

Writers table details the various movies and their pewriters by movie_id and person_id. There could be a relationship between the writers of a movie and the success of the movie in the box office.

*   **movie_basics**:

#Explore movie_basics table
movie_query = """
                      SELECT *
                      FROM movie_basics"""
movie_df = pd.read_sql(movie_query, conn)
movie_df.to_csv('movie.csv')   #create a movies csv file to facilitate EDA on Tableau
movie_df.head()

![image](https://github.com/user-attachments/assets/b491a681-e270-4208-a14c-83f8ddce34b8)

Movie_basics table details the various movie titles, the year they were released, the run-time minutes and the various genres (there may be need for feature engineering around this aspect). There could be a relationship between these parameters and the success of a movie in the box office.

*   **movie_ratings**:

#Explore movie_ratings table
movie_ratings_query = """
                      SELECT *
                      FROM movie_ratings"""
movie_ratings_df = pd.read_sql(movie_ratings_query, conn)
movie_ratings_df.to_csv('movie_ratings.csv')   #create a movies ratings csv file to facilitate EDA on Tableau
movie_ratings_df.head()

![image](https://github.com/user-attachments/assets/f67cf198-7561-4816-bfb9-c9a05a7018a0)

This table shows the average rating for each movie by movie_id and also the number of votes it received (which could give insight into how many people watched it??). There could be a relationship between these parameters and the success of a movie in the box office.

*   **movie_akas**:
  
#Explore movie_akas table
movie_akas_query = """
                      SELECT *
                      FROM movie_akas"""
movie_akas_df = pd.read_sql(movie_akas_query, conn)
movie_akas_df.to_csv('movie_akas.csv')   #create a movies_akas csv file to facilitate EDA on Tableau
movie_akas_df.head()

  ![image](https://github.com/user-attachments/assets/b0070954-a043-40bc-9291-73a28be69b40)

This table shows other movie features e.g. the region, language, type and attributes. There could be a relationship between these features and the success of a movie in the box office.

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
