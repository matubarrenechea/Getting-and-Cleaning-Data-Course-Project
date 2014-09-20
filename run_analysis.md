################################################
########            Coursera            ########
########    Getting and Cleaning Data   ########
########        Course Project          ########
################################################


####    Exercise 1

##  Merges the training and the test sets to create one data set.


#   First of all, set working directory
setwd("~/FACULTAD/CURSOS/Getting and Cleaning Data (Coursera)/Course Project/UCI HAR Dataset")


#   Read data
features <- read.table("features.txt", header=FALSE)  #List of all features
activity_labels <- read.table("activity_labels.txt")  #Training labels (1 to 6)

colnames(activity_labels) <- c("activity_Id", "activity_Type")  #Rename de feature columns


#   Read data from Training
X_Train <- read.table("./train/X_train.txt")  #Training set
Y_Train <- read.table("./train/y_train.txt")  #Training activity labels
Subj_Train <- read.table("./train/subject_train.txt")  #Subject who perfomr the activity

colnames(X_Train) <- features[,2]  #Rename de Training set columns
colnames(Y_Train) <- "activity_Id"  #Rename de Training activity column
colnames(Subj_Train) <- "subject_Id"  #Rename de Subject column

#Create the Training Data Set, merging the 3 elements (X_Train, Y_Train and Subj_Train) 
Data_Train <- data.frame(Subj_Train, Y_Train, X_Train)
    
#   Read data from Test
X_Test <- read.table("./test/X_test.txt")  #Test set
Y_Test <- read.table("./test/y_test.txt")  #Test activity labels
Subj_Test <- read.table("./test/subject_test.txt")  #Subject who perfomr the activity

colnames(X_Test) <- features[,2]  #Rename de Test set columns
colnames(Y_Test) <- "activity_Id"  #Rename de Test activity column
colnames(Subj_Test) <- "subject_Id"  #Rename de Subject column

#Create the Test Data Set, merging the 3 elements (X_Test, Y_Test and Subj_Test) 
Data_Test <- data.frame(Subj_Test, Y_Test, X_Test)


# Solution of Exercise 1, Merging the two Data Sets

Complete_Data_1 <- rbind(Data_Train, Data_Test)



####    Exercise 2

##  Extracts only the measurements on the mean and standard deviation for each measurement.


# With the grepl function, generate a vector with the position of the means and the standard deviations

columns <- colnames(Complete_Data_1)  #Names of the columns

positions_aux <- grepl("(activity|subject)", columns) | (grepl("mean", columns) & !grepl("meanF", columns)) | grepl("std", columns)

positions <- which(positions_aux == TRUE)  #Position of the means and the standar deviations

Complete_Data_2 <- Complete_Data_1[,positions]



####    Exercise 3

## Uses descriptive activity names to name the activities in the data set

# Merge "Complete_Data2" whith "activity_labels" that has the activities names
Complete_Data_3 <- merge(Complete_Data_2, activity_labels, by = "activity_Id", all.x = TRUE)



####    Exercise 4

## Appropriately labels the data set with descriptive variable names. 

columns_3 <- colnames(Complete_Data_3)

columns_3 <- gsub(".mean", "_Mean", columns_3)  #Replace ".mean" by "Mean"
columns_3 <- gsub(".std", "_Std", columns_3)  #Replace ".std" by "Std"
columns_3 <- gsub("...X", "_X", columns_3)  #Replace "...X" by "X"
columns_3 <- gsub("...Y", "_Y", columns_3)  #Replace "...Y" by "Y"
columns_3 <- gsub("...Z", "_Z", columns_3)  #Replace "...Z" by "Z"
columns_3 <- gsub("[..]", "", columns_3)  #Remove the ".." finals
columns_3 <- gsub("tB", "t_B", columns_3)  #Replace the begining with a "_"
columns_3 <- gsub("tG", "t_G", columns_3)  #Replace the begining with a "_"
columns_3 <- gsub("fB", "f_B", columns_3)  #Replace the begining with a "_"
columns_3 <- gsub("BodyBody", "Body", columns_3)  #Replace "BodyBody" by "Body"

colnames(Complete_Data_3) = columns_3



####    Exercise 5

## From the data set in step 4, creates a second, independent tidy data set with the average of each variable for each activity and each subject. 


Tidy_Data_1 <- aggregate(Complete_Data_3[, columns_3 != c("activity_Id", "subject_Id", "activity_Type")], by = list(activity_Id = Complete_Data_3$activity_Id, subject_Id = Complete_Data_3$subject_Id), mean)

# Merge "Tidy_Data_1" whith "activity_labels" that has the activities names
Tidy_DataSet <- merge(Tidy_Data_1, activity_labels, by = "activity_Id", all.x = TRUE)

# Export the Tidy_DataSet
write.table(Tidy_DataSet, "./tidyData.txt", row.names = FALSE, sep = "\t")
