# DICTIONARY

- Unordered collection of key-value pairs
- Used with large amounts of data
- Optimized for retrieving data
- Must know key to retrieve value
- Example:
~~~
	d = {'Class' : 'DSCI 200', 'Type' : 'Online', 'Weeks' : 8 }  
    # dictionary keys: Class, Type, Weeks. The correspoinding values: DSCI 200, Online, 8
	print(d['Class'])  # get the value of the key 'class'
	##  DSCI 200
~~~
	
## Change Dictionary Item Value
- Change value of specific item by reffering to its key name
- Example:
~~~
	d = {'Class':'DSCI 200', 'Type':'Online', 'Weeks':8 } 
	d['Class'] = 'MATH 372'
	print(d) 
    ## {'Class': 'MATH 372', 'Type': 'Online', 'Weeks': 8}
~~~
	
## Add Dictionary Item Value
- Add by using new index key and assign a value to it
- Example:
~~~
	d = {'Class':'DSCI 200', 'Type':'Online', 'Weeks':8 } 
	d['Semester']='Fall'
	print(d) 
    ## {'Class': 'DSCI 200', 'Type': 'Online', 'Weeks': 8, 'Semester': 'Fall'}
~~~
	
## Remove Dictionary Item Value
- To remove items, use `pop()` or `del`
- Example: 
~~~
	d = {'Class':'DSCI 200', 'Type':'Online', 'Weeks':8 } 
	d.pop('Weeks') #delete the tkey 'Weeks' and its value of 8
	print(d) 
    ## {'Class': 'DSCI 200', 'Type': 'Online'}
~~~

## Length of a Dictionary
- Determines how many items (key-value pairs) in a dictionary
- Use `len()` method
- Example:
~~~
	d = {'Class':'DSCI 200', 'Type':'Online', 'Weeks':8 } 
	print(len(d))
    ## 3
~~~

**Read more about <u>dictionary</u> methods [here](https://www.w3schools.com/python/python_dictionaries.asp)** :point_left: