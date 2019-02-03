---
title: 'Tutorial on Merging CSV files '
author: Dilsher Dhillon
date: '2018-12-11'
slug: tutorial-on-merging-csv-files
categories: [Data wrangling]
tags: [Python]
image:
  caption: ''
  focal_point: ''
---

One of our collaborators was generating 20 odd files from a clinical research form (CRF) database. They all had the same identifiers but were broken up into several variables. I was in a meeting with him one day where I saw him trying to `vlookup` and merging these files.... Well, something needed to be done to avoid that tedious process!  

Below is a short post on merging any number of files which have the same identifiers in `python`. There are definitely several ways of doing this, but this one works for me!


The reason I used `python` is because I was in the midst of reading *python for data science* https://jakevdp.github.io/PythonDataScienceHandbook/ by JakeVanderplas and I thought I should try to implement this in `python` rather than `R`, which I was most comfortable at the time. 



*So here we go!*



First off, we need to install Jupyter notebooks to use the below code. Follow the instructions below to install Jupyter notebooks 

Follow this link http://jupyter.org/install 

Use the link to https://www.anaconda.com/download/#macos and download the `Anaconda Distribution`. Follow all steps including all the steps in the terminal to succesfully install Jupyter notebooks  
 



#### Steps to follow after succesfull installation  
1. Once installed, simply go to the terminal and type 'jupyter notebook &'   

2. Browser window will open up and click 'New' - 'Python 3' notebook and work the below code! 
![Python Notebook Pic](/img/csv_tutorial.png)


## Summary of steps required for merging any number of files 
1. We import the required libraries (pandas and OS)
2. All the files should be in the CSV format (xlsx is also supported but not shown here)  
    **a. They should all be placed in their own folder  - eg -  "foo_files"**  
    **b. No other CSV file should be placed in that folder. If you have to, create another folder under in this folder and name it 'Other files'** . 
4. Make sure the common identifier for **ALL** files, in this case 'Patient and Visit ID', should be the same column in each file - in this case, it is in column 3
5. Run the script below by changing the folder names as necessary 
7. **Optional** Once all merging is done, remove rows where ALL values are NaN
8. Finally, export the merged file to CSV 

#### Let's start!! 

1. Make sure only the files we need to merge are ending with .csv in the folder - very important 


```python
import pandas as pd
import os
os.chdir('/Users/dilsherdhillon/Box/Dilsher/Lab Data Extractions/20180601_Data Export/20180601_Data Export/Aim 1') 

## Here we set the directory - this will be unique to your computer 
## Only files of interest that you want to merge should be present in this folder in the CSV format - nothing else  ending in CSV should be present otherwise it will mess it up

dfs = [pd.read_csv(f, index_col=[2])
        for f in os.listdir(os.getcwd()) if f.endswith('csv')]
df = pd.concat(dfs, axis=1, join='outer')
```  

Notice how the **index_col** is "2" - this is because our common identifier is the 3rd column in every file - if it is in the 1st column for your case, change the **index_col** to "0"  


#### This below is optional - in this case I wanted to remove other columns with ID listed since they were reduntant and also remove all rows with NAs  
```python
df.drop(list(df.filter(regex = 'ID')), axis = 1, inplace = True)
df=df.dropna(axis=0,how='all')

## Export the file to a different folder under AIM 1 folder 
df.to_csv('/Users/dilsherdhillon/Box/Dilsher/Lab Data Extractions/20180601_Data Export/20180601_Data Export/Aim 1/Other CSV/MasterAim1.csv')
```

*And that's it !*  

Using a couple of basic rules of files are organized and a few lines of code, we could potentially merge hundreds of files seamlessly!  

Happy to hear thoughts on how this could be made better or more efficient! 


