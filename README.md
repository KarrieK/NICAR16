# Csvkit and other command line tools

We are going to look at how the python library csvkit can manipulate and analyse data from a bash shell

Csvkit is flexible, easy to use and powerful. We should all buy Christopher Groskopf a drink at the bar! 

We are also going some basic unix commands like pwd, cd, curl etc so you can learn how to navigate through a termainal.

If you want a more comprehensive list of unix tools, I'll have one up on github after the class

#Overview
We are going to use the following commands:

* pwd - print working directory 
* cd - change directory
* mkdir - make directory
* ls - list
* curl - grabs data from a url
* in2csv - converts a file into a csv
* csvlook - gives us a preview of our data
* csvcut - cutting too for manipulating csvs
* csvclean - cleans our csv for errors
* csvstat - gives us descriptive stats for the content of our csv
* csvsort - sorts the contents of a csv file
* csvgrep - regex command like a refined search function in our csv
* csvsql - enables us to connect to a sql database 

#Installation
Ideally you will be running a virtualenv or virtualbox running a linux based operating system.
If not, never fear csvkit should operate fine on a Mac OS. 
You need python 2.7 or 3.3 installed. 

You can install csvkit using the following commands, depending on what package manager you're using:

$ pip install csvkit

or 

$ conda install csv

or 

$ sudo apt-get install csvkit

# The set-up

The first thing we need to do is create a folder for your course materials and read some data into a terminal. 

To do that we are going to use a coupld of unix commands on the command line. 

* pwd - print working directory
* cd - change directory
* mkdir - make directory
* curl - grabs data from a url

Open up a terminal and type pwd - this tells you that you should be in your home directory

We want to create a new directory to store our data in. 

Type mkdir csvkit_class this will create a new file in your home directory

Now we need to enter that folder. Type cd csvkit_class and press enter

You can type pwd again to make sure you're in the right directory.

# Reading in data

Now we need to find some data and read it into the terminal. 

We are going to use the command curl which grabs data from urls

$ curl -L -O https://inventory.data.gov/dataset/67567804-073d-40ad-a710-2b0bed8b84e2/resource/e983b323-df6e-43f2-a78d-7af0a2dff997/download/nsnextract.xlsx

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








