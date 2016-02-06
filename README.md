# Csvkit and other command line tools

During this class we are going to look at how the python library csvkit can manipulate and analyse data

We are also going to cover curl and xxxx

#Overview
We are going to use the following commands:

- pwd
- cd
- mkdir
- curl
- in2csv
- csvlook
- csvcut
- csvclean
- csvstat
- csvsort
- csvgrep
- csvsql

#Installation
Ideally you will be running a virtualenv or virtualbox running a linux based operating system.
If not, never fear csvkit should operate fine on a Mac OS. 
You need python 2.7 or 3.3 installed. 

You can install csvkit using the following commands:

pip install csvkit

or 

sudo apt-get install csvkit

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

# Readig in data

Now we need to find some data and read it into the terminal. 

We are going to use the command curl which grabs data from urls

curl -L -O https://inventory.data.gov/dataset/67567804-073d-40ad-a710-2b0bed8b84e2/resource/e983b323-df6e-43f2-a78d-7af0a2dff997/download/nsnextract.xlsx

To make sure that we have been succesful grabbing the data type - ls and it should list the file

#Looking at our data




