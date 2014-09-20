Getting-and-Cleaning-Data-Course-Project
========================================

### Description of the Variables
The experiments have been carried out with a group of 30 volunteers within an age bracket of 19-48 years. Each person performed six activities (WALKING, WALKING_UPSTAIRS, WALKING_DOWNSTAIRS, SITTING, STANDING, LAYING) wearing a smartphone (Samsung Galaxy S II) on the waist. Using its embedded accelerometer and gyroscope, we captured 3-axial linear acceleration and 3-axial angular velocity at a constant rate of 50Hz. The experiments have been video-recorded to label the data manually. The obtained dataset has been randomly partitioned into two sets, where 70% of the volunteers was selected for generating the training data and 30% the test data.

The sensor signals (accelerometer and gyroscope) were pre-processed by applying noise filters and then sampled in fixed-width sliding windows of 2.56 sec and 50% overlap (128 readings/window). The sensor acceleration signal, which has gravitational and body motion components, was separated using a Butterworth low-pass filter into body acceleration and gravity. The gravitational force is assumed to have only low frequency components, therefore a filter with 0.3 Hz cutoff frequency was used. From each window, a vector of features was obtained by calculating variables from the time and frequency domain.

For each record in the dataset it is provided:
- Triaxial acceleration from the accelerometer (total acceleration) and the estimated body acceleration.
- Triaxial Angular velocity from the gyroscope. 
- A 561-feature vector with time and frequency domain variables. 
- Its activity label. 
- An identifier of the subject who carried out the experiment.


### Exercise 1.
#### Merge the training and the test sets to create one data set.

First of all, seting the working directory.

After seting the working directory, read the data:
- features.txt
- activity_labels.txt
- x_train.txt
- y_train.txt
- subject_train.txt
- x_test.txt
- y_test.txt
- subject_test.txt

Then rename the columns of the Training sets and de Test sets.

After this, merge each group of 3 data sets, and after that merge this two data sets.


### Exercise 2.
#### Extracts only the measurements on the mean and standard deviation for each measurement.

Generate a vector with the position of the Id, mean and the standard deviation of the columns names.

Then, select from the data set only the columns from this vector.


### Exercise 3.
#### Uses descriptive activity names to name the activities in the data set.

Merge data set of the exercise 2  with the activity_abels table to add the description of the activity.


### Exercise 4.
#### Appropriately labels the data set with descriptive variable names.

Use the "gsub" function for replace and make appropiate the data set.


### Exercise 5.
#### From the data set in step 4, creates a second, independent tidy data set with the average of each variable for each activity and each subject.

From the last data set is created a new and final data set, with the average of each variable for each activity and each subject.

Then this Final Data Set is generated in a .txt extension
