# TMDB
ML Project - TMDB TV Shows Database
Author: Yonatan Umansky
Course: BIU DS20 Data Science Course

Project Overview:
This project focuses on building a robust regression model to predict the popularity level of TV shows using data from the TMDB TV Show Database.

Database: TMDB TV Show Database (over 160,000 TV show records).

Target Variable: TV Show Popularity (a proprietary TMDB measure based on user engagement metrics like votes, favorites, watchlist additions, and access count).

Goal: Develop a regression model leveraging existing and newly engineered features to predict this continuous popularity score.

The dataset comprises ~160,000 TV show records with various categorical and numerical attributes (languages, genres, creators, networks, etc.).

Methodology and Pipeline:
The project followed a standard ML pipeline with a strong emphasis on Data Preparation and Feature Engineering.

Data Preparation & Cleaning:
Missing Values: Handled by API Augmentation (querying TMDB's API) and dropping features with excessive unrecoverable NaNs (e.g., tagline, homepage).
Multi-Value Features (e.g., genres): Values were split, consolidated into generic categories, and then handled using Multi-Hot Encoding to correctly capture multiple categories per show.

Outlier Treatment: 
Outliers were detected using Box Plots and the IQR method, and subsequently deleted and imputed using the MICE method.

Feature Engineering:
New Features: Created date-based features (show tenure, avg. seasons per year) and numerical measures (e.g., binary indicator for non-English language availability).

Encoding: 
Used One-Hot Encoding for single-value categorical features and Multi-Hot Encoding for multi-value categorical features. Frequency Encoding was also applied to high-cardinality features.

Feature Selection: 
Feature importance tests were executed using multiple models (Ridge, Lasso, SVR, Gradient Boost, Random Forest) to select the most impactful features.

Model Selection and Evaluation:
Approach: Regression was chosen due to the continuous nature of the target variable.

Final Model: 
Random Forest Regressor was selected for its relatively best performance metrics.

Fine-Tuning: 
The model was fine-tuned using Randomized Search and Grid Search methods.

Summary and Future Outlook
The final fine-tuned Random Forest Regressor achieved an $R^2$ of 0.258. The model's predictive ability is limited, likely due to the highly skewed nature of the proprietary Popularity target variable , persistent missing data in key categorical features , and missing crucial predictors in the TMDB database (e.g., production cost, key cast/director names, initial market testing data). As for deployment potential, the model is considered a valuable assisting tool for show production companies to predict a show's potential success, to be updated daily with new data. Better performance is anticipated with a cleaner, richer dataset.
