Clean Data
==========

## Assumsion 
* the files (activity_labels.txt, features.txt) have to be in the same workspace with the run_analysis.R
* two folder test and train need to be in same workspace with the script file
* library reshape2 and plyr installed

## How run_analysis script work

* Collect the information of activity labels and features (activity_labels.txt, features.txt)

* Get data from test folder:
  * collect data from test/subject_test.txt using read.table, set column name as subjects
  * collect data from test/X_test.txt using read.table, set column names as featureNames [features.txt]
    * take subset of the features data by checking features name contains mean or std words
    * write down the origin feature names [meanAndStdFeatures.txt] to help users to map back to the origin data because set column names in R have filter out all special characters.
  * collect data from test/y_test.txt using read.table, set column names as activities
    * convert the activity codes into activity label
      * convert activity codes to numeric
      * Using the numeric as index to get correct label
  * combind all data by column
  
* Get data from train folder:
  * collect data from train/subject_train.txt using read.table, set column name as subjects
  * collect data from train/X_train.txt using read.table, set column names as featureNames [features.txt]
    * take subset of the features data by checking features name contains mean or std words
    * write down the origin feature names [meanAndStdFeatures.txt] to help users to map back to the origin data because set column names in R have filter out all special characters.
  * collect data from train/y_train.txt using read.table, set column names as activities
    * convert the activity codes into activity label
      * convert activity codes to numeric
      * Using the numeric as index to get correct label
  * combind all data by column
* Combind test and train data by row
* Write tidyData

* Create data set with the average of each variable for each activity and each subject.
  * reshape data by using melt on activities and subjects
  * for each activity and subject, apply mean on the value column
  * write down the result in averageMovementByActivityAndSubject.txt

