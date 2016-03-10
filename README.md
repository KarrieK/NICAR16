# csvkit and other command line tools

Wifi:CAR2016

website:www.pythonanywhere.com

Csvkit is the king of csv wrangling libraries. It converts, greps, sorts and outputs large sets of data so you don't need to use Excel or SQL.It provides a user with a nice intro to the awesome power of the command line. 

Csvkit is flexible, easy to use and powerful. It is not limited to a million rows of data like excel, yet is time efficient so you aren't waiting for queries like SQL. It's a great stepping stone to the command line and programming languages. 

We should all buy Christopher Groskopf a drink at the bar! 

We are going to learn how to convert an excel file to a csv then analyse it and output our results. We will also cover some of the basic unix commands like pwd, cd, etc so you can learn how to navigate through a termainal.

If you want a more comprehensive list of unix tools, I'll have one up on github after the class

##Overview
We are going to use the following commands:

* pwd - print working directory 
* cd - change directory
* ls - lists contents of a directory
* in2csv - converts a file into a csv
* csvlook - gives us a preview of our data
* csvcut - cutting too for manipulating csvs
* csvclean - cleans our csv for errors
* csvstat - gives us descriptive stats for the content of our csv
* csvsort - sorts the contents of a csv file
* csvgrep - regex command like a refined search function in our csv
* head - limits data to the top ten rows

##Set up and grabbing our data
We are going to use python anywhere - it's a start-up that hosts bash and python shells in the browser. It's handy and quick to set up and it can be run easily on windows machines. If anyone would like to use this on their own laptop I'll have another readme in the github repo explaining how to run csvkit in a terminal on a linux or OSX operating system. 

Open a browser and create a new beginner account on https://www.pythonanywhere.com/pricing/

Create a new account, it should take just a few moments. 

We are going to use some data on IRS 990 exempted firms - it's only a snapshot of the dataset to practice with. 

It will be in a folder on your computers in the following location

Desktop > 2016 CAR Conference > Command line tools for reporters (PC) > Data > IRSdata.csv

Now  we need to get it into Pythonanywhere. 

Navigate to the files tab of Pythonanywhere upload the data using the uploader button and go back to the consoles tab.

Now we need to get ourselves a terminal. Start a new bash console and wait for it to initialis. 

Once it's up and running then it's time to get csvkit

Now we need to install csvkit in our bash shell. A bash shell is a command-line interpreter or shell which allows users to direct the operation of a computer by entering commands as text instead of with a mouse. 

To do this we are going to use the pip package manager for python version 2.7

$ pip2.7 install --user csvkit

##Unix commands for navigating
Now we need to navigate into the correct folder in the terminal in order to perform analysis on our data

To do that we are going to use a couple of unix commands on the command line. 

* pwd - print working directory
* cd - change directory
* ls - lists the contents of a folder

Type pwd to check that you're in your own home directory

Now we need to check that our data was correctly uploaded into our virtual machine to do this we use the command below:

$ ls 

You should see your data in here - of not shout and someone will give you a hand!

#Looking at our data

* in2csv
* csvlook
* csvcut

Our data set is from the IRE data library - The first thing we need to do get our data into the terminal in the right format. 

If you are dealling with an excel file you can covert your data using the command 

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

Now we start combining our functions to build queries to explore our data.

We use | or a pipe to combine or stack the commands together to build more powerful queries. 

Let's have a look at which states have IRS 990 organisations. 

$ csvcut -c STATE IRSdata.csv | csvlook

We want to see what sort of data we have - so let's use head and have a look at the first 10 rows

$ csvcut -n IRSdata.csv | csvlook | head

Unfortunately that doesn't tell us much so let's look and see if we can get some summary stats on the states. 

$ csvcut -c STATE IRSdata.csv | csvstat | csvlook

Which state has the most amount of organisations? But what does that mean?

Let's take a look to see if there are multiple organisations of the same name in the data set

$ csvcut -c NAME IRSdata.csv | csvstat | csvlook

Let's combine STATE and INCOME_AMT to see what we get

$ csvcut -c STATE,INCOME_AMT IRSdata.csv | csvlook

Obviously there are more organisation in Maine than other states. Let's use csvgrep to take a closer look at what's going on in Maine

$ csvcut -c STATE,INCOME_AMT IRSdata.csv | csvgrep -c STATE -m ME | cvstat | csvlook

What is the total income amount for all 990 organisations in ME? $10,043,698,930
How many organisations have 0 income?
What is the maximum income?
How many rows?
What are the 5 most frequent values?

## Digging deeper

Let's build a query to figure out the names of the organisations with the highest incomes

$ csvcut -c STATE,INCOME_AMT IRSdata.csv | csvgrep -c STATE -m ME | csvsort -c INCOME_AMT | csvlook | head 

Csvkit has sorted the data by INCOME-AMT from lowest to highest - this isn't very convienent so we are going to use the -r flag (reverse) to reverese the sorting order

$ csvcut -c STATE,INCOME_AMT IRSdata.csv | csvgrep -c STATE -m ME | csvsort -c INCOME_AMT -r | csvlook | head 

Now see if we can figure out which organisation in Maine has an income amount of over $2 billion

$ csvcut -c STATE,INCOME_AMT,NAME IRSdata.csv | csvgrep -c STATE -m ME |csvsort -c INCOME_AMT -r | csvlook | head 

Who is on top? If you are a local paper then maybe there are some surprising results here

##Finishing up

Today we only touched briefly on csvkit - while
used csvkit briefly in a bash shell you can combine it with python or SQL to build powerful queries and keep interrogating your data. 

Here are some other custom commands we didn't touch on:

* csvsql - Generates SQL statements for a csv or execute those statements directly on a database. In the latter case supports both creating tables and inserting data
* csvpy - Loads a CSV file into a csvkit.CSVKitReader object and then drops into a Python shell so the user can inspect the data however they see fit
* csvformat - Converts a csv to a custom output format
* csvjson - Converts a CSV file into JSON or GeoJSON 

##Resources

If you want to dig deep and get to know csvkit better then check out the great documentation and tutorial on readthedocs. 

* https://csvkit.readthedocs.org/en/0.9.1/tutorial.html
* https://source.opennews.org/en-US/articles/eleven-awesome-things-you-can-do-csvkit/


##Contact me

Email: karrie.anne.kehoe@gmail.com
Twitter: @karriekehoe

