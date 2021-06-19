# STRINGS AND SUBSTRING

- **Strings**
    -Create them by enclosing characters in quotes
		"='
    - Creating strings as simple as assigning value to variable
- **Substrings**
    - To access, use [ ] for slicing along with the index or indices to obtain substring
    - Index starts from 0
    
Example:
~~~
a = 'Hello, World!'
print(a[1]) 
#Get the character at position 1 (remember that the first character has the position 0)
## e

a = 'Hello, World!'
print(a[2:5])
#Get the characters from position 2 to position 5 (not included)
## llo

a = 'Hello, World!'
print(a[2:])
#Get the characters from position 2 to the end
## llo, World!

a = 'Hello, World!'
print(a[:2])
#Get the characters from the beginning to position 2 ((not included)
## He
~~~

## Methods of Strings; Multiline Strings; Conversion

- **Methods of Strings**
	- Python has set of built-in methods for use:
		- `len(string_name)`: returns the length of a string
		- `lower()`: returns the string in lower case
		- `upper()`: returns the string in upper case
		- `replace()`: replaces a string with another string
		- `split(‘,’)`: splits the string into substrings if it finds instances of the separator ‘,’
		- `split(‘’)`: splits the string into substrings if it finds instances of a whitespace
		- `strip()`: removes any whitespace from the beginning or the end
	- Combine strings and numbers use: `format()` method
		- Takes arguments, formats them, and places them in string where place holders are { }
		- Example:
~~~			
		pop = 3.29e8
		a = "United States Population in 2019 is {}"
		print(a.format(pop))
		## United States Population in 2019 is 329000000.0
~~~

- **Multiline Strings**
    - Assign multiline string to a variable by using three double or single quotes

- **Numbers and Strings Conversion**
    - Convert number to string use: `str()`
    - Convert string to number use: `int()`
