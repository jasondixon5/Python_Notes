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



