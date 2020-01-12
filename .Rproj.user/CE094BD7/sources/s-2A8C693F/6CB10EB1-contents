This code book in .md format attempts to describe the data preparation carried out in a single processing script (run_analysis.R).

## Study design  

**Downloading**. The raw/input are downloaded from <https://d396qusza40orc.cloudfront.net/getdata%2Fprojectfiles%2FUCI%20HAR%20Dataset.zip>; it must then be unzipped. 

**Loading the data**. The data are loaded from .txt files into data frames. The name of the data frame is equal to the .txt file (excluding ".txt""). We load in the following order:  
1. the names of the variables and the activities from "features.txt" and "activity_labels.txt" respectively.  
2. the training data set from "X_train.txt, "y_train.txt", and "subject_train.txt".  
3. similar to the loading of the training data set, we load the test data set from "X_test.txt, "y_test.txt", and "subject_test.txt".


### Mission 1: Merging the training and the test sets to create one data set
We merge the loaded data frames into join data frame:  
- `X_train` and `X_test` into `X_join`  
- `y_train` and `y_test` into `y_join`  
- `subject_train` and `subject_test` into `subject_join`  

### Mission 2: Extracting the mean and standard deviation
We are only interested in the measurements on the mean and standard deviation for each measurement. The associated variables have either `mean()` or `std()` in their variable names. The code consists of   
- identifying the index of the variables (`ind` for the integer vector and `indstr` for the string vector)  
- extract subsets of `X_join` named `extracts`

### Mission 3: Naming the activities in the data set
We want tose descriptive activity names to name the activities in the data set. For this,  
1. define a function `toNameAct` which take input integer, 1 to 6, and return a string representing the activity name.  
2. By making use of `sapply` and `toNameAct`, we replace the integers in `y_join` into corresponding activity-string.  

### Mission 4: Appropriate variable names
We appropriately label the data set with descriptive variable names:
- for data frame `extracts`: the strings in `indstr` (see mission 2)  
- for `y_join` : `"Activity"`  
- for `subject_join` : `"Subject"`

### Mission 5: Independent tidy data set
5.From the data set in step 4, creates a second, independent tidy data set with the average of each variable for each activity and each subject.
We save the tidy data set in the folder "tidyDataset" containing:  
- 'tidyset.txt' : the saved data set without heading  
- 'variables.txt' : the variables



## Code book
The training data set contains 7352 rows, the test data set contains 2947 rows. As a result, the merged data set data set contain 10299 rows.

### The variables
Each variable is a combination of a type of signal and a signal property. Types of signal include body and gravity acceleration signals (tBodyAcc-XYZ and tGravityAcc-XYZ), etc. Signal properties include mean, standard deviation, etc. The six activities represent the label which is done manually.

For the types of signal, prefix 't' represents time domain signals captured at a constant rate of 50 Hz and filtered using a median filter and a 3rd order low pass Butterworth filter with a corner frequency of 20 Hz to remove noise. 

Similarly, the acceleration signal was then separated into body and gravity acceleration signals (tBodyAcc-XYZ and tGravityAcc-XYZ) using another low pass Butterworth filter with a corner frequency of 0.3 Hz.  

Subsequently, the body linear acceleration and angular velocity were derived in time to obtain Jerk signals (tBodyAccJerk-XYZ and tBodyGyroJerk-XYZ). Also the magnitude of these three-dimensional signals were calculated using the Euclidean norm (tBodyAccMag, tGravityAccMag, tBodyAccJerkMag, tBodyGyroMag, tBodyGyroJerkMag).  

Finally a Fast Fourier Transform (FFT) was applied to some of these signals producing fBodyAcc-XYZ, fBodyAccJerk-XYZ, fBodyGyro-XYZ, fBodyAccJerkMag, fBodyGyroMag, fBodyGyroJerkMag. (Note the 'f' to indicate frequency domain signals). 

These signals were used to estimate variables of the feature vector for each pattern:  
'-XYZ' is used to denote 3-axial signals in the X, Y and Z directions.

As a result, **we have the following 33 types of signal**:  
tBodyAcc-XYZ
tGravityAcc-XYZ
tBodyAccJerk-XYZ
tBodyGyro-XYZ
tBodyGyroJerk-XYZ
tBodyAccMag
tGravityAccMag
tBodyAccJerkMag
tBodyGyroMag
tBodyGyroJerkMag
fBodyAcc-XYZ
fBodyAccJerk-XYZ
fBodyGyro-XYZ
fBodyAccMag
fBodyAccJerkMag
fBodyGyroMag
fBodyGyroJerkMag

The set of variables that were estimated from these signals are obtained through calculation such as mean, standard deviation, median, etc. There are 17 of them. For the tidy dataset, however, we take **only the following 2 properties**:  
mean(): Mean value
std(): Standard deviation

As a result the tidy data set has **66 possible measurement variables** based on the combination of the types of signal and the properties.

The measurements are normalized values from gravitational constant. The features/variables:  
- Features are normalized and bounded within [-1,1].
- Each feature vector is a row on the text file.


The tidy data set obtained from selecting 66 columns form the merged data set. It is obtained after averaging these variables for each activity and each subject. Considering 6 activities and 30 subjects, the tidy data set has 180 rows.

In total, the tidy data set has 68 columns, activity, subject, and the average of the 66 aforementioned variables. The name of these 66 variables are concatenations of "Average" and the initial name.





