# NUMBERS

- Python Data Types
    - 6 standard data types
        - Numbers
        - Strings
        - Lists
        - Tuples
        - Sets
        - Dictionaries
    - Numbers
        - 3 numeric types
            - Int (integer) - positive or negative, w/o decimals, unlimited length
            - Float (floating point number) - positive or negative, containing one or more decimals
                - Can also be scientific numbers with an "e" or "E" to indicate power of 10
            - Complex - written with a j as the imaginary part
        - Variables of numeric types created when values are assigned to them
        - To verify type of any object in Python use: 'type()' function
    - Number Type Conversion
        - To convert from one type to another use: 'int()', 'float()', 'complex()' methods
            - Example
~~~			
x = float(-2)# convert from int to float
y = int(2.8)# convert from float to int
z = complex(3)# convert from int to complex
print(x)## -2.0
print(y)## 2
print(z)## (3+0j)
~~~