From http://caisbalderas.com/blog/iterating-with-python-lambdas/

In order to understand advanced applications of lambda, it is best to start by showing a process in a simple loop. Here we are multiplying every number in x by 5 and adding that value the the list y

```
x = [2, 3, 4, 5, 6]
y = []
for v in x :
    y += [v * 5]
assert x == [ 2,  3,  4,  5,  6]
assert y == [10, 15, 20, 25, 30]
```
Simple enough right? Now lets try and recreate that process using a list comprehension.
```
x = [2, 3, 4, 5, 6]
y = [v * 5 for v in x]    
```
Taking it a step further, we can do the same thing using the popular combination of lambda and map().
```
x = [2, 3, 4, 5, 6]
y = map(lambda v : v * 5, x)
```
Don't be afraid of map(), it takes in a function (our lamda function) and an iterable (x) and then returns another iterable.
Now, take a step back to look at both the list comprehension and lambda/map() combination. You'll see that the difference between the two is just a simple rearrangement of statements and removal of "for" and "in".
```
[v * 5 for v in x] --> map(lambda for v: v * 5, in x) -->  map(lambda v : v * 5, x)
```
A slightly more difficult example.
The for loop representation is straightforward; iterate over x, multiply the odd values by 5 and add them to the list y.

```
x = [2, 3, 4, 5, 6]
y = []
for v in x :
    if v % 2 :
        y += [v * 5]
assert x == [2, 3, 4, 5, 6]
assert y == [15, 25]
```
list comprehension of the same process done in loop...

```
x = [2, 3, 4, 5, 6]
y = [v * 5 for v in x if v % 2]
```
Now we have included filter() along with map() and lambda in order to produce the same results as our loop and list comprehension.

```
x = [2, 3, 4, 5, 6]
y = map(lambda v : v * 5, filter(lambda u : u % 2, x))
```
filter() takes in a function(lambda) and iterable(x) and returns an iterable containing "filtered" values that passed through the function.

filter(function, iterable) --> [item for item in iterable if function(item)]
Again, lets compare to our list comprehension to see that our combination of map()/filter()/lambda is simpler than it looks!

```
[v * 5 for v in x if v % 2]  #list comprehension
map(lambda for v: v * 5, for filter(lambda for v: if v % 2, in x)) #"pseudo" lambda and list comprehension
map(lambda v : v * 5, filter(lambda u : u % 2, x)) #lambda, just a 'rearrangement' of what we had before
```
Going all the way.
Going deeper, our loops iterate through x, iterate through y, and adds the sum of the values to z.

```
x = [2, 3, 4]
y = [4, 5]
z = []
for v in x :
    for w in y :
        z += [v + w]
assert x == [2, 3, 4]
assert y == [4, 5]
assert z == [2+4, 2+5, 3+4, 3+5, 4+4, 4+5]
assert z == [6, 7, 7, 8, 8, 9]
```
Now with a list comprehension...

```
x = [2, 3, 4]
y = [4, 5]
z = [v + w for v in x for w in y]
```
And finally with lamdas....

```
x = [2, 3, 4]
y = [4, 5]
t = map(lambda v : map(lambda w : v + w, y), x)
assert t == [[6, 7], [7, 8], [8, 9]]
z = sum(t, [])
```
But wait! Now we are playing with two maps, lets take a closer look and see how our list comprehension was "rearranged" to create this lambda.

```
[v + w for v in x for w in y]                              #list comprehension
map(lambda for v: in map(lambda for w: v + w, in y), in x) #"pseudo" lambda
map(lambda v : map(lambda w : v + w, y), x)                #lambda    
```
now, you might have noticed that we do not end up with what we wanted. t is list of lists! A quick use of the sum() function and ta-da! We've got what we wanted.

 
```
assert t == [[6, 7], [7, 8], [8, 9]]
z = sum(t, [])
assert z == [2+4, 2+5, 3+4, 3+5, 4+4, 4+5]
assert z == [6, 7, 7, 8, 8, 9]
```
