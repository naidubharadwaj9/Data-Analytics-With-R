README.md

Getting and Cleaning Data - Course Project
This repository hosts the R code and documentation files for the Data Science's track course "Getting and Cleaning data", available in coursera.

The dataset being used is: Human Activity Recognition Using Smartphones

Files

The code takes for granted all the data is present in the same folder, un-compressed and without names altered.

CodeBook.md describes the variables, the data, and any transformations or work that was performed to clean up the data.

run_analysis.R contains all the code to perform the analyses described in the 5 steps. They can be launched in RStudio by just importing the file.

The output of the 5th step is called averages_data.txt, and uploaded in the course project's form.




CodeBook.md

Introduction
The script run_analysis.Rperforms the 5 steps described in the course project's definition.

First, all the similar data is merged using the rbind() function. By similar, we address those files having the same number of columns and referring to the same entities.
Then, only those columns with the mean and standard deviation measures are taken from the whole dataset. After extracting these columns, they are given the correct names, taken from features.txt.
As activity data is addressed with values 1:6, we take the activity names and IDs from activity_labels.txt and they are substituted in the dataset.
On the whole dataset, those columns with vague column names are corrected.
Finally, we generate a new dataset with all the average measures for each subject and activity type (30 subjects * 6 activities = 180 rows). The output file is called averages_data.txt, and uploaded to this repository.
Variables
x_train, y_train, x_test, y_test, subject_train and subject_test contain the data from the downloaded files.
x_data, y_data and subject_data merge the previous datasets to further analysis.
features contains the correct names for the x_data dataset, which are applied to the column names stored in mean_and_std_features, a numeric vector used to extract the desired data.
A similar approach is taken with activity names through the activities variable.
all_data merges x_data, y_data and subject_data in a big dataset.
Finally, averages_data contains the relevant averages which will be later stored in a .txt file. ddply() from the plyr package is used to apply colMeans() and ease the development.