# CodeBook
This is a code book that describes the variables, the data, and any transformations or work that you performed to clean up the data.

## The data source
1) Original data: https://d396qusza40orc.cloudfront.net/getdata%2Fprojectfiles%2FUCI%20HAR%20Dataset.zip
2) Original description of the dataset: http://archive.ics.uci.edu/ml/datasets/Human+Activity+Recognition+Using+Smartphones

## Data Set Information
The experiments have been carried out with a group of 30 volunteers within an age bracket of 19-48 years. Each person performed six activities (WALKING, WALKING_UPSTAIRS, WALKING_DOWNSTAIRS, SITTING, STANDING, LAYING) wearing a smartphone (Samsung Galaxy S II) on the waist. Using its embedded accelerometer and gyroscope, we captured 3-axial linear acceleration and 3-axial angular velocity at a constant rate of 50Hz. The experiments have been video-recorded to label the data manually. The obtained dataset has been randomly partitioned into two sets, where 70% of the volunteers was selected for generating the training data and 30% the test data.
The sensor signals (accelerometer and gyroscope) were pre-processed by applying noise filters and then sampled in fixed-width sliding windows of 2.56 sec and 50% overlap (128 readings/window). The sensor acceleration signal, which has gravitational and body motion components, was separated using a Butterworth low-pass filter into body acceleration and gravity. The gravitational force is assumed to have only low frequency components, therefore a filter with 0.3 Hz cutoff frequency was used. From each window, a vector of features was obtained by calculating variables from the time and frequency domain.

## The data
1) features <- features.txt : 561 rows, 2 columns 
    The features selected for this database come from the accelerometer and gyroscope 3-axial raw signals tAcc-XYZ and tGyro-XYZ.
2) activities <- activity_labels.txt : 6 rows, 2 columns 
    List of activities performed when the corresponding measurements were taken and its codes (labels)
3) subject_test <- test/subject_test.txt : 2947 rows, 1 column 
    contains test data of 9/30 volunteer test subjects being observed
4) x_test <- test/X_test.txt : 2947 rows, 561 columns 
    contains recorded features test data
5) y_test <- test/y_test.txt : 2947 rows, 1 columns 
    contains test data of activities’code labels
6) subject_train <- test/subject_train.txt : 7352 rows, 1 column 
    contains train data of 21/30 volunteer subjects being observed
7) x_train <- test/X_train.txt : 7352 rows, 561 columns 
    contains recorded features train data
8) y_train <- test/y_train.txt : 7352 rows, 1 columns 
    contains train data of activities’code labels

## Merges the training and the test sets to create one data set
1) X (10299 rows, 561 columns) is created by merging x_train and x_test using rbind() function
2) Y (10299 rows, 1 column) is created by merging y_train and y_test using rbind() function
3) Subject (10299 rows, 1 column) is created by merging subject_train and subject_test using rbind() function
4) Merged_Data (10299 rows, 563 column) is created by merging Subject, Y and X using cbind() function

## Extracts only the measurements on the mean and standard deviation for each measurement
1) TidyData (10299 rows, 88 columns) is created by subsetting Merged_Data, selecting only columns: subject, code and the measurements on the mean and standard deviation (std) for each measurement

## Uses descriptive activity names to name the activities in the data set
1) Entire numbers in code column of the TidyData replaced with corresponding activity taken from second column of the activities variable

## Appropriately labels the data set with descriptive variable names
1) code column in TidyData renamed into activities
2) All Acc in column’s name replaced by Accelerometer
3) All Gyro in column’s name replaced by Gyroscope
4) All BodyBody in column’s name replaced by Body
5) All Mag in column’s name replaced by Magnitude
6) All start with character f in column’s name replaced by Frequency
7) All start with character t in column’s name replaced by Time

## From the data set in step 4, creates a second, independent tidy data set with the average of each variable for each activity and each subject
1) FinalData (180 rows, 88 columns) is created by sumarizing TidyData taking the means of each variable for each activity and each subject, after groupped by subject and activity.
2) Export FinalData into FinalData.txt file.
