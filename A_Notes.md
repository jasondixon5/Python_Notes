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
