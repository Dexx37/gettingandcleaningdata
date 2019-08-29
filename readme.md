# Script Explanations - Getting and Cleaning Data Project

The "run_analysis.R" script is made to transform the machine learning focused data set from [Human Activity Recognition Using Smartphones Data Set] (http://archive.ics.uci.edu/ml/datasets/Human+Activity+Recognition+Using+Smartphones) into clean and tidy data sets suitable for human analysis.


## Requirements


1. The data set needed for the script can be found in the above link.
2. R needs to be installed.  This script was tested with R version 3.6.1
3. The operating system the script was tested on was Win10 64bit.  
4. The working directory must be properly set prior to running the script.  Once the data set in unarchived, there is a directory called "UCI HAR Dataset".  This script assumes that the directory that contains "UCI HAR Dataset" is also your working directory.  

## Running the Script


1. Downloading and unarchive "UCI HAR Dataset" to the working directory included at script
2. Download and run "run_analysis.R".  For example, if its downloaded to the working directory, then it can be run by `source("run_analysis.R")`
3. Depending on the configuration of your machine, it may take up to several minutes to complete


## Expected Outputs

Once complete, a text file called "tidydata.txt" can be found in your working directory.  Based on the data used, the file size will be 220KB and if the text file was read into a data frame, there will be 167 rows and 68 columns