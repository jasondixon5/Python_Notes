```
#! /usr/bin/env python3
# banfieldSearch.py - A program to search financial files in CSV format for a particular transaction (in this case, Banfield)

import os, csv, re

# TODO - At end, check indentation under function to confirm lines up right

# Build function to take Regex as argument
def csvSearch(term):    #Takes string input as argument!
    #if type != str:
     #   print("Please enter the term as a string, with quotes. You entered {}.".format(term))
    # I could use (term = str(term) but that wouldn't cover fail if no quotes entered with text
    
    searchTerm = re.compile(term, re.IGNORECASE)
    

# Find the files in the CWD, identify CSV files
    cwdFiles = os.listdir('.')
    # Removing - worked, but too many results: print('We will see if any of these files in the directory are in CSV format: {}'.format(cwdFiles))
    csvFiles = []
    for filename in cwdFiles:
        if filename.endswith('.csv'):
            csvFiles.append(filename) #Copy the name of the CSV file and put it in a list
    print('Found these CSV files that we will search: {}'.format(csvFiles))
# Loop over list of filenames in csvFiles
# Open first CSV file, search for the Regex
    foundFiles = []
    foundRows = []
    for filename in csvFiles:
        fileToSearch = open('{}'.format(filename))
        fileReader = csv.reader(fileToSearch)
        fileRows = list(fileReader) # Creates a list containing rows from file
        for row in range(len(fileRows)):
# Search for the Regex term
            mo = searchTerm.search(str(fileRows[row]))
            if mo:
                if mo.group() == term:
                    foundFiles.append(filename)
                    foundRows.append(fileRows[row])

# At end, return and display list of found CSV files/rows
    for filename in foundFiles:
        for row in foundRows:
            print(row, filename)
            #print('Found search term in file {} in row {}'.value(filename, row))####Got error "AttributeError: 'str' object has no attribute 'value'"
            #print('Found {} in file {} in row {}'.value(term, filename, row))
    if not foundFiles:
        print("No matches found in those files for {}!".format(term))
# TODO - Create new CSV file with found row and filename

csvSearch('Banfield')

"""
It's not finding the match for Amex_Mar 2016.csv but it is finding the match in csvTest - Sheet 1.csv
Output:
Jasons-MacBook-Air:~ jasondixon$ ./banfieldSearch.py 
Found these CSV files that we will search: ['Amex_Mar 2016.csv', 'amex_old_statements.csv', 'csvTest - Sheet1.csv', 'example.csv', 'new_example.csv']
['Banfield', '35'] csvTest - Sheet1.csv
"""
```
