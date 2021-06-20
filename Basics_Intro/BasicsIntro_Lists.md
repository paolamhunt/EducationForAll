# Python List
- List: ordered sequence of items
    - Items in the list DO NOT need to be the same type
    - Declaring a list
    	- Items separated by commas enclosed within brackets \[ \]
    - Example:
     ~~~
	    thisList = [1,1,2.2, 'python']
	~~~
    - Access list by referring to the index number or a range of items from a list
   
- Python List Methods

![List Methods.](/Basics_Intro/images/list_methods.png "List Methods")
	
- Lists are mutable: the value of a list can be altered

## PYTHON LIST METHODS EXAMPLES

- Change List Item Value
~~~
    thislist = [1, 1, 2.2, 'python']
    thislist[2] = "SQL'
    print(Thislist)
    ## [1, 1, "SQL", "python"]
~~~
	
- Add List Item Value
    - Use `append()` method to add item to end of list
    ~~~
    thisList = [1, 1, 2.2, "python"]
    thisList.append("SQL")
    print(thisList)
    ## [1, 1, 2.2, "SQL"]
    ~~~
		
    - Use: `insert()` method to add item at the specified index
    ~~~
    thisList = [1, 1, 2.2, "python"]
    thisList.insert(0, -5)   # insert item in the first position
    print(thisList)
    ## [-5, 1, 2.2, "python"]
    ~~~
	
    -  Remove List Item Value
   	 -  Use the `remove()` method to remove the specified item value directly
   	 	```
		thisList = [1, 1, 2.2, 'python']
		thisList.remove('python')
		print(thisList)
		## [1, 1, 2.2]
		```
		
    -  Use: `pop()` method to remove items
    	~~~
		thisList = [1, 1, 2.2, 'python']
		thisList.pop()  #  remove the last item
		print(thisList)
		## [1, 1, 2.2]
	
		thisList = [1, 1, 2.2, 'python']
		thisList.pop(0)  #  remove first item
		print(thisList)
		## [1, 2.2]
		~~~
	
		
    -  Use `Delete` method to delete items or lists
    	~~~
		thisList = [1, 1, 2.2, 'python']
		del thisList[3]  # remove fourth item
		print(thisList)
		##[1, 1, 2.2]

		del thisList # delete list completely
		print(thisList)
		~~~
		
    -  Sort List Item Values
   	-  The `sort()` method sorts list ascending by default. 
            - Parameter `reverse = True` will list descending (default = reverse=False)
         ~~~
		cars = ['Ford', 'BMW', 'Volvo']
		cars.sort()  # sort cars items ascending
		print(cars)
		## ['BMW', 'Ford', 'Volvo']
		
		cars = ['Ford', 'BMW', 'Volvo']
		cars.sort(reverse=True)  #sort cars items descending
		print(cars)
		## ['Volvo', 'Ford', 'BMW']
		~~~
		
    -  List `count()` Method
    	- Counts the number of elements with the specified value
    	 ~~~~
		thisList = [1, 4, 8, 4, 4, 5, 4, 6, 4]
		m = thisList.count(4)
		print(m)
		## 5
			~~~

    - Length of a List
     	-  Use `len()` method to determine how many items in a list
       ~~~
		 cars = ['Ford', 'BMW', 'Volvo']
		 print(len(cars))
		 ## 3
		 ~~~
		
**More List Methods [Here](https://www.w3schools.com/python/python_lists.asp)**
