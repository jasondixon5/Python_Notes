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
```
