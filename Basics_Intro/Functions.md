# Defining and Calling Function

## Rules to Define a Function
We can define functions to provide the required functionality. Here are simple rules to define a function in Python.
- Function blocks begin with the keyword def followed by the function name and parentheses `( )`.
- Any input parameters or arguments should be placed within these parentheses.
- The code block within every function starts with a colon `:` and is indented.
- The statement `return` [expression] exits a function, optionally passing back an expression to the caller.

## Calling a Function
Defining a function only gives it a name, specifies the parameters that are to be included in the function, and structures the blocks of code.

Once the basic structure of a function is finalized, you can execute it by calling it from another function or directly from the Python prompt. Following is the example to define and call a function. 

Here the function `printme()` takes a string as input parameter and prints it on a standard screen.

**Example** 
~~~
# Function definition is here
def printme(str):
    print(str)
    return;

# Now you can call printme function
printme("I'm first call to user defined function!")

## I'm first call to user defined function!

printme("Again second call to the same function")
## Again second call to the same function
~~~

## Function Parameters and Return Values

Parameters are specified after the function name, inside the parentheses. You can add as many parameters as you want, just separate them with a comma. By default, parameters have a positional behavior and you need to inform them in the same order that they were defined.

The following example has a function with one parameter (fname). When the function is called, we pass along a first name, which is used inside the function to print the full name.

**Example** - Function with One Parameter and without Return Values
~~~
# define a function
def my_function(fname):
    print(fname + " Smith")
    
# call the function
my_function("Emil")
## Emil Smith

my_function("Tobias")
## Tobias Smith
~~~

**Example** - Function with One Parameter and One Return Value
~~~
# define a function
def square(x):
    return x*x 
    
# call the function
a=square(5)
print(a)
## 25
~~~

**Example** - Function with One Parameter and Multiple Return Values
~~~
# define a function
def powers (x): # one parameter 
    return x*x, x**3, x**4 # return three values
    
# call the function
a,b,c = powers(10)
print(a,b,c)
## 100 1000 10000
~~~

**Example** - Function with Multiple Parameter and Return Values
~~~
# define a function
import math
def trig (x, y):# two parameters
    return math.cos(x)+y, math.sin(x)-y # return two values

# call the function
a,b = trig(10, 4)
print(a,b)    
## 3.1609284709235475 -4.5440211108893696
~~~

## Default Parameter Values
The following example shows how to use a default parameter value. If we call the function without parameter, it uses the default value.

**Example** - Function with Default Parameter Values
~~~
# define a function
def my_function(x=3, y=2, z=1.5):   
    return z * (x + y)
#the default values for x=3, y=2, z=1.5
# call the function        
a=my_function()
# use the default value x=3, y=2, z=1.5
print(a)
## 7.5

b = my_function(1,2,3) 
# pass value for x=1, y=2, z=3
print(b)
## 9
~~~

**Example** - Function with Default Parameter Values
~~~
# define a function
def my_country(country = "Norway"): 
    print("I am from " + country)
    #the default value for the parameter country is "Norway"

# call the function    
my_country() 
# use the default value for the parameter country
## I am from Norway

my_country("Sweden")
# pass "Sweden" to the paramter country
## I am from Sweden
~~~

## Keyword Arguments
Python allows functions to be called using keyword arguments. When we call functions in this way, the order (position) of the arguments can be changed.

**Example** - Function with keyword Arguments
~~~
def greet(name, msg):
    print("Hello",name + ', ' + msg)

# call the function
greet(name = "Bruce", msg = "How do you do?")
# 2 keyword arguments
## Hello Bruce, How do you do?
greet(msg = "How do you do?",name = "Bruce")
# 2 keyword arguments (out of order)
## Hello Bruce, How do you do?

greet("Bruce", msg = "How do you do?") 
# 1 positional, 1 keyword argument
## Hello Bruce, How do you do?
~~~

As we can see, we can mix positional arguments with keyword arguments during a function call. But we must keep in mind that keyword arguments must follow positional arguments.

:warning: Having a positional argument after keyword arguments will result in errors. For example, the function call as follows:
~~~
greet(name=“Bruce”,“How do you do?”)
will result in an error as follows:
SyntaxError: non-keyword arg after keyword arg
~~~


