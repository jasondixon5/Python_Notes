Return the sum of the numbers in the array, returning 0 for an empty array. Except the number 13 is very unlucky, so it does not count and numbers that come immediately after a 13 also do not count. 

* sum13([1, 2, 2, 1]) → 6
* sum13([1, 1]) → 2
* sum13([1, 2, 2, 1, 13]) → 6

```
def sum13(nums):
  sum_nums = 0
  if nums == []:
    return 0
  else:
    for num in nums:
      if num == 13:
        offset13 = nums.index(num)
        nums.remove(num)
        
        break
      sum_nums += num
    return sum_nums
```
