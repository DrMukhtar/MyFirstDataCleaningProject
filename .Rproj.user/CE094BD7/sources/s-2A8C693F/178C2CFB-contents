if(!file.exists("UCI HAR Dataset")){
  dataUrl <- "https://d396qusza40orc.cloudfront.net/getdata%2Fprojectfiles%2FUCI%20HAR%20Dataset.zip"
  download.file(dataUrl,destfile="./getdata_projectfiles_UCI HAR Dataset.zip",method="curl")
  dateDownloaded <- date()
  unzip("./getdata_projectfiles_UCI HAR Dataset.zip")
}

### Loading the features and the labels 
# features.txt or "names" for the 561 variables and the string-factor
features <- read.table("UCI HAR Dataset/features.txt",sep=" ",header=FALSE)
# activity_labels.txt : 6 integers {1,..,6} and the string-factor {"WALKING",...}
activity_labels <- read.table("UCI HAR Dataset/activity_labels.txt",sep=" ",header=FALSE)

### Loading the entire training data set 
# Each file contains 7352 rows - each corresponds to a data instance
# Training set: 561 variables
X_train <- read.table("UCI HAR Dataset/train/X_train.txt",header=FALSE)
# Training data label: 1 variable 
y_train <- read.table("UCI HAR Dataset/train/y_train.txt",header=FALSE)
# subject_train: 1 variable
subject_train <- read.table("UCI HAR Dataset/train/subject_train.txt",header=FALSE)


### Loading the entire test data set 
# Each file contains 2947 rows - each corresponds to a data instance
# Test set: 561 variables
X_test <- read.table("UCI HAR Dataset/test/X_test.txt",header=FALSE)
# Test data label: 1 variable 
y_test <- read.table("UCI HAR Dataset/test/y_test.txt",header=FALSE)
# subject_test: 1 variable
subject_test <- read.table("UCI HAR Dataset/test/subject_test.txt",header=FALSE)


### Mission 1: merging the training set and THEN the test set; 10299 rows
# Join set: 561 variables
X_join <- rbind(X_train,X_test)
# Join data label: 1 variable 
y_join <- rbind(y_train, y_test)
# subject_train: 1 variable
subject_join <- rbind(subject_train, subject_test)


### Mission 2: Extracts only the measurements on the mean and standard deviation for each measurement.
# Extracting the variables
ind <- grep("(mean|std)\\(\\)",features[,2]) # the index 
indstr <- grep("(mean|std)\\(\\)",features[,2],value = TRUE) # the strings
# Extracting the subset of the merged dataset
extracts <- X_join[,ind] 


### Mission 3: Naming the activities in the dataset
toNameAct <- function(x) {as.character(activity_labels[x,2])}
y_join[,1] <- sapply(y_join[,1],toNameAct)


### Mission 4: Variable names 
names(extracts) <- indstr #gsub("-(mean|std)\\(\\)+(-|)","",indstr)
names(y_join) <- "Activity"
names(subject_join) <- "Subject"


### Mission 5: The tidy data set
# The directory
if(!file.exists("tidyDataset")){
  dir.create("tidyDataset")
}

# the tidy data set
tidyDataSet <- aggregate(extracts, by = list(y_join[,1], subject_join[,1]), 
                         FUN = "mean")
names(tidyDataSet) <- c("Activity","Subject",paste0("Average",indstr))

# Writing the tidy data set
write.table(names(tidyDataSet),"tidyDataset/variables.txt",quote = FALSE,col.names = FALSE, row.names = FALSE)
write.table(tidyDataSet,"tidyDataset/tidyset.txt",quote = FALSE,col.names = FALSE, row.names = FALSE)


