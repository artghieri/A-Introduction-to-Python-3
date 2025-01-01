## Introduction

Python's allure lies not only in its simplicity but also in its adaptability across a wide range of projects and domains. As we explore the intricacies of Python, this guide aims to provide you with a solid understanding of its core concepts and commands, empowering you to unlock the language's potential for diverse applications.  

Think of this guide as an open invitation to the expansive world of programming, crafted to support learners at any proficiency level. Whether you're a beginner taking your first steps in Python or an experienced coder seeking to sharpen your skills, this journey is tailored to meet your needs, helping you build confidence and expertise in Python programming.  

In the sections ahead, we will dive into key features, best practices, and real-world applications, giving you a well-rounded grasp of Python's capabilities. Stay tuned for an enriching journey that will prepare you to navigate the programming landscape with skill and confidence.  

## Installing Packages With pip

Up to this point, you have been working exclusively with the **Python standard library**. In the remainder of this course, you will explore various **packages** that are not included with Python by default.  

Many programming languages provide a **package manager** to simplify the installation, upgrading, and removal of third-party packages—and Python is no exception.  

Python's de facto package manager is called `pip`. Historically, `pip` needed to be downloaded and installed separately. However, starting with [Python 3.4](https://www.python.org/downloads/release/python-340/), it has been bundled with most Python distributions, making it easier than ever to manage packages.  

## 

### Installing Third-Party Packages With pip

Python’s package manager pip is used to install and manage third party packages. It is a separate program from Python, although it’s likely that pip was installed on your computer whenever you downloaded and installed Python.

>  ***Note:** pip is a command line tool. That means you must run it from a command line or terminal program.*

Installing third-party packages with Pip is a fundamental and efficient way to extend the functionality of your Python projects. Pip, which stands for "Pip Installs Packages," is a package management system that simplifies the process of acquiring and installing external libraries or modules.

The concept of a package manager might be familiar to you if you’re coming from another programming language. [JavaScript](https://developer.mozilla.org/en-US/docs/Web/JavaScript) uses [npm](https://www.npmjs.com/) for package management, Ruby uses [gem](https://rubygems.org), and the [.NET platform](https://dotnet.microsoft.com/languages) uses [NuGet](https://www.nuget.org/). In Python, pip has become the standard package manager.

### **Windows:**  
Press the Windows key and type `cmd` and press `Enter` to open the **Command Prompt** application. 

![image](https://github.com/artghieri/Python-Guide-A-Introduction-to-Python-3/assets/102708433/9089ad2b-274f-4bfd-82ac-4b6a81d2be25)

### **macOS:**  
Press `Cmd` + `Spacebar` to open the **Spotlight** search window. Type `terminal` and press `Enter` to open the Terminal app. 

![image](https://github.com/artghieri/Python-Guide-A-Introduction-to-Python-3/assets/102708433/9131384d-25de-4791-b085-118960d46e6f)


### **Ubuntu and Linux:**  
Click on the **Show Applications** button at the bottom of your toolbar and search for `terminal`. 

![image](https://github.com/artghieri/Python-Guide-A-Introduction-to-Python-3/assets/102708433/8dde88a8-f91e-4cc4-b2b0-30c101c3e199)


To determine if `pip` is installed on your system, use the following command in your terminal:

```bash
python3 -m pip --version
```

Upon successful installation, you should observe output similar to the following:

```
pip 19.3.1 from c:\users\David\appdata\local\programs\python\python38-32\lib\site-packages\pip (python 3.8)
```

This output signifies that pip version 19.3.1 is installed and associated with the Python 3.8 installation.

Note that the displayed version and linked Python installation may differ on your computer, which is acceptable as long as it reflects any Python 3 version.

If your operating system reports that `pip3` is an unrecognized command, it indicates that pip was not included with your Python distribution.

> [!IMPORTANT]
> **macOS and Ubuntu Linux:**  
> Ensure the use of the `python3` command for pip commands, not `python`, to utilize the Python 3 version of pip.
> 
> **Windows:**  
> If `python3` does not work, try using `python`. If successful, replace all instances of `python3` commands with `python`.


### Running Pip as a Module

When using your system's `pip` directly, the command may not indicate the Python version it is associated with. This ambiguity can lead to packages being installed in the `site-packages` directory of an unintended Python version. To avoid this, it is recommended to run `pip` as a Python module using the following command:  

```bash
python3 -m pip
```  

The `-m` switch instructs Python to run a module as an executable using the `python3` interpreter. This ensures that the pip command is executed with your system's default Python 3 version. For more details about this approach, you can read Brett Cannon’s insightful article on [the advantages of using python3 -m pip](https://snarky.ca/why-you-should-use-python-m-pip/).  

In some cases, you may want to limit package installations to a specific project. To achieve this, you should use pip within a **virtual environment**.  


### Exploring Alternatives to pip

While `pip` is the default package manager for Python, there are several other tools available that provide enhanced functionality and simplify package management. Here are some of the most popular alternatives:

| Tool    | Description             |
|---------|-------------------------|
| [**Conda**](https://conda.io/en/latest/)        | **Conda** is a package, dependency, and environment manager for multiple languages, including Python. Originating from [Anaconda](https://www.anaconda.com/), Conda is particularly popular in the data science and [machine learning](https://realpython.com/python-windows-machine-learning-setup/) communities. It has its own [package index](https://repo.continuum.io/) to host compatible packages and is widely used for managing complex environments.                                                                                                           |
| [**Poetry**](https://python-poetry.org/)        | **Poetry** is a modern package management tool that will feel familiar if you're coming from JavaScript and [npm](https://www.npmjs.com/). Poetry not only manages packages but also helps with building and distributing Python applications, making it an all-in-one solution for dependency management, packaging, and deployment to PyPI. You can learn more about it in the guide on [dependency management with Poetry](https://realpython.com/dependency-management-python-poetry/). |
| [**Pipenv**](https://github.com/pypa/pipenv)    | **Pipenv** merges virtual environment management and package management into a single tool. It automatically creates and manages a virtual environment for your projects, ensuring that the right dependencies are installed. To learn more, check out [Pipenv: A Guide to the New Python Packaging Tool](https://realpython.com/pipenv-guide/).                                                                                                           |

> [!NOTE]
> **For more details about pip and Python Virtual Environments, check the [Python Virtual Environment guide](https://github.com/artghieri/A-Introduction-to-Python-3/blob/main/extras/Python_Virtual_Environment.md).**

## Variables

Variables in programming serve as symbolic containers, offering a means to hold and reference values within your code. The analogy of a named box is frequently employed to elucidate the concept of variables – envisioning them as storage units with unique identifiers that allow convenient access to the information they contain.

Within the Python programming language, variables are akin to labeled boxes, each housing specific pieces of information in the computer's memory. The name assigned to a variable acts as a reference, providing a convenient way to interact with and manipulate the associated value. 

The use of variables in Python is fundamental for two primary reasons:

**Accessibility of Values**  
Variables streamline the storage of values, allowing you to perform operations without repeatedly executing time-consuming tasks. For example, if a computation involves significant data processing, assigning the result to a variable ensures that the computation is executed only once. Subsequently, you can access the stored result whenever needed, optimizing the efficiency of your code.

**Example:** Calculate the area of a rectangle
```python
# The variables length and width store the dimensions of a rectangle
length = 5
width = 8

# The area variable holds the result of the multiplication.
area = length * width

# Now, the 'area' variable holds the calculated result
print(f"The area of the rectangle is: {area}")
```

> ***Note:** By utilizing variables, the code becomes more readable, and the result can be easily accessed and reused.*

**Contextualization of Values**  
The meaning of values can vary depending on the context. For instance, the numeric value 28 might represent the number of students in a class or the count of times a user has accessed a website. By assigning meaningful names like `num_students` to variables, you provide context and clarity about the significance of the associated value. This naming practice enhances the readability of your code, making it more comprehensible for others and facilitating a better understanding of the variable's purpose and content.

**Example:** Count of students in a class
```python
# The variables num_students and num_visits represent different quantities.
num_students = 28

# Count of website visits
num_visits = 1000

# Displaying the contextualized values
print(f"The number of students in the class: {num_students}")
print(f"The count of website visits: {num_visits}")
```

> ***Note:** Meaningful variable names provides clarity about the context, making the code more understandable for anyone reviewing it.*

###  Declaration and Initialization of Variables

The Python programming language follows a dynamic and strong typing system, distinguishing it from statically typed languages like C. In Python, you do not need to explicitly declare the data type of a variable. Instead, the interpreter dynamically determines the type of a variable during runtime.

Unlike C, Python is not concerned with the direct allocation of physical memory space, making it a more flexible and convenient language for developers. The absence of explicit type declarations allows for easier and quicker coding, as you can assign values to variables without specifying their types.

```python
# Example of dynamic typing in Python
variable_example = 42  # Python interpreter dynamically determines the type

# Reassigning the variable with a different type
variable_example = "Hello, Python!"  # No need for explicit type declaration
```

> ***Note:** The use of the assignment operator is employed to assign values to variables, similar to other programming languages.*

In the provided Python example, the variable `variable_example` is dynamically assigned an integer value and later reassigned a string value. This flexibility enhances code readability and simplifies the development process. So, what is the difference?

 **Declaring a Variable**  
In Python, the concepts of declaring and initializing variables are often intertwined due to the language's dynamic typing. Unlike statically typed languages such as C, where you explicitly declare a variable's data type before use, Python allows for a more fluid approach.

Declaring a variable doesn't involve a separate step for specifying its data type. Instead, the declaration and assignment of a value often occur simultaneously. When you first assign a value to a variable using the assignment operator (`=`), Python dynamically creates the variable.

```python
my_variable = 42  # Here, `my_variable` is declared and assigned the value 42 in one step.
```

**Initializing a Variable**  
Initialization is the process of providing a variable with its initial value. In Python, initialization frequently happens at the moment of declaration. You can assign a specific value to a variable when declaring it, but it's not mandatory. Alternatively, you can declare a variable first and assign a value to it later in the code.

```python
uninitialized_variable  # This is a declaration without initialization.

initialized_variable = "Hello, world!"  # Here, `initialized_variable` is declared and initialized.
```

In summary, Python's dynamic typing allows variables to be declared and initialized in a single step. The need for explicit data type declarations is eliminated, making the language more adaptable to changing values and reducing redundancy in the code.


### The Assignment Operator

In Python, values are assigned to variables using the assignment operator, represented by the symbol `=`. Operators in programming, such as `=` or `+`, perform specific operations on values. The `=` operator, unlike its appearance in mathematics, holds a distinct meaning in Python, where it is used for variable assignment.

Let's explore the assignment operator in action by modifying the **"Hello, world"** program from the previous section. This time, we'll introduce a variable to store some text before printing it to the screen:

```python
>>> phrase = "Hello, world"
>>> print(phrase)
Hello, world
```

In the first line, a variable named `phrase` is created and assigned the value "Hello, world" using the = operator. This variable is then used in the `print()` function instead of the original string. When executing `print(phrase)`, Python looks up the name `phrase` and finds it assigned the value "Hello, world."

It's crucial to note that variable names are case-sensitive in Python. For example, a variable named `phrase` is distinct from a variable named `Phrase` (with a capital P). If you attempt to use an undefined variable like `Phrase`, you will encounter a `NameError`.

```python
>>> phrase = "Hello, world"
>>> print(Phrase)
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
NameError: name 'Phrase' is not defined
```

Remember, whenever you encounter the `=` operator, it signifies that whatever is to the right of it is being assigned to the variable on the left. Paying attention to these details and ensuring precise syntax alignment is crucial in Python programming to avoid errors. Computers interpret code literally, and minor discrepancies can lead to unexpected outcomes.


### Valid Variable Names

When working with variables in Python, there are specific rules for creating valid variable names. While variable names can vary in length, they must adhere to the following rules:

1. Variable names can only contain uppercase and lowercase letters $(A–Z, a–z)$, digits $(0–9)$, and underscores ( _ ).
2. Variable names cannot begin with a digit.

For instance, the following examples demonstrate valid variable names: `phrase`, `string1`, `_a1p4a`, and `list_of_names`. On the other hand, `9lives` is not a valid variable name due to starting with a digit.

It's worth noting that Python allows variable names to contain a wide range of valid [Unicode](https://en.wikipedia.org/wiki/Unicode) characters. Unicode, a standard for representing text in various writing systems, permits the use of letters from non-English alphabets, special characters like é and ü, and symbols from languages such as Chinese, Japanese, and Arabic. However, it's advisable to avoid decorated characters if code sharing involves people from different regions, as not every system can display these characters.

While a variable name may be technically valid, choosing a good and meaningful name is essential. Naming variables appropriately enhances code readability and understanding. Keep these guidelines in mind when selecting variable names to improve the clarity and maintainability of your code.


**Descriptive Names Are Better Than Short Names**  
Choosing descriptive variable names over short names is crucial, especially in the context of complex programs. When dealing with intricate code structures, opt for longer, more descriptive names, as they contribute significantly to code readability and comprehension.

Consider the example below, where the value $3600$ is assigned to the variable `s`:

```python
# The name s lacks clarity and is ambiguous. Enhance understanding by using a more descriptive name
s = 3600

# While seconds is an improvement, it still doesn't fully convey the purpose of the code.
# It leaves room for interpretation. To eliminate ambiguity, choose a name that explicitly communicates the meaning
seconds = 3600

# In this case, seconds_per_hour provides clear and unambiguous information about the code's intent.
# Despite the longer length, the improved clarity justifies the choice of a more descriptive name.
seconds_per_hour = 3600
```


While embracing descriptive variable names is beneficial, it's essential to strike a balance. Avoid excessively long names that might hinder code readability. Although the definition of "excessively long" is subjective, a practical guideline is to limit variable names to fewer than three or four words. This ensures that your variable names remain informative without becoming unwieldy.

**Python Variable Naming Conventions**  
In various programming languages, the convention is to use **camelCase** for variable names. This naming style involves capitalizing the first letter of every word except the first, creating a camel-hump-like appearance with the juxtaposition of lowercase and uppercase letters, such as `numStudents`.

However, a different convention is more prevalent - **snake_case**. In snake_case, variable names like `num_students` are formed by making every letter lowercase and separating words with underscores. Although Python doesn't strictly enforce the use of snake_case, it is widely embraced and recommended in PEP 8, the official style guide for Python. 

By following [PEP 8 guidelines](https://peps.python.org/pep-0008/), you contribute to a standardized and consistent coding style, making it simpler for others to collaborate, share, and maintain code. This adherence to conventions fosters a cohesive coding environment and facilitates effective communication within the Python programming community.

> [!IMPORTANT]
> **Python’s support for Unicode is covered in the [official Python documentation](https://docs.python.org/3/howto/unicode.html#python-s-unicode-support).**

### The Scope of a Variable

In Python, the scope of a variable refers to the region of code where the variable is accessible. There are two main types of variable scopes in Python: global scope and local scope.

```mermaid
stateDiagram-v2
    state GLOBAL {
        Global_Variable
        LOCAL

        state LOCAL{
          Local_Variable
        }
    }
```

**Local Scope** is where variables are confined to a specific function, accessible only within that function. Unlike global scope variables, they can't be directly modified or read from outside. If a local variable shares its name with a global one, it takes precedence within that function, ensuring isolated functionality and minimizing naming conflicts.
```python
def example_function():
    local_var = 5  # Local variable
    print(local_var)

example_function()  # Output: 5

# Attempting to access the local variable outside the function would result in an error.
```


**Global Scope** encompasses variables defined outside any function. These variables are accessible from anywhere in the code, including within functions. They can be modified and read from any function unless there's a local variable with the same name. 

```python
globvar = 0

def set_globvar_to_one():
    global globvar  # Needed to modify global copy of globvar
    globvar = 1

def print_globvar():
    print(globvar)  # No need for global declaration to read value of globvar

set_globvar_to_one()
print_globvar()  # Prints 1
```

Since it's unclear whether `globvar = 1` is creating a local variable or changing a global variable, Python defaults to creating a local variable, and makes you explicitly choose the other behavior with the `global` keyword.

Additionally, Python has block scope within conditional structures (if, else) and loops. The nonlocal statement is used to access and modify variables from an outer (non-global) scope within nested functions. An example would be:

```python
def outer_function():
    outer_var = 15

    def inner_function():
        nonlocal outer_var 
        outer_var = 10
        print(outer_var) # Output: 10

    inner_function()  
    print(outer_var)  # Output: 10

outer_function()
```

## Writing Comments in the Code

As programmers, we often revisit our code months later and find ourselves wondering, "What does this do?" Even with well-chosen variable names, understanding the reasoning behind certain code structures can be challenging over time. Comments are essential tools for documenting the intended functionality of your code, helping you (and others) understand its purpose and behavior.

In Python, comments are lines of text that do not affect the execution of the program. They serve as documentation to clarify what the code is doing, what certain sections are intended to accomplish, or why specific decisions were made. This section explains how to write comments in Python and offers guidelines for effective comment formatting.

#### How to Write a Comment

The most common way to write a comment in Python is by starting a line with the `#` symbol. Any text following this symbol on the same line will be ignored by the Python interpreter.

**Block Comments**  
These are comments that start on a new line and typically explain a larger portion of the code or provide more context.

```python
# This is a block comment.
phrase = "Hello, world."
print(phrase)  
```

> ***Note:** The first line `(# This is a block comment)` is ignored by Python, so no code is executed there. On the other hand, the `print(phrase)` line is executed, but the text following the `#` is ignored by the interpreter.*

**In-line Comments**  
These are comments placed on the same line as a statement. They provide additional information about that specific line of code.

```python
phrase = "Hello, world."  # This is an in-line comment explaining the variable
print(phrase)  # Print the phrase to the console
```

**Multi-line Block Comments**  
While it's advisable to keep comments concise, there are scenarios where more extended explanations are necessary. In such cases, you can continue the comment on a new line starting with `#`.

```python
# This is my first Python script.
# It prints the phrase "Hello, world." to the console.
# Comments like these are helpful for beginners who are just learning.
phrase = "Hello, world."
print(phrase)
```

Comments are not only useful for providing context but also serve during code testing. You can comment out specific lines of code to temporarily disable them without deleting the code entirely. This allows you to experiment and test changes while preserving the original code. This flexibility facilitates testing and debugging processes.

#### Conventions and Pet Peeves

According to PEP 8, comments should be written in complete sentences with a single space between the `#` and the first word of the comment:

```python
# This comment is formatted to PEP 8.
#Avoid this
```

For in-line comments, PEP 8 recommends having at least two spaces between the code and the `#` symbol.

```python
phrase = "Hello, world"  # This comment is PEP 8 compliant.
print(phrase)# This comment isn't.
```

While comments are essential for code documentation, they can become pet peeves for programmers when they describe the obvious. For instance, comments that duplicate the functionality of the code:

```python
# Print "Hello, world"
print("Hello, world")
```

> ***Note:**  The comment is redundant because the code itself clearly states its purpose. The best use of comments is to provide insights into complex or non-intuitive sections of code, explaining the reasoning behind a specific approach.*

PEP 8 emphasizes the judicious use of comments, suggesting that they should add value by enhancing code comprehension. In cases where descriptive variable names suffice to convey the purpose of the code, comments describing the functionality may be deemed unnecessary. Following these conventions ensures that comments contribute positively to code clarity and understanding.

## Data Types in Python

Python is a dynamic, high-level programming language that provides a rich set of data types to handle a variety of data efficiently. These data types can be categorized into several groups, including numeric types, sequential types, sets, and mappings. Let's dive into the numeric data types and explore their characteristics in Python.

#### NUMERIC DATA TYPES IN PYTHON
Numeric data types are fundamental for representing numerical values in Python. These types allow you to perform a wide range of mathematical operations and handle numbers of different forms. Python provides three main numeric data types: **integers**, **floating-point numbers**, and **complex numbers**.

Each of these data types is designed to store and manipulate different kinds of numbers:

**Integers**   
Integers are whole numbers that can be either positive or negative. They are represented by the `int` class in Python. One of the advantages of Python's int type is its ability to handle numbers of arbitrary size, allowing you to work with very large or very small integers without worrying about overflow.

```python
x = 100
y = -200
```

**Float**   
The `float` type represents real numbers that can include a decimal point. Floats are used when precision is required for decimal values. Additionally, Python allows for scientific notation, where numbers are written in the form of a base number multiplied by 10 raised to an exponent `(e.g., 1.23e4)`.

```python
pi = 3.14159
temperature = -10.5
distance = 1.2e3  # Scientific notation for 1200.0
```

**Complex Numbers**   
Python supports `complex numbers`, which consist of a real part and an imaginary part. These are represented in the form `a + bj`, where `a` is the real part, `b` is the imaginary part, and `j` represents the imaginary unit. Complex numbers are used in fields such as electrical engineering and quantum physics.

```python
z = 4 + 3j  # Real part 4, imaginary part 3
```

You can check the type of a variable using the `type()` function. This function returns the type of the object, which can be useful for debugging and development.

```python
x = 10
y = 3.14
z = 2 + 5j

print(type(x))  # Output: <class 'int'>
print(type(y))  # Output: <class 'float'>
print(type(z))  # Output: <class 'complex'>
```

Python's numeric data types — integers, floating-point numbers, and complex numbers — are versatile tools for representing various forms of numerical data. These types allow for flexibility in handling mathematical operations and provide the foundation for more advanced computations in Python.


#### SEQUENTIAL DATA TYPES IN PYTHON

Sequential data types in Python are essential for managing ordered collections of elements. These types include `strings`, `lists`, and `tuples`, each designed to meet different needs when it comes to organizing and manipulating data.

**Strings**  
Strings in Python, represented by the `str` `class`, are used to handle textual data. A string is a sequence of characters enclosed in single, double, or triple quotes. Python provides a wide range of operations for working with strings, such as concatenation (joining strings), slicing (extracting parts of a string), and indexing (accessing individual characters). Strings are fundamental in text processing and are integral to any Python program that involves human-readable data.

```python
message = "Hello, world!"
print(message[0])  # Output: 'H'
print(message[7:12])  # Output: 'world'
```

**Lists**  
Lists, represented by the `list` `class`, offer a flexible way to store ordered, mutable collections of items. Unlike strings, lists are mutable, meaning their elements can be changed, added, or removed. This flexibility makes lists particularly useful for situations where you need to manage a dynamic set of items. Lists are defined by enclosing elements within square brackets.

```python
fruits = ["apple", "banana", "cherry"]
fruits.append("orange")  # Adds 'orange' to the list
fruits[1] = "blueberry"  # Changes 'banana' to 'blueberry'
print(fruits)  # Output: ['apple', 'blueberry', 'cherry', 'orange']
```

**Tuples**  
Tuples, represented by the `tuple` `class`, are similar to lists but with a key difference: tuples are immutable. Once a tuple is created, its elements cannot be altered, added, or removed. This immutability makes tuples ideal for situations where you need to maintain the integrity of the data. Tuples are defined by enclosing elements within parentheses.

```python
coordinates = (4, 5)
# coordinates[1] = 6  # This would raise an error because tuples are immutable
print(coordinates)  # Output: (4, 5)
```

The `len()` function is commonly used to determine the length of a sequence in Python, whether it's a string, list, or tuple. It returns the number of elements present in the sequence, which is crucial for effective data management and manipulation.

```python
text = "Python is amazing!"
numbers = [1, 2, 3, 4, 5]
values = (10, 20, 30)

print(len(text))     # Output: 18
print(len(numbers))  # Output: 5
print(len(values))   # Output: 3
```


**SET DATA TYPES IN PYTHON**

The set data type in Python is a powerful tool for handling unordered collections of unique elements. Represented by the set class, sets offer efficient methods for performing operations like **intersection**, **union**, and **difference**, making them invaluable for scenarios where distinct and unordered elements are a priority.

- **Sets:** Belonging to the `set` `class`, are characterized by their unordered nature, ensuring that each element is unique within the collection. This uniqueness property is particularly useful when eliminating duplicate values and performing set operations. Sets are defined by enclosing elements within curly braces, such as `set_colors = {"red", "green", "blue"}`.

**Example:**
The following code exemplifies the utilization of set operations and the len() function to showcase the functionality of sets in Python. It defines two sets, 'set1' and 'set2', performs set operations (union and intersection), and determines the length of each set. This demonstrates the effectiveness of sets in managing unique and unordered collections of elements.

```python
set1 = {1, 2, 3, 4, 5}
set2 = {4, 5, 6, 7, 8}

union_set = set1.union(set2)
intersection_set = set1.intersection(set2)

print(union_set)         # Output: {1, 2, 3, 4, 5, 6, 7, 8}
print(intersection_set)  # Output: {4, 5}
print(len(set1))         # Output: 5
print(len(set2))         # Output: 5
```


**MAPPING DATA TYPES IN PYTHON**

Mapping data types in Python are essential for associating keys with corresponding values. The primary mapping type in Python is the dictionary, represented by the dict class. Dictionaries allow developers to create flexible and efficient data structures for storing and retrieving information based on unique identifiers.

- **Dictionaries:** Dictionaries, belonging to the dict class, consist of `key-value` pairs. Each key within a dictionary must be **unique**, and it is mapped to a specific value. This mapping allows for quick and direct access to values, making dictionaries efficient for scenarios where fast data retrieval is crucial. Dictionaries are defined using curly braces, with key-value pairs separated by colons, such as `dictionary_people = {"name": "John", "age": 25, "city": "São Paulo"}`.

**Example:** The following code exemplifies the usage of dictionaries in Python. It defines a dictionary 'person_info' with keys representing different aspects of a person and their corresponding values. The code demonstrates how to access specific values using keys and how to retrieve all keys and values from the dictionary.

```python
person_info = {"name": "Alice", "age": 30, "city": "New York"}

print(person_info["name"])    # Output: Alice
print(person_info["age"])     # Output: 30
print(person_info["city"])    # Output: New York

all_keys = person_info.keys()
all_values = person_info.values()

print(all_keys)               # Output: dict_keys(['name', 'age', 'city'])
print(all_values)             # Output: dict_values(['Alice', 30, 'New York'])
```

## Operators in Python

Python, renowned for its versatility and readability, provides a rich set of operators that serve as fundamental building blocks for manipulating data and enabling decision-making in programs. Operators allow you to perform various operations on variables and values efficiently. Below, we explore four primary categories of operators in Python: **arithmetic operators, augmented assignment operators, logical operators, and relational operators.**

**Arithmetic Operators**  
Arithmetic operators are fundamental for performing basic mathematical operations. They enable programmers to conduct various calculations efficiently. The key arithmetic operators in Python include:

- `+` **Addition.**
- `-` **Subtraction.**
- `*` **Multiplication.**
- `/` **Division.**
- `%` **Modulus, determining the remainder of a division.**
- `**` **Exponentiation.**
- `//` **Floor division, division rounding down to the nearest whole number.**

**Reduced Expressions**  
Augmented assignment operators combine an operation with assignment, simplifying code by reducing redundancy.

| &nbsp;&nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Reduced Expression&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp;&nbsp;    | &nbsp;&nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Normal Expression&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp;&nbsp;    | 
|:---------------------:|:---------------:|
|  `x += 5`           | `x = x + 5`   |
|  `x -= 3`           | `x = x - 3`   |
|  `x *= 2`           | `x = x * 2`   |
|  `x /= 4`           | `x = x / 4`   |
|  `x //= 3`          | `x = x // 3`  |
|  `x %= 2`           | `x = x % 2`   |
  |  `x **= 2`          | `x = x ** 2`  |




**Relational Operators**  
Relational operators are used to compare two values, expressing relationships between them, and return a Boolean result. 

- `==`  Equal To
- `!=`  Not Equal To
- `<`   Less Than
- `>`   Greater Than
- `<=`  Less Than or Equal To
- `>=`  Greater Than or Equal To

```python
print(10 == 5)  # Output: False
print(10 <= 5)  # Output: False
```


**Logical Operators**  
Logical operators are used to combine conditional statements or evaluate Boolean expressions. 

-  `and`: returns `True` if both conditions are true 
-  `or`:   returns `True` if at least one condition is true
-  `not`: reverses the Boolean value | `not True` 


```python
print(10 > 5 and 5 > 0)  # Output: True
print(10 < 5 or 5 > 0)   # Output: True
print(not (10 < 5))      # Output: True
```

> [!NOTE]
> **When using a relational or logical operator, there is always a return value as a Boolean value.**


#### Ternary Operator 

The ternary operator in Python allows you to write conditional statements in a concise and readable format, all in a single line. It provides an elegant alternative to traditional `if-else` blocks, especially when working with simple conditions.

```julia
variable = expression1 if condition1 else expression2 if condition2 (...)
```

This operator is particularly useful for inline assignments or when you want to quickly evaluate conditions without cluttering your code with multiple lines. 

While the ternary operator is concise, it may reduce readability for complex conditions or when used excessively. In such cases, it is better to use traditional if-else structures

#### Example
Suppose you want to determine whether a number is even or odd and print an appropriate message. 

The ternary operator allows you to accomplish this succinctly:

```python
number = 15
result = "even" if number % 2 == 0 else "odd"
print(f"The number {number} is {result}.")
```

> ***Note:*** *For single-line conditional assignments, the ternary operator can make your code cleaner and easier to understand.*


#### Walrus Operator

Introduced in Python 3.8, the walrus operator (`:=`) offers a concise way to assign values to variables as part of an expression. Named for its resemblance to a walrus (its "eyes" and "tusks"), this operator enables more compact and efficient code, particularly in scenarios where you’d otherwise need to repeat a calculation.

The **walrus operator** (`:=`) enables inline assignments, making Python code more concise and efficient. It offers several benefits:  

1. **Inline Assignment**: Assign a value to a variable and use it within the same expression.  
2. **Efficiency**: Avoid redundant computations by combining assignment and evaluation in a single step.  
3. **Readability**: Streamline repetitive constructs, reducing code clutter and enhancing clarity.  


#### Example
Suppose you want to read lines from a file and print those containing the word "python," along with their line numbers. Without the walrus operator, the code might look like this:

```python
with open("example.txt", "r") as file:
    lines = file.readlines()
    for i, line in enumerate(lines):
        if "python" in line:
            print(f"Line {i + 1}: {line.strip()}")
```

The walrus operator simplifies the same task by combining assignment and iteration into a single step:

```python
with open("example.txt", "r") as file:
    for i, line in enumerate(lines := file.readlines()):
        if "python" in line:
            print(f"Line {i + 1}: {line.strip()}")
```

> ***Note:*** *By embedding assignments within expressions, the walrus operator eliminates redundancy and improves code maintainability.*

Here, the walrus operator assigns the result of `file.readlines()` to `lines` and uses it within the same loop. This eliminates the need for a separate assignment line, resulting in cleaner and more concise code.

While the walrus operator can enhance clarity and efficiency, it’s important to use it wisely:

- **Appropriate Scenarios**: Use the walrus operator for straightforward, repetitive tasks where it genuinely simplifies the code.
- **Avoid Overuse**: In complex expressions, the operator might obscure intent, making the code harder to read and maintain.
- **Balance Clarity and Conciseness**: Readable code should remain a priority, especially in collaborative or long-term projects.

Operators in Python are essential tools that enable developers to perform calculations, make comparisons, and manage logical conditions efficiently. By understanding and using these operators effectively, you can build powerful and expressive Python programs.


## **Lambda Expressions in Python**

Lambda expressions are a powerful feature in Python that allow you to create anonymous functions in a single line. These compact functions are ideal for situations where simple operations are needed temporarily, without the overhead of defining a full function using the `def` keyword.

```python
lambda arguments: expression
```  

The expression is implicitly returned, making lambda functions concise and suitable for quick tasks. They are particularly useful in operations like **mapping**, **filtering**, or when a short-lived function is required.


#### Example

Lambda expressions can streamline operations that would otherwise require a longer function definition. For instance, converting temperatures from Celsius to Fahrenheit can be achieved in a single line:

```python
celsius_to_fahrenheit = lambda celsius: (celsius * 9/5) + 32
temperature_celsius = 25
temperature_fahrenheit = celsius_to_fahrenheit(temperature_celsius)

print(f"{temperature_celsius}°C is equal to {temperature_fahrenheit}°F.")
```

> ***Note:*** *The lambda expression defines a temporary function for the conversion, eliminating the need for a function definition.*

#### Using Lambda Expressions in Filtering

One of the most common applications of lambda expressions is in filtering operations. For example, you can extract even numbers from a list using the `filter` function and a lambda expression:

```python
numbers = [1, 2, 3, 4, 5, 6, 7, 8, 9, 10]
even_numbers = list(filter(lambda x: x % 2 == 0, numbers))

print(f"Even numbers in the list: {even_numbers}")
```

This concise approach makes it easy to filter data based on specific criteria.


#### Mapping with Lambda Expressions

Lambda expressions are also commonly used with the `map` function, which applies a function to every item in an iterable. For instance, doubling the values in a list can be done efficiently:

```python
numbers = [1, 2, 3, 4, 5]
doubled = list(map(lambda x: x * 2, numbers))

print(f"Doubled values: {doubled}")
```

> ***Note:*** *The lambda function here defines the operation to double each number, making the process simple and expressive.*

#### Balancing Simplicity and Clarity

While lambda expressions are powerful for short, single-purpose operations, they can become less readable when handling more complex logic. For such cases, using the `def` keyword to define a full function is often a better choice, as it allows for more clarity and maintainability. 

Instead of using a lambda for a multi-step calculation, a regular function with descriptive documentation might be more appropriate:

```python
def multiply_by_two(x):
    """Returns the input number multiplied by two."""
    return x * 2

print(multiply_by_two(5))  # Output: 10
```

Lambda expressions in Python are a convenient tool for creating short, anonymous functions that simplify code in scenarios requiring quick transformations or evaluations. They excel in tasks like **filtering** or **mapping** data but are best suited for **straightforward operations**. For more complex logic, regular functions should be preferred to ensure code readability and maintainability. 


## Casting Data Types

When an expression combines variables of different data types in Python, the interpreter checks whether conversions between these types are possible. If they are not, the runtime process encounters a TypeError, and an error message is displayed. Otherwise, the interpreter performs all necessary type conversions automatically during runtime.

### **Implicit Type Conversion**  

In Python, when expressions involve variables of different data types, the interpreter automatically performs implicit type conversions to ensure compatibility. If these conversions are not possible, a TypeError will be raised, and the programmer needs to handle it explicitly.

Python follows the following rules for implicit type conversions:

- **Conversion to a Common Type:**  
When combining values of different types, Python automatically converts them to a common type. For example, an integer (`int`) combined with a floating-point number (`float`), the result is automatically promoted to `float`.

- **Specific Type Promotion:**  
For pairs of operands with different types, the result takes the type that has higher capacity. For instance, if one operand is of type `float` and the other is of type `int`, the result will be of type `float`.

#### Example of Implicit Conversion
```python
a = 7
print(type(a))  # <class 'int'>

b = 3.0
print(type(b))  # <class 'float'>

c = a + b  
print(c)        # Output: 10.0
print(type(c))  # <class 'float'>
```

### **Explicit Type Conversion**  
Explicit type conversion, or type casting, gives programmers control over data type changes. This is useful when you need a specific type for operations, storage, or further processing.

```python
variable = datatype(expression)
```

#### Example of Explicit  Conversion
```python
num = 10
text = str(num)
print(type(text))  # Output: <class 'str'>
```

Keep in mind that explicit type casting should be used judiciously. When converting between types, there can be data loss or unexpected results. For instance, converting a float to an integer truncates the decimal part.

### Balancing Implicit and Explicit Conversion
While Python handles implicit conversions seamlessly, there are scenarios where explicit conversions are necessary for precision or compatibility. Understanding when and how to use these mechanisms is key to writing efficient, error-free code.

#### Example
For instance, when dealing with user input, which is always treated as a string, explicit conversion is often required:

```python
age = input("Enter your age: ")  # Input is a string
age = int(age)  # Convert to an integer for calculations
print(f"In 5 years, you will be {age + 5}.")
```

## Input and Output Commands

In Python, data input and output are fundamental processes for user interaction and information manipulation. Let's explore how these operations are performed in the language.

### Data Input

To receive data from the user, you can use the `input()` function. This versatile function reads a line from the standard input, typically the keyboard, and returns it as a string. Here's a simple example:

```python
# Input for an integer
age = int(input("Enter your age: "))

# Input for a string
name = input("Enter your name: ")

print("Hello, " + name + "! You are " + str(age) + " years old.")
```

In the example above, the user is prompted to enter their age and name. The `input()` function returns these values as strings, and the use of `int()` is employed to convert the age into an integer.


### Data Output

Consider having a string `name = "Zaphod"` and two integers `heads = 2` and `arms = 3`. The objective is to construct a sentence like "Zaphod has 2 heads and 3 arms." This process is known as **string interpolation**, a technique where variables are inserted into specific locations within a string.

The first method involves using commas to insert spaces between each part of the string within a `print()` function:

```python
print(name, "has", str(heads), "heads and", str(arms), "arms")
```

Another approach is to concatenate the strings using the `+` operator:

```python
print(name + " has " + str(heads) + " heads and " + str(arms) + " arms")
```


## Input and Output in Python

In Python, input and output operations are fundamental for interacting with users and processing data. These operations allow you to gather information from users, process it, and present meaningful results.

### Receiving  Input

The `input()` function is the primary tool for capturing user input. It reads a line of text entered by the user and returns it as a string. To work with numeric data, the string returned by `input()` can be explicitly converted to another type.

#### Example
For example, suppose you want to collect a user’s name and age:

```python
name = input("Enter your name: ")
age = int(input("Enter your age: "))

print(f"Hello, {name}! You are {age} years old.")
```

Here, the `input()` function is used to prompt the user, and the `int()` function converts the string representation of the age into an integer. This ensures that `age` can be used in numerical calculations later.


### Displaying Output

Python’s `print()` function is versatile for displaying results. There are multiple ways to format and present information, ranging from basic concatenation to advanced string formatting techniques.

#### Example

For instance, consider variables that describe a fictional character:

```python
name = "Zaphod"
heads = 2
arms = 3
```

You can present this information in various ways:

* **Basic Printing**: Using commas within `print()` automatically separates values with spaces:

```python
print(name, "has", heads, "heads and", arms, "arms")
```

* **String Concatenation**: You can also use the `+` operator. However, `non-string` values must be converted to strings explicitly:

```python
print(name + " has " + str(heads) + " heads and " + str(arms) + " arms")
```

> ***Note:** While effective, concatenation can make the code harder to read and maintain.*

### Using Formatted Strings (f-Strings)

Python provides a modern, elegant, and efficient way to format strings using [formatted string literals](https://docs.python.org/3/reference/lexical_analysis.html#formatted-string-literals), commonly known as `f-strings`. Introduced in [Python 3.6](https://www.python.org/downloads/release/python-360/), `f-strings` allow you to seamlessly embed variables and expressions directly within a string, enhancing readability and reducing boilerplate code. 

The easiest way to understand it is to see them in action. Here’s what the above string looks like when written as an `f-strings`:
```python
name = "Zaphod"
heads = 2
arms = 3
print(f"{name} has {heads} heads and {arms} arms.")
```

There are two important things to notice about the above examples:
* The string literal starts with the letter $f$ before the opening quotation mark.
* Variables such as `name`, `heads`, and `arms` are embedded within curly braces `{}`, and their values are automatically inserted into the `string` without any type conversion.

#### Embedding Expressions 
`f-Strings` can evaluate and embed expressions directly. For instance:

 ```python
 n = 3
 m = 4
 print(f"{n} times {m} is {n * m}")
 ```

> ***Note:** Here, the expression `{n * m}` is evaluated, and the result `12` is dynamically inserted into the output.*

While `f-strings` are powerful, it’s important to use them judiciously:

- **Keep Expressions Simple:**  
  Avoid placing overly complex expressions inside `{}`. If a computation is intricate, assign the result to a variable.

- **Use Descriptive Variables:**  
  Clear variable names improve the readability of your `f-strings` and make your code easier to maintain.

> [!IMPORTANT]
> **If you’d like to explore f-strings further, check out Python’s official documentation or detailed guides like [Python 3’s f-Strings: An Improved String Formatting Syntax (Guide)](https://realpython.com/python-f-strings/).**


## Strings and String Methods

In Python, strings are sequences of characters that represent text. They are one of the core data types and are fundamental for handling textual data in any program. Python offers a wide range of string methods, allowing you to perform various tasks such as converting text to `uppercase` or `lowercase`, trimming `whitespace`, replacing `substrings`, and more.

### The String Data Type

The `str` data type is a fundamental data type in Python, representing values that signify text. Strings are classified as a basic data type because they cannot be broken down into smaller values of a different type. Once a string is created, its content cannot be altered, making it immutable. This is a key characteristic of strings, although not all data types in Python share this trait.

> ***Note:** The term "data type" refers to the kind of data a particular value represents.*


You can check the type of a string using the `type()` function:

```python
>>> type("Hello, world")
<class 'str'>
```

> ***Note:** The output `<class 'str'>` signifies that the value "Hello, world" is an instance of the str data type, meaning it is a string.*

It's worth noting that `class` is currently synonymous with `data type` for conceptual purposes at the moment.

You can also use `type()` to check the type of variables that hold string values:

```python
>>> phrase = "Hello, world"
>>> type(phrase)
<class 'str'>
```

#

### String Literals

In Python, strings are created by enclosing text in either single quotes (`'`) or double quotes (`"`). Both types of quotes are functionally identical, and the choice between them is often a matter of preference:

```python
string1 = 'Hello, world'
string2 = "1234"
```

These are called **string literals**, as they are explicitly defined in the code. The key thing to remember is that you should use matching quotation marks at both ends of the string. Additionally, when using one type of quote to define the string, you can safely use the other type of quote inside the string without causing issues:

```python
string3 = "We're #1!"
string4 = 'I said, "Put it over by the llama."'
```

> ***Note:** Python recognizes the first delimiter and considers all characters until the matching second delimiter is encountered.*

However, if you try to use the same type of quotes within a string, it will result in a `SyntaxError`:

```python
>>> text = "She said, "What time is it?""
File "<stdin>", line 1
text = "She said, "What time is it?""
^
SyntaxError: invalid syntax
```

This happens because Python misinterprets the string's boundaries due to the conflicting quotation marks.

#

### Handling Special Characters and Unicode

Python strings can contain any valid [Unicode character](https://home.unicode.org/technical-quick-start-guide/), which means you can store text in any language or use symbols from various alphabets. For example:

```python
string_with_unicode = "×Pýŧħøŋ×"
```

This string includes characters that are beyond the standard ASCII set, demonstrating Python's ability to handle a wide range of symbols and characters. You can also use symbols like the pound sign (`#`) within strings:

```python
string_with_symbol = "We're #1!"
```

While Python allows flexibility in choosing between single and double quotes for strings, it's considered good practice to maintain consistency within a project. By sticking to one style for string delimiters, you make the code cleaner and easier to maintain.



#



### Determining the Length of a String

In Python, the length of a string refers to the number of characters it contains, including spaces. For example, the string `"abc"` has a length of 3, while the string `"Don't Panic"` has a length of 11.

You can easily determine the length of a string using the built-in `len()` function. For example:

```python
>>> len("abc")
3
```

> ***Note:** The `len()` function is used to calculate the length of a string.*

The `len()` function can also be used with strings assigned to variables:

```python
>>> letters = "abc"
>>> num_letters = len(letters)
>>> num_letters
3
```

In this example, the string `"abc"` is assigned to the variable `letters`. The `len()` function calculates the length of `letters` and stores the result in the variable `num_letters`. The output confirms that the length is 3.

#

### Multiline Strings

When dealing with long strings, especially those that exceed the recommended line length of 79 characters (as per PEP 8), Python provides several ways to create multiline strings.

You can split long strings into multiple lines using a backslash (`\`) at the end of each line. This ensures that the total length of each line remains under 79 characters:

```python
paragraph = "This planet has - or rather had - a problem, which was \
this: most of the people living on it were unhappy for pretty much \
of the time. Many solutions were suggested for this problem, but \
most of these were largely concerned with the movements of small \
green pieces of paper, which is odd because on the whole it wasn't \
the small green pieces of paper that were unhappy."
```

Alternatively, you can use triple quotes (`"""` or `'''`) to create multiline strings without needing backslashes. This method allows you to preserve the string’s formatting, including line breaks:

```python
paragraph = """This planet has - or rather had - a problem, which was
this: most of the people living on it were unhappy for pretty much
of the time. Many solutions were suggested for this problem, but
most of these were largely concerned with the movements of small
green pieces of paper, which is odd because on the whole it wasn't
the small green pieces of paper that were unhappy."""
```

Triple-quoted strings are particularly useful for preserving formatting or when documenting code, as they allow for clean, structured output when printed.

#

### Concatenation, Indexing, and Slicing

Strings are a versatile data type in Python, and there are several ways to manipulate and work with them, including concatenation, indexing, and slicing.

#### String Concatenation

You can concatenate (combine) strings in Python using the `+` operator. This allows you to join strings together. For instance:

```python
>>> string1 = "abra"
>>> string2 = "cadabra"
>>> magic_string = string1 + string2
>>> magic_string
'abracadabra'
```

> ***Note:** The two strings are combined without any spaces between them.*

Concatenation is also useful for combining related strings, such as creating a full name from a first and last name:

```python
>>> first_name = "Arthur"
>>> last_name = "Dent"
>>> full_name = first_name + " " + last_name
>>> full_name
'Arthur Dent'
```

In this example, the first name and last name are concatenated with a space between them to produce the full name "Arthur Dent". This showcases how easy it is to combine strings dynamically in Python.


#### String Indexing

In Python, each character in a string is assigned a position known as an **index**. To access the character at a specific position, you can use square brackets with the index number. For example:

```python
>>> flavor = "apple pie"
>>> flavor[1]
'p'
```

> ***Note:** In this case, `flavor[1]` retrieves the character at index 1 in "apple pie," which is 'p'.*

In Python, indices start from 0. Therefore, to get the first character of a string, you access the character at index 0:

```python
>>> flavor[0]
'a'
```

A common mistake is forgetting that indexing starts at 0. Attempting to access the first character with index 1 can lead to an off-by-one error, which is a frequent source of bugs.

The following table shows the indices for each character of the string "apple pie":

<table align="center">
  <tr>
    <td>0</td>
    <td>1</td>
    <td>2</td>
    <td>3</td>
    <td>4</td>
    <td>5</td>
    <td>6</td>
    <td>7</td>
    <td>8</td>
  </tr>
  <tr>
    <td>a</td>
    <td>p</td>
    <td>p</td>
    <td>l</td>
    <td>e</td>
    <td> </td>
    <td>p</td>
    <td>i</td>
    <td>e</td>
  </tr>
</table>

Accessing an index that is beyond the string’s length results in an `IndexError`. For instance:

```python
>>> flavor[9]
Traceback (most recent call last):
  File "<pyshell#4>", line 1, in <module>
    flavor[9]
IndexError: string index out of range
```

> ***Note:** The highest valid index is always one less than the length of the string.*

Python also supports **negative indices**, where the last character of a string has index `-1`. For example:

```python
>>> flavor[-1]
'e'
```

In this case, `flavor[-1]` accesses the last character of the string, which is 'e'. The second-to-last character can be accessed with `-2`, and so on. Negative indices offer a convenient way to access characters from the end of the string.

The following table shows the negative indices for each character in the string "apple pie":

<table align="center">
  <tr>
    <td>-9</td>
    <td>-8</td>
    <td>-7</td>
    <td>-6</td>
    <td>-5</td>
    <td>-4</td>
    <td>-3</td>
    <td>-2</td>
    <td>-1</td>
  </tr>
  <tr>
    <td>a</td>
    <td>p</td>
    <td>p</td>
    <td>l</td>
    <td>e</td>
    <td> </td>
    <td>p</td>
    <td>i</td>
    <td>e</td>
  </tr>
</table>

Attempting to access an index that is too negative also leads to an `IndexError`:

```python
>>> flavor[-10]
Traceback (most recent call last):
  File "<pyshell#5>", line 1, in <module>
    flavor[-10]
IndexError: string index out of range
```

Negative indices may not seem immediately useful, but they can simplify situations where you need to access characters from the end of the string. For example, to get the last character of a string input by a user, using a negative index simplifies the process:

```python
last_character = user_input[-1]
```

This is more concise than calculating the final index using `len()`.

#### String Slicing

To extract a portion of a string, Python offers **slicing**, which allows you to create a substring. For example, to get the first three characters of the string `"apple pie"`, you could manually index each character:

```python
>>> first_three_letters = flavor[0] + flavor[1] + flavor[2]
>>> first_three_letters
'app'
```

However, this method is inefficient for larger substrings. Instead, you can use slicing:

```python
>>> flavor[0:3]
'app'
```

> ***Note:** The slice `[0:3]` returns characters from index 0 up to, but not including, index 3.*

In this case, `flavor[0:3]` gives you the first three characters of `"apple pie"`. The slice notation `[x:y]` means "start from index `x`, and go up to but not including index `y`." To understand slicing better, think of a string as a sequence of numbered slots, each corresponding to a character.

For the string "apple pie":

<table align="center">
  <tr>
    <td>0</td>
    <td>1</td>
    <td>2</td>
    <td>3</td>
    <td>4</td>
    <td>5</td>
    <td>6</td>
    <td>7</td>
    <td>8</td>
  </tr>
  <tr>
    <td>a</td>
    <td>p</td>
    <td>p</td>
    <td>l</td>
    <td>e</td>
    <td> </td>
    <td>p</td>
    <td>i</td>
    <td>e</td>
  </tr>
</table>

For example, `flavor[0:3]` returns `"app"`, while `flavor[3:9]` returns `"le pie"`.

If you omit the first index in a slice, Python assumes you want to start from index 0:

```python
>>> flavor[:5]
'apple'
```

Here, `flavor[:5]` is equivalent to `flavor[0:5]` and returns the first five characters of the string.

If you omit the second index in a slice, Python assumes you want to extract from the start index up to the end of the string:

```python
>>> flavor[5:]
' pie'
```

> ***Note:** The slice `[5:]` is equivalent to `[5:9]`.*

If you omit both indices, you get the entire string:

```python
>>> flavor[:]
'apple pie'
```

Unlike indexing, Python won’t raise an `IndexError` for out-of-range slices. For example:

```python
>>> flavor[:14]
'apple pie'
>>> flavor[13:15]
''
```

In the first case, even though the string length is 9, slicing beyond the string's length returns the whole string. In the second case, slicing out-of-bounds (`flavor[13:15]`) returns an empty string.

You can also use negative indices in slicing. Negative indices work the same way as positive indices, but they start counting from the end of the string:

<table align="center">
  <tr>
    <td>-9</td>
    <td>-8</td>
    <td>-7</td>
    <td>-6</td>
    <td>-5</td>
    <td>-4</td>
    <td>-3</td>
    <td>-2</td>
    <td>-1</td>
  </tr>
  <tr>
    <td>a</td>
    <td>p</td>
    <td>p</td>
    <td>l</td>
    <td>e</td>
    <td> </td>
    <td>p</td>
    <td>i</td>
    <td>e</td>
  </tr>
</table>

For example:

```python
>>> flavor[-9:-6]
'app'
```

The slice `flavor[-9:-6]` returns `"app"`, just like `flavor[0:3]`. However, attempting to use a negative index as the upper boundary of a slice may not work as expected. For instance:

```python
>>> flavor[-9:0]
''
```

This returns an empty string because Python assumes the range between `-9` and `0` is empty.

Lastly, you can use a third index for **step slicing**, which indicates the interval between the characters to be included in the slice. For instance:

```python
>>> flavor[2:9:2]
'pepe'
```

> ***Note:** The slice `[2:9:2]` starts at index 2, includes the character at that position, and steps forward by 2 indices each time.*


#### Strings Are Immutable

In Python, **strings are immutable**, which means once a string is created, its contents cannot be modified. For example, trying to change a specific character in a string will result in an error:

```python
>>> word = "goal"
>>> word[0] = "f"
Traceback (most recent call last):
  File "<pyshell#16>", line 1, in <module>
    word[0] = "f"
TypeError: 'str' object does not support item assignment
```

> ***Note:** In Python, `str` is the internal name for the string data type.*

In this case, Python raises a `TypeError`, indicating that strings do not support item assignment.

To modify a string, you must create a new one. For example, to change `"goal"` to `"foal"`, you can use slicing and concatenation:

```python
>>> word = "goal"
>>> word = "f" + word[1:]
>>> word
'foal'
```

In this example, the letter `"f"` is concatenated with the slice of `word[1:]`, which includes everything from index 1 onwards. This creates a new string `"foal"`, leaving the original string `"goal"` unchanged. 

Thus, while you can create new strings based on existing ones, the original string remains unchanged.


#




### Manipulate Strings With Methods

Strings in Python come with various built-in methods that allow you to manipulate and interact with them in different ways. While there are many string methods available, we will focus on some of the most commonly used ones to demonstrate how they work.

#### Converting String Case

In Python, strings are objects, and you can call methods on them to alter their behavior. Some of the most useful methods for changing case include `.lower()`, `.upper()`, and `.capitalize()`:

- The `.lower()` method converts all characters in a string to **lowercase**.
- The `.upper()` method converts all characters in a string to **uppercase**.
- The `.capitalize()` method converts the **first letter** of the string to **uppercase** and all other letters to **lowercase**.

> ***Note:** The dot (`.`) before a method name indicates that the function is being called on the object that precedes it, the string.*

#### Example

```python
name = "Jean-luc picard"
upper_case_name = name.upper()
capitalize_name = name.capitalize()

print(upper_case_name)  # 'JEAN-LUC PICARD'
print(capitalize_name)  # 'Jean-luc picard'
```

You can also use string methods on strings stored in variables. For example:

```python
>>> name = "Jean-luc Picard"
>>> name.lower()
'jean-luc picard'
```

Notice the usage of a dot before the method name. This signifies that the method is being invoked on the string object `name`. 

This syntax helps distinguish string methods from built-in functions like `print()` or `type()`.

#### Detecting Whitespace Strings

The `.isspace()` method is useful when you need to check if a string consists solely of whitespace characters (spaces, tabs, newlines, etc.). This method returns `True` if all characters in the string are whitespace; otherwise, it returns `False`.

```python
>>> name = " "
>>> name.isspace()
True
```

If a string contains any non-whitespace characters, `.isspace()` will return `False`:

```python
>>> name = " j"
>>> name.isspace()
False
```

This method helps to easily detect empty or purely whitespace strings, which can be useful in many programming scenarios.



#### Removing Whitespace From a String

Whitespace characters are any characters that represent blank space, such as spaces, tabs, and line feeds. When dealing with user input or string manipulation, extra whitespace characters are often unintentionally introduced, particularly at the beginning or end of a string. This can cause issues with string comparisons or formatting. Fortunately, Python provides string methods to remove this unnecessary whitespace.

The three main methods for removing whitespace are:

1. **`.rstrip()`**: Removes whitespace from the **right side** (end) of a string.
2. **`.lstrip()`**: Removes whitespace from the **left side** (beginning) of a string.
3. **`.strip()`**: Removes whitespace from **both sides** of a string.

#### Example

```python
>>> name = "Jean-luc Picard     "
>>> name.rstrip()
'Jean-luc Picard'

>>> name = "     Jean-luc Picard"
>>> name.lstrip()
'Jean-luc Picard'


>>> name = "     Jean-luc Picard     "
>>> name.strip()
'Jean-luc Picard'
```

> ***Note:** These methods do not remove spaces from the middle of the string.*

#### Determine if a String Starts or Ends With a Particular String

Two methods, `.startswith()` and `.endswith()`, are useful for checking if a string begins or ends with a specific substring. Both methods return a Boolean value: `True` if the string matches, and `False` if it doesn't.

#### Example

Using `.startswith()` to check if a string starts with specific characters:

```python
>>> starship = "Enterprise"
>>> starship.startswith("en")
False
```

Here, `.startswith("en")` returns `False` because "Enterprise" starts with "E", not "e", and the method is **case-sensitive**.

To make the check case-insensitive, you would need to match the exact casing:

```python
>>> starship.startswith("En")
True
```

Similarly, `.endswith()` checks if a string ends with a specific substring:

```python
>>> starship.endswith("rise")
True
```

Again, `.endswith()` is **case-sensitive**. If you wanted to check in a case-insensitive manner, you'd have to adjust the case or use `.lower()` on both the string and the comparison substring.

The `.startswith()` and `.endswith()` methods return Boolean values (`True` or `False`). These are special data types used to represent logical truth or falsity in Python, and are not the same as strings.


#

### Working With Strings and Numbers

In Python, when user input is obtained through the `input()` function, it is always returned as a string. This becomes particularly important when the input represents numbers. This section explores how to handle strings containing numerical data, how arithmetic operations behave with strings, and how to avoid errors through proper type conversion.

#### Strings and Arithmetic Operators

Although strings in Python can contain digits, they are not the same as numbers. Consider the following example:

```python
>>> num = "2"
>>> num + num
'22'
```

Here, instead of performing numeric addition, Python performs string `concatenation`, combining the two `"2"` characters into `"22"` as a new string.

However, you can "multiply" a string by an integer, which results in the string being repeated:

```python
>>> num = "12"
>>> num * 3
'121212'
```

This operation concatenates the string `"12"` with itself three times, producing `"121212"`. 

On the other hand, attempting to multiply two strings directly results in an error:

```python
>>> "12" * "3"
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
TypeError: can't multiply sequence by non-int of type 'str'
```

Here, Python raises a `TypeError` because the multiplication operator expects an integer on the right side, not another string.

#### Adding Strings and Numbers

What happens when you attempt to add a string and a number?

```python
>>> "3" + 3
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
TypeError: can only concatenate str (not "int") to str
```

This results in a `TypeError` because Python cannot add a string (`"3"`) and an integer (`3`) directly. The `+` operator expects both operands to be of the same type. To perform the addition, you need to convert the string to a number or vice versa.

#### Converting Strings to Numbers

When you want to perform arithmetic operations on strings containing numbers, you need to convert the string to an actual number using `int()` for integers or `float()` for floating-point numbers.

#### Example using `int()`

```python
>>> num = int(input("Enter a number to be doubled: "))
>>> doubled_num = num * 2
>>> print(doubled_num)
```

If the user inputs `2`, the output will be `4`, as the string `"2"` is converted to the integer `2`, allowing for proper arithmetic.

#### Example using `float()`

If the input contains a decimal number:

```python
>>> num = float(input("Enter a decimal number to be doubled: "))
>>> doubled_num = num * 2
>>> print(doubled_num)
```

If the user enters `3.5`, the output will be `7.0`.

Attempting to convert a string representing a floating-point number to an integer, however, results in a `ValueError`:

```python
>>> int("12.0")
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
ValueError: invalid literal for int() with base 10: '12.0'
```

This error occurs because the conversion function `int()` cannot handle decimals. To handle this properly, you would need to first convert the string to a `float`, then round or manipulate it as needed.

#### Converting Numbers to Strings

To concatenate numbers with strings, you must convert the number to a string. Attempting to directly concatenate a number with a string leads to a `TypeError`:

```python
>>> num_pancakes = 10
>>> "I am going to eat " + num_pancakes + " pancakes."
Traceback (most recent call last):
File "<stdin>", line 1, in <module>
TypeError: can only concatenate str (not "int") to str
```

To solve this, use `str()` to convert the integer to a string:

```python
>>> num_pancakes = 10
>>> "I am going to eat " + str(num_pancakes) + " pancakes."
'I am going to eat 10 pancakes.'
```

You can also directly call `str()` on numbers or expressions:

```python
>>> "I am going to eat " + str(10) + " pancakes."
'I am going to eat 10 pancakes.'
```

This method also works with arithmetic expressions:

```python
>>> total_pancakes = 10
>>> pancakes_eaten = 5
>>> "Only " + str(total_pancakes - pancakes_eaten) + " pancakes left."
'Only 5 pancakes left.'
```

#### Find a String in a String

One of the most useful string methods is `.find()`, which allows you to locate a substring within a string. The `.find()` method returns the index of the first occurrence of the substring, or `-1` if the substring is not found.

```python
>>> phrase = "the surprise is in here somewhere"
>>> phrase.find("surprise")
4
```

In this example, `.find("surprise")` returns `4`, which is the index of the first character of "surprise". Python counts indices starting from 0.

If the substring is not found, `.find()` returns `-1`:

```python
>>> phrase.find("eyjafjallajökull")
-1
```

> [!IMPORTANT]
> **The `.find()` method is case-sensitive.** 

```python
>>> "the surprise is in here somewhere".find("SURPRISE")
-1
```

To find all occurrences of a substring, `.find()` will only return the index of the first occurrence. If you want to replace all occurrences of a substring, you can use the `.replace()` method.

#### Replacing Substrings

The `.replace()` method replaces all occurrences of a substring with another string. Here’s an example:

```python
>>> my_story = "I'm telling you the truth; nothing but the truth!"
>>> my_story.replace("the truth", "lies")
"I'm telling you lies; nothing but lies!"
```

Since strings are immutable, the `.replace()` method returns a new string, leaving the original string unchanged:

```python
>>> my_story = my_story.replace("the truth", "lies")
>>> my_story
"I'm telling you lies; nothing but lies!"
```

If you want to replace multiple substrings, call `.replace()` multiple times:

```python
>>> text = "some of the stuff"
>>> new_text = text.replace("some of", "all")
>>> new_text = new_text.replace("stuff", "things")
>>> new_text
'all the things'
```

This shows how to handle more complex string manipulations using `.replace()`.










## Numbers and Math

Python is a versatile programming language that provides robust support for mathematical operations and number manipulation. 

### Integers and Floating-Point Numbers

Python supports three built-in number data types: integers, floating-point numbers, and complex numbers. We will focus on integers and floating-point numbers, the two most commonly used number types.

**Integers**  
An integer is a whole number without any decimal places. For instance, $1$ is an integer, while $1.0$ is not. The data type for integers is called `int`, as shown by the `type()` function:

```python
>>> type(1)
<class 'int'>
```

> ***Note:** There is no limit to how large an integer can be, despite computers having finite memory.*

An integer literal is an explicitly written integer value in your code, similar to a string literal (e.g $1$, $100$). 

Integer literals can be written in two ways:

```python
>>> 1000000
1000000
>>> 1_000_000
1000000
```

Python allows the use of underscores (_) to separate digits and expresses them in a more readable manner.

**Floating-Point Numbers**  
A floating-point number, or `float`, contains a decimal place. The data type for floating-point numbers is `float`:

```python
>>> type(1.0)
<class 'float'>
```

A floating-point literal is a floating-point value explicitly written in your code (e.g, $1.25$).

Floating-point literals can be created in three ways:

```python
>>> 1000000.0
1000000.0
>>> 1_000_000.0
1000000.0
>>> 1e6
1000000.0
```

The first two methods are similar to creating integer literals. For larger numbers, E-notation can be used:

```python
>>> 1e-4
0.0001
```

> ***Note:** E-notation represents a number as the product of a decimal number and $10$ raised to a power.*

Unlike integers, floats have a maximum size, but it is typically well beyond most machines' capabilities.

When exceeding the maximum floating-point number, Python returns a special float value `inf`:

```python
>>> 2e400
inf
```

`inf` stands for infinity and signifies that the number is beyond the maximum floating-point value allowed on your computer. Additionally, there is `-inf` for negative infinity.

#

### Arithmetic Operators and Expressions

In this section, you’ll learn how to do basic arithmetic with numbers in Python, such as addition, subtraction, multiplication, and division. 

**Addition**  
Addition is performed with the `+` operator:

```python
>>> 1 + 2
3
```

> ***Note:** Any time a float is added to a number, the result is another float.*

The two numbers on either side of the + operator are called operands. In the previous example, both operands are integers, but operands do not need to be the same type.

**Subtraction**  
To subtract two numbers, just put a `-` in between them:

```python
>>> 1 - 1
0
>>> 5.0 - 3
2.0
```

> ***Note:** The - operator is also used to denote negative numbers.*

Just like adding two integers, subtracting two integers always results in an `int`. Whenever one of the operands is a `float`, the result is also a `float`.

**Multiplication**  
To multiply two numbers, use the `*` operator:

```python
>>> 3 * 3
9
>>> 2 * 8.0
16.0
```

The type of number you get from multiplication follows the same rules as addition and subtraction. Multiplying two integers results in an `int`, and multiplying a number with a `float` results in a `float`.

**Division**  
The `/` operator is used to divide two numbers:

```python
>>> 9 / 3
3.0
>>> 5.0 / 2
2.5
```

Unlike addition, subtraction, and multiplication, division with the `/` operator always returns a `float`. If you want to make sure that you get an integer after dividing two numbers, you can use `int()` to convert the result:

```python
>>> int(9 / 3)
3
```

> ***Note:** Keep in mind that int() discards any fractional part of the number.*

**Integer Division**  
If writing `int(5.0 / 2)` seems a little long-winded to you, Python provides a second division operator, `//`, called the integer division operator:

```python
>>> 5.0 // 2
2.0
```

> ***Note:** Keep in mind that int() discards any fractional part of the number.*

The `//` operator first divides the number on the left by the number on the right and then rounds down to an integer. This might not give the value you expect when one of the numbers is negative.

For example, $-3$ // $2$ returns $-2$. First, $-3$ is divided by $2$ to get $-1.5$. Then $-1.5$ is rounded down to $-2$. On the other hand, $3$ // $2$ returns $1$.

**Exponents**  
You can raise a number to a power using the `**` operator:

```python
>>> 2 ** 4
16
```

> ***Note:** Exponents don’t have to be integers. They can also be floats.*

**The Modulus Operator**  
The `%` operator, or the modulus, returns the remainder of dividing the left operand by the right operand:

```python
>>> 5 % 3
2
```

One of the most common uses of `%` is to determine whether or not one number is divisible by another. For example, a number $n$ is even if and only if $n$ % $2$ is $0$.

#

### Arithmetic Expressions

In Python, you can create complex expressions by combining operators, numbers, and parentheses. An expression is a combination that Python can evaluate to produce a value. Here are some examples of arithmetic expressions:

```python
>>> 2 * 3 - 1
5
>>> 4 / 2 + 2**3
10.0
>>> -1 + (-3 * 2 + 4)
-3
```

The rules for evaluating expressions in Python follow the same principles as everyday arithmetic, often referred to as the "order of operations." 

| Operator | Description          | Precedence |
|----------|----------------------|------------|
| `**`     | Exponentiation       | High    |
| `*`, `/`, `//`, `%` | Multiplication, Division, Floor division, Modulus | Medium     |
| `+`, `-` | Addition, Subtraction | Low        |

In the example `2 * 3 - 1`, the `*` operator has higher precedence than `-`, so `2 * 3` is evaluated first, resulting in `6`. Then the subtraction is performed, giving the final result of `5`.

It's worth noting that the expressions in the examples may not always follow the rule of placing spaces on either side of all operators. According to [PEP 8](https://pep8.org/#other-recommendations) (Python Enhancement Proposal), which provides style guide recommendations for Python code.

#

### Math Functions and Number Methods

Python has a few built-in functions you can use to work with numbers. In this section, you’ll learn about three of the most common ones:

1. `round()`: Used for rounding numbers to a specified number of decimal places.
2. `abs()`: Gets the absolute value of a number, representing the distance of the number from zero.
3. `pow()`: Raises a number to a specified power.
4. `sqrt()`: Gets the square root of a number.

**The round() function**  

You can use `round()` to round a number to the nearest integer:

```python
>>> round(2.3)
2
```

You can round a number to a given number of decimal places by passing a second argument to `round()`:

```python
>>> round(3.14159, 3)
3.142
```

> ***Note:** The second argument of round() must be an integer. If it isn’t, Python raises a TypeError*

#

**The abs() Function**  

The absolute value of a number $n$ is just $n$ if $n$ is positive, and $-n$ if $n$ is negative. 

To get the absolute value of a number in Python, you use the `abs()` function:

```python
>>> abs(3)
3
>>> abs(-5.0)
5.0
```

The absolute function always returns a positive number of the same type as its argument. 

#

**The pow() Function**  

The `pow()` function takes two arguments. The first is the base, that is the number to be raised to a power, and the second argument is the exponent.

For example, the following uses `pow()` to raise $2$ to the exponent $3$:

```python
>>> pow(2, 3)
8

>>> pow(2, -2)
0.25
```

So, what’s the difference between ** and `pow()`? The pow() function accepts an optional third argument that computes the first number raised to the power of the second number and then takes the modulo with respect to the third number.

In other words, `pow(x, y, z)` is equivalent to ($x ** y$) % $z$. Here’s an example with $x = 2$, $y = 3$, and $z = 2$:

```python
>>> pow(2, 3, 2)
0
```

First, $2$ is raised to the power $3$ to get $8$. Then $8$ % $2$ is calculated, which is $0$.

#

**The sqrt() Method**

The `sqrt()` function in Python is used to calculate the square root of a given number. It is part of the `math` module, so you need to import the module before using it.

Here's an example of using the `sqrt()` function:

```python
>>> import math
>>> math.sqrt(25)
5.0

>>> math.sqrt(2)
1.4142135623730951
```

> [!IMPORTANT]
> **To learn all of python's built-in methods, check the [Mathematical Functions](https://docs.python.org/3/library/math.html) page.**

## Conditional Statements

Conditional Statements in programming enable the program to make decisions and execute specific code blocks based on certain conditions, enhancing its flexibility and adaptability.

### Conditional Statements and Truth Tables

Conditional Statements in programming enable diverse execution paths based on logical conditions using `if`, `elif` and `else` statements. Utilizing truth tables to evaluate conditions, they systematically ensure precise decision-making, enhancing program functionality and reliability.

```python
number = 10;    

if ( number > 0 ):   
  print(f"It's a positive number")
```

When a conditional statement is executed, two possible outcomes are provided: `True` and `False`. In the previous case, the compiler substitutes the variable `number` with its stored value, resulting in the following evaluation: *is 10 greater than 0?*. 

In this instance, the answer is `True`. As a result, the compiler returns a value other than $0$ to the `if()` function, permitting the execution of the subsequent command line.

Boolean expressions are essential in programming, denoting true/false conditions. They employ logical operators (`AND`, `OR`, `NOT`) to combine or negate conditions, enabling intricate decision-making in code. Evaluating these expressions empowers programs to execute tailored actions based on outcomes, optimizing efficiency and functionality.


<table>
<tr><th>&nbsp;&nbsp;&nbsp;TRUTH TABLE FOR AND &nbsp;&nbsp;&nbsp;
</th><th>&nbsp;&nbsp;&nbsp;TRUTH TABLE FOR OR&nbsp;&nbsp;&nbsp;</th>
<th>&nbsp;&nbsp;&nbsp;TRUTH TABLE FOR NOT &nbsp;&nbsp;&nbsp;</th>
</tr>
<tr>
  <td>
  
|  OPERAND 1    |  OPERAND 2  | RESULT |
|:-----------:|:-----------:|:-------------:|
|   **`false`**   |   **`false`**   |    **`false`**    |
|   **`false`**   |   **`true`**   |    **`false`**    |
|   **`true`**   |   **`false`**   |    **`false`**    |
|   **`true`**   |   **`true`**   |    **`true`**    |

</td>
<td>

|  OPERAND 1    |  OPERAND 2  | RESULT |
|:-----------:|:-----------:|:-------------:|
|   **`false`**   |   **`false`**   |    **`false`**    |
|   **`false`**   |   **`true`**    |     **`true`**    |
|   **`true`**    |   **`false`**   |     **`true`**    |
|   **`true`**    |   **`true`**    |     **`true`**    |

</td>

<td>

| &nbsp;OPERAND &nbsp;|  &nbsp; RESULT &nbsp;&nbsp;|
|:-----------:|:-----------:|
|   **`not true`**   |      **`false`**    |
|   **`not false`**   |      **`true`**    |

</td>
</tr> 
</table>
</td><td>
  
> *Any result from a comparison that is a non-zero value is treated as true, whereas 0 is interpreted as false.*

#

### The if Statement

An `if` statement instructs Python to execute a specific portion of code only when a certain condition is satisfied. 

For instance, the check following `if` statement:

```python
if 2 + 2 == 4:
    print("2 and 2 is 4")

print("Try another operation !")
```

> ***Note:** Omitting the colon (:) after the test condition in an if / elif / else statement results in a SyntaxError.*

You can interpret this as: "if $2 + 2$ equals $4$, then print the string ' $2$ and $2$ is $4$ '.”

An `if` statement consists of three components:

1. The `if` keyword.
2. A test condition, followed by a colon.
3. An indented block of code that executes if the test condition is True.

In the given example, the test condition is $2 + 2 == 4$. Since this expression is `True`, executing the `if` statement in IDLE displays the text " $2$ and $2$ is $4$ ". If the test condition is `False` (for instance, $2 + 2 == 5$), Python skips over the indented block of code and continues execution on the next non-indented line.

#

### The else Keyword

The `else` keyword is used after an `if` statement in order to execute some code only if the `if` statement’s condition is `False`.

```mermaid
flowchart LR
  start[Start] --> a{Test}
  a{Test} --> | True | code1{{Code}}
  a{Test} --> | False | code2{{Code}}
```

The following script uses else to shorten the code in the previous script for displaying whether or not a student passed a class:

```python
grade = 40

if grade >= 70:
  print("You passed the class!")
else:
  print("You did not pass the class")

print("Thank you for attending.")
```

> ***Note:** The line that prints "Thank you for attending." still runs, even if the indented block of code after else is executed.*

In English, the if and else statements together read as: *If the grade is at least* $70$, *then print the string* " $You \\:\\:  passed \\:\\:  the \\:\\:  class!$ "; o*therwise, print the string* " $You \\: \\: did \\:\\:  not \\:\\:  pass \\:\\:  the \\:\\:  class!$ ".


Notice that the `else` keyword has no test condition, and is followed by a colon. No condition is needed, because it executes for any condition that fails the `if` statement’s test condition.

#

### The elif Keyword

The `elif` keyword is short for "else if" and can be used to add additional conditions after an `if` statement.

Just like if statements, elif statements have three parts:
1. The `elif` keyword.
2. A test condition, followed by a colon.
3. An indented code block that is executed if the test condition evaluates to `True`.


The following script combines `if`, `elif`, and `else` to print the letter grade a student earned in a class:

```python
1.   grade = 85
2. 
3.   if grade >= 90:
4.     print("You passed the class with a A.")
5.   elif grade >= 80: 
6.     print("You passed the class with a B.")
7.   elif grade >= 70: 
8.     print("You passed the class with a C.")
9.   else: 
10.    print("You did not pass the class :(")
11.
12.   print("Thanks for attending.")
```

Analyzing the code above, we can observe that the condition for the `if` statements is checked on both lines $5$ and $7$.

However, only the block associated with the first `True` test condition, which is the condition on line 5, is executed. All remaining `elif` and `else` blocks are skipped, so executing the script has the following output:

```
You passed the class with a B.
Thanks for attending.
```

Let’s break down the execution of the script step-by-step:

1. `grade` is assigned the value $85$ in the line $1$.
2. `grade` >= $90$ is `False`, so the `if` statement in the line $3$ is skipped.
3. `grade` >= $80$ is `True`, so the block under the `elif` statement in line $5$ is executed.
4. The `elif` and `else` statements in lines $7$ and $9$ are skipped, since the condition for the `elif` statement on line $5$ was met.
5. Finally, line $6$ is executed and "Thanks for attending." is printed.

The `if`, `elif`, and `else` keywords are some of the most commonly used keywords in the Python language. They allow you to write code that responds to different conditions with different behavior.

You can even nest an `if` statement inside another one to write code that handles tremendously complex logic!

#

### Nested if Statements

A `nested if` statement involves placing an if statement within another if statement. In cases where the execution desires a `True` statement after an `else` statement has failed, the utilization of nested if statements becomes crucial to maintain the overall code flow in a semantically ordered structure.

The complexity that results from using deeply `nested if` statements may make it difficult to predict how your program will behave under given conditions. For this reason, this kind of statement must be used with caution.

```mermaid
flowchart LR
  start[Start] --> a{Test}
  a{Test} --> | True | code1{{Code}}
  a{Test} --> | False | code2{{Code}}

  code2 --> b{Test}
  b --> | True | code3{{Code}}
  b--> | False | code4{{Code}}
```

> ***Note:** Flowchart of a nested if statement.*

Consider a scenario where a business offers discounts based on the age and student status of its customers. The following Python code implements a discount eligibility system with nested if statements and logical conditions.

```python
age = int(input("Enter an Age: "))
is_student = True if input("It is a Student? (y/n)").lower() == "y" else False

# Nested if statements with and/or conditions to determine discount eligibility
if is_student:
  if age <= 18:
      discount = "50%"
  elif age <= 25:
      discount = "20%"
  else:
      discount = "10%"
else:
    discount = "No discount"

# Display the result
print(f"For a {age}-year-old {'student' if is_student else 'non-student'}, the discount is: {discount}")
```

Let's break down the execution of the script step-by-step:

1. `age` is assigned the value entered by the user in the line marked $1$.
2. The user is prompted to input whether they are a student (yes/no), and `is_student` is assigned `True` or `False` accordingly.
3. If `is_student` is `True`, the nested `if` statements in lines $5$ - $11$ are evaluated:
   - If `age` is $18$ or below, `discount` is assigned $50$%.
   - If `age` is $25$ or below, `discount` is assigned $20$%.
   - If neither condition is met, `discount` is assigned $10$%.
4. If `is_student` is `False`, `discount` is assigned "No discount" in line $13$ .
5. The result is displayed in the last line, indicating the age, student status, and the corresponding discount.

Using nested if statements can become complex and potentially make the code harder to understand. If you notice that you have multiple layers of nested if statements, it's advisable to reconsider your approach and explore ways to simplify the code for better readability and maintainability.

### Truthy and Falsy Values in Python

In Python, evaluating the truthiness or falsiness of a variable can be crucial when determining its state. The concept of truthy and falsy values revolves around understanding which values are considered equivalent to `True` or `False` in a boolean context.

Let's explore this with a practical example:

```python
count = 0

if count:
    print(f"Count is: {count}")
else:
    print("Count is zero.")
```
In this scenario, we check whether the variable `count` holds a falsy value, meaning it is equivalent to zero. If the condition is met, the program prints the count; otherwise, it prompts the user that the count is zero.

Here are some common examples of falsy values in Python:

- `None`
- `False`
- Numbers numerically equal to zero, such as $0$, $0.0$, $0j$, `decimal.Decimal(0)`, and `fraction.Fraction(0, 1)`
- Empty sequences and collections, like `[]`, `{}`, `()`, `set()`, `''`, `b''`, `bytearray(b'')`, `memoryview(b'')`, and `range(0)`.
- Objects for which `obj.__bool__()` returns `False` or `obj.__len__()` returns 0, given that `obj.__bool__` is undefined.




## Loop Structures

A loop is a block of code that gets repeated over and over again either a specified number of times or until some condition is met. There are two kinds of loops in Python: `while` loops and `for` loops. These structures provide efficiency and flexibility in implementing repetitive logic.

### The while Loop

While loops repeat a section of code as long as a certain condition is `True`. The structure consists of two main parts:

1. **The While Statement:** It begins with the `while` keyword, followed by a test condition, and ends with a colon `:`.

2. **The Loop Body:** This section contains the code that gets repeated at each iteration of the loop.

When a `while` loop is executed, Python evaluates the test condition. If the condition is `True`, the code in the loop body is executed. If the condition is `False`, the code in the body is skipped, and the program proceeds to the next section.

After executing the loop body, Python returns to the `while` statement, re-evaluates the test condition, and repeats the process. This cycle continues until the test condition becomes `False`. If the test condition is initially `False`, the body is skipped entirely.

This process repeats until the test condition fails, causing Python to loop over the code in the body of the `while` loop.

```mermaid
---
title: While Loop Flowchart
---
flowchart LR
  start[Start]
  start --> teste{Condition}
  teste --> |False| endcode{{End}}
  teste --> |True| code2{{Loop Body}}
  code2 --> teste
```


Let’s look at an example:

```python
n = 1
while n < 5:
  print(n)
  n = n + 1
```

Let's break down the code script step-by-step:

1. The variable `n` is initially assigned the value $1$.
2. A `while` loop is initiated with the condition $n < 5$. The loop's body executes as long as the condition $n < 5$ is `True`.
    - Inside the loop body:
      - The current value of `n` is printed to the screen.
      - `n` is incremented by $1$.
3. The loop continues executing until the condition $n < 5$ becomes `False`.

This process repeats until the test condition $n < 5$ becomes `False`. The table below summarizes the steps:



| Step   | Value of `n` | Test Condition | Action Taken                           |
| :------: | :------------: | :---------------: | -------------------------------------- |
| 1      | 1            | 1 < 5 `True`    | Print 1; Increment `n` to 2            |
| 2      | 2            | 2 < 5 `True`     | Print 2; Increment `n` to 3            |
| 3      | 3            | 3 < 5 `True`     | Print 3; Increment `n` to 4            |
| 4      | 4            | 4 < 5 `True`    | Print 4; Increment `n` to 5            |
| 5      | 5            | 5 < 5 `False`   | Loop ends; Nothing printed, loop ends |


In summary, the `while` loop iterates over the code block as long as the condition $n < 5$ remains true. The loop prints the current value of $n$ and increments it until the condition becomes `False`.

If you're not careful, you can unintentionally create an infinite loop, which occurs when the test condition always evaluates to true. In an infinite loop, the loop body keeps executing endlessly.

Consider the following example of an infinite loop:

```python
n = 1
while n < 5:
    print(n)
```

The key distinction between this `while` loop and the previous one is that $n$ is never incremented within the loop body. In each iteration of the loop, $n$ remains equal to $1$. Consequently, the test condition $n < 5$ is always `True`, leading to the continuous printing of the number $1$. This loop persists indefinitely, resulting in an infinite loop.

Infinite loops aren’t inherently bad. Sometimes they are exactly the kind of loop you need. For instance, code interacting with hardware might use an infinite loop to continually check if a button or switch has been activated.

If your program enters an infinite loop, you can force Python to quit by pressing Ctrl+C when using a Terminal:

```python
Traceback (most recent call last):
  File "<pyshell#8>", line 2, in <module>
    print(n)
KeyboardInterrupt
```

> ***Note:** Python will stop the program and raise a KeyboardInterrupt error.*

Now, let's look into a practical example of a `while` loop. One common use of a while loop is to validate user input continuously. The program keeps prompting the user until valid input is provided. 

Consider the following example, where a user is repeatedly asked for a positive number:

```python
num = float(input("Enter a positive number: "))
while num <= 0:
    print("That's not a positive number!")
    num = float(input("Enter a positive number: "))
```

Here, the test condition $num <= 0$ checks if the user entered a positive number. If the input is positive, the loop ends; otherwise, the user is notified of the mistake, and the loop continues until valid input is received.

While loops are ideal for repeating a code section as long as a certain condition is met. However, they are not designed for iterating a fixed number of times.

#

### The for Loop

In Python, a `for` loop is a control flow statement that iterates over a sequence of elements, executing a specified block of code for each element in the sequence. The loop allows you to process each item in a collection (such as a list, tuple, or string) one at a time, making it convenient for tasks like iterating through the characters of a string or processing elements in a list. The loop continues until it has processed all the elements in the collection.

```mermaid
---
title: For Loop Flowchart
---
flowchart LR
  start[Start]
  start --> teste{Last Element?}
  teste --> |False| endcode{{End}}
  teste --> |True| code2{{Loop Body}}
  code2 --> code3{{Next Iteration}}
  code3 --> teste
```

Similar to the `while` loop, the `for` loop consists of two primary components:
1. **The for statement:** Begins with the `for` keyword, followed by a membership expression, and ends in a colon `(:)`.
2. **The loop body:** Encompasses the code segment to be executed in each iteration of the loop.


Let's examine an example where the following `for` loop prints each letter of the string "Python" individually:

```python
for letter in "Python":
  print(letter)
```

In this instance, the `for` statement is `for letter in "Python"`, and the membership expression is `letter in "Python"`. In each iteration, the variable `letter` is assigned the next letter in the string "Python," followed by printing the value of `letter`.

The loop iterates once for each character in the string "Python". The table below summarizes the execution of this `for` loop:

<table align = "center">
  <th>Step</th>
  <th>Value of letter</th>
  <th>Action</th>
  <body>
    <tr align = "center">
      <td>1</td>
      <td>P</td>
      <td>P is printed</td>
    </tr>
    <tr align = "center">
      <td>2</td>
      <td>y</td>
      <td>y is printed</td>
    </tr>
    <tr align = "center">
      <td>3</td>
      <td>t</td>
      <td>t is printed</td>
    </tr>
    <tr align = "center">
      <td>4</td>
      <td>h</td>
      <td>h is printed</td>
    </tr>
    <tr align = "center">
      <td>5</td>
      <td>o</td>
      <td>o is printed</td>
    </tr>
    <tr align = "center">
      <td>6</td>
      <td>n</td>
      <td>n is printed</td>
    </tr>
  </body>
</table>

To illustrate the advantage of `for` loops in iterating over collections, let's transform the previous example, originally implemented with a `for` loop, into an equivalent `while` loop. In this case, we'll introduce a variable to keep track of the index representing the next character in the string. At each iteration, we'll print the character at the current index and then increment the index.

The loop will terminate when the value of the index variable is equal to the length of the string. It's important to note that indices start at $0$, and for the string "Python," the last index is $5$.

Here's how you might implement the same logic using a while loop:

```python
word = "Python"
index = 0
while index < len(word):
  print(word[index])
  index = index + 1
```

Comparatively, this `while` loop version is noticeably more complex than the original `for` loop. Not only is the for loop less intricate, but the code itself also appears more natural and intuitive.


Sometimes, it's beneficial to iterate over a range of numbers, and Python offers a convenient built-in function called `range()` for precisely that purpose. The `range()` function generates a sequence of numbers.

For instance, `range(3)` produces the range of integers starting from $0$ up to, but not including, $3$ – namely, $0, 1,$ and $2$. Using `range(n)`, where n is any positive number, allows you to execute a loop exactly n times. Consider the following example where a `for` loop prints the string "Python" three times:

```python
for _ in range(3):
  print("Python")
```

> ***Note:** The use of _ in this context is to indicate that the variable is not relevant to the code inside the loop.* 

Additionally, you can specify a starting point for the range. For example, `range(1, 5)` creates the range of numbers 1, 2, 3, and 4. The first argument is the starting number, and the second argument is the endpoint, which is not included in the range.

Using the two-argument version of `range()`, the subsequent for loop prints the square of every number from $10$ up to, but not including, $20$:

```python
for n in range(10, 20):
  print(n * n)
```

Now, let's explore a practical example. The following program prompts the user to input an amount and then displays how to split that amount between $2, 3, 4,$ and $5$ people:

```python
amount = float(input("Enter an amount: "))
for num_people in range(2, 6):
    print(f"{num_people} people: ${amount / num_people:,.2f} each")
```

> ***Note:** The formatting specifier , .2f is used to format the amount as a fixed-point number rounded to two decimal places.*

The for loop iterates over the numbers $2, 3, 4$ and $5$, printing the number of people and the amount each person should pay. 

Executing the program with an input of $10$ produces the following output:

```
Enter an amount: 10
2 people: $5.00 each
3 people: $3.33 each
4 people: $2.50 each
5 people: $2.00 each
```

In Python, for loops are generally used more frequently than while loops. Most of the time, a for loop is more concise and easier to read than an equivalent while loop.

#

### Nested Loops

As long as you indent the code correctly, you can even put loops inside of other loops.

Peço desculpas pela confusão. Vamos corrigir e melhorar o texto sem alterar o código:

```python
for n in range(1, 4):
  for j in range(1, 4):
    print(f"n = {n} e j = {j}")
```

When Python enters the body of the first for loop, the variable n is assigned the value $1$. Then the body of the second for loop is executed, and $j$ is assigned values from $1$ to $3$ (inclusive). The first thing printed is $n = 1$ and $j = 1$.

After executing the `print()` function, Python continues within the inner for loop, assigns to $j$ the next value in the range, and then prints $n = 1$ and the updated $j$ value. This process repeats until all values in the inner loop are exhausted. 

Next, the outer for loop increments $n$ to $2$, and the inner for loop executes again, printing $n = 2$ and the values of $j$ in the range $1$ to $3$. This pattern continues until the outer for loop completes its iterations.

The two loops continue to execute in this fashion, and the final output looks like this:

```
n = 1 and j = 1
n = 1 and j = 2
n = 1 and j = 3
n = 2 and j = 1
n = 2 and j = 2
n = 2 and j = 3
n = 3 and j = 1
n = 3 and j = 2
n = 3 and j = 3
```

A loop inside of another loop is called a nested loop, and they come up more often than you might expect. You can nest while loops inside of for loops, and vice versa, and even nest loops more than two levels deep!

Important: Nesting loops inherently increases the complexity of your code, as you can see by the dramatic increase in the number of steps run in the previous example compared to examples with a single for loop. Using nested loops is sometimes the only way to get something done, but too many nested loops can have a negative effect on a program’s performance.


## Jump Statements

Jump Statements are used to control the execution flow of a program. They allow the program to skip to a specific part of the code, exit a loop prematurely, or return from a function. Some examples of jump statements include break, continue, pass and return. These commands are powerful but should be used with caution to maintain code readability and structure.

Sometimes, it's convenient to control the output of a looping structure (`for` and `while`), in a way other than the conditional tests at the beginning or end of it. For this purpose, you can use certain commands that allow you to divert the normal execution of a program.

#

### Jump Statements - Break Command

The `break` command is used to abruptly exit from a loop - `for` and `while`. It helps control the flow by immediately ending the current loop, allowing the program to proceed with the next instructions outside of the loop.

```python
break
```

The `break` command is a powerful tool for controlling program flow, providing enhanced control over how your code behaves in specific situations, including:

- **Loop Termination:** The `break` command is employed to exit a loop prematurely, based on certain conditions. This enables efficient loop control, allowing you to halt iterations when specific criteria are met.
- **Switch Statement Control:** Within switch statements, `break` is used to terminate the current case and prevent fall-through behavior. This ensures that only the intended case is executed, enhancing the predictability of your code.
- **Emergency Exit:** In scenarios where unexpected conditions or errors arise, the `break` command can be utilized to perform an emergency exit from a loop, preventing the program from getting stuck in an infinite loop or erroneous processing.

These applications of the *break* command exemplify its significance in managing program execution and ensuring logical and structured code.

```python
# Prompting user for input
while True:
  user_input = input("Enter a number (or 'exit' to end): ")

  # Check if the user wants to exit
  if user_input.lower() == 'exit':
    print("Exiting the loop.")
    break  # Exit the loop if the user enters 'exit'
  
  # Check if the input is a positive number
  if user_input.isdigit() and int(user_input) > 0:
    print(f"Square of {user_input}: {int(user_input) ** 2}")
  else:
    print("Invalid input. Please enter a positive number or 'exit'.")

```

> ***Note:** When executed within a nested loop, the break command interrupts the innermost loop, allowing the program to continue processing in the next iteration of the immediate outer loop.*

#

### Jump Statements - Return Command

The `return` command plays a crucial role in Python functions. When included within a function, it concludes the function's execution and conveys a value back to the calling code. This not only provides a means to terminate the function but also supplies essential data for further processing.

```python
return return_expression
```

By providing a method for functions to deliver results, the `return` command contributes to enhanced modularity and efficient data flow within programs. Now, let's delve into its three key applications:

- **Function Output:** Use `return` to provide meaningful output from functions. It allows functions to generate results that can be utilized in other parts of the program.
- **Function Termination:** The `return` command acts as an exit point for a function. Once encountered, the function's execution terminates, and control returns to the calling code.
- **Error Handling:** `return` can also be used to handle errors. By returning specific error codes or values, functions can indicate failures and allow the calling code to respond appropriately.

Effectively utilizing the `return` command is essential for producing modular and organized code structures.

```python
def add(a, b):
    sum_result = a + b
    return sum_result

# Call the add function and store the returned value in result
num1, num2 = 5, 3
result = add(num1, num2)
print(f"The sum of {num1} and {num2} is: {result}")
```

> ***Note:** The return command in the add function calculates the sum of its two integer arguments and returns the result, allowing the calculated value to be used in the calling code.*

#

### Jump Statements - Pass Command

The `pass` command in Python serves as a minimalist placeholder, functioning as a no-operation statement. Essentially, it acts as a syntactic filler, enabling the creation of empty code blocks without triggering syntax errors. While it doesn't execute any specific tasks, it provides a means to preserve the structural integrity of your code when a block requires no action.

```python
pass
```

The `pass` command proves useful in various scenarios:

- **Code Skeletons:** During the initial stages of code development, when creating a rough outline, you can utilize `pass` as a temporary placeholder to define the structure before implementing the actual logic.
- **Conditional Blocks:** In situations where conditional statements or loops have branches that require no action, `pass` can be employed to avoid syntax errors and maintain syntactical correctness.
- **Class Definitions:** When defining a class that is currently empty or not yet implemented, *pass* prevents errors until the class methods are implemented.

While seemingly minimal, the *pass* command is a valuable tool for preserving code readability and structure during different stages of development.

```python
# Placeholder class for database connection (to be implemented later)
class DatabaseConnection:
    def connect(self):
        pass  # Placeholder for connection logic

    def query(self, sql):
        pass  # Placeholder for query logic

# Usage of the functions and class
numbers_to_process = [1, 2, 3, 4, 5, 6, 7, 8, 9]
process_even_numbers(numbers_to_process)

# Creating a database connection (to be implemented later)
db_connection = DatabaseConnection()
db_connection.connect()
```

> ***Note:** In this example, the pass command it is employed in a class definition as a placeholder until the class methods are implemented.*

#

### Jump Statements - Continue Command

The `continue` command is a powerful tool that allows precise control over loop flow in Python. When encountered within a loop, it instantly jumps to the next iteration, bypassing the remaining code for the current iteration. This is especially useful when you want to skip certain iterations based on specific conditions, without prematurely exiting the loop.

```python
continue
```

By elegantly sidestepping the remaining code within the current iteration, it proves invaluable for selectively bypassing iterations influenced by distinct conditions. This adept maneuver fortifies loop efficiency and pliability, a testament to the versatile capabilities of the *continue* command. Now, let's delve into its three key applications:

- **Selective Skipping:** Use `continue` when you need to skip specific iterations of a loop based on certain conditions while continuing the loop's execution. This can help avoid unnecessary calculations or processing.
- **Loop Efficiency:** By skipping certain iterations using `continue` you can optimize your loops for better performance, especially when dealing with large datasets or complex conditions.
- **Avoid Infinite Loops:** Be cautious not to create infinite loops inadvertently by using *continue* without proper logic. Make sure your loop's exit conditions are still achievable despite using the *continue* statement.

These applications of the `continue` command allow you to harness finer control over your code, leading to more efficient and concise programming.

```python
# Example: Using continue to skip iterations in a loop
for i in range(1, 6):
    if i == 3:
        print(f"Skipping iteration {i}")
        continue  # Skip the remaining code for this iteration
    print(f"Iteration: {i}")
```

> ***Note:** In this example, the program uses a for loop to iterate from 1 to 5. When i is equal to 3, the continue statement is encountered. This skips the remaining code inside the loop for that iteration and proceeds to the next iteration.*


## Recover From Errors

Encountering errors in your code might be frustrating, but it’s entirely normal! Even the best programmers face such challenges.

Errors aren’t always a negative thing. For instance, attempting to divide $1$ by $0$ results in a `ZeroDivisionError`. If the divisor is entered by a user, you have no way of knowing ahead of time whether or not the user will input a $0$!

To create robust programs, it's crucial to handle errors caused by invalid user input or any other unpredictable sources. 

### A Zoo of Exceptions

When encountering an exception in Python, understanding the nature of the error is crucial. Python provides a variety of built-in exception types, each describing different kinds of errors. Throughout this book, you've come across various errors, and here we'll compile some, along with introducing a few new ones to the list.

**ValueError**  
A `ValueError` occurs when an operation encounters an invalid value. 

For instance, attempting to convert the string "not a number" to an integer results in a `ValueError`:

```python
>>> int("not a number")
Traceback (most recent call last):
  File "<pyshell#1>", line 1, in <module>
    int("not a number")
ValueError: invalid literal for int() with base 10: 'not a number'
```

> ***Note:** The exception name is displayed on the last line, followed by a description of the specific problem.*

**TypeError**  
A `TypeError` occurs when an operation is performed on a value of the wrong type. 

For example, attempting to add a string and an integer will result in a `TypeError`:

```python
>>> "1" + 2
Traceback (most recent call last):
  File "<pyshell#1>", line 1, in <module>
    "1" + 2
TypeError: can only concatenate str (not "int") to str
```

**NameError**  
A `NameError` occurs when attempting to use a variable name that hasn't been defined yet:

```python
>>> print(does_not_exist)
Traceback (most recent call last):
  File "<pyshell#3>", line 1, in <module>
    print(does_not_exist)
NameError: name 'does_not_exist' is not defined
```

**ZeroDivisionError**   
A `ZeroDivisionError` occurs when the divisor in a division operation is $0$:

```python
>>> 1 / 0
Traceback (most recent call last):
  File "<pyshell#4>", line 1, in <module>
    1 / 0
ZeroDivisionError: division by zero
```

**OverflowError**  
An `OverflowError` occurs when the result of an arithmetic operation is too large, typically with floating-point numbers:

```python
>>> pow(2.0, 1_000_000)
Traceback (most recent call last):
  File "<pyshell#6>", line 1, in <module>
    pow(2.0, 1_000_000)
OverflowError: (34, 'Result too large')
```

> ***Note:** Note that OverflowErrors can only occur with floating-point numbers due to Python's integers having unlimited precision.*

For a comprehensive list of Python's built-in exceptions, you can refer to the [official documentation](https://docs.python.org/3/library/exceptions.html).

#

### Handling Exceptions with try and except

Encountering exceptions is a common aspect of programming, but rather than letting the program crash, you can use the `try` and `except` keywords to catch errors and handle them appropriately. 

For instance, if you expect a user to input an integer and want to handle the case where they provide a non-integer value, you can utilize these keywords.

Let's look at an example:

```python
try:
  number = int(input("Enter an integer: "))
except ValueError:
  print("That was not an integer")
```

Let's break down the code step-by-step:
- The `try` block contains the code that might raise an exception.
- In this case, the user is prompted to input an integer. The `int()` function is used to convert the input to an integer.
- If the user inputs a non-integer value, a `ValueError` will be raised.
- The `except` block is executed when a `ValueError` occurs, preventing the program from crashing. Instead, it prints the message "That was not an integer."

Handling multiple exception types is possible by listing them in parentheses after `except`:

```python
def divide(num1, num2):
  try:
    print(num1 / num2)
  except (TypeError, ZeroDivisionError):
    print("encountered a problem")
```

Let's break down the code step-by-step:
- The function `divide()` attempts to perform the division operation on `num1` and `num2`.
- If a `TypeError` or `ZeroDivisionError` occurs, the `except` block is executed, displaying the message "Encountered a problem".

For more detailed and user-friendly error messages, you can handle each exception individually:

```python
def divide(num1, num2):
  try:
    result = num1 / num2
    print("Result of division:", result)
  except ZeroDivisionError:
    print("num2 must not be 0")
  except TypeError:
    print("An unexpected error occurred")
```

Let's break down the code step-by-step:
- In this example, a `TypeError` and a `ZeroDivisionError` are handled separately.
- If `num1` or `num2` is not a number, a `TypeError` is raised, and the message "Both arguments must be numbers" is displayed.
- If `num2` is 0, a `ZeroDivisionError` is raised, and the message "num2 must not be 0" is displayed.

#

### The "Bare" except Clause

It's possible to use the `except` keyword without specifying a particular exception, creating what's known as a "bare" `except` clause:

```python
try:
  # Do lots of hazardous things that might break
except:
  print("Something bad happened!")
```

If any exception is raised during the execution of the code within the `try` block, the associated `except` block will run, and the message "Something bad happened!" will be displayed.

While this might seem like a way to ensure your program never crashes, it's generally considered a bad practice and is frowned upon. There are several reasons for this, with the primary one being that catching every exception could potentially hide bugs in your code. Relying on a broad `except` clause may give you a false sense of confidence that your code works as expected.

For new programmers, it's crucial to note that if you only catch specific exceptions, Python will print the traceback and error information when unexpected errors occur. This provides more information for debugging, allowing you to identify and address issues in your code effectively.




## Iterables in Python: Unveiling the Magic of Iteration

Python, renowned for its readability and simplicity, offers a variety of powerful and flexible data structures. Among them, iterables play a crucial role, enabling efficient iteration through elements. Let's delve into the concept of iterables in Python, understand how they work, and discover some of the structures falling under this category.

### What are Iterables

In the Python programming language, the concept of iterables plays a pivotal role in enabling the iteration operation, allowing developers to traverse elements seamlessly. An object is deemed iterable if it supports this operation, permitting the sequential traversal of its elements, typically accomplished through the utilization of a `for` loop. Widely-used iterable examples include strings, lists, tuples, dictionaries, and sets. Furthermore, Python extends the flexibility of iterability to custom objects by allowing the implementation of special methods, namely `__iter__` and `__next__`.

The significance of iterables extends beyond mere technicalities; they offer a powerful and expressive means of representing and interacting with diverse collections of data. Whether dealing with fundamental data structures or creating bespoke objects, iterables enhance the readability and efficiency of Python code when working with a variety of data types.

Consider the following perspective: iterables serve as a gateway to a more elegant and streamlined coding experience. The ability to seamlessly traverse elements one at a time contributes to the expressiveness of Python, aligning with its philosophy of code readability and simplicity.

In essence, iterables are not just a technical feature of the language; they embody a fundamental aspect of Python's design philosophy. By embracing the concept of iterables, developers can create code that is not only functional but also exhibits a level of elegance and efficiency that defines Python as a language celebrated for its readability and versatility.

### Harnessing the Power of Iteration with the for Loop

The `for` loop stands as a cornerstone in the Python programming language, providing a robust and intuitive mechanism for iterating through various iterables. Its operation is elegantly simple: at each iteration, the loop retrieves the next element from the iterable, presenting an optimal environment for performing operations on each item. This distinctive feature not only enhances code readability but also mitigates the necessity for cumbersome manual index handling, promoting a cleaner and more expressive coding style.

Let's delve into a practical example to illuminate the efficiency and clarity that the `for` loop brings to the iterative process:

```python
# Using the for loop to iterate through elements
for element in iterable:
    print(element)
```

In this concise snippet, the `for` loop effortlessly navigates through the elements of the iterable, assigning each element to the variable `element` in turn. This streamlined syntax encapsulates the essence of iteration in Python, emphasizing the language's commitment to readability and simplicity.

The `for` loop is not just a functional construct; it encapsulates a philosophy that aligns with Python's core principles. It transforms iteration from a mundane task into a fluid and expressive operation, contributing to the overall elegance of Python code. As developers, embracing the `for` loop empowers us to write code that not only functions effectively but also communicates its intent in a clear and accessible manner.

### The iter() and next() Functions

The `iter()` and `next()` functions are integral components in the process of iteration in Python, providing developers with a powerful and flexible mechanism for traversing elements within iterables. Understanding these functions is crucial for gaining precise control over the iteration process and efficiently accessing elements in a sequential manner.

**The iter() Function**  
When a `for` loop is initiated on an iterable object, such as a list or a tuple, it implicitly calls the `iter()` function on that object. The purpose of this function is to return an iterator, a specialized object with a `__next__` method. The iterator is responsible for keeping track of the current state of the iteration, allowing elements to be retrieved one at a time.

```python
# Using iter() to create an iterator
iterator = iter(iterable)
```

By obtaining an iterator through `iter()`, the loop gains the ability to call the `__next__` method on it, making it possible to retrieve elements sequentially.

**The next() Function**  
The `next()` function plays a pivotal role in the iteration process. It is employed to fetch the next element from the iterator, advancing the iteration state. This function is particularly beneficial when developers need more fine-grained control over the iteration, enabling them to dictate when and how elements are retrieved.

```python
# Using next() to retrieve the next element from the iterator
element = next(iterator)
```

Using `next()` allows developers to dictate the pace of iteration, facilitating conditional retrieval or skipping of elements based on specific criteria. Moreover, it helps in scenarios where a developer may want to extract elements from an iterator selectively.

These functions, `iter()` and `next()`, empower developers with the flexibility needed to navigate through various data structures efficiently. Whether working with standard iterables or custom objects implementing iteration protocols, mastering these functions enhances the precision and control one can exert over the iteration flow. This, in turn, contributes to writing more expressive, readable, and efficient Python code.

### Elevating Code Efficiency with List Comprehensions

List comprehensions stand out as versatile and potent constructs within the Python programming paradigm, providing a concise and expressive means for list creation. Their inherent capability lies in swiftly generating lists from existing iterables by applying operations to each element, thereby fostering a programming style that is both functional and expressive.

Let's delve into a concrete example to illuminate the prowess of list comprehensions:

```python
# List comprehension example
new_list = [x**2 for x in range(10)]
print(new_list)
```

In this succinct snippet, the list comprehension efficiently generates a new list, `new_list`, by squaring each element in the range from $0$ to $9$. This compact syntax encapsulates the entire operation, from iteration to transformation, in a single line. The result is not just a reduction in code length but also an enhancement in code clarity and readability.

List comprehensions transcend mere utility; they embody a programming style that aligns with the functional principles Python embraces. By succinctly expressing the transformation of elements, list comprehensions contribute to more readable and maintainable code. This approach aligns with Python's commitment to providing developers with tools that not only perform tasks efficiently but also promote a codebase that is elegant and expressive.

### Unveiling the Power of Enumeration in Python

The `enumerate()` function emerges as a valuable asset in the Python programming arsenal, providing a streamlined approach for simultaneously acquiring both the index and value of each element within an iterable during the iteration process. This functionality proves instrumental in simplifying tasks that necessitate tracking the position of elements within a sequence.

Let's delve into a practical application of the `enumerate()` function to illuminate its effectiveness:

```python
# Using enumerate() function
iterable = ['a', 'b', 'c']
for index, value in enumerate(iterable):
    print(f"Index: {index}, Value: {value}")
```

In this succinct code snippet, the `enumerate()` function seamlessly integrates into the `for` loop, enabling the extraction of both the index and value of each element in the iterable. The result is a clean and expressive output that provides a structured view of the iteration process.

The `enumerate()` function, through its simplicity, enhances the readability of code that involves traversing iterables while simultaneously requiring awareness of the index. This functionality aligns with Python's commitment to providing developers with tools that not only perform tasks efficiently but also contribute to the overall clarity and expressiveness of the codebase. By incorporating `enumerate()`, developers can streamline their code, making it not only functional but also more comprehensible and maintainable.

### Unleashing the Power of Special Iterables in Python

In the rich landscape of Python, special iterables such as `range()` and `zip()` emerge as indispensable tools, offering unique functionalities that elevate code efficiency and elegance, particularly when dealing with specific use cases.

**Leveraging range() for Sequential Number Generation**  
The `range()` function is a versatile construct that effortlessly generates a sequence of numbers, providing an efficient means for iterating over a range. Here's a succinct example:

```python
# Using range() for a sequence of numbers
for number in range(5):
    print(number)
```

In this snippet, the `range()` function generates a sequence from $0$ to $4$, and the `for` loop iterates over each number in the sequence. This concise syntax provides a clear and efficient way to handle numerical iterations.

**Uniting Elements with the Mighty zip() Function**  
The `zip()` function proves to be a powerhouse when it comes to combining elements from different iterables in a synchronized manner. Consider the following illustration:

```python
# Using zip() to combine elements from different iterables
iterable1 = ['a', 'b', 'c']
iterable2 = [1, 2, 3]
for element1, element2 in zip(iterable1, iterable2):
    print(f"Element1: {element1}, Element2: {element2}")
```

Here, `zip()` seamlessly aligns the elements from `iterable1` and `iterable2`, facilitating parallel iteration. This capability is particularly beneficial when working with related data from multiple sources.

By incorporating these special iterables into Python code, developers not only enhance the efficiency of their programs but also contribute to the overall elegance of the codebase. These constructs exemplify Python's commitment to providing tools that empower developers to write expressive, readable, and efficient code tailored to diverse application scenarios.

### Embracing Endless Possibilities with Infinite Iterators in Python

In the dynamic realm of Python, certain iterables transcend the constraints of finite sequences, ushering in a realm of infinite possibilities. Notably, the `itertools.count()` function stands as a prime example, capable of generating an unbounded sequence of numbers. While harnessing the potential of infinite iterators, developers must employ strategic control techniques to manage and extract finite subsets of elements. One such technique involves the judicious use of `itertools.takewhile()`.

Let's delve into a practical example showcasing the utilization of `itertools.count()` and `itertools.takewhile()`:

```python
# Using itertools.count() for an infinite iterator
from itertools import count, takewhile

infinite = count(1)
finite = takewhile(lambda x: x < 10, infinite)

# Printing elements from the finite iterator
for element in finite:
    print(element)
```

In this illustrative snippet, `itertools.count(1)` generates an infinite sequence of numbers starting from $1$. To harness a finite subset, `itertools.takewhile()` is employed with a lambda function specifying the condition `x < 10`. This effectively creates a controlled iteration, extracting elements from the infinite sequence until the specified condition is met.

Understanding the nuances of infinite iterators underscores a developer's proficiency in wielding Python's iteration capabilities. The strategic use of control techniques ensures that the power of infinite sequences is harnessed without overwhelming computational resources.

Mastering the concept of iterables, be they finite or infinite, is foundational for effective Python development. Whether navigating built-in data structures or crafting custom iterables, a nuanced understanding of iteration enriches the coding experience, contributing to the elegance and functionality that define Python as a versatile and expressive programming language.








## Tuples, Sets, Lists, and Dictionaries


So far, you have been working with fundamental data types like **str**, **int**, and **float**. However, many real-world problems become more manageable when simple data types are combined into more complex **data structures**.

A data structure serves as a model for organizing and representing collections of data. This could include scenarios like managing a list of numbers, handling rows in a spreadsheet, or working with records in a database. Selecting the appropriate data structure to model the data that your program interacts with is often crucial for creating simple and effective code.


### Tuples Are Immutable Sequences

One of the simplest compound data structures is a sequence of items. A sequence represents an ordered list of values, where each element is assigned an integer known as an index, determining its position in the sequence. Similar to strings, the initial value in a sequence is $0$.

For instance, consider the English alphabet, where the letters form a sequence with $A$ as the first element and $Z$ as the last. Strings, too, are sequences. Take the string $Python$, which comprises six elements. The sequence begins with $P$ at index $0$ and concludes with $n$ at index $5$.

Real-world instances of sequences encompass the values emitted by a sensor every second, a student's test scores over time, or the daily stock values for a company throughout a specific period.

#### What is a Tuple? 
The term "tuple" originates from mathematics, where it refers to a finite ordered sequence of values. In mathematical notation, tuples are typically represented by listing each element separated by commas and enclosed within a pair of parentheses. 

For example, $(1, 2, 3)$ is a tuple consisting of three integers maintaining the current order, meaning their elements follow a specific sequence. In the tuple $(1, 2, 3)$, the first element is $1$, the second is $2$, and the third is $3$.

> ***Note:** Python adopts both the name and notation for tuples directly from mathematics.*

#### How to Create a Tuple   
In Python, tuples can be created using various methods. Two commonly used approaches are:

**Tuple Literals**  
Similar to a **string literal** that is created by enclosing text within quotes, a **tuple literal** is formed by specifying a comma-separated list of values enclosed in **parentheses**. Here's an example:

```python
my_first_tuple = (1, 2, 3)

# To confirm its type, you can use the type() function:
type(my_first_tuple)  # Output: <class 'tuple'>
```

> ***Note:** Unlike strings, tuples can hold values of different types. For instance, (1, 2.0, "three") is a valid tuple.*

An empty tuple, denoted by two parentheses with nothing between them, is also a valid concept:

```python
empty_tuple = ()
# or
empty_tuple = tuple()
```

In practice, the direct use of empty parentheses $(\\: \\:)$ is more concise and commonly used when creating empty tuples. The $tuple()$ constructor is often used when you need to convert an iterable or another sequence type into a tuple.

**The tuple() Built-In**   
Another method to create a tuple involves using the built-in `tuple()` function, which proves useful when converting from another sequence type, like a string:

```python
tuple("Python")  # Output: ('P', 'y', 't', 'h', 'o', 'n')
# or
tuple()
```

> ***Note:** Leaving the parameter empty produces an empty tuple*

The `tuple()` function accepts only one parameter. Attempting to pass multiple values as arguments raises a `TypeError`:

```python
tuple(1, 2, 3)  # TypeError: tuple expected at most 1 argument, got 3

# Similarly, attempting to create a tuple from a non-iterable object results in a `TypeError`:
tuple(1)  # TypeError: 'int' object is not iterable
```

#

#### Similarities Between Tuples and Strings

Tuples and strings have a lot in common. Both are sequence types with a finite length, support indexing and slicing, are immutable, and can be iterated over in a loop.

The main difference between strings and tuples is that the elements of tuples can be any kind of value you like, whereas strings can only contain characters.

**Finite Length**  
Both strings and tuples have a finite length. For strings, the length is determined by the number of characters, while for tuples, it is the count of elements. 

The `len()` function can be used to obtain the length of either:

```python
numbers = (1, 2, 3)
len(numbers)  # Output: 3
```

**Indexing and Slicing**  
Indexing and slicing are supported by both strings and tuples. In strings, characters can be accessed using index notation:

```python
name = "David"
name[1]  # Output: 'a'

# Similarly, tuples support index notation:
values = (1, 3, 5, 7, 9)
values[2]  # Output: 5
```

Slicing, the extraction of a substring or subsequence, is also a shared feature:

```python
name[2:4]  # Output: "vi"
values[2:4]  # Output: (5, 7)
```

> ***Note:** The same rules governing string slices also apply to tuple slices.*

**Immutability**  
Both tuples and strings are immutable, meaning their values cannot be changed after creation. 

If an attempt is made to modify an element at a specific index, a `TypeError` is raised:
```python
>>> values[0] = 2
Traceback (most recent call last):
  File "<pyshell#1>", line 1, in <module>
    values[0] = 2
TypeError: 'tuple' object does not support item assignment
```

> ***Note:** While tuples are generally immutable, there are specific cases where the values in a tuple can change.*

**Tuples Are Iterable**  
Similar to strings, tuples are iterable, allowing you to loop through their elements. Here's an example demonstrating a loop over a tuple of vowels:

```python
vowels = ("a", "e", "i", "o", "u")
for vowel in vowels:
    print(vowel.upper())
```

During each iteration, the loop extracts a value from the tuple `vowels`. The extracted value, such as $a$, is then converted to uppercase using the `.upper()` string method and subsequently displayed using `print()`.

The loop proceeds to repeat these steps for each of the values $e$, $i$, $o$, and $u$, resulting in the uppercase display of each vowel:

```
A
E
I
O
U
```

#

#### Tuple Packing and Unpacking

Apart from using tuple literals and the `tuple()` built-in, there's a less common yet interesting way to create tuples through **packing** and **unpacking**.

**Tuple Packing**  
You can create a tuple by typing out a comma-separated list of values without enclosing them in parentheses:

```python
coordinates = 4.21, 9.29
type(coordinates)  # Output: <class 'tuple'>
```

It may seem like two values are assigned to the variable `coordinates`, but, in reality, both values are packed into a single tuple. 

**Tuple Unpacking**  
Values in a tuple can be unpacked into distinct variables:

```python
x, y = coordinates
x  # Output: 4.21
y  # Output: 9.29
```

> ***Note:** Here, the values from the tuple coordinates are unpacked into the variables x and y.*

Combining tuple packing and unpacking enables multiple variable assignments in a single line:

```python
name, age, occupation = "David", 34, "programmer"
name  # Output: 'David'
age  # Output: 34
occupation  # Output: 'programmer'
```

However, it's crucial to note that the number of variable names on the left must match the number of values in the tuple on the right. Otherwise, Python raises a `ValueError`:

```python
>>> a, b, c, d = 1, 2, 3
Traceback (most recent call last):
  File "<pyshell#0>", line 1, in <module>
    a, b, c, d = 1, 2, 3
ValueError: not enough values to unpack (expected 4, got 3)
```

Similarly, if the tuple has more values than the number of variable names:

```python
>>> a, b, c = 1, 2, 3, 4
Traceback (most recent call last):
  File "<pyshell#1>", line 1, in <module>
    a, b, c = 1, 2, 3, 4
ValueError: too many values to unpack (expected 3)
```

In both cases, the error indicates a mismatch between the expected and actual number of values for unpacking. It's essential to maintain this balance for successful tuple packing and unpacking.

#

#### Checking Existence of Values With in

You can determine whether a value exists in a tuple using the `in` keyword:

```python
vowels = ("a", "e", "i", "o", "u")
"o" in vowels  # Output: True
"x" in vowels  # Output: False
```

If the value to the left of `in` is present in the tuple to the right, the result is `True`; otherwise, it's `False`.

#### Returning Multiple Values From a Function

Tuples are often employed to return multiple values from a single function:

```python
def adder_subtractor(num1, num2):
    return (num1 + num2, num1 - num2)

adder_subtractor(3, 2)  # Output: (5, 1)
```

> ***Note:** In this example, the adder_subtractor() function takes two parameters and returns a tuple.*

#

#### Tuples Methods

Tuples, like other sequence types in Python, provide useful methods that facilitate data manipulation and analysis. 

Two of these methods, `count` and `index`, are particularly relevant when working with tuples.

**count Method**  
The `count` method is used to tally the occurrences of a specific value within the tuple. For instance:

```python
vowels = ("a", "e", "i", "o", "u")
```

We can employ the `count` method to determine how many times the vowel $o$ appears in the tuple:

```python
count_o = vowels.count("o")  # Output: 1
```

The result, in this case, would be $1$, indicating that the vowel $o$ occurs once in the `vowels` tuple.

**index Method**  
On the other hand, the `index` method is utilized to find the index of the first occurrence of a specific value in the tuple. 

```python
index_i = vowels.index("i")  # Output: 2
```

> ***Note:** It's important to note that the returned index is zero-based, meaning the first position is represented by index 0.*

Both the `count` and `index` methods offer valuable functionalities when dealing with tuples in Python, enabling content analysis and obtaining specific information about the structure of the sequence.



## Sets Are Unordered Collections
One of the fundamental compound data structures in Python is a collection of unique items known as a set. A set represents an unordered grouping of values, where each element is distinct and cannot be duplicated within the set. Unlike sequences, sets do not assign indices to elements based on their position in the collection.

For example, consider a set representing unique integers: { $1, 2, 3, 4, 5$ }. In this set, each element is unique, and the order in which they are defined does not determine their position within the set.

Real-world instances of sets include unique identifiers for users in a database, the distinct elements in a dataset, or the unique items in a shopping cart.

#### What is a Set?

The term "set" in Python is borrowed from mathematical sets, referring to an unordered collection of unique elements. In Python notation, sets are typically represented by listing elements separated by commas and enclosed within curly braces.

For instance, the order of elements is not guaranteed. It could be { $3, 1, 2$ } or { $2, 1, 3$ }, as sets do not follow a predefined sequence. Unlike a tuple, a set does not maintain a specific order. 

Sets are commonly used for tasks where uniqueness of elements is crucial, such as eliminating duplicates from a collection, testing membership, and performing mathematical set operations like union, intersection, and difference.

> ***Note:** Python adopts both the name and notation for sets directly from mathematical sets.*

#### How to Create a Set
In Python, sets can be created using different methods. Two commonly used approaches are:

**Set Literals**  
Similar to creating a tuple or a list, a set literal is formed by specifying a comma-separated list of values enclosed in curly braces. Here's an example:

```python
my_first_set = {1, 2, 3}

# To confirm its type, you can use the type() function:
type(my_first_set)  # Output: <class 'set'>
```

> ***Note:** Sets, like tuples, can hold values of different types. For example, {1, 2.0, "three"} is a valid set.**

An empty set is denoted by two curly braces:

```python
empty_set = {}
# or
empty_set = set()
```

In practice, the direct use of empty curly braces `{}` is more concise and commonly used when creating empty sets.

**The set() Built-In**  
Another method to create a set involves using the built-in `set()` function, which is useful when converting from another iterable or sequence type:

```python
set("Python")  # Output: {'P', 'h', 'n', 'o', 't', 'y'}

# Or an empty set:
set()
```

The `set()` function accepts only one parameter. Attempting to pass multiple values as arguments or creating a set from a non-iterable object will result in a `TypeError`:

```python
# TypeError: set expected at most 1 argument, got 3
set(1, 2, 3)
# TypeError: 'int' object is not iterable
set(1)        
```

#

#### Set Size and Membership
The `len()` function returns the number of elements in a set, and the $in$ and $not$ in operators can be used to test for membership:

```python
>>> x = {'foo', 'bar', 'baz'}
>>> len(x)
3
>>> 'bar' in x
True
```

#

#### Operating on a Set
While many operations applicable to other composite data types in Python, like indexing or slicing, don't apply to sets, Python provides a rich set of operations specifically designed for set objects, aligning with [mathematical set operations](https://en.wikipedia.org/wiki/Set_(mathematics)#Basic_operations).

**Operators vs. Methods**  
Most set operations in Python can be executed in two ways: using operators or methods. Let's delve into how these operators and methods function, using set union as an illustrative example.

Assuming two sets, x1 and x2, the union of x1 and x2 includes all elements from both sets.

Consider the sets:

```python
x1 = {'foo', 'bar', 'baz'}
x2 = {'baz', 'qux', 'quux'}

The union of x1 and x2 is `{'foo', 'bar', 'baz', 'qux', 'quux'}`.
```

> ***Note:** The element baz, common to both x1 and x2, appears only once in the union, as sets do not allow duplicate values.*

In Python, set union can be achieved using the `|` operator:

```python
x1 = {'foo', 'bar', 'baz'}
x2 = {'baz', 'qux', 'quux'}
x1 | x2
# Output: {'baz', 'quux', 'qux', 'bar', 'foo'}
```

Set union can also be obtained with the `.union()` method, invoked on one set with the other passed as an argument:

```python
x1.union(x2)
# Output: {'baz', 'quux', 'qux', 'bar', 'foo'}
```

While the operator and method behave identically in the provided examples, there is a subtle difference. When using the `|` operator, both operands must be sets. In contrast, the `.union()` method can take any iterable as an argument, convert it to a set, and then perform the union.

Observe the distinction between these two statements:

```python
>>> x1 | ('baz', 'qux', 'quux')
Traceback (most recent call last):
  File "<pyshell#43>", line 1, in <module>
    x1 | ('baz', 'qux', 'quux')
TypeError: unsupported operand type(s) for |: 'set' and 'tuple'

>>> x1.union(('baz', 'qux', 'quux'))
{'baz', 'quux', 'qux', 'bar', 'foo'}
```

Both attempts aim to compute the union of x1 and the tuple ('baz', 'qux', 'quux'). The `|` operator fails, while the `.union()` method succeeds by converting the tuple to a set before performing the union operation.

#

#### Available Operators and Methods

Here is a comprehensive list of set operations available in Python. These operations can be performed using operators, methods, or both. The key principle is that, where a set is expected, methods typically accept any iterable as an argument, while operators require actual sets as operands.

**Union**   
Compute the union of two or more sets.
* **Operator:** `x1 | x2 | x3 ... | xn`
* **Method:** `x1.union(x2, x3, ..., xn)`

```python
>>> a = {1, 2, 3, 4}
>>> b = {2, 3, 4, 5}
>>> c = {3, 4, 5, 6}
>>> d = {4, 5, 6, 7}

>>> a.union(b, c, d)
{1, 2, 3, 4, 5, 6, 7}

>>> a | b | c | d
{1, 2, 3, 4, 5, 6, 7}
```

**Intersection**   
Compute the intersection of two or more sets.
* **Operator:** `x1 & x2 & x3 ... & xn`
* **Method:** `x1.intersection(x2, x3, ..., xn)`

```python
>>> a = {1, 2, 3, 4}
>>> b = {2, 3, 4, 5}
>>> c = {3, 4, 5, 6}
>>> d = {4, 5, 6, 7}

>>> a.intersection(b, c, d)
{4}

>>> a & b & c & d
{4}
```

**Difference**  
Compute the difference between two or more sets.
* **Operator:** `x1 - x2 - x3 ... - xn`
* **Method:** `x1.difference(x2, x3, ..., xn)`

```python
>>> a = {1, 2, 3, 30, 300}
>>> b = {10, 20, 30, 40}
>>> c = {100, 200, 300, 400}

>>> a.difference(b, c)
{1, 2, 3}

>>> a - b - c
{1, 2, 3}
```

**Symmetric Difference**  
Compute the symmetric difference between sets.
* **Operator:** `x1 ^ x2 ^ x3 ... ^ xn`
* **Method:** `x1.symmetric_difference(x2)`

```python
>>> x1 = {'foo', 'bar', 'baz'}
>>> x2 = {'baz', 'qux', 'quux'}

>>> x1.symmetric_difference(x2)
{'foo', 'qux', 'quux', 'bar'}

>>> x1 ^ x2
{'foo', 'qux', 'quux', 'bar'}
```

> ***Note:** x1.symmetric_difference(x2) and x1 ^ x2 return the set of all elements in either x1 or x2, but not both*

**Is Disjoint**  
Determines whether or not two sets have any elements in common.
* **Method:** `x1.isdisjoint(x2)`
  
```python
>>> x1 = {'foo', 'bar', 'baz'}
>>> x2 = {'baz', 'qux', 'quux'}

>>> x1.isdisjoint(x2)
False

>>> x2 - {'baz'}
{'quux', 'qux'}
>>> x1.isdisjoint(x2 - {'baz'})
True
```

> ***Note:** x1.isdisjoint(x2) returns True if x1 and x2 have no elements in common*

**Is Subset**  
Determine whether one set is a subset of the other.
* **Operator:** `x1 <= x2`
* **Method:** `x1.issubset(x2)`


```python
>>> x1 = {'foo', 'bar', 'baz'}
>>> x1.issubset({'foo', 'bar', 'baz', 'qux', 'quux'})
True

>>> x2 = {'baz', 'qux', 'quux'}
>>> x1 <= x2
False
```

> ***Note:** In set theory, a set x1 is considered a subset of another set x2 if every element of x1 is in x2.*

**Is Proper Subset**  
Determines whether one set is a proper subset of the other.
* **Operator:** `x1 < x2`

A proper subset is the same as a subset, except that the sets can’t be identical. A set x1 is considered a proper subset of another set x2 if every element of x1 is in x2, and x1 and x2 are not equal.
```python
>>> x1 = {'foo', 'bar'}
>>> x2 = {'foo', 'bar', 'baz'}
>>> x1 < x2
True

>>> x1 = {'foo', 'bar', 'baz'}
>>> x2 = {'foo', 'bar', 'baz'}
>>> x1 < x2
False
```

**Is Superset**
Determine whether one set is a superset of the other.

* **Operator:** `x1 >= x2`
* **Method:** `x1.issuperset(x2)`

A superset is the reverse of a subset. A set x1 is considered a superset of another set x2 if x1 contains every element of x2.
```python
>>> x1 = {'foo', 'bar', 'baz'}

>>> x1.issuperset({'foo', 'bar'})
True

>>> x2 = {'baz', 'qux', 'quux'}
>>> x1 >= x2
False
```

**Is Proper Superset**  
Determines whether one set is a proper superset of the other.

* **Operator:** `x1 > x2`

A proper superset is the same as a superset, except that the sets can’t be identical. A set x1 is considered a proper superset of another set x2 if x1 contains every element of x2, and x1 and x2 are not equal.
```python
>>> x1 = {'foo', 'bar', 'baz'}
>>> x2 = {'foo', 'bar'}
>>> x1 > x2
True

>>> x1 = {'foo', 'bar', 'baz'}
>>> x2 = {'foo', 'bar', 'baz'}
>>> x1 > x2
False
```

These operations provide a robust set of tools for manipulating and comparing sets in Python.

#

#### Modifying a Set

Sets in Python, while containing elements of immutable types, can be modified using a mix of operators and methods. Augmented assignment operators and corresponding methods provide ways to change the contents of a set.

**Augmented Assignment Operators and Methods**  
| Operation           | Operator                  | Method                               | Description                                          |
|----------------------|---------------------------|--------------------------------------|------------------------------------------------------|
| Union                | `x1 \|= x2`                | `x1.update(x2)`    | Update set `x1` by union with set `x2`.               |
| Intersection         | `x1 &= x2`                | `x1.intersection_update(x2)` | Update set `x1` by intersection with set `x2`.        |
| Difference           | `x1 -= x2`                | `x1.difference_update(x2)` | Update set `x1` by difference with set `x2`.         |
| Symmetric Difference | `x1 ^= x2`                | `x1.symmetric_difference_update(x2)` | Update set `x1` symmetrically with set `x2`.         |

**Examples:**
```python
x1 = {'foo', 'bar', 'baz'}
x2 = {'foo', 'baz', 'qux'}

x1 |= x2
# or
x1.update(['corge', 'garply'])

x1 &= x2
# or
x1.intersection_update(['baz', 'qux'])

x1 -= x2
# or
x1.difference_update(['foo', 'bar', 'qux'])

x1 ^= x2
# or
x1.symmetric_difference_update(['qux', 'corge'])
```

**Other Methods for Modifying Sets**  
| Method   | Description                                |
|----------|--------------------------------------------|
| `x.add(<elem>)`      | Adds an element to a set.                       |
| `x.remove(<elem>)`   | Removes an element from a set.                  |
| `x.discard(<elem>)`  | Removes an element from a set if present.       |
| `x.pop()`            | Removes and returns a random element from a set.|
| `x.clear()`          | Clears all elements from a set.                 |

**Examples:**
```python
x = {'foo', 'bar', 'baz'}

x.add('qux')

x.remove('baz')
# Raises KeyError if 'qux' is not present
x.remove('qux')

x.discard('baz')
# No error if 'qux' is not present
x.discard('qux')

x.pop()
# Removes and returns a random element from the set

x.clear()
# Clears all elements from the set
```

#

### Lists Are Mutable Sequences

The list is a versatile data structure in Python, representing a sequence of items similar to strings and tuples. Like strings and tuples, lists are indexed by integers, starting with $0$.

At first glance, lists share similarities with tuples. They support index and slicing operations, allow checking for the existence of an element using "in," and can be iterated over with a for loop.

However, a significant distinction is that lists are mutable, enabling you to alter the value at a specific index even after the list's creation. Unlike tuples, which are immutable, lists provide flexibility for modifications.

#### Creating Lists

A list in Python is denoted by square brackets (`[]`). Similar to tuples, lists can store a variety of values, and they are mutable, meaning their elements can be changed after the list is created.

**List Literal**  
You can create a list using a literal, surrounded by square brackets:

```python
colors = ["red", "yellow", "green", "blue"]

# The type() function confirms that it's a list:
>>> type(colors)
<class 'list'>
```

Inspecting the list reveals its content:

```python
>>> colors
['red', 'yellow', 'green', 'blue']
```

> ***Note:** Lists can contain elements of different types, just like tuples: mixed_list = ["one", 2, 3.0]*

**Using the list() Built-In**  
You can also create a list from other sequences using the `list()` built-in:

```python
>>> list((1, 2, 3))
[1, 2, 3]
```

Even a string can be converted into a list:

```python
>>> list("Python")
['P', 'y', 't', 'h', 'o', 'n']
```

**Creating Lists from Strings**  
To create a list from a comma-separated string, you can use the `split()` method:

```python
groceries = "eggs, milk, cheese"
grocery_list = groceries.split(", ")
```

The resulting list:

```python
>>> grocery_list
['eggs', 'milk', 'cheese']
```

You can customize the separator with the `split()` method, allowing flexible string-to-list conversions:

```python
>>> "a;b;c".split(";")
['a', 'b', 'c']

>>> "The quick brown fox".split(" ")
['The', 'quick', 'brown', 'fox']

>>> "abbaabba".split("ba")
['ab', 'ab', '']
```

Note that if the separator is not found in the string, `split()` returns a list with the entire string as its only element:

```python
>>> "abbaabba".split("c")
['abbaabba']
```

Lists support the all of the same operations supported by tuples.

**Counting Elements**: The `count()` method returns the number of occurrences of a specified value:

```python
>>> numbers = [1, 2, 3, 1, 4, 1, 5]
>>> numbers.count(1)
3
```

**Finding Index**: The `index()` method returns the index of the first occurrence of a specified value:

```python
>>> numbers.index(1, 4)
5
```

#

#### Basic List Operations
Indexing and slicing operations on lists function similarly to tuples in Python.

**Indexing Elements**  
You can access list elements using index notation:

```python
numbers = [1, 2, 3, 4]
>>> numbers[1]
2
```

**Slicing Lists** 
Creating a new list from an existing one using slice notation:

```python
>>> numbers[1:3]
[2, 3]
```

**Checking Existence**  
The $in$ operator helps verify the existence of list elements:

```python
>>> "Bob" in numbers
False
```

**Iterating Over Lists**  
Since lists are iterable, you can iterate over them using a $for$ loop:

```python
# Print only the even numbers in the list
for number in numbers:
    if number % 2 == 0:
        print(number)
```

The significant difference between lists and tuples is that elements in lists can be changed, while elements in tuples cannot. This mutability of lists allows for dynamic modifications after the list's creation.

#

#### Changing Elements in a List

Think of a list as a sequence of numbered slots. Each slot holds a value, and every slot must be filled at all times, but you can swap out the value in a given slot with a new one whenever you want.

The ability to swap values in a list for other values is called **mutability**. Lists are **mutable**. The elements of tuples may not be swapped for new values, so tuples are said to be **immutable**. 

To swap a value in a list, assign a new value to a slot using index notation:

```python
>>> colors = ["red", "yellow", "green", "blue"]
>>> colors[0] = "burgundy"
```

This changes the value at index $0$ from "red" to "burgundy":

```python
>>> colors
['burgundy', 'yellow', 'green', 'blue']
```

Multiple values in a list can be changed simultaneously with **slice assignment**:

```python
>>> colors[1:3] = ["orange", "magenta"]
>>> colors
['burgundy', 'orange', 'magenta', 'blue']
```

This selects slots with indices $1$ and $2$, assigning $orange$ and $magenta$:

The list assigned to a slice does not need to have the same length as the slice. For instance, you can assign a list of three elements to a slice with two elements:

```python
>>> colors = ["red", "yellow", "green", "blue"]
>>> colors[1:3] = ["orange", "magenta", "aqua"]
>>> colors
['red', 'orange', 'magenta', 'aqua', 'blue']
```

The values "orange" and "magenta" replace the original values "yellow" and "green" in colors at the indices 1 and 2. Then a new slot is created at index $4$ and "blue" is assigned to this index. Finally, "aqua" is assigned to index $3$.

When the length of the list being assigned to the slice is less than the length of the slice, the overall length of the original list is reduced:

```python
>>> colors
['red', 'orange', 'magenta', 'aqua', 'blue']
>>> colors[1:4] = ["yellow", "green"]
>>> colors
['red', 'yellow', 'green', 'blue']
```

The values "yellow" and "green" replace the values "orange" and "magenta" in colors at the indices $1$ and $2$. Then the value at index $3$ is replaced with the value "blue". Finally, the slot at index $4$ is removed from colors entirely.

#

#### List Methods For Adding and Removing Elements

While you can manipulate lists with slice notation for adding and removing elements, list methods offer a more intuitive and readable approach.

**list.insert(i, x)**  
The `list.insert()` method inserts a single value $x$ at a specified index $i$ in the list. It shifts existing values to accommodate the new one.

```python
colors = ["red", "yellow", "green", "blue"]
colors.insert(1, "orange")
# Result: ['red', 'orange', 'yellow', 'green', 'blue']
```

If the value for the index parameter of `.insert()` is larger than the greatest index in the list, the value is inserted at the end of the list:

```python
>>> colors.insert(10, "violet")
>>> colors
['red', 'orange', 'yellow', 'green', 'blue', 'violet']
Here the value "violet" is actually inserted at index 5, even though
.insert() was called with 10 for the index.
```

> ***Note:** If the index is larger than the greatest index in the list, the value is inserted at the end.*

**list.pop(i)**  
The `list.pop()` method removes and returns the element at the specified index `i`. If no index is provided, it removes and returns the last element in the list. 

```python
>>> colors = ["red", "orange", "yellow", "blue", "indigo", "violet"]
>>> color = colors.pop(3)
'green'
>>> colors
['red', 'orange', 'yellow', 'blue', 'indigo', 'violet']
```

> ***Note:** The value that is removed is returned by the method*

Unlike .insert(), Python raises an IndexError if you pass to .pop() an argument larger than the last index:
```python
>>> colors.pop(10)
Traceback (most recent call last):
  File "<pyshell#0>", line 1, in <module>
    colors.pop(10)
IndexError: pop index out of range
```

Negative indices also work with .pop():
```python
>>> colors.pop(-1)
'violet'
>>> colors
['red', 'orange', 'yellow', 'blue', 'indigo']
```

**list.append(x)**  
The `list.append()` method appends a new element $x$ to the end of the list.

```python
>>> colors.append("indigo")
>>> colors
['red', 'orange', 'yellow', 'blue', 'indigo']
```

After calling `.append()`, the length of the list increases by one and the value "indigo" is inserted into the final slot. Note that `.append()` alters the list in place, just like `.insert()`.


**list.extend(iterable)**  
The `list.extend()` method adds elements from an iterable to the end of the list. It is commonly used with another list or tuple.

```python
>>> colors.extend(["violet", "ultraviolet"])
>>> colors
['red', 'orange', 'yellow', 'blue', 'indigo', 'violet', 'ultraviolet']
```

> ***Note:** The elements of the iterable are appended to the list in the same order that they appear in the argument passed to .extend().*

Just like `.insert()` and `.append()`, `.extend()` alters the list in place.

#

#### Lists of Numbers

A common operation with lists of numbers is to calculate the sum of all the values to obtain the total. This can be achieved using a for loop:

```python
nums = [1, 2, 3, 4, 5]
total = 0
for number in nums:
    total = total + number

print(total)
```

While this for loop is straightforward, Python provides a more concise way to achieve the same result using the built-in `sum()` function:

```python
total = sum([1, 2, 3, 4, 5])
print(total)
```

The `sum()` function takes a list as an argument and returns the total of all the values in the list.

If the list passed to `sum()` contains non-numeric values, a `TypeError` is raised:

```python
>>> sum([1, 2, 3, "four", 5])
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
TypeError: unsupported operand type(s) for +: 'int' and 'str'

```

Additionally, there are two other built-in functions, `min()` and `max()`, useful for working with lists of numbers. They return the minimum and maximum values in the list, respectively:

```python
min([1, 2, 3, 4, 5 ])
# Output: 1

max([1, 2, 3, 4, 5])
# Output: 5
```

It's worth noting that `sum()`, `min()`, and `max()` also work seamlessly with tuples:

```python
sum((1, 2, 3, 4, 5))
# Output: 15

min((1, 2, 3, 4, 5))
# Output: 1

max((1, 2, 3, 4, 5))
# Output: 5
```

The inclusion of these functions as built-ins underscores their frequent usage in Python.

#

#### List Comprehensions

Another concise way to create a list from an existing iterable is by using a **list comprehension**:

```python
numbers = (1, 2, 3, 4, 5)
squares = [num**2 for num in numbers]
print(squares)
# Output: [1, 4, 9, 16, 25]
```


A list comprehension serves as a shorthand for a for loop. In the example above, a tuple literal containing five numbers is created and assigned to the `numbers` variable. The list comprehension on the second line loops over each number in `numbers`, squares each number, and adds it to a new list called `squares`.

To achieve the same result using a traditional for loop, you would need to create an empty list, loop over the numbers in `numbers`, and append the square of each number to the list:

```python
squares = []
for num in numbers:
    squares.append(num**2)

print(squares)
# Output: [1, 4, 9, 16, 25]
```

List comprehensions are often used to convert values in one list to a different type. For example, converting a list of strings containing floating-point values to a list of float objects:

```python
str_numbers = ["1.5", "2.3", "5.25"]
float_numbers = [float(value) for value in str_numbers]
print(float_numbers)
# Output: [1.5, 2.3, 5.25]
```

List comprehensions, while not unique to Python, are one of its many beloved features. If you find yourself creating an empty list, looping over some other iterable, and appending new items to the list, chances are you can replace your code with a list comprehension!

#

#### Nesting, Copying, and Sorting Tuples and Lists

Now that you have learned what tuples and lists are, how to create them, and some basic operations with them, let’s look at three more concepts:

**Nesting Lists and Tuples**  
Lists and tuples in Python can contain values of any type. This means they can also contain lists and tuples as values, creating nested structures. A nested list or tuple is one that is contained as a value within another list or tuple.

```python
two_by_two = [[1, 2], [3, 4]]
>>> print(len(two_by_two))
2
>>> print(two_by_two[0])    
[1, 2]
>>> print(two_by_two[1])    
[3, 4]
>>> print(two_by_two[1][0]) 
3
```

In loose terms, a list of lists or a tuple of tuples can be thought of as a table with rows and columns. However, it's essential to note that there is no requirement for all lists in a list of lists to have the same length.

**Copying a List**  
Copying lists in Python involves careful consideration due to the nature of object-oriented programming. Assigning one list to another directly creates a reference, not an independent copy. Here's an example:

```python
animals = ["lion", "tiger", "frumious Bandersnatch"]
large_cats = animals.copy()
large_cats.append("leopard")
>>> print(large_cats)
['lion', 'tiger', 'frumious Bandersnatch', 'leopard']
>>> print(animals)
["lion", "tiger", "frumious Bandersnatch"]
```

Alternatively, slicing notation ([:]) can also be used for creating an independent copy:

```python
animals = ["lion", "tiger", "frumious Bandersnatch"]
large_cats = animals[:]
large_cats.append("leopard")
>>> print(large_cats)  
['lion', 'tiger', 'frumious Bandersnatch', 'leopard']
>>> print(animals)
["lion", "tiger", "frumious Bandersnatch"]
```

For lists of lists, be cautious, as a simple copy (copy() or [:]) creates a **shallow copy**, meaning references to nested lists remain the same. For deep copies and more advanced copying methods, further exploration is recommended.

**Sorting Lists**  
Lists in Python have a `.sort()` method for sorting items in ascending order. The sorting is done in place:

```python
colors = ["red", "yellow", "green", "blue"]
colors.sort()
print(colors)  # Output: ['blue', 'green', 'red', 'yellow']

numbers = [1, 10, 5, 3]
numbers.sort()
print(numbers) # Output: [1, 3, 5, 10]
```

The `.sort()` method also supports an optional `key` parameter for custom sorting. For instance, to sort a list of strings by length:

```python
colors = ["red", "yellow", "green", "blue"]
colors.sort(key=len)
>>> print(colors)
['red', 'blue', 'green', 'yellow']
```

> ***Note:** User-defined functions can be used with the `key` parameter as well.*

You don’t need to call the function when you pass it to key. Pass the name of the function without any parentheses. For instance, in the previous example the name len is passed to key, and not len().

The function that gets passed to key must only accept a single argument.

You can also pass user defined functions to key. In the following example, a function called get_second_element() is used to sort a list of tuples by their second elements:

```python
>>> def get_second_element(item):
... return item[1]
...
>>> items = [(4, 1), (1, 2), (-9, 0)]
>>> items.sort(key=get_second_element)
>>> items
[(-9, 0), (4, 1), (1, 2)]
```

Keep in mind that any function that you pass to key must accept only a single argument.

The `.reverse()` method can be used to reverse the order of elements in a list:

```python
colors = ["red", "yellow", "green", "blue"]
colors.reverse()
>>> print(colors)  
['blue', 'green', 'yellow', 'red']
```

> ***Note:** This method reverses the list in place, similar to .sort().*

These concepts—nesting, copying, and sorting—provide essential tools for handling complex data structures in Python.


## Store Relationships in Dictionaries

Dictionaries are a fundamental and powerful data structure in Python. Unlike lists and tuples, which are sequences indexed by integers, dictionaries allow you to associate a key with a value. This association is often referred to as a "key-value pair."

**What is a Dictionary?**  
In everyday terms, think of a Python dictionary as a digital version of a word dictionary. Just like a traditional dictionary, each entry in a Python dictionary has two main parts: the word (key) being defined, and its definition (value).

Let's break down the analogy:

- **Word Dictionary:**
  - **Word (Key):** Unique name identifying the entry.
  - **Definition (Value):** Explanation or meaning associated with the word.

- **Python Dictionary:**
  - **Key-Value Pair:** Corresponds to a word-definition entry.
  - **Key:** Unique name identifying the value.
  - **Value:** Actual data or information associated with the key.

For example, consider a Python dictionary storing information about states and their capitals:

```python
# Python Dictionary
state_capitals = {
    "California": "Sacramento",
    "New York": "Albany",
    "Texas": "Austin"
}
```

In this dictionary, the state names are **keys**, and their respective capitals are **values**. The relationship between a key and its value is flexible; any key can be paired with any value.

Here's the crucial distinction: Unlike an English dictionary where words are specifically linked to their definitions, a Python dictionary creates a more abstract connection. It resembles a mathematical map, defining relationships between two sets of values (keys and values).

In summary, a Python dictionary serves as a data structure that establishes connections between keys and values, creating a map-like relationship. This versatile feature makes dictionaries powerful for organizing and accessing data in Python code.

**Differences from Lists and Tuples**  
1. **Unordered:** Unlike lists or tuples, dictionaries are unordered. Items are not stored in a specific order.
2. **Key-Value Pairs:** Dictionaries are composed of key-value pairs, allowing for easy retrieval of values based on keys.
3. **Mutability:** Dictionaries are mutable, meaning you can change, add, or remove key-value pairs after the dictionary is created.

**Defining and Using Dictionaries**  
Dictionaries can be defined using curly braces or the `dict()` constructor. Keys and values can be of any data type, and a key can be associated with any value.

```python
# Alternative dictionary creation
book = dict(title="Python 101", author="Jane Doe", year=2022)

# Accessing and modifying values
>>> print(book["title"])  
Python 101
book["year"] = 2023   # Modifying value
>>> print(book)
{'title': 'Python 101', 'author': 'Jane Doe', 'year': 2023}
```

**Use Cases for Dictionaries**  
Dictionaries are useful when dealing with data that has a clear mapping between keys and values. They are commonly used for:

- Storing settings and configurations.
- Representing real-world entities and their attributes.
- Handling data with a structured format.

#

#### Accessing Values in Python Dictionaries

To retrieve a value from a Python dictionary, use square brackets `[]` with the corresponding key:

```python
# Example Dictionary
capitals = {
    "California": "Sacramento",
    "New York": "Albany",
    "Texas": "Austin"
}

# Accessing Value
print(capitals["Texas"])  # Output: 'Austin'
```

The syntax for accessing dictionary values resembles index notation used in strings, lists, and tuples. However, it's crucial to understand that dictionaries differ fundamentally from sequence types like lists and tuples.

For illustration, imagine if we defined the `capitals` dictionary as a list:

```python
# Equivalent List
capitals_list = ["Sacramento", "Albany", "Austin"]
```

In this scenario, you would access the capital of each state using index notation:

```python
# Accessing List Values
print(capitals_list[0])  # Capital of California: 'Sacramento'
print(capitals_list[2])  # Capital of Texas: 'Austin'
```

While both approaches achieve the same goal, dictionaries provide clarity by associating keys (state names) with values (capitals). This is especially beneficial when dealing with larger datasets, as you won't need to rely on the order of elements in a list or tuple.

In summary, dictionaries use keys to access values, offering a more intuitive and context-driven method compared to the ordered index approach of sequence types.

#

#### Modifying and Removing Items in Python Dictionaries

Dictionaries in Python are mutable, allowing the addition and removal of items. Below are examples of how to add and remove items from a dictionary:

**Adding Items**  
To add an item to a dictionary, assign a value to a new key:

```python
# Example Dictionary
capitals = {
    "California": "Sacramento",
    "New York": "Albany",
    "Texas": "Austin"
}

# Adding a New Item
capitals["Colorado"] = "Denver"
print(capitals)
# {'California': 'Sacramento', 'New York': 'Albany', 'Texas': 'Austin', 'Colorado': 'Denver'}
```

If the key already exists, assigning a new value will overwrite the existing one:

```python
# Overwriting an Existing Item
capitals["Texas"] = "Houston"
print(capitals)
# {'California': 'Sacramento', 'New York': 'Albany', 'Texas': 'Houston', 'Colorado': 'Denver'}
```

**Removing Items**  
To remove an item from a dictionary, use the `del` keyword with the key:

```python
# Removing an Item
del capitals["Texas"]
print(capitals)
# {'California': 'Sacramento', 'New York': 'Albany', 'Colorado': 'Denver'}
```

**Checking Key Existence**  
If you try to access a value in a dictionary using a key that doesn’t exist, Python raises a `KeyError`:
```python
>>> capitals["Arizona"]
Traceback (most recent call last):
  File "<pyshell#1>", line 1, in <module>
    capitals["Arizona"]
KeyError: 'Arizona'
```

The `KeyError` is the most common error encountered when working with dictionaries. Whenever you see it, it means that an attempt was made to access a value using a key that doesn’t exist

Before accessing a key, you can check its existence using the `in` keyword:

```python
# Checking Key Existence
print("Arizona" in capitals)
# False
print("California" in capitals)
# True
```

This way, you can avoid encountering a `KeyError` when attempting to access a non-existent key. It's important to note that `in` checks only the existence of keys, not values.

```python
# Checking Value Existence (Does not work)
print("Sacramento" in capitals)  # Output: False
```

This example returns `False` because `"Sacramento"` is a value, not a key, in the `capitals` dictionary.

#

#### Iterating Over Dictionaries in Python

In Python, dictionaries can be iterated over to access their keys and values. Here's how you can iterate over a dictionary using a `for` loop and the `.items()` method:

```python
# Example Dictionary
capitals = {
    "California": "Sacramento",
    "New York": "Albany",
    "Texas": "Austin",
    "Colorado": "Denver"
}

# Iterating Over Keys
print("Iterating Over Keys:")
for key in capitals:
    print(key)
# Output:
# California
# New York
# Texas
# Colorado

# Iterating Over Keys and Values using .items()
print("\nIterating Over Keys and Values:")
for state, capital in capitals.items():
    print(f"The capital of {state} is {capital}")
# Output:
# The capital of California is Sacramento
# The capital of New York is Albany
# The capital of Texas is Austin
# The capital of Colorado is Denver
```

In the first loop, the variable `key` iterates over the keys of the dictionary. In the second loop, the `.items()` method is used to iterate over both keys and values simultaneously.

The `.items()` method returns a special type called `dict_items`, which is a view object. You can use it to loop over key-value pairs directly in the `for` loop, where each iteration produces a tuple containing the key and its corresponding value. Unpacking the tuple into separate variables (`state` and `capital` in this case) allows easy access to both parts of the key-value pair.

#

#### Exploring Dictionary Methods in Python

Dictionaries in Python are extremely useful data structures that allow you to store information in key-value pairs. Here are some essential methods for working with dictionaries in Python:


**`keys():`** Returns a view of the keys in the dictionary. Useful for iterating over keys.

```python
keys = my_dictionary.keys()
# keys will contain a view of the keys in my_dictionary.
```

**`values():`** Returns a view of the values in the dictionary. Useful for iterating over values.

```python
values = my_dictionary.values()
# values will contain a view of the values in my_dictionary.
```

**`items():`** Returns a view of tuples (key, value) from the dictionary. Useful for iterating over key-value pairs.

```python
pairs = my_dictionary.items()
# pairs will contain a view of tuples (key, value) in my_dictionary.
```

**`get(key, default_value):`** Returns the value associated with the key. If the key doesn't exist, returns the default value.

```python
age = my_dictionary.get("age", 0)
# If "age" exists, age will have the corresponding value; otherwise, it will have the default value 0.
```

**`clear():`** Removes all items from the dictionary.

```python
my_dictionary.clear()
# Removes all items from my_dictionary.
```

 **`pop(key, default_value):`** Removes the specified key and returns the associated value. If the key doesn't exist, it returns the default value.

```python
age = my_dictionary.pop("age", 0)
# If "age" exists, age will have the corresponding value; otherwise, it will have the default value 0.
# Also, the key "age" will be removed from the dictionary.
```

 **`popitem():`** Removes and returns an arbitrary key-value pair from the dictionary. Useful for situations where you don't care about the order of items.

```python
removed_item = my_dictionary.popitem()
# removed_item will contain a randomly removed key-value pair from the dictionary.
```

**`update(dictionary):`** Updates the dictionary with elements from another dictionary or an iterable of key-value pairs.

```python
new_dictionary = {"profession": "Engineer", "age": 35}
my_dictionary.update(new_dictionary)
# Adds elements from new_dictionary to my_dictionary. Existing keys have their values updated.
```

 **`setdefault(key, default_value):`** Returns the value associated with the key. If the key doesn't exist, inserts the key with the default value and returns it.

```python
age = my_dictionary.setdefault("age", 0)
# If "age" exists, age will have the corresponding value
# otherwise, inserts "age" with the default value 0 and returns 0.
```

**`fromkeys(iterable, default_value):`** Creates a new dictionary with keys from the iterable and values set to the default value.

```python
keys = ["a", "b", "c"]
new_dictionary = dict.fromkeys(keys, 0)
# Creates a new dictionary with keys "a", "b", "c", and default values of 0.
```

#

#### Dictionary Keys and Immutability in Python

In Python dictionaries, keys must be of **immutable** types. While values in a dictionary can be of any type, keys need to be immutable because dictionaries use a mechanism called hashing for efficient key lookup. Here are the key points:

**Valid Dictionary Key Types:**
- Integers
- Floats
- Strings
- Booleans
- Tuples

For example:

```python
# Valid Dictionary Keys
capitals = {
    1: "One",
    3.14: "Pi",
    "Python": "Language",
    True: "Boolean",
    (1, 2, 3): "Tuple"
}
```

However, mutable types, such as lists, are not allowed as dictionary keys. Attempting to use a mutable type as a key will result in a `TypeError`:

```python
>>> capitals[[1, 2, 3]] = "Bad"
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
TypeError: unhashable type: 'list'
```

The error occurs because lists are mutable, and their content can be changed. If a mutable object were allowed as a key and modified later, it would break the dictionary's internal structure. This is why only immutable types are allowed as keys, ensuring a consistent and predictable behavior in Python dictionaries.

#

#### Nested Dictionaries in Python

Nested dictionaries in Python allow you to create a dictionary where the values associated with keys are themselves dictionaries. This is a powerful way to structure data, especially when dealing with complex relationships. Here's an example:

```python
# Creating a Nested Dictionary
states = {
    "California": {
        "capital": "Sacramento",
        "flower": "California Poppy"
    },
    "New York": {
        "capital": "Albany",
        "flower": "Rose"
    },
    "Texas": {
        "capital": "Austin",
        "flower": "Bluebonnet"
    }
}

# Accessing Values in Nested Dictionaries
texas_info = states["Texas"]
print(texas_info)
# Output: {'capital': 'Austin', 'flower': 'Bluebonnet'}

# Accessing a Specific Value (e.g., Texas state flower)
texas_flower = states["Texas"]["flower"]
print(texas_flower)
# Output: 'Bluebonnet'
```

In this example, each state is a key in the `states` dictionary, and the associated value for each state is another dictionary containing information such as the capital city and state flower.

Nested dictionaries are commonly used in scenarios where you need to represent hierarchical or structured data. They are especially useful when working with APIs, web data, or any data format where information has a nested structure.














## Functions

Functions serve as the fundamental building blocks of nearly every Python program, where the real action unfolds! You've already encountered various built-in functions like `print()`, `len()`, and `round()`. These functions are inherent to the Python language.

Functions play a pivotal role in breaking down code into smaller, manageable chunks, especially for tasks that a program needs to perform repeatedly. Instead of duplicating the same code each time the task arises, you can encapsulate the functionality within a function and call it when needed. This not only enhances code organization but also promotes reusability and maintainability.

```python
def function_name(#parameters):
  # function_body
  return value 
```

> ***Note:** The return command is only required for functions that have a non-void return type.*

Each variable declared in the parameter list is treated as a local variable within the function. When a function has no input arguments, the parameter list remains empty. However, the parentheses in the function declaration are mandatory.

Upon encountering a return statement, the function immediately terminates. If any data is provided after the return keyword, its value is returned by the function. While a function can have multiple return statements, only one will be executed per function call. It's essential to understand that the function concludes as soon as the program reaches the first return statement.


### How Python Executes Functions

One crucial aspect to note is that you can't execute a function by merely typing its name; you must call the function to instruct Python to execute it. Let's explore this concept using the `len()` function as an example:

```python
# Typing just the name doesn't execute the function.
# IDLE inspects the variable as usual.
>>> len
<built-in function len>

# Use parentheses to call the function.
>>> len()
Traceback (most recent call last):
  File "<pyshell#3>", line 1, in <module>
    len()
TypeError: len() takes exactly one argument (0 given)
```

In this example, a `TypeError` is raised when `len()` is called because the function expects an argument. An argument is a value passed to the function as input. While some functions can be called without arguments, others can take as many arguments as needed. In the case of `len()`, it requires exactly one argument.

Once a function completes its execution, it returns a value as output. The return value typically, but not always, depends on the values of any arguments passed to the function.

The process of executing a function can be summarized in three steps:

1. **Function Call:** The function is called, and any arguments are passed to the function as input.
2. **Execution:** The function executes, performing some action with the provided arguments.
3. **Return:** The function returns, and the original function call is replaced with the return value.

Let's observe this in practice and understand how Python executes the following line of code:

```python
>>> num_letters = len("four")
```

Firstly, `len()` is called with the argument "four". The length of the string is calculated, resulting in the number $4$. Then, `len()` returns the number 4, replacing the function call with this value.

After the function executes, the line of code transforms to:

```python
>>> num_letters = 4
```

Subsequently, Python assigns the value $4$ to `num_letters` and proceeds to execute any remaining lines of code in the program. This process illustrates how functions contribute to the flow of code by performing specific actions and providing values that can be utilized in subsequent parts of the program.


### Functions Can Have Side Effects

You've learned how to call a function and that they return a value upon completion. However, functions can do more than just return a value; they can have side effects. A side effect occurs when a function changes or influences something external to the function itself. One example of a function with a side effect is `print()`.

When you call `print()` with a string argument, the string is displayed in the Python shell as text. Yet, `print()` doesn't return any text as a value. To demonstrate what `print()` returns, you can assign its return value to a variable:

```python
>>> return_value = print("What do I return?")
What do I return?
>>> return_value
None
```

Here, when you assign `print("What do I return?")` to `return_value`, the string "What do I return?" is displayed. However, when you inspect the value of `return_value`, it is `None`, indicating the absence of data.

`print()` returns a special value called `None`, indicating the absence of data. `None` has a type called `NoneType`:

```python
>>> type(return_value)
<class 'NoneType'>
>>> print(return_value)
None
```

> ***Note:** When you call print(), the displayed text is not the return value; it is a side effect of print().*

### Write Your Own Functions

As your programs grow in length and complexity, you may find the need to reuse the same few lines of code multiple times or calculate the same formula with different values. While copying and pasting similar code might be tempting, it's generally a bad idea as repetitive code can become challenging to maintain. Fixing a mistake in duplicated code requires changes in every instance, which can be error-prone.

**The Anatomy of a Function**  
Every function consists of two essential parts:

1. **Function Signature:** Defines the name of the function and any inputs it expects.
2. **Function Body:** Contains the code that runs each time the function is used.

Let's start by creating a simple function that takes two numbers as input and returns their product. The function will be named `multiply`, and here's what it looks like with comments identifying the signature, body, and return statement:

```python
def multiply(x, y):  # Function signature
  # Function body
  product = x * y
  return product
```

While creating a function for the multiplication operator might seem unnecessary, this example serves as a fundamental illustration of how functions are defined.

**The Function Signature**  
The first line of a function, known as the function signature, always starts with the `def` keyword (short for "define"). Let's break down the signature of the `multiply` function:

```python
def multiply(x, y):
```

> ***Note:** A function name can only contain numbers, letters, and underscores, and must not begin with a number.*

The function signature consists of four parts:

1. The `def` keyword.
2. The function name, which is `multiply` in this case.
3. The parameter list, `(x, y)`.
4. A colon `:` at the end of the line.

When Python encounters a line beginning with the `def` keyword, it creates a new function and assigns it to a variable with the same name as the function.

**The Parameter List**  
The parameter list in a function is a set of parameter names enclosed within parentheses. It defines the expected inputs for the function. For example, in the `multiply` function:

```python
def multiply(x, y):
```

The parameter list `(x, y)` signifies that the function `multiply` takes two parameters, `x` and `y`. These parameters act as placeholders for actual values provided when the function is called with arguments. While parameters resemble variables, they don't have values; they serve as templates for values to be supplied during execution.

The function body can utilize these parameters as if they were real variables. For instance, the expression `x * y` in the function body is a template, and Python fills in the actual values when the function is executed. It's important to note that a function can have any number of parameters, including none at all.

**The Function Body**  
The function body contains the code that executes whenever the function is called in your program. Taking the `multiply` function as an example:

```python
def multiply(x, y):
  # Function body
  product = x * y
  return product
```

This simple function has a two-line body. The first line creates a variable `product` and assigns to it the value `x * y`. Since `x` and `y` are placeholders at this point, this line serves as a template for the actual value assigned during execution.

The second line is a `return` statement, starting with the `return` keyword followed by the variable `product`. When Python encounters this statement, it stops running the function and returns the value of `product`.

It's crucial to maintain proper indentation in the function body. Every line indented below the function signature is considered part of the function body. For example:

```python
def multiply(x, y):
  product = x * y
  return product
  print("Where am I?")  # Not in the function body.
```

In this case, the `print()` function is not part of the function body because it lacks the required indentation. However, if `print()` were indented, even with a blank line between it and the previous line, it would be considered part of the function body.

One essential rule for code indentation in a function's body is that every line must be indented by the same number of spaces.

### Writing Your Own Functions: Indentation Rules

When writing Python functions, it's crucial to adhere to proper indentation rules. Incorrect indentation can lead to errors, as illustrated in the following examples:

**Example 1: Unexpected Indent**  
If the `return` statement is indented differently than the line before it, Python raises an "unexpected indent" error. Modify the `multiply.py` file to look like this:

```python
def multiply(x, y):
    product = x * y
     return product  # Indented with one extra space.
```

Attempting to run this code in IDLE will result in an error dialog with the message "unexpected indent."

**Example 2: Unmatched Indentation**  
If a line of code is indented less than the line above it, and the indentation doesn't match any previous lines, Python raises an "unindent does not match any outer indentation level" error. Modify the `multiply.py` file to look like this:

```python
def multiply(x, y):
    product = x * y
  return product  # Indented less than the previous line.
```

Running this modified code in IDLE will lead to an error with the message "unindent does not match any outer indentation level."

### Function Behavior with Incorrect Indentation

Once a `return` statement is executed, the function stops running and returns the value. If there is any code below the `return` statement that is indented to be part of the function body, it will never run. For example:

```python
def multiply(x, y):
    product = x * y
    return product
    print("You can't see me!")
```

Calling this version of `multiply()` will not display the string "You can't see me!" because it is below the `return` statement and, due to indentation, is not considered part of the function body.

Ensuring consistent and correct indentation is essential for proper Python code execution.

### Calling a User-Defined Function

When calling a user-defined function in Python, it's essential to follow best practices for proper execution. Here are key points to remember:

**Syntax for Calling Functions**  
To call a user-defined function, use the function name followed by a list of arguments enclosed in parentheses. For example, to call `multiply()` with arguments 2 and 4:

```python
multiply(2, 4)
```

**Function Definition Placement**  
Unlike built-in functions, user-defined functions must be defined with the `def` keyword before they are called. Ensure that the function is defined in your script or module before making any function calls.

Consider the following script:

```python
num = multiply(2, 4)
print(num)

def multiply(x, y):
    product = x * y
    return product
```

When Python reads the line `num = multiply(2, 4)`, it doesn’t recognize the name multiply and raises a `NameError`:

```python
Traceback (most recent call last):
  File "C:Usersdaveamultiply.py", line 1, in <module>
    num = multiply(2, 4)
NameError: name 'multiply' is not defined
```

To resolve this, ensure that the function definition is placed before any function calls:

```python
def multiply(x, y):
    product = x * y
    return product

num = multiply(2, 4)
print(num)
```

It is a best practice to organize your script with function definitions at the beginning, creating a clear structure. This helps in avoiding `NameError` and makes your code more readable.

### Functions Without a Return Statement

In Python, all functions return a value, even if that value is `None`. However, not every function requires a `return` statement. Consider the following example:

```python
def greet(name):
    print(f"Hello, {name}!")
```

The `greet` function has no explicit `return` statement, yet it works perfectly:

```python
greet("Dave")
# Output: Hello, Dave!
```

Even though `greet` has no `return` statement, it implicitly returns `None`. If you assign the result to a variable, you'll notice that the variable holds `None`:

```python
return_value = greet("Dave")
# Output: Hello, Dave!
print(return_value)
# Output: None
```

It's important to note that the string "Hello, Dave!" is printed due to the `print()` statement inside the `greet` function, showcasing a side effect.

When creating your own functions, especially those without explicit `return` statements, it's crucial to document their behavior. Proper documentation helps other developers understand how to use the function and what to expect when calling it. This practice enhances code readability and collaboration.

### Python Function Mastery: Args, Kwargs, and Defaults

In Python functions, we encounter indispensable tools that include *args, catering to variable positional arguments, **kwargs, adept at managing keyword arguments, and default parameters, offering heightened adaptability. These elements are instrumental in the art of crafting functions that transcend rigidity, ensuring versatility and the ability to seamlessly adjust to a myriad of scenarios. 

**Positional Arguments**  
Positional Arguments are crucial when working with functions in Python. They refer to the values passed to a function's parameters in the order they are defined. The order of these arguments directly affects the function's output. For instance, consider the function `person(name, age)`:

```python
def person(name, age):
    print(f"{name} {age}")

person("nicholas", 22)  # Output: nicholas 22
person(22, "nicholas")  # Output: 22 nicholas
```

When calling the `person` function, the order of the arguments "nicholas" and 22 affects how they are assigned to the `name` and `age` parameters.


**Keyword Arguments**   
In contrast, Keyword Arguments allow values to be directly assigned to function parameters, regardless of their order. Here's an example using the same `person` function:

```python
def person(name, age):
    print(f"{name} {age}")

person(age="22", name="nicholas")  # Output: nicholas 22
```

Using Keyword Arguments provides more flexibility, especially in functions with many parameters where the order can become confusing.


**Default Parameters**   
In some situations, it is useful to set default values for function parameters. This is accomplished through Default Parameters. Consider the following example:

```python
def person(name="Jojo", age=22):
    print(f"{name} {age}")

person()               # Output: Jojo 22
person("nicholas", 30)  # Output: nicholas 30
```

Default Parameters enable the function to be called without providing values for all parameters, using pre-defined values when necessary.


**Handling Variable Sets of Elements in a Function**  
In addressing a dynamic assortment of elements, Python provides robust mechanisms through *args and **kwargs, particularly beneficial when dealing with collections such as lists, dictionaries, and more. These features enhance a function's adaptability and versatility.

*args, designated by an asterisk, allows a function to accept a variable number of positional arguments. In the following example, the function `process_data(*args)` demonstrates how to iterate through a list and calculate the sum:

```python
def process_data(*args):
    return sum(args)

data_list = [1, 2, 3, 4, 5]
result = process_data(*data_list)  # Output: 15
```

On the other hand, **kwargs, denoted with a double asterisk, enables the acceptance of keyword arguments. The subsequent example illustrates a function, `process_info(**kwargs)`, which extracts and sums the values associated with the provided keys in a dictionary:

```python
def process_info(**kwargs):
    total = sum(kwargs.values())
    return total

data_dict = {'num1': 2, 'num2': 1}
result = process_info(**data_dict)  # Output: 3
```

The true potency arises when *args and **kwargs are combined in a function, providing unparalleled flexibility. This allows the function to gracefully handle diverse data structures, making it applicable to a myriad of scenarios.

It's imperative to maintain awareness of the specified order when using these elements in conjunction: parameters, *args, default parameters, and **kwargs. By embracing these concepts, developers can craft Python functions that seamlessly adapt to different types and quantities of data, from lists to dictionaries and beyond.

### Recursive Functions

Functions in Python can exhibit recursion, where a function calls itself to accomplish a specific task. This self-invoking process is termed "recursion," and the function involved is known as a recursive function.

In a recursive function, the problem at hand is broken down into smaller, similar subproblems. Each subproblem is then tackled by applying the same function recursively. This recursive process persists until a base case is satisfied, indicating when the recursion should halt.

**Syntax of Recursive Function in Python:**

```python
def recursive_function(parameters):
    # Base case
    if base_case_condition:
        # Return a value or perform some action
        pass
    else:
        # Recursive case
        # Call the function with modified arguments
        return recursive_function(modified_parameters)
```

In this example:
- **Base Case:** This serves as the termination condition, dictating when the recursion should cease. It prevents the function from endlessly calling itself. When the base case is met, the recursion unwinds.  
- **Recursive Case:** In this segment, the function invokes itself with adjusted arguments, typically smaller or simpler than the original problem.

Let's consider a classic example of recursion in Python: calculating the factorial of a number.

```python
def factorial(n):
    # Base case: factorial of 0 or 1 is 1
    if n == 0 or n == 1:
        return 1
    else:
        # Recursive case: n! = n * (n-1)!
        return n * factorial(n - 1)

num = 5
result = factorial(num)
print(f"Factorial of {num} is {result}")
```

> *The base case checks if n is 0 or 1, returning 1 in such cases. In the recursive case, the function calls itself with n-1 to calculate (n-1)! and multiplies it by n to obtain n!. The recursion continues until the base case is satisfied.*

It's worth noting that recursive functions in Python may consume more memory and have slower processing compared to their iterative counterparts. This is due to the memory used in a function call being released only upon completion. However, recursive code is often more concise and can be easier to comprehend. Additionally, certain algorithms, especially those dealing with abstract data structures like trees, may be more efficiently implemented using recursion.




### Documenting Your Functions

Proper documentation enhances code understanding and usability. To provide helpful information about a function in IDLE's interactive window, you can use the `help()` function. For instance:

```python
help(len)
# Output:
# Help on built-in function len in module builtins:
# len(obj, /)
# Return the number of items in a container.
```

This information reveals that `len` is a built-in function returning the number of items in a container - a container is a special name for an object that contains other
objects. A string is a container because it contains characters.

However, when you use `help()` on a user-defined function without a docstring, you might not get the details you need:

```python
help(multiply)
# Output:
# Help on function multiply in module __main__:
# multiply(x, y)
```

In this case, there's no information about what the function does. To address this, add a **docstring** - a triple-quoted string placed at the top of the function body. The docstring should describe the function's purpose and the types of parameters it expects. For example:

```python
def multiply(x, y):
    """Return the product of two numbers x and y."""
    product = x * y
    return product
```

Now, when you use `help()` on `multiply`, you'll get a more informative output:

```python
help(multiply)
# Output:
# Help on function multiply in module __main__:
# multiply(x, y)
# Return the product of two numbers x and y.
```

There are a number of standardized docstring formats, but we won’t get into them here. Some general guidelines for writing docstrings can be found in [PEP 257](https://www.python.org/dev/peps/pep-0257/).


## Modules and Packages

**Modular programming** refers to the process of breaking a large, unwieldy programming task into separate, smaller, more manageable subtasks or **modules**. Individual modules can then be cobbled together like building blocks to create a larger application.

There are several advantages to **modularizing** code in a large application:

- **Simplicity:**  Rather than focusing on the entire problem at hand, a module typically focuses on one relatively small portion of the problem. If you’re working on a single module, you’ll have a smaller problem domain to wrap your head around. This makes development easier and less error-prone.

- **Maintainability:** Modules are typically designed so that they enforce logical boundaries between different problem domains. If modules are written in a way that minimizes interdependency, there is decreased likelihood that modifications to a single module will have an impact on other parts of the program.

- **Reusability:** Functionality defined in a single module can be easily reused (through an appropriately defined interface) by other parts of the application. This eliminates the need to duplicate code.

- **Scoping:** Modules typically define a separate namespace, which helps avoid collisions between identifiers in different areas of a program.

### Working With Modules

There are actually three different ways to define a module in Python:

1. A module can be written in Python itself.
2. A module can be written in C and loaded dynamically at run-time, like the re (regular expression) module.
3. A built-in module is intrinsically contained in the interpreter, like the itertools module.
   
A module’s contents are accessed the same way in all three cases: with the `import` statement.

Here, the focus will mostly be on modules that are written in Python. All you need to do is create a file that contains legitimate Python code and then give the file a name with a `.py` extension. That’s it! No special syntax is necessary.

For example, suppose you have created a file called `mod.py` containing the following:

```python
s = "If Comrade Napoleon says it, it must be right."
a = [100, 200, 300]

def foo(arg):
    print(f'arg = {arg}')

class Foo:
  pass
```

> ***Note:** Several objects are defined in mod.py: s (a string), a (a list), foo() (a function).*
  
Assuming `mod.py` is in an appropriate location, these objects can be accessed by importing the module as follows:

```python
>>> import mod
>>> print(mod.s)
If Comrade Napoleon says it, it must be right.
>>> mod.a
[100, 200, 300]
>>> mod.foo(['quux', 'corge', 'grault'])
arg = ['quux', 'corge', 'grault']
>>> x = mod.Foo()
>>> x
<mod.Foo object at 0x03C181F0>
```

### The Module Search Path

Continuing with the above example, let’s take a look at what happens when Python executes the statement:

```python
import mod
```

When the interpreter executes the `import` statement, it searches for `mod.py` in a list of directories assembled from the following sources:

- The directory from which the input script was run or the **current directory** if the interpreter is being run interactively
- The list of directories contained in the [PYTHONPATH](https://docs.python.org/3/using/cmdline.html#envvar-PYTHONPATH) environment variable, if it is set. (The format for PYTHONPATH is OS-dependent but should mimic the PATH environment variable.)
- An installation-dependent list of directories configured at the time Python is installed

The resulting search path is accessible in the Python variable `sys.path`, which is obtained from a module named sys:

```python
>>> import sys
>>> sys.path
['', 'C:\\Users\\john\\Documents\\Python\\doc', 'C:\\Python36\\Lib\\idlelib',
'C:\\Python36\\python36.zip', 'C:\\Python36\\DLLs', 'C:\\Python36\\lib',
'C:\\Python36', 'C:\\Python36\\lib\\site-packages']
```


> ***Note:** The  contents of sys.path are installation-dependent. The above will almost certainly look different on your computer.*


Thus, to ensure your module is found, you need to do one of the following:

- Put `mod.py`  in the directory where the input script is located or the **current directory**, if interactive.
- Modify the PYTHONPATH environment variable to contain the directory where mod.py is located before starting the interpreter.
  - Or: Put `mod.py` in one of the directories already contained in the PYTHONPATH variable.
- Put `mod.py`  in one of the installation-dependent directories, which you may or may not have write-access to, depending on the OS.


### The import Statement

Module  contents are made available to the caller with the import statement. The import statement takes many different forms, shown below.

**import <module_name>**  
The simplest form is the one already shown above:
```python
import <module_name>
```

Note that this does not make the module contents directly accessible to the caller. Each module has its own **private symbol table**, which serves as the global symbol table for all objects defined in the module. Thus, a module creates a separate **namespace**, as already noted.

The statement `import` <module_name> only places <module_name> in the caller’s symbol table. The objects that are defined in the module remain in the module’s private symbol table.

From the caller, objects in the module are only accessible when prefixed with <module_name> via dot notation, as illustrated below.

After the following `import` statement, mod is placed into the local symbol table. Thus, mod has meaning in the caller’s local context:

```python
>>> import mod
>>> mod
<module 'mod' from 'C:\\Users\\john\\Documents\\Python\\doc\\mod.py'>
```

To be accessed in the local context, names of objects defined in the module must be prefixed by mod:

```python
>>> mod.s
'If Comrade Napoleon says it, it must be right.'
>>> mod.foo('quux')
arg = quux
```


**from <module_name> import <name(s)>**  
An alternate form of the import statement allows individual objects from the module to be imported directly into the caller’s symbol table:

```python
from <module_name> import <name(s)>
```

Following execution of the above statement, <name(s)> can be referenced in the caller’s environment without the <module_name> prefix:

```python
>>> from mod import s, foo
>>> s
'If Comrade Napoleon says it, it must be right.'
>>> foo('quux')
arg = quux

>>> from mod import Foo
>>> x = Foo()
>>> x
<mod.Foo object at 0x02E3AD50>
```

Because this form of import places the object names directly into the caller’s symbol table, any objects that already exist with the same name will be overwritten:

```python
>>> a = ['foo', 'bar', 'baz']
>>> a
['foo', 'bar', 'baz']

>>> from mod import a
>>> a
[100, 200, 300]
```

It is even possible to indiscriminately import everything from a module at one fell swoop:

```python
from <module_name> import *
```

> ***Note:** This will place the names of all objects from <module_name> into the local symbol table, with the exception of any that begin with the underscore (_) character.*

This isn’t necessarily recommended in large-scale production code. It’s a bit dangerous because you are entering names into the local symbol table en masse. Unless you know them all well and can be confident there won’t be a conflict, you have a decent chance of overwriting an existing name inadvertently. However, this syntax is quite handy when you are just mucking around with the interactive interpreter, for testing or discovery purposes, because it quickly gives you access to everything a module has to offer without a lot of typing.


**from <module_name> import <name> as <alt_name>**  
It is also possible to import individual objects but enter them into the local symbol table with alternate names:

```python
from <module_name> import <name> as <alt_name>[, <name> as <alt_name> …]
```

This makes it possible to place names directly into the local symbol table but avoid conflicts with previously existing names:

```python
>>> s = 'foo'
>>> a = ['foo', 'bar', 'baz']

>>> from mod import s as string, a as alist
>>> s
'foo'
>>> string
'If Comrade Napoleon says it, it must be right.'
>>> a
['foo', 'bar', 'baz']
>>> alist
[100, 200, 300]
```


**import <module_name> as <alt_name>**  

You can also import an entire module under an alternate name:

```python
>>> import mod as my_module
>>> my_module.a
[100, 200, 300]
>>> my_module.foo('qux')
arg = qux
```

### Summary of Import Statements
The following table summarizes what you’ve learned about importing modules:

| Import Statement                   | Result                       |
| ---------------------------------- | --------------------------------------------------------------------------------------------------------------------------------------- |
| `import <module>`                  | Import all of `<module>`’s namespace into the name `<module>`. Import module names can be accessed from the calling module with `<module>.<name>`.|
| `import <module> as <other_name>`  | Import all of `<module>`’s namespace into the name `<other_name>`. Import module names can be accessed from the calling module with `<other_name>.<name>`.|
| `from <module> import <name1>, <name2>, ...` | Import only the names `<name1>`, `<name2>`, etc., from `<module>`. The names are added to the calling module’s local namespace and can be accessed directly.|

Separate namespaces are one of the great advantages of dividing code into individual modules, so let’s take some time to explore why namespaces matter and why you should care about them.

### Why Use Namespaces?

Imagine assigning a unique ID number to every individual on the planet, ensuring that each person is distinguishable from the next. To achieve this, we require a vast array of unique ID numbers. The world is divided into countries, providing a natural way to group people based on their country of birth. By assigning each country a unique code, we can incorporate this code into a person's ID number. For instance, a person from the United States might have an ID like US-357, while someone from Great Britain could have an ID such as GB-246.

This approach allows two individuals from different countries to share the same ID number, with differentiation provided by the distinct country codes at the beginning of their IDs. While every person from the same country must have a unique ID number, there is no longer a need for globally unique ID numbers.

The country codes in this scenario serve as examples of namespaces, illustrating three primary reasons namespaces are utilized:

1. They **group** names into logical containers.
2. They **prevent clashes** between duplicate names.
3. They **provide** context to names.

Applying namespaces in code provides the same advantages. Three different ways to import a module into another have been introduced. Considering the advantages of namespaces can help determine the most suitable import statement:

- In general, `import <module>` is preferred as it keeps the imported module's namespace entirely separate from the calling module's namespace. Every name from the imported module is accessed using the `<module>.<name>` format, indicating its origin.

- `import <module> as <other_name>` is used when the module name is lengthy, or there's a clash with an existing name in the calling module. While it maintains separation of namespaces, the chosen name may be less recognizable.

- Importing specific names from a module (`from <module> import <name1>, <name2>, ...`) is generally the least preferred method, as it adds names directly to the calling module's namespace, removing them from their original context.

In some cases, modules contain a single function or class with the same name as the module itself. For example, the datetime module includes a class called datetime. To address potential redundancy, Python programmers commonly use variations of the import statement. For instance:

Suppose you add the following import statement to your code:

```python
import datetime
```

This imports the `datetime` module into your code’s namespace. To use the `datetime` class contained in the `datetime` module, you would typically need to type the following:

```python
datetime.datetime(2020, 2, 2)
```

This is a great example of when it’s appropriate to use one of the variations of the import statement. To keep the context of the `datetime` package, it is common for Python programmers to import the package and rename it as `dt`:

```python
import datetime as dt
```

Now, to use the `datetime` class, you only need to type `dt.datetime`:

```python
dt.datetime(2020, 2, 2)
```

It is also common for Python programmers to import the `datetime` class directly into the calling module’s namespace:

```python
from datetime import datetime
```

This is fine because the context isn’t really lost. The class and the module share the same name, after all. When imported directly, you no longer have to use dotted module names to access the `datetime` class:

```python
datetime(2020, 2, 2)
```
While these import statements reduce typing and long dotted module names, it's crucial to exercise good judgment to avoid a loss of context and maintain code clarity.

### Reloading a Module

For reasons of efficiency, a module is only loaded once per interpreter session. That is fine for function and class definitions, which typically make up the bulk of a module’s contents. But a module can contain executable statements as well, usually for initialization. Be aware that these statements will only be executed the first time a module is imported.

Consider the following file mod.py:

```python
a = [100, 200, 300]
print('a =', a)
```

```python
>>> import mod
a = [100, 200, 300]
>>> import mod
>>> import mod

>>> mod.a
[100, 200, 300]
```

The print() statement is not executed on subsequent imports. (For that matter, neither is the assignment statement, but as the final display of the value of mod.a shows, that doesn’t matter. Once the assignment is made, it sticks.)

If you make a change to a module and need to reload it, you need to either restart the interpreter or use a function called reload() from module importlib:

```python
>>> import mod
a = [100, 200, 300]

>>> import mod

>>> import importlib
>>> importlib.reload(mod)
a = [100, 200, 300]
<module 'mod' from 'C:\\Users\\Alighieri\\Documents\\Python\\doc\\mod.py'>
```


### Working With Packages

Modules allow you to divide a program in to individual files that can be reused as needed. Related code can be organized into a single module and kept separate from other code.

Packages allow for a hierarchical structuring of the module namespace using dot notation. In the same way that modules help avoid collisions between global variable names, packages help avoid collisions between module names.

### Creating Packages
A package is a folder that contains one or more Python modules. It must also contain a special module called `__init__.py`. Here is an example of a package so that you can see this structure:

```plaintext
mypackage/
|-- __init__.py
|-- module1.py
|-- module2.py
```

> ***Note:** Creating a package is straightforward, since it makes use of the operating system’s inherent hierarchical file structure.*

The `__init__.py` module serves a specific purpose — it doesn't require any code. Its sole existence is crucial for Python to recognize the `mypackage/` folder as a valid Python package.

To illustrate, use your computer's file explorer or a preferred tool to create a new folder named `packages_example/` somewhere on your computer. Within this folder, create another one called `mypackage/`.

The `packages_example/` folder is commonly referred to as the project folder or project root folder. It encompasses all files and folders in the `packages_example` project. On the other hand, the `mypackage/` folder is destined to become a Python package. However, at its current state, it doesn't qualify as one since it lacks any modules.

This distinction emphasizes the significance of the `__init__.py` module, as its presence signals to Python that `mypackage/` is intended to be treated as a Python package. It serves as an essential marker for package recognition, even though it may not contain any code itself.

Now that the package structure is established, let's incorporate some code. In the `module1.py` file, include the following function:

```python
# module1.py
def greet(name):
    print(f"Hello, {name}!")
```

In the `module2.py` file, add the following function:

```python
# module2.py
def depart(name):
    print(f"Goodbye, {name}!")
```

Ensure that you save both the `module1.py` and `module2.py` files. With these additions, your package is now equipped with functions that can be imported and utilized in the `main.py` module.

### Importing Modules From Packages

In your `main.py` file, you've encountered an issue where importing the `mypackage` module does not automatically import the `module1` and `module2` namespaces. To resolve this, you need to import them explicitly. Modify the import statement at the top of the `main.py` file as follows:

```python
# main.py
import mypackage.module1  # <-- Change this line
# Leave the below code unchanged
mypackage.module1.greet("Pythonista")
mypackage.module2.depart("Pythonista")
```

After saving and running `main.py`, you'll notice that only `mypackage.module1.greet()` was called, and an attribute error was raised for `mypackage.module2.depart()`. This is because, at this point, only `module1` has been imported from `mypackage`.

To import `module2`, add the following import statement to the top of your `main.py` file:

```python
# main.py
import mypackage.module1
import mypackage.module2  # <-- Add this line
# Leave the below code unchanged
mypackage.module1.greet("Pythonista")
mypackage.module2.depart("Pythonista")
```

Now, after saving and running `main.py`, both `greet()` and `depart()` functions get called:

```python
Hello, Pythonista!
Goodbye, Pythonista!
```

For general reference, modules are imported from packages using dotted module names with the following format:

```python
import <package_name>.<module_name>
```

Keep in mind that both module file names and package folder names must be valid Python identifiers, adhering to rules such as containing only letters (upper and lower case), numbers, and underscores (_), and not starting with a digit. There are also various variations of the import statement that can be employed when importing packages.

### Import Statement Variations for Packages

In addition to the import statement variations learned for importing names from modules, there are four corresponding variations for importing modules from packages:

1. `import <package>`
2. `import <package> as <other_name>`
3. `from <package> import <module>`
4. `from <package> import <module> as <other_name>`

These variations operate similarly to their counterparts for modules.

For example, instead of importing `mypackage.module1` and `mypackage.module2` separately, both modules can be imported from the package on the same line. Update your `main.py` file as follows:

```python
# main.py
from mypackage import module1, module2

module1.greet("Pythonista")
module2.depart("Pythonista")
```

When you save and run the module, the output remains the same as before in the interactive window.

You can also change the name of an imported module using the `as` keyword:

```python
# main.py
from mypackage import module1 as m1, module2 as m2

m1.greet("Pythonista")
m2.depart("Pythonista")
```

Individual names from a package module can also be imported. For instance, you can rewrite your `main.py` without changing the printed output:

```python
# main.py
from mypackage.module1 import greet
from mypackage.module2 import depart

greet("Pythonista")
depart("Pythonista")
```

These techniques provide flexibility in managing package imports, making code more concise and readable.

### Guidelines for Importing Packages

The same principles that apply to importing names from modules also extend to importing modules from packages. It is advisable to prioritize explicit imports to ensure that the modules and names brought into the calling module maintain appropriate context.

In general, the most explicit format is as follows:

```python
import <package>.<module>
```

To access names from the module, you would then type something like the following:

```python
<package>.<module>.<name>
```

This format ensures clarity regarding the origin of names used from the imported module. However, in cases where package and module names are lengthy, repeatedly typing `<package>.<module>` in the code can become cumbersome.

To address this, the following format allows you to skip the package name and import just the module name into the calling module’s namespace:

```python
from <package> import <module>
```

Now, you can simply type `<module>.<name>` to access a name from the module. While this omits information about the package's origin, it preserves the context of the module.

Finally, the following format should be used with caution, as it is generally ambiguous and should only be employed when there is no risk of importing a name from a module that clashes with a name in the calling module:

```python
from <package>.<module> import <name>
```

Always exercise discretion when choosing the import format to strike a balance between explicitness and conciseness, ensuring the code remains clear and maintainable.

### Importing Modules From Subpackages

A package, in essence, is nothing more than a folder that encompasses one or more Python modules. Crucially, among these modules, there must be one named `__init__.py`. This signifies a minimal package structure and underscores the flexibility in designing package compositions. The package structure could look like the following:

```plaintext
mypackage/
|-- mysubpackage/
|   |-- __init__.py
|   |-- module3.py
|
|-- __init__.py
|-- module1.py
|-- module2.py
```

> ***Note:** A package nested inside of another package is called a subpackage.*

In this example, mypackage is the main package that contains three modules: module1.py, module2.py, and `__init__.py`. Additionally, there is a subpackage named mysubpackage, which includes `module3.py` and its own `__init__.py` file.

This structure illustrates the hierarchical organization you can achieve with packages and subpackages in Python projects. The `__init__.py` file is crucial to indicate that a directory is a recognized package or subpackage by the Python interpreter.

Using your computer's file explorer or another tool, create the `mysubpackage/` folder on your computer. Ensure that you place the folder inside the `mypackage/` folder you previously created.

In IDLE, open two new script windows. Create the files `__init__.py` and `module3.py` and save both modules to the `mysubpackage/` folder.

In your `module3.py` file, add the following code:

```python
# module3.py
people = ["John", "Paul", "George", "Ringo"]
```

Now open the `main.py` file in your root `packages_examples/` project folder. Remove any existing code and replace it with the following:

```python
# main.py
from mypackage.module1 import greet
from mypackage.mysubpackage.module3 import people

for person in people:
    greet(person)
```

The `people` list from the `module3` module inside the `mysubpackage` is imported via the dotted module name `mypackage.mysubpackage.module3`.

Save and run `main.py`. The following output is displayed in the interactive window:

```
Hello, John!
Hello, Paul!
Hello, George!
Hello, Ringo!
```

Subpackages are excellent for organizing code inside very large packages, helping to maintain a clean and organized folder structure. However, deeply nested subpackages can result in long dotted module names. Imagine the effort required to import a module from a subpackage of a subpackage of a subpackage of a package. It is advisable to keep subpackages at most one or two levels deep to maintain good practice.


## Exploring Powerful Features in Python: map, zip, filter, and reduce

Python, a versatile and powerful programming language, provides an array of tools that facilitate efficient data manipulation. Among these tools are the functions `map`, `zip`, `filter`, and `reduce`, which belong to the arsenal of functional programming in Python. In this text, we will delve into each of these functions, understand how they can be applied, and analyze practical examples to illustrate their utility.

### map Function

The `map` function in Python is an essential built-in feature meticulously crafted to facilitate the application of a designated function to every element within an iterable. This process yields a fresh iterable containing the outcomes of the applied function. This functionality proves especially advantageous when there is a need to execute operations seamlessly across all elements of a list or any other comparable sequence. 

```python
map(function, iterables)
# function: The function to apply to each item.
# iterable: One or more iterables whose elements will be processed by the function.
```

> ***Note:** The map function transforms data without explicit loops, ensuring cleaner, readable code.*

By leveraging the `map` function, developers can enhance the efficiency of their code, as it streamlines the process of iterating through data structures and applying a specified operation to each element, thereby promoting concise and readable code. This versatility empowers programmers to perform transformations on data structures with ease, contributing to the creation of more elegant and maintainable Python code.

**Example:**
```python
# Doubling each element of a list using map
numbers = [1, 2, 3, 4, 5]

# Apply the function to each element using map
doubled = map(lambda x: x * 2, numbers)

# Convert the map object to a list for printing
print(list(doubled))
# Output: [2, 4, 6, 8, 10]
```


#

### zip Function

The `zip` function in Python serves as a valuable tool for amalgamating elements from two or more iterables, generating an iterable of tuples. This functionality becomes particularly advantageous when there is a requirement for concurrent iteration over multiple lists. By utilizing the `zip` function, developers can efficiently pair corresponding elements from distinct iterables, encapsulating them within tuples for seamless traversal. 

```python
zip(iterable1, iterable2, ...)
# iterable1, iterable2, ...: The iterables to be combined.
```
 
> ***Note:** zip simplifies the process of working with multiple sequences concurrently, facilitating parallel data processing.*

This capability streamlines the process of working with data from multiple sources simultaneously, enhancing code conciseness and readability. Whether it's aligning values from different lists or merging data structures in a synchronized manner, the `zip` function proves to be a versatile and essential asset in Python programming, contributing to the creation of more elegant and efficient solutions.

**Example:**
```python
# Combining two lists into tuples using zip
names = ['Alice', 'Bob', 'Charlie']
ages = [25, 30, 35]

# Combine the lists using zip
combined = zip(names, ages)

# Convert the zip object to a list for printing
print(list(combined))
# Output: [('Alice', 25), ('Bob', 30), ('Charlie', 35)]
```

#

### filter Function

The `filter` function in Python stands out as a powerful tool used to selectively extract elements from an iterable according to a designated condition. Its primary purpose is to streamline the process of identifying and retaining only those elements that meet specific criteria, thereby generating a fresh iterable enriched with the desired subset of data.

When employing the `filter` function, developers can provide a custom condition or predicate, specifying the criteria that elements must satisfy to be included in the resulting iterable. This capability is particularly valuable in scenarios where a comprehensive data set needs to be refined, extracting only the elements that align with specific requirements.

```python
filter(function, iterable)
# function: The function that tests if each element of the iterable meets the specified condition.
# iterable: The iterable to be filtered.
```
> ***Note:** filter  enhances code readability by straightforwardly returning elements from the iterable that evaluate to true.*

This function enhances code clarity and conciseness by eliminating the need for manual iteration and conditional statements. Developers can focus on defining the filtering criteria, allowing Python to handle the intricate task of sifting through the iterable and assembling a new collection of elements that pass the specified test.

Whether dealing with lists, tuples, or other iterable structures, the `filter` function empowers programmers to efficiently manage data and extract subsets that are pertinent to their specific needs. Its versatility extends across various use cases, ranging from data cleaning and preprocessing to the dynamic creation of subsets based on dynamic conditions, contributing to the development of more expressive, modular, and efficient Python code.

**Example:**
```python
# Filtering even numbers from a list using filter
numbers = [1, 2, 3, 4, 5, 6]

# Apply the function to filter even numbers
evens = filter(lambda x: x % 2 == 0, numbers)

# Convert the filter object to a list for printing
print(list(evens))
# Output: [2, 4, 6]
```

#

### reduce Function

The `reduce` function, a valuable component within the `functools` module in Python, plays a pivotal role in iteratively applying a binary function to the elements of an iterable. Unlike other functions like `map` or `filter` that produce iterables of the same length as the input, `reduce` systematically combines the elements of the iterable, progressively condensing it into a singular, accumulated value.

To employ the `reduce` function, developers provide a binary function that takes two arguments, typically representing the current accumulated result and the next element in the iterable. This binary function is successively applied to pairs of elements in the iterable until the entire sequence is reduced to a single value.


```python
functools.reduce(function, iterable, initializer)
# function: The binary function to apply cumulatively to the items of the iterable.
# iterable: The iterable to be reduced.
# initializer: An optional argument providing the initial value for the accumulator.
```

> ***Note:** While not a standard built-in function, reduce is a potent tool for iteratively combining elements into a single value.*

The utility of the `reduce` function becomes apparent in scenarios where a cumulative computation, such as summing a sequence of numbers or finding the maximum element, is required. It simplifies the code by encapsulating the iterative process within a concise function call, promoting code readability and maintainability.

While the `reduce` function might not be as commonly used as some other built-in functions, its capability to systematically aggregate values in an iterable provides a valuable tool for tasks that involve cumulative operations. Understanding how to harness the power of `reduce` contributes to the creation of more expressive and efficient Python code, especially in scenarios where a step-wise reduction of a sequence to a single result is a key requirement.

**Example:**
```python
# Summing all elements of a list using reduce
from functools import reduce

numbers = [1, 2, 3, 4, 5]

# Apply the function to reduce the list to a single value
sum_result = reduce(lambda x, acc: x + acc, numbers, 0) 

# Print the final accumulated value
print(sum_result)
# Output: 15
```

## Object-Oriented Programming (OOP)

Object-Oriented Programming (OOP) is a methodology for organizing a program by grouping related properties and behaviors into distinct objects. In a conceptual sense, these objects can be likened to components within a system, analogous to a factory assembly line.

Consider a program as a virtual assembly line in a factory. At each stage of the assembly line, a system component processes material to some extent, ultimately culminating in the transformation of raw material into a finished product.

Each object, akin to the components at various stages of the assembly line, encompasses both data and behavior. The data within an object corresponds to the raw or pre-processed materials found at each step of the assembly line. Meanwhile, the behavior encapsulates the actions undertaken by each component along the assembly line.

### Define a Class

Primitive data structures, such as numbers, strings, and lists, are designed to represent simple entities like costs, poem names, and favorite colors. However, for more complex representations, such as tracking employees in an organization, a more structured approach is necessary.

For instance, if you need to store basic information about each employee, like their **name, age, position,** and **start year**, using **lists** may lead to several issues. Consider the following examples:

```python
kirk = ["James Kirk", 34, "Captain", 2265]
spock = ["Spock", 35, "Science Officer", 2254]
mccoy = ["Leonard McCoy", "Chief Medical Officer", 2266]
```

There are problems with this approach. Firstly, referencing `kirk[0]` in a distant part of the code may lead to confusion about what the $0$th element represents. Additionally, the inconsistency in the number of elements in the list, as seen in the `mccoy` example where the age is missing, can result in errors.

To enhance code manageability and maintainability, a recommended approach is to use **classes**.

### Classes vs Instances

Classes serve as a means to create user-defined data structures, incorporating special functions known as **methods** that delineate behaviors and actions that objects, instantiated from the class, can undertake with their data.

In this chapter, a Dog class is introduced, aiming to store fundamental information about a dog.

It is crucial to understand that a class primarily provides structure, essentially acting as a blueprint for defining something. However, a class does not inherently contain real content. For example, the Dog class may outline that a name and age are requisite for defining a dog, yet it does not specify the name or age of a particular dog.

While the class serves as the blueprint, an **instance** is a concrete object constructed from a class, possessing real data. An instance of the Dog class ceases to be a mere blueprint; it becomes an actual dog with specific attributes, such as a name like Miles, who is four years old.

Alternatively, likening a class to a form or questionnaire helps to clarify its role. The class establishes the necessary information, similar to what a form outlines. Once the form is filled out, the resultant specific copy becomes an instance of the class, containing actual information pertinent to the individual or object.

In essence, a class is akin to a guide that provides structure and requirements. Creating multiple instances involves filling out multiple copies of the form. Without the class as a guide, creating instances would be confusing, as the required information would be unclear. Therefore, prior to creating individual instances of an object, it is imperative to first specify the necessary details by defining a class.

### How to Define a Class

All class definitions commence with the `class` keyword, followed by the name of the class and a colon. This structure resembles the signature of a function, with the distinction that no parameters need to be enclosed in parentheses. Any code indented below the class definition is regarded as part of the class's body.

Here is an example of a simple Dog class:

```python
class Dog:
    pass
```

The body of the `Dog` class comprises a single statement: the `pass` keyword. `pass` is often used as a placeholder where code will eventually be inserted, allowing the code to run without generating an error.

In Python, unlike functions and variables, the convention for naming classes is to use [CamelCase notation](https://en.wikipedia.org/wiki/Camel_case), initiating with a capital letter. For instance, a class for a specific dog breed, such as the Jack Russell Terrier, would be named `JackRussellTerrier`.

As the `Dog` class lacks distinct properties, let's enhance it by defining some attributes that all `Dog` objects should possess. Properties like name, age, coat color, and breed are options, but for simplicity, let's focus on just two for now: `name` and `age`.

To define these properties, or instance attributes, for all `Dog` objects, a special method called `.__init__()` must be defined. This method runs every time a new `Dog` object is created, specifying the initial state or values of the object's properties.

The first positional argument of `.__init__()` is invariably a variable that references the class instance, typically named `self`. After the `self` argument, other arguments required for creating an instance of the class can be specified.

The updated `Dog` class definition illustrates how to write an `.__init__()` method that creates two instance attributes: `.name` and `.age`:

```python
class Dog:
    def __init__(self, name, age):
        self.name = name
        self.age = age
```

Note the indentation of four spaces for the function signature and eight spaces for the function body. This indentation is crucial as it informs Python that the `.__init__()` method is associated with the `Dog` class. Without indentation, Python would treat `__init__()` as a standalone function.

> ***Note:** Instance methods in a class, like list.append() and string.find(), are functions tied to the class instance.*


In the body of the `.__init__()` method, two statements utilize the `self` variable. The first line, `self.name = name`, establishes an instance attribute named `name` and assigns it the value of the `name` variable passed to the `.__init__()` method. Similarly, the second line creates an instance attribute named `age` and assigns it the value of the `age` argument.

This may appear a bit peculiar, as the `self` variable refers to an instance of the `Dog` class, even though no instance has been created yet. It serves as a placeholder used to construct the blueprint. Remember, the class defines the structure of the `Dog` data but doesn't instantiate specific dogs with unique names and ages.

While instance attributes are specific to each object, **class attributes** remain the same for all instances, representing properties shared by all instances. In the next example, a class attribute named `species` is introduced and assigned the value "Canis familiaris":

```python
class Dog:
    # Class Attribute
    species = "Canis familiaris"

    def __init__(self, name, age):
        self.name = name
        self.age = age
```

Class attributes are defined directly below the first line of the class and outside any method definition. They must be assigned a value since they are created on a class instance without arguments to determine their initial value.

Class attributes should be used when a property needs to have the same initial value for all instances of a class. On the other hand, instance attributes are more suitable for properties that must be specified before an instance is created, and their values may vary across instances.


### Instantiate an Object

Once a class has been defined, it serves as a blueprint for creating, or **instantiating**, new objects. To instantiate an object, you use the name of the class, in the original CamelCase, followed by parentheses containing any values that must be passed to the class's `. __init__()` method.

For example:

```python
class Dog:
    pass

dog_instance = Dog()
```

This code creates a new `Dog` class with no attributes or methods and then instantiates a new `Dog` object named `dog_instance`.

When you instantiate a new object, you get an output indicating the memory address of the object. For instance:

```python
>>> Dog()
<__main__.Dog object at 0x106702d30>
```

The memory address displayed will likely differ on your screen.

Instantiate another `Dog` object:

```python
>>> Dog()
<__main__.Dog object at 0x0004ccc90>
```

The new `Dog` instance is located at a different memory address, signifying that it is an entirely new instance, distinct from the first `Dog` object instantiated.

To demonstrate this further:

```python
>>> a = Dog()
>>> b = Dog()
>>> a == b
False
```

Here, two new `Dog` objects are created and assigned to the variables `a` and `b`. When comparing `a` and `b` using the `==` operator, the result is `False`. For user-defined classes, the default behavior of the `==` operator is to compare the memory addresses of two objects and return `True` if the addresses are the same, and `False` otherwise.

This implies that even though the `a` and `b` objects are instances of the `Dog` class with the exact same attributes and methods (none in this case), `a` and `b` represent two distinct objects in memory.

Certainly, you can use the `type()` function to ascertain an object's class. For example:

```python
>>> type(a)
<class '__main__.Dog'>
```

Here, `type(a)` returns `<class '__main__.Dog'>`, indicating that `a` is an instance of the `Dog` class.

Despite `a` and `b` being distinct `Dog` instances, they share the same type:

```python
>>> type(a) == type(b)
True
```

The comparison `type(a) == type(b)` evaluates to `True`, emphasizing that both `a` and `b` belong to the same class, which is the `Dog` class in this case.

### Class and Instance Attributes

In the provided example using the `Dog` class with `.name` and `.age` instance attributes:

```python
class Dog:
    species = "Canis familiaris"
    
    def __init__(self, name, age):
        self.name = name
        self.age = age

buddy = Dog("Buddy", 9)
miles = Dog("Miles", 4)
```

Two instances of the `Dog` class are created—one named Buddy, who is nine years old, and another named Miles, who is four years old.

You might notice that even though the `.__init__()` method has three parameters (including `self`), only two arguments are passed to it when instantiating the `Dog` objects. This is because, when you create a `Dog` object, Python automatically creates a new instance and passes it to the `self` parameter, essentially removing the need to explicitly provide `self` as an argument.

After creating the `Dog` instances, you can access their instance attributes using **dot notation**:

```python
>>> buddy.name
'Buddy'
>>> buddy.age
9
>>> miles.name
'Miles'
>>> miles.age
4
```

Class attributes are accessed similarly:

```python
>>> buddy.species
'Canis familiaris'
```

One of the significant advantages of using classes is that instances are guaranteed to have the attributes you expect. Both `buddy` and `miles` have the `.species` attribute, contrasting with the potential issues encountered when using lists to represent similar data structures.

Both instance and class attributes can be modified dynamically:

```python
>>> buddy.age = 10
>>> buddy.age
10
>>> miles.species = "Felis silvestris"
>>> miles.species
'Felis silvestris'
```

In this example, the `.age` attribute of the `buddy` object is changed to 10, and the `.species` attribute of the `miles` object is changed to "Felis silvestris," making Miles a peculiar dog, but it is valid Python.

The key takeaway is that custom objects are mutable by default, meaning they can be altered dynamically. Objects like lists and dictionaries are mutable, while strings and tuples are immutable. Understanding these concepts lays the foundation for exploring instance methods in more detail.

### Instance Methods

Instance methods in Python are functions defined inside a class. They operate within the context of the object itself and cannot be called without referencing the object. Similar to `.__init__()`, the first argument of an instance method is always `self`.

Here's an example using the `Dog` class:

```python
class Dog:
    species = "Canis familiaris"

    def __init__(self, name, age):
        self.name = name
        self.age = age

    # Instance method
    def description(self):
        return f"{self.name} is {self.age} years old"

    # Another instance method
    def speak(self, sound):
        return f"{self.name} says {sound}"
```

In this example, two instance methods are defined:
1. `.description()` returns a string displaying the name and age of the dog.
2. `.speak()` has one parameter called `sound` and returns a string containing the dog’s name and the sound the dog makes.

To see instance methods in action:

```python
miles = Dog("Miles", 4)
print(miles.description())   # Output: 'Miles is 4 years old'
print(miles.speak("Woof Woof"))   # Output: 'Miles says Woof Woof'
print(miles.speak("Bow Wow"))     # Output: 'Miles says Bow Wow'
```

The `.description()` method returns a string containing information about the `Dog` instance `miles`. It's a good practice to have a method that returns a string with useful information about an instance.

When you print an object, the default output might not be very informative:

```python
print(miles)
# Output: <__main__.Dog object at 0x00aeff70>
```

You can improve this by defining a special instance method called `.__str__()`:

```python
class Dog:
    # Other parts of Dog class remain unchanged
    # Replace .description() with __str__()
    def __str__(self):
        return f"{self.name} is {self.age} years old"
```

Now, when you print the `miles` object, you get a more friendly output:

```python
miles = Dog("Miles", 4)
print(miles)
# Output: 'Miles is 4 years old'
```

Methods like `.__str__()` are commonly referred to as dunder methods because they begin and end with double underscores. These methods allow your classes to work well with other Python language features.

### Inherit From Other Classes

Inheritance is a process in object-oriented programming where one class acquires the attributes and methods of another class. The newly formed classes are referred to as child classes, and the classes from which **child classes** are derived are known as **parent classes**.

Child classes have the ability to **override** and extend the attributes and methods of parent classes. Essentially, child classes inherit all of the parent's attributes and methods but can also introduce new attributes and methods unique to themselves. Moreover, they can redefine methods inherited from their parent class.

The concept of object inheritance can be likened to genetic inheritance, although the analogy is not perfect. For instance, consider inheriting hair color from your mother — it's an attribute you are born with. If you decide to color your hair purple, you are effectively overriding the hair color attribute inherited from your mom.

Similarly, language can be inherited in a sense. If your parents speak English, you are likely to speak English as well. However, you might decide to extend your linguistic capabilities by learning a second language, such as German. In this scenario, you are **extending** attributes by adding a language attribute that your parents did not have.

### The object Class

In Python, the most basic type of class is an object, and generally, all other classes implicitly inherit from it as their parent. When you define a new class, Python 3 automatically uses `object` as the parent class. Therefore, the following two class definitions are equivalent:

```python
class Dog(object):
    pass
```

In Python 3, this is equivalent to:

```python
class Dog:
    pass
```

The inheritance from `object` is explicitly stated in the first definition by placing `object` in parentheses after the `Dog` class name. This pattern is consistent with creating child classes from your own custom classes.

Let’s see how and why you might create child classes from a parent class.

**Dog Park Example**  
Imagine being at a dog park surrounded by dogs of various breeds, each engaged in unique dog behaviors. Now, let's consider modeling this dog park using Python classes.

The `Dog` class from the previous section can distinguish dogs by name and age but lacks the ability to identify them by breed. To address this, we can enhance the `Dog` class by introducing a `.breed` attribute:

```python
class Dog:
    species = "Canis familiaris"
    
    def __init__(self, name, age, breed):
        self.name = name
        self.age = age
        self.breed = breed
```

> ***Note:** The instance methods defined earlier are omitted here as they are not crucial for the current discussion.*

Now, to model the diversity in the dog park, we can instantiate various dogs:

```python
miles = Dog("Miles", 4, "Jack Russell Terrier")
buddy = Dog("Buddy", 9, "Dachshund")
jack = Dog("Jack", 3, "Bulldog")
jim = Dog("Jim", 5, "Bulldog")
```

Different dog breeds exhibit slightly distinct behaviors. For instance, bulldogs have a low bark resembling "woof," while dachshunds have a higher-pitched bark akin to "yap."

Using only the `Dog` class, one would need to provide a string for the sound argument of the `.speak()` method every time it's called on a `Dog` instance:

```python
buddy.speak("Yap")  # Output: 'Buddy says Yap'
jim.speak("Woof")   # Output: 'Jim says Woof'
jack.speak("Woof")  # Output: 'Jack says Woof'
```

Having to pass a string for every `.speak()` call is both repetitive and inconvenient. Moreover, the string representing the sound made by each `Dog` instance depends on the `.breed` attribute, but there's nothing preventing someone from passing any string they wish.

To simplify working with the `Dog` class, a better approach is to create a child class for each breed of dog. This allows for extending the functionality inherited by each child class, including specifying a default argument for `.speak()`.

### Parent Classes vs Child Classes

Let's create a child class for each of the three dog breeds mentioned earlier: Jack Russell Terrier, Dachshund, and Bulldog. For reference, here is the complete definition of the `Dog` class:

```python
class Dog:
    species = "Canis familiaris"
    
    def __init__(self, name, age):
        self.name = name
        self.age = age
    
    def __str__(self):
        return f"{self.name} is {self.age} years old"
    
    def speak(self, sound):
        return f"{self.name} says {sound}"
```

To create a child class, you establish a new class with its own name and then include the name of the parent class in parentheses. Here, we create three new child classes for the `Dog` class:

```python
class JackRussellTerrier(Dog):
    pass

class Dachshund(Dog):
    pass

class Bulldog(Dog):
    pass
```

Now, with the child classes defined, you can instantiate dogs of specific breeds:

```python
miles = JackRussellTerrier("Miles", 4)
buddy = Dachshund("Buddy", 9)
jack = Bulldog("Jack", 3)
jim = Bulldog("Jim", 5)
```

Instances of child classes inherit all attributes and methods of the parent class:

```python
print(miles.species)  # Output: 'Canis familiaris'
print(buddy.name)     # Output: 'Buddy'
print(jack)           # Output: Jack is 3 years old
print(jim.speak("Woof"))  # Output: 'Jim says Woof'
```

To determine the class to which an object belongs, use the built-in `type()` function:

```python
print(type(miles))  # Output: <class '__main__.JackRussellTerrier'>
```

To check if an object is an instance of a specific class, use `isinstance()`:

```python
print(isinstance(miles, Dog))      # Output: True
print(isinstance(miles, Bulldog))  # Output: False
print(isinstance(jack, Dachshund))  # Output: False
```

In summary, all objects created from a child class are instances of the parent class, although they may not be instances of other child classes. Now that we have child classes for different breeds of dogs, let's assign each breed its distinctive sound.

### Extending the Functionality of a Parent Class

At this point, we have four classes in play: a parent class—`Dog`—and three child classes—`JackRussellTerrier`, `Dachshund`, and `Bulldog`. All three child classes inherit every attribute and method from the parent class, including the `.speak()` method.

Since different breeds of dogs have slightly different barks, we want to provide a default value for the sound argument of their respective `.speak()` methods. To do this, we need to override the `.speak()` method in the class definition for each breed. Overriding a method from the parent class involves defining a method with the same name on the child class.

Let's consider the example of the `JackRussellTerrier` class:

```python
class JackRussellTerrier(Dog):
    def speak(self, sound="Arf"):
        return f"{self.name} says {sound}"
```

Now, the `.speak()` method is defined on the `JackRussellTerrier` class with the default argument for sound set to "Arf". You can call `.speak()` on a `JackRussellTerrier` instance without passing an argument to sound:

```python
miles = JackRussellTerrier("Miles", 4)
print(miles.speak())  # Output: 'Miles says Arf'
```

If Miles gets angry and growls, you can still call `.speak()` with a different sound:

```python
print(miles.speak("Grrr"))  # Output: 'Miles says Grrr'
```

One advantage of class inheritance is that changes to the parent class will automatically propagate to their child classes, as long as the attribute or method being changed isn’t overridden in the child class. For example, if we decide to change the string returned by `.speak()` in the `Dog` class:

```python
class Dog:
    # Other attributes and methods omitted...
    def speak(self, sound):
        return f"{self.name} barks: {sound}"
```

Now, when you create a new `Bulldog` instance named `jim`, the result of `jim.speak("Woof")` will be 'Jim barks: Woof' instead of 'Jim says Woof':

```python
jim = Bulldog("Jim", 5)
print(jim.speak("Woof"))  # Output: 'Jim barks: Woof'
```

However, calling `.speak()` on a `JackRussellTerrier` instance won’t reflect the new style of output:

```python
miles = JackRussellTerrier("Miles", 4)
print(miles.speak())  # Output: 'Miles says Arf'
```

Sometimes, it makes sense to completely override a method from a parent class. However, in this instance, we don’t want the `JackRussellTerrier` class to lose any changes that might be made to the formatting of the output string of `Dog.speak()`.

To achieve this, you need to define a `.speak()` method on the `JackRussellTerrier` class. But instead of explicitly defining the output string, you should call the `Dog` class’s `.speak()` method inside the child class’s `.speak()` method and make sure to pass to it whatever is passed to the sound argument of `JackRussellTerrier.speak()`.

You can access the parent class from inside a method of a child class by using the `super()` function. Here’s how you could re-write the `JackRussellTerrier.speak()` method using `super()`:

```python
class JackRussellTerrier(Dog):
    def speak(self, sound="Arf"):
        return super().speak(sound)
```

When you call `super().speak(sound)` inside of `JackRussellTerrier`, Python searches the parent class, `Dog`, for a `.speak()` method and calls it with the variable sound. Now, when you call `miles.speak()`, you will see output reflecting the new formatting in the `Dog` class:

```python
miles = JackRussellTerrier("Miles", 4)
print(miles.speak())  # Output: 'Miles barks: Arf'
```

In more complex **class hierarchies**, where one class inherits from a parent class, which inherits from another parent class, and so on, the `super()` function does more than just search the parent class for a method or an attribute. It traverses the entire class hierarchy for a matching method or attribute. If you aren’t careful, `super()` can have surprising results.



--- 

### Conclusion

As we wrap up this introductory text, it's important to recognize that Python's allure stems not only from its simplicity but also from its remarkable adaptability across a diverse array of projects in various domains. Our journey through the intricacies of Python has been geared towards providing you with a robust comprehension of its fundamental concepts and commands. This knowledge equips you to leverage Python's potential across a spectrum of applications.

This guide serves as an open invitation to the expansive realm of programming, accommodating individuals at different proficiency levels. Whether you're taking your initial steps into Python or seeking to refine your skills as an experienced coder, our exploration aims to cater to your needs, instilling confidence and proficiency in Python programming.

Looking ahead, our exploration will venture into specific features, delve into best coding practices, and unveil real-world applications. This comprehensive approach aims to deepen your understanding of Python's functionalities. Stay engaged for an enriching journey that will empower you to navigate the programming landscape with finesse and expertise.

Additionally, beyond the content covered in this folder, we encourage you to explore supplementary materials available in the [extras section](https://github.com/artghieri/A-Introduction-to-Python-3/tree/main/extras). These resources can provide additional insights, challenges, and opportunities for hands-on practice, further enhancing your Python learning experience. 


<!--
Iterables
Iterables são objetos ou coleções que podem ser verificados um por um.

Iterabale -> list, dictionary, tuple, set, string
Iterate -> verificação um por um de cada item de uma coleção
Para dicionários eu preciso informar quais itens serão percorridos: keys, values ou items

for key in dictionary.keys():
for values in dictionary.values();
for key, values in dictonary.items()
Range
Range é um tipo especial de objeto em python que cria uma objeto com um intervalo.

range(start, end, step)

list(range(start, end, step)) 
Cria uma lista com valores inteiros em um intervalo determinado.
Enumerate
Se precisar o indíce de um iterable object, podemos utilizar a função enumerate.

for index, value in enumerate(iterable_object)
for index, value in enumerate([1,2,3,4,5])

 


