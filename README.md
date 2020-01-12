==================================================================  
Coursera Project: Getting and Cleaning Data  
Wearable Computing Data Project  
==================================================================  
Musawwadah Mukhtar  
PhD of University of Paris Saclay  
Massy, France  
https://github.com/DrMukhtar  
==================================================================  

The data are originated from an experiments in which a group of 30 volunteers performing six activities (WALKING, WALKING_UPSTAIRS, WALKING_DOWNSTAIRS, SITTING, STANDING, LAYING) while wearing a smartphone (Samsung Galaxy S II) on the waist. Thanks to an embedded accelerometer and a gyroscope, we captured 3-axial linear acceleration and 3-axial angular velocity at a constant rate of 50Hz.  

The raw data is downloaded when the processing script is launched

The raw/input dataset
======================================  

The obtained dataset has been randomly partitioned into two sets, where 70% of the volunteers was selected for generating the training data and 30% the test data. The obtained dataset contains measured values after a series of signal processing techniques. These measurements are encoded into 561 variables. Each variable is a combination of a type of signal and a signal property. Types of signal include body and gravity acceleration signals (tBodyAcc-XYZ and tGravityAcc-XYZ), etc. Signal properties include mean, standard deviation, etc. The six activities represent the label which is done manually.

In the obtained dataset, we are interested in the following:  
- "features.txt" : List of all features, i.e. names of the variables  
- "activity_labels.txt" : Links the class labels with their activity name  
- folder 'train' : the training data set  
- folder 'test' : the test data set.  

In the folder 'train', we are interested in the following files: 
- "X_train.txt : values of the 561 variables  
- "y_train.txt" : the activity label for each data instance
- "subject_train.txt" : the volunteer/subject label.
For folder 'test', we are interested in the similar files: "X_test.txt", "y_test.txt", and "subject_test.txt"; their descriptions are equivalent to those in the folder 'train'. 


The repository includes the following files:
=========================================
- 'README.md' 

- 'run_analysis.R' : download the input data set, process it into tidy data set, and save it into folder 'tidyDataset'

- 'CodeBook.md' : Description of the variable, the data, and the data treatment included in the 'run_analysis.R'

- 'tidyDataset' : folder containing the tidy dataset generated by 'run_analysis.R'. It contains: 'tidyset.txt' (the saved data set without heading) and 'variables.txt' (the variables)


Notes: 
======
- Features are normalized and bounded within [-1,1].
- Each feature vector is a row on the text file.


Reference:
========
By using the downloaded dataset, we acknowledge the following publication [1] 

[1] Davide Anguita, Alessandro Ghio, Luca Oneto, Xavier Parra and Jorge L. Reyes-Ortiz. Human Activity Recognition on Smartphones using a Multiclass Hardware-Friendly Support Vector Machine. International Workshop of Ambient Assisted Living (IWAAL 2012). Vitoria-Gasteiz, Spain. Dec 2012


