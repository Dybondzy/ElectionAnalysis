# ElectionAnalysis
# Dinah---ElectionAnalysis
3rd Project on Boot Camp Exercise for Data Analystics

In this project, our final Python script will need to be able to deliver the following information when the script is run: 

Total number of votes cast
A complete list of candidates who received votes
Total number of votes each candidate received
Percentage of votes each candidate won
The winner of the election based on popular vote

To facilitate the design process, programmers use pseudocode to create models or flowcharts for their programs. Pseudocode is like a roadmap of what you think your code will look like or the steps you'll take to complete the task at hand.

Pseudo means "fake," so pseudocode is essentially fake code. Pseudocode is an informal language that has no syntax rules and is not meant to be executed. The point of using pseudocode is to focus on the overall design of the program.

For example, let's say someone asks you how to wash clothes. You might break down this task into a series of basic steps, like this:

Open the lid of the washing machine.
Put clothes in the washing machine.
Turn on the water.
Add detergent.
Close the lid.
These well-defined, logical steps that are sequentially ordered is an example of an algorithm.

Similarly, a programmer or analyst may write the steps to count the votes of an election like this:

Open the data file.
Write down the names of all the candidates.
Add a vote count for each candidate.
Get the total votes for each candidate.
Get the total votes cast for the election.


Launch VS Code and create a new file named PyPoll.py. Create a high-level list of the necessary steps given to you using pseudocode.

The election_results.csv file should be located in the Resources folder

Let's break down what is happening in the code above as it relates to the dependency "datetime". The datetime module comes with our Python installation.

To use the datetime module all we need to do is to import it using import datetime.
In line 4, we declare the now variable to hold the time right "now".
The now variable is set equal to datetime.datetime.now(), where:
The first datetime is the datetime module, (first doll).
The second datetime is the datetime class (second doll).
Then we use the datetime attribute, now(), (third doll) on the datetime class, i.e., datetime.now(), to get the current time.
When we run this code, the output will be the current time at the moment the code is run, and will look similar to the following: 

The time right now is 2019-09-18 14:11:42.394131
To reduce the confusion on importing a module with the same name as a class we can use an abbreviated alias dt for the datetime module.

# Import the datetime class from the datetime module.
import datetime as dt
# Use the now() attribute on the datetime class to get the present time.
now = dt.datetime.now()
# Print the present time.
print("The time right now is ", now)

To see all the functions available in the csv module, follow these steps:

Launch the Python interpreter.
Type import csv to import the module.
Press Enter.
Type dir(csv). The "dir" is short for "directory".

After providing the file path in our Python script, we will be able to open and read the file. When the program reads the file, it creates a file object in the computer's memory, which provides a way for the program to work with that file. In our script, we can use a variable to reference the file object.

The general format for opening a file is, file_variable = open(filename, mode).

Let's break down what each component is doing in the general format.

file_variable is the name of the variable that will reference the file object.
filename is a string specifying the name of the file.
mode is a string specifying the mode for reading or writing the file object. The possible modes are:
"r": Open a file to be read.
"w": Open a file to write to it. This will overwrite an existing file and create a file if one does not already exist.
"x": Open a file for exclusive creation. If the file does not exist, it will not create one.
"a": Open a file to append data to an existing file. If a file does not exist, it creates one, if a file has been created the data will be added to the file.
"+": Open a file for reading and writing.
Now that we know how to open a file, we need to open our election_results.csv file and read the data in the file.

Inside the parentheses of the join() function, we will add the folder and file to join together. In this case, we'll add the Resources folder and election_results.csv separated by a comma, like this:

os.path.join("Resources", "election_results.csv")

Then, we use a filename variable to reference the path to election_data.csv, like this:

file_to_load = os.path.join("Resources", "election_results.csv")

Let's put all of this to practical use! In the VS Code PyPoll.py file, complete the following steps:

Import the csv and os modules.
Add the filename variable that references the path to election_results.csv.
Open the election_results.csv using the with statement as the filename object, election_data.
Print the filename object.
Your PyPoll.py file should look like this:

import csv
import os
# Assign a variable for the file to load and the path.
file_to_load = os.path.join("Resources", "election_results.csv")
# Open the election results and read the file.
with open(file_to_load) as election_data:

    # Print the file object.
     print(election_data)
When we run this file in the VS Code terminal, the output is similar to when we used the direct path for the file variable:

<open file 'Resources/election_results.csv', mode 'r' at 0x10479c780>

Open election_analysis.txt and you'll see that it's empty. As we perform the election analysis, we'll write data to this file. For now, let's practice adding some simple data to this file and saving it in the "analysis" folder.

In election_analysis.txt add "Hello World" to the first line by adding the following code to PyPoll.py and running the file in VS Code.

# Create a filename variable to a direct or indirect path to the file.
file_to_save = os.path.join("analysis", "election_analysis.txt")

# Using the with statement open the file as a text file.
outfile = open(file_to_save, "w")
# Write some data to the file.
outfile.write("Hello World")

# Close the file
outfile.close()
Here's what's happening in this code:

After we create the file_to_save variable, we set the open(file_to_save, "w") to a filename variable, outfile.
Then, we use the filename variable to write "Hello World" to the file using the write() function from the os module.
Lastly, we use outfile.close() to close the file.
When we execute this file and open election_analysis.txt, we see the string Hello World in the first line.

Now it's time to read the election_results.csv file. As a reminder, the code in our PyPoll.py file should look similar to this code: 

# Add our dependencies.
import csv
import os
# Assign a variable to load a file from a path.
file_to_load = os.path.join("Resources", "election_results.csv")
# Assign a variable to save the file to a path.
file_to_save = os.path.join("analysis", "election_analysis.txt")

# Open the election results and read the file.
with open(file_to_load) as election_data:

    # To do: read and analyze the data here.
Next, we'll use the reader function to read election_data.csv.

While this output was being generated, two things happened:

We did not see the headers or columns printed because the output was generated very quickly.
Each row in the CSV file was printed out as a list.

At this point, PyPoll.py should look like this:

# Add our dependencies.
import csv
import os
# Assign a variable to load a file from a path.
file_to_load = os.path.join("Resources", "election_results.csv")
# Assign a variable to save the file to a path.
file_to_save = os.path.join("analysis", "election_analysis.txt")

# Open the election results and read the file.
with open(file_to_load) as election_data:
    file_reader = csv.reader(election_data)

    # Read and print the header row.
    headers = next(file_reader)
    print(headers)
    
    code to GitHub. Committing early and often is the best practice to save your work on projects. Plus, Seth and Tom said they might look over your work before tomorrow, so you'll want to update your repository and email them the link, if you have not done so yet.
Save PyPoll.py to the Election_Analysis folder. To commit your code to your GitHub repository, follow the steps associated with your operating system.

Check out the macOS instructions below, or jump to the Windows instructions.

