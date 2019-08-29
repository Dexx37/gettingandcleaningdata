# Code Book - Getting and Cleaning Data Project

The description of the original (dirty) data set in the following: [Human Activity Recognition Using Smartphones Data Set](http://archive.ics.uci.edu/ml/datasets/Human+Activity+Recognition+Using+Smartphones)


## Goals and Assumptions


This data set needs to be transformed to a clean data set and then summarized into a tidy data set and saved to a file for further analysis.  As such, the following are the goals of this script:


1. Merges the training and the test sets to create one data set.
  * Extracts only the measurements on the mean and standard deviation for each measurement. 
  * Uses descriptive activity names to name the activities in the data set
  * Appropriately labels the data set with descriptive activity names. 

2. Creates a second, independent tidy data set with the average of each variable for each activity and each subject.
  * Write tidy data set to a file


For the purpose of analysis, the following assumptions are made by inferring the data set description and the format and grouping of the data set:
* The data set was formatted for machine learning
* Data under the "Intertial Signals" directories are the raw data that was used to calculate the "X_train.txt" and "X_test.txt" data.  As such, the files in the "Inertial Signals" directories are not needed for this analysis
* Differentiating between train and test groups are unimportant for our needs


## Data

The data set was the result of experiments measuring the linear and angular velocity from the smartphones of 30 volunteers performing six activities (walking, walking_upstairs, walking_downstairs, sitting, standing, and laying).  The volunteers were video taped during the experiments and their activities were labeled as one of the activities mentioned in the previous sentence.  The data is divided into two groups - train and test.  70% of the volunteers were randomly chosen to be part of the train group and the other 30% were placed in the test group.


Below are the eight files, and their descriptions, that compose the data set:

1. "subject_train.txt"
  * Volunteers in the train group
  * The valid numbers are 1-30
  * Each row corresponds to an activity and its measurements

2. "subject_test.txt"
  * Volunteers in the test group
  * The valid numbers are 1-30
  * Each row corresponds to an activity and its measurements

3. "y_train.txt"
  * Activties in the train group
  * The valid numbers are 1-6
  * Each row corresponds to a volunteer and its measurements

4. "y_test.txt"
  * Activties in the test group
  * The valid numbers are 1-6
  * Each row corresponds to a volunteer and its measurements

5. "X_train.txt"
  * Measurements in the train group
  * There are 561 measurements per row
  * Each row corresponds to a volunteer and activity

6. "X_test.txt"
  * Measurements in the test group
  * There are 561 measurements per row
  * Each row corresponds to a volunteer and activity

7. "activity_labels.txt"
  * Legend for the activity numbers in "y_train.txt" and "y_test.txt"

8. "features.txt"
  * Description for the measurements in "X_train.txt" and "X_test.txt"
  * The number corresponds to columns for the measurements in "X_train.txt" and "X_test.txt"


## Variables


The "features.txt" file from the data set provide an excellent overview of the variables, which are called features in the data set.  The variables are contained in "X_train.txt" and "X_test.txt"  The blockquotes below are copied directly from that file.


> The features selected for this database come from the accelerometer and gyroscope 3-axial raw signals tAcc-XYZ and tGyro-XYZ. These time domain signals (prefix 't' to denote time) were captured at a constant rate of 50 Hz. Then they were filtered using a median filter and a 3rd order low pass Butterworth filter with a corner frequency of 20 Hz to remove noise. Similarly, the acceleration signal was then separated into body and gravity acceleration signals (tBodyAcc-XYZ and tGravityAcc-XYZ) using another low pass Butterworth filter with a corner frequency of 0.3 Hz.
> 
> 
> Subsequently, the body linear acceleration and angular velocity were derived in time to obtain Jerk signals (tBodyAccJerk-XYZ and tBodyGyroJerk-XYZ). Also the magnitude of these three-dimensional signals were calculated using the Euclidean norm (tBodyAccMag, tGravityAccMag, tBodyAccJerkMag, tBodyGyroMag, tBodyGyroJerkMag). > 
> 
> 
> Finally a Fast Fourier Transform (FFT) was applied to some of these signals producing fBodyAcc-XYZ, fBodyAccJerk-XYZ, fBodyGyro-XYZ, fBodyAccJerkMag, fBodyGyroMag, fBodyGyroJerkMag. (Note the 'f' to indicate frequency domain signals).
> 
> 
> These signals were used to estimate variables of the feature vector for each pattern:  
> '-XYZ' is used to denote 3-axial signals in the X, Y and Z directions.
> 
> 
> tBodyAcc-XYZ
> 
> tGravityAcc-XYZ
> 
> tBodyAccJerk-XYZ
> 
> tBodyGyro-XYZ
> 
> tBodyGyroJerk-XYZ
> 
> tBodyAccMag
> 
> tGravityAccMag
> 
> tBodyAccJerkMag
> 
> tBodyGyroMag
> 
> tBodyGyroJerkMag
> 
> fBodyAcc-XYZ
> 
> fBodyAccJerk-XYZ
> 
> fBodyGyro-XYZ
> 
> fBodyAccMag
> 
> fBodyAccJerkMag
> 
> fBodyGyroMag
> 
> fBodyGyroJerkMag> 
> 
> The set of variables that were estimated from these signals are:
> 
> mean(): Mean value
> 
> std(): Standard deviation
> 
> mad(): Median absolute deviation 
> 
> max(): Largest value in array
> 
> min(): Smallest value in array
> 
> sma(): Signal magnitude area
> 
> energy(): Energy measure. Sum of the squares divided by the number of values. 
> 
> iqr(): Interquartile range 
> 
> entropy(): Signal entropy
> 
> arCoeff(): Autorregresion coefficients with Burg order equal to 4
> 
> correlation(): correlation coefficient between two signals
> 
> maxInds(): index of the frequency component with largest magnitude
> 
> meanFreq(): Weighted average of the frequency components to obtain a mean frequency
> 
> skewness(): skewness of the frequency domain signal 
> 
> kurtosis(): kurtosis of the frequency domain signal 
> 
> bandsEnergy(): Energy of a frequency interval within the 64 bins of the FFT of each window.
> 
> angle(): Angle between to vectors.
> 
> 
> Additional vectors obtained by averaging the signals in a signal window sample. These are used on the angle() variable:
> 
> 
> gravityMean
> 
> tBodyAccMean
> 
> tBodyAccJerkMean
> 
> tBodyGyroMean
> 
> tBodyGyroJerkMean


## Transformations


Achieving the goals require creating a clean data set and then a tidy data set.  The following are general data transformations used:


1. Concatenate "subject_train.txt" and "subject_test.txt"
2. Concatenate "y_train.txt" and "y_test.txt"
3. Concatenate "X_train.txt" and "X_test.txt"
4. Set names to variables
  * Descriptive column name for dataSubject is "subject"
  * Descriptive column name for dataActivity is "activity"
  * Descriptive column name for dataFeatures is dataFeaturesNames$V2
4. Merge columns to the data frame Data 
5. Subset Name of Features by measurements on the mean and standard deviation 
6. Read descriptive activity names from "activity_labels.txt"
7. Factorize Variable activity in the data frame Data using descriptive activity names
8. Replace Names of Feteatures with descriptive variable names.
9. Creates a second,independent tidy data set and ouput it.