#Csvkit on your own machine

If you're installing this library onto your own linux, OSX or virtual machine then here are some instructions to help get you going. 

For those of you who would like to install and run csvkit on their own machines, you can install it easily for linux or OSX operating systems. 

If you run windows, never fear, you can install virtual box and run a linux enviroment from there. 

##Getting going

You need python 2.7 or 3.3 installed. 

You can install csvkit using the following commands, depending on what package manager you're using:

$ pip install csvkit

or 

$ conda install csv

or 

$ sudo apt-get install csvkit

If you have any problms check out csvkit's documentation at https://csvkit.readthedocs.org/en/0.9.1/install.html

#Unix commands and reading in data

So unlike python anywhere you need to be able to make folders on the command line

Open a terminal and type pwd to make sure you're in your home directory

Now we need to make a new folder to contain our work - type:
$ mkdir csvkit

The next move is to navigate into the folder, to do this we use _cd_ which lets us change directory

$ cd csvkit

To check the folder is empty we type ls this checks the contents of a folder. 

If you want to grab your data from here you can use Curl

$ We are going to use the command curl which grabs data from urls

$ curl -L -O https://inventory.data.gov/dataset/67567804-073d-40ad-a710-2b0bed8b84e2/resource/e983b323-df6e-43f2-a78d-7af0a2dff997/download/nsnextract.xlsx

This will load your data into the terminal. From here you can follow the rest of the instructions from the class.
