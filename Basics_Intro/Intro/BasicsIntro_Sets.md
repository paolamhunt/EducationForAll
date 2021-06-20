# SET
- Unordered collection of unique items - index has no meaning, slicing operator does not work
- Defined by values separated by comma inside braces {}
- Eliminates duplicates
- Example:
~~~
	s = {1, 2, 2, 3, 3, 3, 'MU'}
	print(s)  #there are no duplicates
	## {1, 2, 3, 'MU'}
~~~
	
- Add Set Item
    - Once created, cannot change its items but can add new items
    - Use `add()` method
    - Example:
    ~~~
		s = {1, 2, 2, 3, 3, 3, 'MU'}
		s.add('DSCI 200')
		print(s)
		## {1, 2, 3, 'DSCI 200', 'MU'}
    ~~~
	
- Remove Set Item
    - Use `remove()` or `discard()` methods
    ~~~
		s = [1, 2, 2, 3, 3, 3, 'MU'}
		s.remove(2)  #removes the element 2
		print(s)
		## {1, 3, 'MU'}

		s.discard('MU')  #removes element 'MU'
		print(s)
		## {1, 3}
    ~~~
		
- Length of a Set
    - Use `len()` method to determine how many items a set has
    - Example:
    ~~~
		s = {1, 2, 2, 3, 3, 3, 'MU'} 
		print(len(s))  # the length is 4 not 7. Set elements have no duplication
		## 4 
    ~~~

		
**More about <u>SET</u> methods [here](https://www.w3schools.com/python/python_sets.asp)** :point_left: