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

##Set up and grabbing our data
Because we are limited on time and many of you are most likely running windows we are going to use python anywhere - a shell hosted in the browser.

Open a browser and create a new beginner account on https://www.pythonanywhere.com/pricing/

Create a new account, it should take just a few moments. 

We are going to use some data on IRS 990 exempted firms - it's only a snapshot of the dataset to practice with. 
It is in the data folder of this github repo. 

Download it and move to the files tab of Pythonanywhere. 

Upload our data using the uploader button and go back to the consoles tab.

Now we need to get ourselves a terminal. Start a new bash console and wait for it to initialis. 

Once it's up and running then it's time to get csvkit

Now we need to install csvkit in our bash shell. 

To do this we are going to use the pip package manager for python version 2.7

$ pip2.7 install --user csvkit

##Looking at our data 
Now we need to navigate into the correct folder in the terminal in order to perform analysis on our data

To do that we are going to use a couple of unix commands on the command line. 

* pwd - print working directory
* cd - change directory
* ls - lists the contents of a folder

Type pwd_to check that you're in your own home directory

Now we need to check that our data was correctly uploaded into our virtual machine to do this we use the command below:

$ ls 

You should see your data in here - of not shout and someone will give you a hand!

#Looking at our data

* in2csv
* csvlook
* csvcut

Our data set is from the ire data library - The first thing we need to do get our data into the terminal in the right format. 

- If you are dealling with an excel file you can covert your data using the command 

$ in2csv sampledata.xlsx > data.csv

But as our data set is already a csv we need to navigate into the right folder so we can look at our data and figure out what we've got. 

Csvlook will dump the entire csv into your terminal 

$ csvlook data.csv

Your data is probably going to look like a mess. The rows and columns can't all fit in  the width of your terminal and so it's going to be pretty dificult to make any sense of what you've got. 

We need to refine and figure out the schema of what we're looking at. 

$ csvcut -n data. csv 

The -n means that we should see the names of the columns 

This is about the time that we grab a data dictionary to figure out what each column means

##Data formatting

* csvclean
* csvstat

Let's clean the data quickly to make sure it's formatted correctly. 

$ csvclean IRSdata.csv

Now we get look at some basic stats to look for trends in our data. 

$ csvstat IRSdata.csv

This is another handy way of checking how clean your data is - look for values that are out of place like if there was more than 12 unique values for Month. 

Time to start wrangling. 

##Data Wrangling

* csvgrep - Regular expression allowing us to filter our data
* csvsort - sorts the data
* csvsql - Connects our data to a sql database to allow us to query it



