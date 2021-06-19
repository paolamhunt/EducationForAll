# Python List
- List: ordered sequence of items
    - Items in the lst DO NOT need to be the same type
    - Declaring a list:
        - Items separated by commas enclosed within brackets [ ]
    - Example:
	    '''thisList - [1,1,2.2, 'python']'''
    - Access list by referring to the index number or a range of items from a list
- Python List Methods
![List Methods.](/Basics_Intro/images/list_methods.png "List Methods")
    - Lists are mutable: the value of a list can be altered

## PYTHON LIST METHODS EXAMPLES

- Change List Item Value

    Thislist = [1, 1, 2.2, 'python']
	Thislist[2] ="SQL'
	Print (Thislist)
	\\## [1,1,"SQL", "python]
	
- Add List Item Value
    - Use append() method to add item to end of list
		thisList = [1, 1, 2.2, "python"]
		thisList.append("SQL")
		Print (thisList)
		\\## [1, 1, 2.2, "SQL"]
		
    - Use: insert() method to add item at the specified index
		thisList = [1, 1, 2.2, "python"]
		thisList.insert(0, -5)   # insert n item in the first position
		Print (thisList)
		\\## [-5, 1, 2.2, "python"]
		
    -  Remove List Item Value
        - Use: 'remove()' method to remove the specified item value directly
		thisList = [1, 1, 2.2, 'python']
		thisList.remove('python')
		Print (thisList)
		\\## [1, 1, 2.2]
		
    -  Use: pop() method to remove items
		thisList = [1, 1, 2.2, 'python']
		thisList.pop()  #  remove the last item
		Print (thisList)
		## [1, 1, 2.2]
		
		thisList = [1, 1, 2.2, 'python']
		thisList.pop(0)  #  remove first item
		Print (thisList)
		\\## [1, 2.2]
		
    -  Use Delete method to delete items or lists
		thisList = [1, 1, 2.2, 'python']
		Del thisList[3]  # remove fourth item
		Print (thisList)
		\\## [1, 1, 2.2]
		
		Del thisList # delete list completely
		\\## print (thisList)
		
    -  Sort List Item Values
        - Sort() method sorts list ascending by default. 
            - Parameter reverse=True will list descending (default = reverse=False)
		Cars = ['Ford', 'BMW', 'Volvo']
		Cars.sort()  # sort cars items ascending
		Print (Cars)
		\\## ['BMW', 'Ford', 'Volvo']
		
		Cars = ['Ford', 'BMW', 'Volvo']
		Cars.sort(reverse=True)  #sort cars items descending
		Print (Cars)
		\\## ['Volvo', 'Ford', 'BMW']
		
    -  List Count() Method
       -  Counts the number od elements with the specified value
		    thisList = [1, 4, 8, 4, 4, 5, 4, 6, 4]
		    M = thisList.count(4)
		    Print(M)
		    \\## 5

    - Length of a List
       -  Use len() method to determine how many items in a list
		    Cars = ['Ford', 'BMW', 'Volvo']
		    Print(len(Cars))
		    \\## 3
		
		**More List Methods [Here](https://www.w3schools.com/python/python_lists.asp)**
