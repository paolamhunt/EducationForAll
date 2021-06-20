# TUPLE
- Ordered sequence of items same as a list but cannot be modified once created
- Used to write-protect data and are usually faster than list as it doesn't change dynamically
- Defined within parentheses () where items are separated by commas
- Example:
~~~
    T = (5, 'program, 1+3j)
~~~
	
- Length of a Tuple
    - Use `len()` method to determine how many items in a tuple
    ~~~
		t = (5, 'program', 1+3j)
		print(len(t))
		## 3
    ~~~
- Tuple =  read-only, cannot change any values
