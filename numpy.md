
Adapted from: Intro to Python For Data Science, Chapter 4 - NumPy 

Source: https://www.datacamp.com/courses/intro-to-python-for-data-science


```
import numpy as np
```
Use np.array() to create a Numpy array from a Python collection like a list.

Do operations on Numpy arrays that are harder to do with two or more lists.

For example:
```
>>> import numpy as np
>>> baseball = [180, 215, 210, 210, 188, 176, 209, 200]
>>> np_height = np.array(baseball)
>>> np_height_m = np_height * 0.0254
>>> np_height
array([180, 215, 210, 210, 188, 176, 209, 200])
>>> np_height_m
array([ 4.572 ,  5.461 ,  5.334 ,  5.334 ,  4.7752,  4.4704,  5.3086,  5.08  ])
```
Index and slice items in a Numpy array:
```
>>> np_height
array([180, 215, 210, 210, 188, 176, 209, 200])
>>> np_height[3]
210
>>> np_height[2:4]
array([210, 210])
```
Perform greater than and less than finds.
(Presumably this could also work for range and find functions.)
Note that these finds require an intermediate step that results in a list of Booleans for each item in the array.

```
>>> np_height_m
array([ 4.572 ,  5.461 ,  5.334 ,  5.334 ,  4.7752,  4.4704,  5.3086,  5.08  ])
>>> tall = np_height_m > 5
>>> tall
array([False,  True,  True,  True, False, False,  True,  True], dtype=bool)
>>> np_height_m[tall]
array([ 5.461 ,  5.334 ,  5.334 ,  5.3086,  5.08  ])
```
##Multi-Dimensional Arrays

Create 2- or more dimensional arrays.
2D arrays are like tables of rows and columns.
The following list creates an entry for each player. The player's weight (in lbs) and height (in inches) are given.
The list is then converted to a 2D array.

```
>>> baseball_2D = [[180, 78.4],
...             [215, 102.7],
...             [210, 98.5],
...             [188, 75.2]]
>>> 
>>> baseball_2D
[[180, 78.4], [215, 102.7], [210, 98.5], [188, 75.2]]
>> np_baseball_2D = np.array(baseball_2D)
>>> np_baseball_2D
array([[ 180. ,   78.4],
       [ 215. ,  102.7],
       [ 210. ,   98.5],
       [ 188. ,   75.2]])
``` 
 The "shape" attribute shows the dimensions of the array.
 ```
 >>> np_baseball_2D.shape
(4, 2)
```
Index and slice items in a 2D array similar to how a list of lists is sliced in Python.
```
# regular list of lists
x = [["a", "b"], ["c", "d"]]
[x[0][0], x[1][0]]

# numpy
import numpy as np
np_x = np.array(x)
np_x[:,0]
```
Perform arithmetic on arrays.
```
import numpy as np
np_mat = np.array([[1, 2],
                   [3, 4],
                   [5, 6]])
np_mat * 2
np_mat + np.array([10, 10])
np_mat + np_mat
```

NumPy has built-in statistics functions.
Use them on Python collections like lists or on NumPy arrays.

```
import numpy as np
x = [1, 4, 8, 10, 12]
np.mean(x)
np.median(x)
np.std(x)
np.corrcoef(x)
np.corrcoef(x, y)
```
Regarding coefficient (from NumPy documenation):

Format:
numpy.corrcoef(x, y=None, rowvar=1)

Parameters:	
x : array_like
A 1-D or 2-D array containing multiple variables and observations. 
Each row of x represents a variable, and each column a single observation of all those variables. 
Also see rowvar below.

y : array_like, optional
An additional set of variables and observations. 
y has the same shape as x.

rowvar : int, optional
If rowvar is non-zero (default), then each row represents a variable, with observations in the columns. 
Otherwise, the relationship is transposed: each column represents a variable, while the rows contain observations.

Sample Exercise from DataCamp:
```
# Exercise to prove that in soccer goalkeepers are taller than other players, on average.

# heights and positions are available as lists of following format:
# positions = ['GK', 'M', 'A', 'D', ...]
# heights = [191, 184, 185, 180, ...]

import numpy as np

# Convert positions and heights to numpy arrays: np_positions, np_heights
np_positions = np.array(positions)
np_heights = np.array(heights)

# Heights of the goalkeepers: gk_heights
gk_heights = np_heights[np_positions == 'GK']

# Heights of the other players: other_heights
other_heights = np_heights[np_positions != 'GK']

# Print out the median height of goalkeepers. Replace 'None'
print("Median height of goalkeepers: " + str(np.median(gk_heights)))

# Print out the median height of other players. Replace 'None'
print("Median height of other players: " + str(np.median(other_heights)))
```
