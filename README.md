Getting-and-Cleaning-Data-Course-Project
========================================

This is the repo for the Course Project for the  Getting and Cleaning Data Course, from the Data Science Specialization of the Johns Hopkins University.

The main purpose of this course is earn how to gather and clean data from a variety of sources.
This is the third course in the Johns Hopkins Data Science Specialization.

One of the most exciting areas in all of data science right now is wearable computing - see for example this article . Companies like Fitbit, Nike, and Jawbone Up are racing to develop the most advanced algorithms to attract new users. The data linked to from the course website represent data collected from the accelerometers from the Samsung Galaxy S smartphone. A full description is available at the site where the data was obtained:

[http://archive.ics.uci.edu/ml/datasets/Human+Activity+Recognition+Using+Smartphones](http://archive.ics.uci.edu/ml/datasets/Human+Activity+Recognition+Using+Smartphones)

Here are the data for the project: 

[https://d396qusza40orc.cloudfront.net/getdata%2Fprojectfiles%2FUCI%20HAR%20Dataset.zip](https://d396qusza40orc.cloudfront.net/getdata%2Fprojectfiles%2FUCI%20HAR%20Dataset.zip)


Once you have downloaded this file and unziped it you can run the_analysis.R fil from this repo, be careful of the setwd() function for seting the working directory, may be you have to change it for your convenience.


####This are the Course Project Instructions:
- Merges the training and the test sets to create one data set.
- Extracts only the measurements on the mean and standard deviation for each measurement. 
- Uses descriptive activity names to name the activities in the data set
- Appropriately labels the data set with descriptive variable names. 
- From the data set in step 4, creates a second, independent tidy data set with the average of each variable for each activity and each subject.

The CodeBook.md has the explanation of variables, data and any transformations or work that the sdript makes to clean up the data (also in the script there are comments of th data manipulation).

The tidyData.txt has the Tidy Data that the script generates.
