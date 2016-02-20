Given an array of ints, return True if the array contains a 2 next to a 2 somewhere. 

* has22([1, 2, 2]) → True
* has22([1, 2, 1, 2]) → False
* has22([2, 1, 2]) → False

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
