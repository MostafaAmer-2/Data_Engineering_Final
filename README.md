# Data_Engineering_Final

This repository contains a notebook that aims to estimate missing App Rating values in “The Android App Market on Google Play” dataset. 

Different stages are covered in this repo which include:
1. Data collection by downloading the relevant dataset: Data was collected by downloading the datasets from online sources.
2. Data Cleaning and Tidiness: 
    * Drop Duplicates along the App Column subset and drop NaN values for columns with small percentage of missing value.
    * Merging Category and Genre in one column due to their similarity and removing duplicates between them. In addition, Genre contains more subcategories than the category column, hence giving more information.
    * Remove columns Last Updated, Current Ver, Android Ver for their irrelevance. Moreover, we removed columns Category and Price as Category was merged with Genre and Price as we found it unnecessary as we were interested with the fact that the app is Paid or Free only.
    * We encoded the Content Rating column by labeling coding since the data inside it is ordered. Moreover, we resolved the issue of unrated data.
3. Data transformation:
    * Correct and convert size column to int
    * Convert installs to int
    * Convert Reviews to int
    * Convert non-null Ratings to float
    * One Hot encode all genres
4. Outlier detection and handling:
    * We were interested in only 3 relations that affect our main problem of imputing the missing ratings. The 3 relations are Reviews-Rating, Size-Rating and Installs-Rating. We removed the outliers in these 3 relations so that they will not affect our algorithm of imputation. 
5. Final predictions for missing data using Bayesian Ridge:
    * The estimator that we used is the Bayesian Ridge. We used the multi variable imputation to impute the missing data in the App Rating column by fitting (Training) the data in the dataset and transforming this dataset by the imputing the missing values.
6. Data Visualizations:
    * Graph to show the distribution of the Rating value as a frequency. 
    * Visualizations for Category against Rating, Android ver against Rating and Price against Rating as examples to show that such columns have no specific pattern but rather just different random values for the different Ratings. Thus proving they can be easily dropped as the make no use to our goal of missing Rating values estimation.
    * Plots of Reviews, Size and Installs against Rating for demonstrations.
    * The most important visualization from our point of view is the plot of Reviews against Rating but only for the predicted values. This indicates that predicted values all lie within the range of most Ratings and that the Bayesian Ridge method is correctly working.
    * One final plot of Ratings against Reviews for all values is shown for final demonstration.


