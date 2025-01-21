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


## Data Cleaning

From the data cleaning requiements identified during the data understanding step, the following cleaning exercises were implemented:
*   Removing rows with empty **Event.ID** values since for such cases, most of the other values were blank. This yielded clean **Investigation.Type** columns as well.
*   Removing rows with empty **Make** values since the main objective of this study is to identify the lowest-risk air crafts to invest in.
*   Removing the bracketed number of fatalities in the **Injury.Severity** column since the same can be evaluated from the **Total.Fatal.Injuries** column. 
*   Normalizing capitalization formatting in all the categorical fields to ensure clean categories.
*   Replacing **UNK** with **Unknown** in all relevant fields to enhance understanding of the data.
*   Converting Date Columns **Event.Date** and **Publication.Date** to Python Datetime format
*   Handling missing values: We will use different strategies to handle different categories of missing data:

    *   Most of the longitude and latitude data is missing, and it does not seem to be relevant to this study. Additionally, we also have location data which is more readily available. Thus, we can drop the longitude and latitude columns
    *   FAR.Description data seems irrelelevant to the study, and so it was dropped
    *   For the few missing values of relevant categorical columns, we can **fill missing values with **Unknown". We may be able to extract insight even with "Unknown" parameters if others related parameters are known e.g. you may have an unknown model but know the manufacturer. This remains relevant to our study.
    *   For the data on total number of injuries, it is best to assume that the data meant to be there is '0' e.g. if Total.Serious.Injuries is empty, it means there were no fatal injuries
*   Checking and removing any duplicates
*   Encoding categorical data into numbers to facilitate correlation calculations.
# Exploratory Data Analysis

We can check for correlation in the measures in our data:

<div align="center">
    <img src="data/Pictures/measurescorrelationheatmap.png" alt="correlation heatmap" width="800">
    <p><em>Testing for Correlation in the Data Measures </em></p>
</div>

There is no immediate correlationary insight noted from correlation heat map. This could be due to the several cases of "Unknown" category. It is prudent to carry out further exploratory analysis using Tableau.

## Tableau EDA

Most of the accidents occur in the USA, distributed across almost all the states.

<div align="center">
    <img src="data/Pictures/AccidentLocation.png" alt="accident location map" width="600">
    <p><em>Recorded Accident Locations </em></p>
</div>

Cessna, Piper, Beech, Boeing and Bell registered the most accidents.

<div align="center">
    <img src="data/Pictures/AccidentFrequencyPerMaker.png" alt="accident frequency per maker bubble" width="600">
    <p><em>Aviation Accidents Per Maker </em></p>
</div>

In the event of an accident, it is almost guaranteed that the aircraft damage will be substantial to totally damaged for most of the makers.

<div align="center">
    <img src="data/Pictures/AircraftDamagePerMaker.png" alt="aircraft damage per maker barchart" width="800">
    <p><em>Aircraft Damage Per Maker </em></p>
</div>

If you remove events where the aircraft damage is "Unknown", the following makers emerge as better candidates where there is a high likelihood of minor the accident only resulting in minor damage:

*   Airbus
*   Boeing
*   Mcdonnell Douglas
*   Embraer
*   Douglas

<div align="center">
    <img src="data/Pictures/AircraftDamage PerMaker2.png" alt="aircraft damage per maker normalized barchart" width="800">
    <p><em>Aircraft Damage Per Maker </em></p>
</div>

To analyze fatalities in the event of an accident, it is important to understand the total number of passengers involved in this data. This can be done by summing up all the fatalities, serious injuries, minor injuries and uninjured passengers.

<div align="center">
    <img src="data/Pictures/TotalOccupancy.png" alt="Total Occupancy per maker" width="800">
    <p><em>Total Occupancy Per Maker </em></p>
</div>

We go a step further to assess the average occupancy per flight from the data. This will tell us the relative sizes of the aircrafts.

<div align="center">
    <img src="data/Pictures/AverageOccupancyPerMaker.png" alt="Average Occupancy per maker" width="800">
    <p><em>Average Occupancy Per Maker </em></p>
</div>

Airbus, Mcdonnel Douglas, Boeing, Douglas and Embraer are generally bigger planes carrying more people, hence their high number of average occupancy. Cessna has a very low average occupancy, i.e. they make small aircrafts carrying very few people (around 2).

It is important to consider the purpose of the flight from the accident data.

<div align="center">
    <img src="data/Pictures/AccidentFrequencyBasedonPurposeofFlight.png" alt="Average Occupancy per maker" width="800">
    <p><em>Accident Distribution Based on Purpose of Flight </em></p>
</div>

Most of the accidents occured during personal flights. 

**NB:- Thus, this branch of aviation seems the most risky that our company should steer clear from, or only engage in with extreme caution**.

Next, it is important to understand distribution of accidents across different aircraft categories over the years.

<div align="center">
    <img src="data/Pictures/AccidentTrendsPerAircraftCategory.png" alt="Trends Per Category" width="800">
    <p><em>Accidents Trends per Aircraft Category </em></p>
</div>

Majority of the aircraft category data is "unknown". Filtering out unknown data will give a better indication.

<div align="center">
    <img src="data/Pictures/AccidentTrendsPerAircraftCategory(less Unknown Categories).png" alt="Trends Per Category with Unknowns Filtered Out" width="800">
    <p><em>Accidents Trends per Aircraft Category with "Unknown" Filtered Out</em></p>
</div>

Airplanes register the most accidents, and it is possible that it is just because their the most used category.

**NB:- A recommendation for further study is to compare this against the total number of aircrafts of each category in operation. This will give a better sense of the probability of accident per aircraft category.**

Next, we analyze the aircraft damage per engine type.

<div align="center">
    <img src="data/Pictures/AircraftDamageperEngineType.png" alt="Accident Damage per Engine Type" width="800">
    <p><em>Accidents Damage per Engine Type</em></p>
</div>

Reciprocating engines register an overwhelming majority of accidents with guaranteed substantial or total damage.

**NB:- It is likely that this is the cae due to their overwhelming majority for all faircrafts in operation. Analyzing this against the total population of reciprocating engine-type aircrafts in operation will give a better sense.**

It is important to understand the trend in accidents for different engine technologies over time.

<div align="center">
    <img src="data/Pictures/AccidentTrendsPerEngineType.png" alt="Accident Trends per Engine Type" width="800">
    <p><em>Accidents Trends per Engine Type</em></p>
</div>

The total number of accidents is droping significantly, in parallel with a steep reduction in the number of accidents for reciprocating engine-type aircrafts. This indicates either of the following:

*    Reciprocating Engine-type Aircrafts are becoming significantly safer with time, hence low number of accident, or,
*   Reciprocating Engine-type Aircrafts are becoming less popular and hence not used as much

**NB:- Comparing this with data showing the engine types for all aircrafts in operation for the given years will give a better sense of this.**