
# Netflix Dataset – Data Analysis with Python

Exploratory Data Analysis (EDA) of Netflix movies and TV shows using Python, Pandas, Matplotlib, and Seaborn.

## 📌 Project Overview

This project analyzes a Netflix dataset containing information about movies and TV shows available on Netflix up to 2021. The analysis explores content distribution, release trends, ratings, directors, countries, movie durations, and TV show characteristics.

The goal is to extract useful insights from the dataset through data cleaning, transformation, filtering, grouping, and visualization.

## 🎯 Project Objectives

- Understand the distribution of movies and TV shows.
- Analyze Netflix content release trends by year.
- Identify the most frequently listed directors.
- Explore content from different countries.
- Analyze movie and TV show ratings.
- Identify movies featuring a specific actor.
- Examine movie durations and TV show seasons.
- Handle duplicate records and missing values.
- Visualize findings using Python libraries.

## 📂 Dataset Information

- **Dataset:** Netflix Movies and TV Shows
- **Original records:** 7,789
- **Columns:** 11
- **Duplicate records identified:** 2
- **Records after duplicate removal:** 7,787

### Key Columns

| Column | Description |
|---|---|
| `Show_Id` | Unique show identifier |
| `Category` | Movie or TV Show |
| `Title` | Name of the content |
| `Director` | Director information |
| `Cast` | Actors and cast members |
| `Country` | Country or countries associated with the content |
| `Release_Date` | Date recorded in the dataset |
| `Rating` | Content rating |
| `Duration` | Movie duration or number of TV show seasons |
| `Type` | Genre or content classification |
| `Description` | Short content summary |

## 🛠️ Tools and Technologies

- **Python** – Data analysis
- **Pandas** – Data manipulation and analysis
- **NumPy** – Numerical operations
- **Matplotlib** – Data visualization
- **Seaborn** – Statistical visualization
- **Google Colab** – Notebook environment

## 🧹 Data Cleaning and Preparation

The following data preparation steps were performed:

1. Loaded the Netflix CSV dataset into a Pandas DataFrame.
2. Inspected the dataset using `head()`, `tail()`, `shape`, `columns`, and `info()`.
3. Identified and removed duplicate records using `drop_duplicates()`.
4. Checked missing values using `isnull().sum()`.
5. Visualized missing values using a Seaborn heatmap.
6. Converted `Release_Date` into a datetime column.
7. Extracted the release year for year-based analysis.
8. Split the `Duration` column into numeric duration and unit fields for further investigation.
9. Used filtering, grouping, sorting, and aggregation to answer business questions.

**Data quality note:** Missing values were identified in columns such as Director, Cast, Country, Release_Date, and Rating. The notebook also uses `dropna()` for some later analyses, which removes rows with missing values across any column. This can affect the results and should be considered when interpreting the findings.

## 📊 Key Analysis and Findings

### 1. Movies vs. TV Shows

The dataset contains the following records after duplicate removal:

| Category | Number of Titles |
|---|---:|
| Movies | 5,377 |
| TV Shows | 2,410 |
| **Total** | **7,787** |

Movies make up the larger share of the catalog represented in this dataset.

### 2. Content Release Trends

The analysis groups records by the year in `Release_Date`.

| Year | Number of Records |
|---|---:|
| 2017 | 1,225 |
| 2018 | 1,685 |
| 2019 | 2,153 |
| 2020 | 2,009 |
| 2021 | 117 |

**Insight:** Among the years listed, 2019 has the highest count of recorded release dates, followed by 2020 and 2018.

*Note: These figures describe the year in the dataset's `Release_Date` field, not necessarily the original production or theatrical release year.*

### 3. Movies Released in 2020

Filtered the dataset to identify movies with a release date in 2020.

- **Number of matching records in the original analysis:** 1,312
- Used Boolean filtering on `Category` and the extracted year.

### 4. Indian TV Shows

Filtered the dataset to identify TV shows where the country field is exactly `India`.

- **Matching TV shows:** 71
- Retrieved the titles using Pandas filtering and column selection.

### 5. Top 10 Directors

Identified the directors associated with the highest number of records.

| Director | Number of Records |
|---|---:|
| Raúl Campos, Jan Suter | 18 |
| Marcus Raboy | 16 |
| Jay Karas | 14 |
| Cathy Garcia-Molina | 13 |
| Martin Scorsese | 12 |
| Youssef Chahine | 12 |
| Jay Chapman | 12 |
| Steven Spielberg | 10 |
| David Dhawan | 9 |
| Hakan Algül | 8 |

**Insight:** The analysis counts the director field as recorded. Some entries contain multiple directors in a single field, so the results are not necessarily counts for individual directors.

### 6. Content Ratings

Identified 14 distinct rating labels in the dataset after filtering rows with missing values.

Examples include:
- TV-MA
- TV-14
- TV-PG
- R
- PG-13
- TV-Y
- TV-G
- NR

The analysis also filters movies rated `TV-14` with the country field equal to `Canada`.

- **Matching records reported by the notebook:** 9

### 7. Movies Featuring Tom Cruise

Searched the cast information to identify titles featuring Tom Cruise.

The analysis identified two matching movies after removing rows with missing values:

- Magnolia
- Rain Man

The search uses substring matching, which is more appropriate than exact equality when a cast column contains multiple actors.

### 8. Movie and TV Show Duration

Split the `Duration` column into a numeric-looking value and a unit, such as `min` or `Seasons`.

This allows duration information to be examined separately for movies and TV shows.

**Data quality note:** The notebook uses string-based maximum and minimum calculations on the duration values. Numeric conversion and filtering by unit are required before reliably identifying the longest movie or the TV show with the most seasons.

### 9. Country-Level Analysis

Analyzed the country information associated with TV shows by splitting comma-separated country values and expanding them into individual entries.

The notebook reports the United States as the top country in the filtered results, with 39 records.

**Important:** This count comes from `df_new`, which excludes rows with missing values across any column. It should not be interpreted as the total number of US TV shows in the full cleaned dataset.

### 10. Movies by Genre and Country

Filtered movie records where either:
- The `Type` field equals `Comedies`, or
- The `Country` field equals `United Kingdom`.

The notebook returned 281 records for this combined filter.

The `Type` field can contain multiple comma-separated genre labels, so exact matching only identifies rows where the entire field equals `Comedies`.


## 👨‍💻 Author

**Aravind K**

