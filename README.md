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
We are going to use python anywhere - it's a start-up that hosts bash and python shells in the browser. It's handy and quick to set up and it can be run easily on windows machines. If anyone would like to use this on their own laptop I'll have another readme in the github repo explaining how to run csvkit in a terminal on a linux or OSX operating system. 

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

##Unix commands for navigating
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

* head - limits to the top 10 rows
* csvcut - slices away segements of our data
* csvgrep - Regular expression allowing us to filter our data
* csvsort - sorts the data
* csvsql - Connects our data to a sql database to allow us to query it

Now we start combining our functions to build queries to explore our data.

We use | or a pipe to combine or stack the commands together to build more powerful queries. 

Let's have a look at which states have IRS 990 organisations. 

$ csvcut -c STATE IRSdata.csv | csvlook

We want to see what sort of data we have - so let's use head and have a look at the first 10 rows

$ csvcut -n data. csv | csvlook | head

Unfortunately that doesn't tell us much so let's look and see if we can get some summary stats on the states. 

$ csvcut -c STATE IRSdata.csv | csvstat | csvlook

Which state has the most amount of organisations? But what does that mean?

Let's add in another column and look at Income Amount

$ csvcut -c STATE,INCOME_AMT IRSdata.csv | csvlook

Obviously there are more organisation in Maine than other states. Let's use csvgrep to take a closer look at what's going on in Maine

$ csvcut -c STATE,INCOME_AMT IRSdata.csv | csvgrep -c STATE -m ME |csvstat | csvlook

What is the total income amount for all 990 organisations in ME? $10,043,698,930
How many organisations have 0 income?
How many rows?
What are the 5 most frequent values?

## Digging deeper

Let's see if we can find out the names of the organisations with the highest income

$ csvcut -c STATE,INCOME_AMT IRSdata.csv | csvgrep -c STATE -m ME |csvsort -c INCOME_AMT -r | csvlook | head 

Now let's take a look at the names of those organisations.

$ csvcut -c STATE,INCOME_AMT IRSdata.csv | csvgrep -c STATE -m ME |csvsort -c INCOME_AMT -r | csvlook | head 



