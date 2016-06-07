## Functions

### Arguments

   - Positional
   - Keyword
   - Default

Note: Default argument values are calculated when function is defined, not when it is run. So a list or dictionary does not make a good default argument. Instead, declare the empty list/dictionary within the function definition.

Multiple position: gather with *
>When used inside the function with a parameter, an asterisk groups a variable number of positional arguments into a tuple of parameter values. If your function has required positional arguments as well, *args goes at the end and grabs all the rest.

Multiple keyword: gather with **
>Use two asterisks to group keyword arguments into a dictionary, where the argument names are the keys and their values are the corresponding values.

>If you mix positional parameters with *args and **kwargs, they need to occur in that order.

Calling the tuple parameter args and the dictionary parameter kwargs is a common idiom in Python but is not mandatory.

### Docstrings

To access, call the Python's help() function with the name of the function as the argument.
Or, to see the raw version, call `print(function.__doc__)`, e.g., `print(echo.__doc__)` if 'echo' were the name of a function.

Source: Introducing Python: Modern Computing in Simple Packages, Bill Lubanovic

### Exiting a Function
You "return" from a function. Once you return something you exit the function.
Return is always about returning from the function.
Return means "I'm done in this function and here's the value I'm giving back."
This includes stopping iteration if that is going on.

At the end of a function, you can return True or False (rather than returning a variable or other value).
e.g.,
```
def has22(nums):
    
    First2Found = False
    
    for x in nums:
        if x == 2 and First2Found:
            return True
        elif x == 2 and not First2Found:
            First2Found = True
        elif x != 2:
            First2Found = False
    
    return False
```
The "exit condition" in the first if statement returns True and exits both the loop & the function.
At the end, need to return something. If you returned the variable "First2Found" it would return True if 2 were the last value in the series, even if there were no 2's after or before it.
So you can just return False so you're saying, if the exit/True condition wasn't met then it returns False.

## Referring to Files

Command Repetoire
```
import os
os.path.join('string', 'string', 'string')
os.path.abspath('path')
os.path.isabs('path')
os.path.relpath('path', 'start') #'start' path is optional
os.path.dirname('path') #file or folder - returns string of pathname up to the last slash in the path argument
os.path.basename('path') #file or folder - returns string of everything after the last slash in the path argument
os.path.split('path') #works like using .dirname and .basename together; recommend using variable for filename/path 
os.path.sep #variable automatically set to '/' or '\' based on computer running program
'string'.split # plain old string split method; replace 'string' with filename (with path) or variable
os.path.exists('path')
os.path.isfile('path')
os.path.isdir('path')
os.makedirs('path') # Will create intermediate folders to build the new structure specified.
os.getcwd()
os.chdir('new dir') #new dir as string
os.path.getsize('path') #returns size in bytes of file in 'path' argument
os.listdir('path') #like 'ls' but returns a list
```
Files and Filenames

Pass string of individual file and folder names in your path.
Returns string with file path using correct path separators (\ for Windows, / for OS X and Linus)
```
import os
os.path.join()
```
```
>>> import os
>>> os.path.join('usr', 'bin', 'spam')
'usr/bin/spam'
```
Note that in Windows, the command would have returned:
```
'usr\\bin\\spam'
```
In Windows, backslashes have to be escaped with a second backslash character.

Pass a list of string filenames and the root path and you can create valid full filename with path:
```
>>> alFiles = ['accounts.txt', 'details.csv', 'invite.docx']
>>> for filename in alFiles:
...     print(os.path.join('/users/jasondixon', filename))
/users/jasondixon/accounts.txt
/users/jasondixon/details.csv
/users/jasondixon/invite.docx
```
Absolute and Relative Paths
```
>>> os.getcwd()
'/Users/jasondixon/Downloads'
>>> os.path.abspath('.')
'/Users/jasondixon/Downloads'
>>> os.path.abspath('..')
'/Users/jasondixon'
>>> os.path.isabs('.')
False
>>> os.path.isabs(os.path.abspath('.'))
True
```
```
>>> os.getcwd()
'/Users/jasondixon/Downloads'
>>> os.path.dirname('/Users/jasondixon/Downloads')
'/Users/jasondixon'
>>> os.path.basename('/Users/jasondixon/Downloads')
'Downloads'
>>> os.path.dirname('/Users/jasondixon/Downloads/Budget - 2015-09.xlsx')
'/Users/jasondixon/Downloads'
>>> os.path.basename('/Users/jasondixon/Downloads/Budget - 2015-09.xlsx')
'Budget - 2015-09.xlsx'
```
```
>>> os.path.abspath('./Budget - 2015-09.xlsx')
'/Users/jasondixon/Downloads/Budget - 2015-09.xlsx'
>>> budgetFile = '/Users/jasondixon/Downloads/Budget - 2015-09.xlsx'
>>> (os.path.dirname(budgetFile), os.path.basename(budgetFile)) #() to put results in a tuple
('/Users/jasondixon/Downloads', 'Budget - 2015-09.xlsx')
>>> os.path.split(budgetFile)
('/Users/jasondixon/Downloads', 'Budget - 2015-09.xlsx') #result of os.path.split is a tuple of two strings
```
```
>>> os.path.sep
'/'
>>> budgetFile.split(os.path.sep)
['', 'Users', 'jasondixon', 'Downloads', 'Budget - 2015-09.xlsx']
```
Command-Line Commands
```
>>>import os
>>>os.getcwd()
'C:\\Python34'
>>>os.chdir('C:\\Windows\\System32')
>>>os.getcwd()
'C:\\Windows\\System32'
```
```
>>> os.getcwd()
'/Users/jasondixon'
>>> os.chdir('/Users/jasondixon/Documents')
>>> os.getcwd()
'/Users/jasondixon/Documents'
```
```
>>> os.getcwd()
'/Users/jasondixon/Documents'
>>> os.chdir('..')
>>> os.getcwd()
'/Users/jasondixon'
>>> os.chdir('./Downloads')
>>> os.getcwd()
'/Users/jasondixon/Downloads'
```
Reading and Writing Files

1.  Call the `open()` method to return a File object.
2.  Call the `read()` or `write()` method on the File object.
3.  Call the `close()` method on the File object to close the file.

Command Repetoire
```
variable = open('path/filename.txt') #can use relative or absolute path; opens in read mode by default
variable = open('path/filename.txt', 'r') #explicitly open in read mode
variable = open('path/filename.txt', 'w') #creates file (if doesn't exist) or overwrites (if exists)
variable = open('path/filename.txt', 'a') #creates file (if doesn't exist) or appends to end (if exists)
variable.close()
variable.read()
variable.readlines()
```
Use shelve Module to Save Data
```
import shelve
variable = shelve.open('filename')
variable.close()
```
```
>>>import shelve
>>>shelfFile = shelve.open('mydata')
>>>cats = ['Zophie', 'Pooka', 'Simon']
>>>shelfFile['cats'] = cats
>>>shelfFile.close()
```
Call shelve.open() and pass it a filename, then store returned shelf value in a variable. Make changes to shelf value as if it were a dictionary. When done, call close() on the shelf value. Above, our shelf value is stored in shelfFile. We created a list, cats, and write shelfFile['cats'] = cats to store the list in shelfFile as a value associated with the key 'cats' (like in a dictionary). Then we call close() on shelfFile.

Shelf values have keys() and values() methods, just like dictionaries, that will return list-like values of the keys and values in the shelf. They are not true lists, so you should pass them to the list() function to get them in list form.

The code run above will cause new files to be created: mydata.db in OSX and mydata.bak, mydata.dat, mydata.dir in Windows.
Your programs can use the shelve module to later reopen and retrieve data from these shelf files. Shelf values don't have to be opened in read or write mode--they can do both once opened.


##Excel Files

Import module to begin working with Excel files  
Load workbook

```
import openpyxl
wb = openpyxl.load_workbook('example.xlsx')     #Takes in filename, returns Workbook object that represents Excel file
#                                           #Filename should be in cwd; if needed import os, os.getcwd(), os.chdir()
```
Get information about sheets and cells
```
wb.get_sheet_names()        #Typical workbook would return ['Sheet1', 'Sheet2', 'Sheet3']
workingSheet = wb.get_sheet_by_name('Sheet3')       #To work with Sheet3 specifically; returns Worksheet object
workingSheet.title      #returns 'Sheet3'
anotherSheet = wb.active        #returns active worksheet
workingSheet['A1']      #returns cell object representing cell A1
workingSheet['A1'].value        #returns value of that cell; will return dates in datetime.datetime() format
anotherCell = workingSheet['B1']        #returns cell object for that cell and stores in variable
anotherCell.value       #obtains that cell object/variable's value

>>>cB1 = activeSheet['B1']
>>>'{}, {}, {}'.format(cB1.coordinate, cB1.row, cB1.column)
'B1, 1, B'
>>> activeSheet.cell(row=1, column=2)
<Cell Sheet1.B1>
>>> activeSheet.cell(row=1, column=2).value
'Apples'

activeSheet.columns[1] #columns attribute of worksheet object returns cell objects for that column
#can then iterate over cells in that column, e.g.,:
for cellObj in activeSheet.columns[1]:
    print(cellObj.value)
#******Note about above attribute - unlike using references with cells this uses 0 as 1st column, 1 as 2nd column, etc.
#This is the case because the attribute returns a tuple of tuples, with each of the inner tuples containing the Cell objects in that column. The same happens for the .rows[n] attribute.
```
Review of steps to access Excel data:  
1. Import the openpyxl module.  
2. Call the openpyxl.load_workbook() function.  
3. Get a Workbook object.  
4. Call the get_active_sheet() or get_sheet_by_name() workbook method.  
5. Get a Worksheet object.  
6. Use indexing or the cell() sheet method with row and column keyword arguments.  
7. Get a Cell object.  
8. Read the Cell object's value attribute.  

##CSV Files

Review of steps to read CSV files:  
1. import csv  
2. open file, pass as variable  
3. create reader object with csv.reader (instead of read() or readlines() as you would a File object returned by open())  
4. access values in reader object  
5. take action (iterate, etc.)  

Can pass values to list via list() method and store result in variable. This will result in a list of lists (a list containing sublist of the contents of each row)

Can access list of lists via variable[x][y] where x = row (index position of sublist) and y = col (index position of value in sublist)  

```
import csv
exampleFile = open('example.csv')
exampleReader = csv.reader(exampleFile)
for row in exampleReader:
    print(row)
```



