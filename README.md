# Goibibo-Flight-Data-Analysis
This project explores and analyzes flight price data to gain insights into various factors affecting pricing. The analysis includes data cleaning, preprocessing, and visualization to understand trends and patterns in flight prices. The dataset used in this project contains approximately 300,000 flight records
1. Data Loading and Initial Inspection

Code: data = pd.read_csv('goibibo_new_data project.csv'), df = pd.DataFrame(data), df.head(), df.info()
Insight:
The project begins by loading flight data using Pandas. This establishes the foundation for all subsequent analysis.
df.head() gives us a quick view of the data structure, column names, and sample values. This is crucial for understanding the variables we're working with (e.g., airline, from, to, price).
df.info() provides essential metadata: column data types, non-null counts, and memory usage. This helps in identifying potential data cleaning needs (e.g., handling missing values, converting data types).
Business Relevance: Understanding the raw data is the first step in any analytical project. It informs how we proceed with cleaning, processing, and analysis to ensure reliable results.
2. Data Cleaning

Code: df = df.rename(columns={'flight_num':'flight_id'}), df.isnull().any(), df = df.dropna(subset=['duration'])
Insight:
The project addresses data quality:
Renaming columns (flight_num to flight_id) improves clarity and consistency.
Checking for missing values (df.isnull().any()) and removing rows with missing 'duration' (df.dropna(subset=['duration'])) ensures that the analysis is performed on complete data, avoiding errors or biased results.
Business Relevance: Clean data is essential for accurate analysis. Handling missing or incorrectly labeled data prevents misleading conclusions about flight prices.
3. Data Type Conversion and Preparation

Code: df['flight date'] = pd.to_datetime(df['flight date'], format='%d-%m-%Y', errors='coerce'), Conversion of dep_time and arr_time to datetime components.
Insight:
The code converts the 'flight date' column to datetime objects. This enables time-based analysis, like identifying trends over time.
Converting dep_time and arr_time from fractions of a day to HH:MM format makes the times more interpretable and useful for calculating time differences or analyzing schedules.
Business Relevance: Working with dates and times in the correct format is crucial for analyzing how flight prices vary by date, time of day, or flight duration.
4. Exploratory Data Analysis (EDA) and Visualization

Code: df['stops'].value_counts(), df.groupby('airline')['price'].mean().sort_values().plot(kind='bar'), Histograms for price and duration, Boxplots for class vs. price, Line plot for average price over time.
Insight:
df['stops'].value_counts() reveals the distribution of flights by the number of stops, highlighting that 1-stop flights are most common. This is important for understanding the composition of the dataset.
Visualizations are used to explore relationships:
Bar charts compare average prices across airlines, showing which airlines tend to be more expensive.
Histograms and boxplots illustrate the distribution of prices and duration, and how price varies by flight class.
The line plot visualizes price trends over time, which can reveal seasonal patterns or the impact of external events.
Business Relevance:
EDA helps uncover patterns and anomalies in the data.
Visualizations make it easier to communicate findings to stakeholders. For example, airlines can use this analysis to understand their pricing relative to competitors, or travelers can identify the best times to book flights.
5.  Feature Engineering (If Present - Not Extensive in Given Code)

Code: (Limited in this snippet, but could involve) Calculating time differences from dep_time and arr_time.
Insight:
While the provided code snippet focuses on cleaning and basic visualization, feature engineering could be a significant part of a full flight analysis. For example, calculating the actual flight time from departure and arrival times, or creating categorical variables for day of the week or month.
Business Relevance: Creating new features can improve the accuracy of predictive models or reveal more complex relationships in the data
