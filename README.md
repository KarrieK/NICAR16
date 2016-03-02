# Csvkit and other command line tools

Csvkit is the king of csv wrangling libraries. It converts, greps, sorts and outputs large sets of data so you don't need to use Excel or SQL.It provides a user with a nice intro to the awesome power of the command line. 

Csvkit is flexible, easy to use and powerful. We should all buy Christopher Groskopf a drink at the bar! 

We are going to convert an excel file to a csv, then analyse it and output our results. We will also cover some of the basic unix commands like pwd, cd, curl etc so you can learn how to navigate through a termainal.

If you want a more comprehensive list of unix tools, I'll have one up on github after the class

##Overview
We are going to use the following commands:

* pwd - print working directory 
* cd - change directory
* mkdir - make directory
* ls - list
* in2csv - converts a file into a csv
* csvlook - gives us a preview of our data
* csvcut - cutting too for manipulating csvs
* csvclean - cleans our csv for errors
* csvstat - gives us descriptive stats for the content of our csv
* csvsort - sorts the contents of a csv file
* csvgrep - regex command like a refined search function in our csv
* csvsql - enables us to connect to a sql database 

##Environment
Because we are limited on time and many of you are most likely running windows we are going to use python anywhere - a shell hosted in the browser.

Open a browser and create a new beginner account on https://www.pythonanywhere.com/pricing/

Create a new account, it should take just a few moments. 

In another tab in your broswer go to this link http://catalog.data.gov/dataset/formal-enforcement-actions-fy-2004-fy-2010-1088e

Download the excel file and then upload it into pythonanywhere in the files tab. 

To do that we are going to use a coupld of unix commands on the command line. 

* pwd - print working directory
* cd - change directory
* ls - lists the contents of a folder

We start running a bash shell and wait for it to initialise. 
Then type _pwd_ to check that you're in your own home directory

$ cd csvkit_class 

Check that you are in the correct folder
$ pwd 

## Installing csvkit

Now we need to install csvkit in our cash shell. 

To do this we are going to use the pip package manager for python version 2.7

$ pip2.7 install --user csvkit


To make sure that we have been succesful grabbing the data type - ls and it should list the file

#Looking at our data

The first thing we need to do is turn our excel file into a csv and change its name

To do this we are going to use the command in2csv and then rename it

$ in2csv nsnextract.xlsx > data.csv

Now we have some data in a csv format it's time to look at it and figure out what we've got. 

Csvlook will dump the entire csv into your terminal 

$ csvlook data.csv

Your data is probably going to look like a mess. The rows and columns can't all fit in  the width of your terminal and so it's going to be pretty dificult to make any sense of what you've got. 

We need to refine and figure out the schema of what we're looking at. 

$ csvcut -n data. csv 

The -n means that we should see the names of the columns 

Now we have 6 columns - this is a good time to get our data dictionary out and figute out what type of data we're looking at. 








