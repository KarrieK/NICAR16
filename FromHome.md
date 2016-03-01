#Csvkit on your own machine

If you're installing this library onto your own linux, OSX or virtual machine then here are some instructions to help get you going. 

For those of you who would like to install and run csvkit on their own machines, you can install it easily for linux or OSX operating systems. 

If you run windows, never fear, you can install virtual box and run a linux enviroment from there. 

#Getting going

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

Open a terminal and type _pwd_ to make sure you're in your home directory

Now we need to make a new folder to contain our work - type _mkdir csvkit_
The next move is to navigate into the folder, to do this we use _cd_ which lets us change directory

$ _cd csvkit_

To check the folder is empty we type _ls_ this checks the contents of a folder. 

If you want to grab your data from here you can use _Curl_

$ _curl -L -0 *your url*_

This will load your data into the terminal. From here you can follow the rest of the instructions from the class.
