## reduce( )
Reduce was removed from Python 3 core library.
It's now in the functools module.

## map( )

* In Python 2 map( ) returns a list.
* In Python 3 map( ) returns an iterator.

In Python3, wrap the map( ) statement in a list( ) call to make it mimic the behavior of Python 2. 
That's what conversion tools like 2to3 do.

```
Python 2.7.10 (default, Oct 23 2015, 18:05:06) 
[GCC 4.2.1 Compatible Apple LLVM 7.0.0 (clang-700.0.59.5)] on darwin
Type "help", "copyright", "credits" or "license" for more information.
>>> Celsius = [39.2, 36.5, 37.3, 37.8]
>>> Fahrenheit = map(lambda x: (float(9)/5)*x + 32, Celsius)
>>> print Fahrenheit
[102.56, 97.7, 99.14, 100.03999999999999]
>>> Fahrenheit
[102.56, 97.7, 99.14, 100.03999999999999]
>>> type(Fahrenheit)
<type 'list'>
```
```
Python 3.5.1 (v3.5.1:37a07cee5969, Dec  5 2015, 21:12:44) 
[GCC 4.2.1 (Apple Inc. build 5666) (dot 3)] on darwin
Type "help", "copyright", "credits" or "license" for more information.
>>> Celsius = [39.2, 36.5, 37.3, 37.8]
>>> Fahrenheit = map(lambda x: (float(9)/5)*x + 32, Celsius)
>>> print(Fahrenheit)
<map object at 0x1010e6c50>
>>> for x in Fahrenheit: print(x)
... 
102.56
97.7
99.14
100.03999999999999
>>> Fahrenheit
<map object at 0x1010e6c50>
>>> C = map(lambda x: (float(5)/9)*(x-32), Fahrenheit)
>>> for x in C: print(x)
... 
>>> Fahrenheit = map(lambda x: (float(9)/5)*x + 32, Celsius)
>>> C = map(lambda x: (float(5)/9)*(x-32), Fahrenheit)
>>> for x in C: print(x)
... 
39.2
36.5
37.300000000000004
37.8
```
```
Python 3.5.1 (v3.5.1:37a07cee5969, Dec  5 2015, 21:12:44) 
[GCC 4.2.1 (Apple Inc. build 5666) (dot 3)] on darwin
Type "help", "copyright", "credits" or "license" for more information.
>>> Celsius = [39.2, 36.5, 37.3, 37.8]
>>> Fahrenheit = list(map(lambda x: (float(9)/5)*x + 32, Celsius))
>>> print(Fahrenheit)
[102.56, 97.7, 99.14, 100.03999999999999]
>>> Fahrenheit
[102.56, 97.7, 99.14, 100.03999999999999]
>>> type(Fahrenheit)
<class 'list'>
```

References: 
* http://python3porting.com/differences.html 
* http://www.python-course.eu/lambda.php

## print( )

* In Python 2 `print variable` prints the variable.
* In Python 3 the print call requires parentheses: `print(variable)`
