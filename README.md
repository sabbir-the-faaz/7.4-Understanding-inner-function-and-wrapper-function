# 7.4-Understanding-inner-function-and-wrapper-function
In Python, functions are considered first-class objects, meaning they can be treated like any other object (such as integers, strings, and lists). They can be passed around as arguments, returned from other functions, assigned to variables, and stored in data structures.

Let's break down the provided code to illustrate these concepts:

Function as a First-Class Object
Example 1: Returning a Function from Another Function
python
Copy code
def double_decker():
    print('starting the double decker')
    def inner_fun():
        print('inside the inner')
        return 3000
    return inner_fun
double_decker Function:
This function defines another function inner_fun inside it.
inner_fun prints a message and returns a value.
double_decker then returns the inner_fun function itself, not its result.
Let's see what happens when we call double_decker:

python
Copy code
# Assigns the returned function `inner_fun` to the variable `inner`
inner = double_decker()

# Calls the `inner_fun` function
result = inner()
print(result)  # This prints 3000
When double_decker() is called, it prints "starting the double decker" and returns the inner_fun function. Assigning this to inner and then calling inner() executes inner_fun, printing "inside the inner" and returning 3000.

You can directly print the results as well:

python
Copy code
print(double_decker())  # Prints the function reference: <function double_decker.<locals>.inner_fun at ...>
print(double_decker()())  # Prints "starting the double decker", "inside the inner", and then 3000
Example 2: Passing a Function as an Argument
python
Copy code
def do_something(work):
    print('work started')
    work()  # Call the passed function
    print('work ended')

def coding():
    print('coding in python')

do_something(coding)
do_something Function:

Takes a function work as an argument.
Prints "work started".
Calls the passed function work.
Prints "work ended".
coding Function:

Simply prints "coding in python".
When you call do_something(coding), the coding function is passed as an argument to do_something. This demonstrates that functions can be passed around like other objects.

The output will be:

python
Copy code
work started
coding in python
work ended
Incorrect Usage Example
python
Copy code
#do_something(2)
Attempting to pass a non-function value like 2 to do_something would cause an error because 2 is not callable. The function do_something expects a function as its argument, not an integer.

Summary
Returning Functions: You can return a function from another function, allowing dynamic creation and behavior.
Passing Functions: You can pass functions as arguments to other functions, enabling flexible and reusable code.
This flexibility is a hallmark of functions being first-class objects in Python. They can be created at runtime, assigned to variables, passed as arguments, and returned from other functions, just like any other object.
