## Introduction


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

#

**Initializing a Variable**  
Initialization is the process of providing a variable with its initial value. In Python, initialization frequently happens at the moment of declaration. You can assign a specific value to a variable when declaring it, but it's not mandatory. Alternatively, you can declare a variable first and assign a value to it later in the code.

```python
uninitialized_variable  # This is a declaration without initialization.

initialized_variable = "Hello, world!"  # Here, `initialized_variable` is declared and initialized.
```

In summary, Python's dynamic typing allows variables to be declared and initialized in a single step. The need for explicit data type declarations is eliminated, making the language more adaptable to changing values and reducing redundancy in the code.

#

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

#

### Rules for Valid Variable Names

When working with variables in Python, there are specific rules for creating valid variable names. While variable names can vary in length, they must adhere to the following rules:

1. Variable names can only contain uppercase and lowercase letters $(A–Z, a–z)$, digits $(0–9)$, and underscores ( _ ).
2. Variable names cannot begin with a digit.

For instance, the following examples demonstrate valid variable names: `phrase`, `string1`, `_a1p4a`, and `list_of_names`. On the other hand, `9lives` is not a valid variable name due to starting with a digit.

It's worth noting that Python allows variable names to contain a wide range of valid [Unicode](https://en.wikipedia.org/wiki/Unicode) characters. Unicode, a standard for representing text in various writing systems, permits the use of letters from non-English alphabets, special characters like é and ü, and symbols from languages such as Chinese, Japanese, and Arabic. However, it's advisable to avoid decorated characters if code sharing involves people from different regions, as not every system can display these characters.

While a variable name may be technically valid, choosing a good and meaningful name is essential. Naming variables appropriately enhances code readability and understanding. Keep these guidelines in mind when selecting variable names to improve the clarity and maintainability of your code.

> [!IMPORTANT]
> **Python’s support for Unicode is covered in the [official Python documentation](https://docs.python.org/3/howto/unicode.html#python-s-unicode-support).**

#

**Descriptive Names Are Better Than Short Names**  
Choosing descriptive variable names over short names is crucial, especially in the context of complex programs. When dealing with intricate code structures, opt for longer, more descriptive names, as they contribute significantly to code readability and comprehension.

Consider the example below, where the value $3600$ is assigned to the variable `s`:

```python
s = 3600
```

The name `s` lacks clarity and is ambiguous. Enhance understanding by using a more descriptive name:

```python
seconds = 3600
```

While `seconds` is an improvement, it still doesn't fully convey the purpose of the code. It leaves room for interpretation — is $3600$ the duration of a process or the length of a movie? To eliminate ambiguity, choose a name that explicitly communicates the meaning:

```python
seconds_per_hour = 3600
```

In this case, `seconds_per_hour` provides clear and unambiguous information about the code's intent. Despite the longer length compared to `s` or `seconds`, the improved clarity justifies the choice of a more descriptive name.

While embracing descriptive variable names is beneficial, it's essential to strike a balance. Avoid excessively long names that might hinder code readability. Although the definition of "excessively long" is subjective, a practical guideline is to limit variable names to fewer than three or four words. This ensures that your variable names remain informative without becoming unwieldy.

#

**Python Variable Naming Conventions**  
In various programming languages, the convention is to use **camelCase** for variable names. This naming style involves capitalizing the first letter of every word except the first, creating a camel-hump-like appearance with the juxtaposition of lowercase and uppercase letters, such as `numStudents`.

However, a different convention is more prevalent - **snake_case**. In snake_case, variable names like `num_students` are formed by making every letter lowercase and separating words with underscores. Although Python doesn't strictly enforce the use of snake_case, it is widely embraced and recommended in PEP 8, the official style guide for Python. 

By following [PEP 8 guidelines](https://peps.python.org/pep-0008/), you contribute to a standardized and consistent coding style, making it simpler for others to collaborate, share, and maintain code. This adherence to conventions fosters a cohesive coding environment and facilitates effective communication within the Python programming community.

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

Programmers often revisit their code after several months and find themselves wondering, "What does this do?" Even with well-chosen variable names, it can be challenging to recall the reasoning behind certain code structures over time. To mitigate this issue, comments play a crucial role in documenting the intended functionality of the code.

In Python, comments are lines of text that do not impact the script's execution. They serve as documentation to explain what is supposed to happen in a particular section of the code. This section discusses three ways to include comments in Python code and provides conventions for formatting comments.

### How to Write a Comment

The most common method of writing a comment in Python is to begin a new line with the `#` character. When the code is executed, any lines starting with `#` are disregarded. Comments starting on a new line are referred to as block comments.

```python
# This is a block comment.
phrase = "Hello, world."
print(phrase)  # This is an in-line comment.
```

> ***Note:** The first line, starting with #, does not execute any code, and the print(phrase) line is executed, but everything after # is ignored.*

While it's advisable to keep comments concise, there are scenarios where more extended explanations are necessary. In such cases, you can continue the comment on a new line starting with `#`.

```python
# This is my first script.
# It prints the phrase "Hello, world."
# The comments are longer than the script!
phrase = "Hello, world."
print(phrase)
```

Comments are not only useful for providing context but also serve during code testing. By adding `#` at the beginning of a line, you can effectively comment out code, allowing you to run the program as if that specific line did not exist, without the need to delete any code. This flexibility facilitates testing and debugging processes.

### Conventions and Pet Peeves

According to PEP 8, comments should always be written in complete sentences with a single space between the `#` and the first word of the comment:

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

In this example, the comment is redundant because the code itself clearly states its purpose. The best use of comments is to provide insights into complex or non-intuitive sections of code, explaining the reasoning behind a specific approach.

PEP 8 emphasizes the judicious use of comments, suggesting that they should add value by enhancing code comprehension. In cases where descriptive variable names suffice to convey the purpose of the code, comments describing the functionality may be deemed unnecessary. Following these conventions ensures that comments contribute positively to code clarity and understanding.

## Data Types in Python

Python is a dynamic, high-level programming language that offers a variety of data types to handle different kinds of information. Data types in Python can be classified into main categories, including numeric, sequential, sets, and mappings. Let's explore some of these categories and their corresponding data types:

**Numeric Data Types**

Numeric data types in Python play a crucial role in representing various forms of numerical values within the language. These data types include **integers**, **floating-point numbers**, and **complex numbers**, each belonging to the **int**, **float**, and **complex** classes, respectively.

- **Integers:** Integers, represented by the int class, cover positive or negative whole numbers without fractions or decimals. An intriguing aspect of Python is the absence of a limit on the length of an integer value, allowing for flexibility in handling large numbers seamlessly.

- **Float:** The float class represents real numbers with a floating-point representation. These numbers include a decimal point, and optionally, scientific notation can be employed by appending the character $e$ or $E$ followed by a positive or negative integer. This flexibility allows for precise representation of a wide range of numerical values.

- **Complex Numbers:** Complex numbers, belonging to the complex class, are expressed in the form (real part) + (imaginary part)j. An example of a complex number is $2+3j$, where $2$ is the real part, $3$ is the imaginary part, and $j$ signifies the imaginary unit. Python's support for complex numbers enhances its capability to handle advanced mathematical computations.

> ***Note:** The type() function serves as a valuable tool to determine the data type of a variable.*

**Example:** This code demonstrates how to determine the data type of variables in Python using the `type()` function. It prints the data types of three variables: `a` (**integer**), `b` (**float**), and `c` (**complex**). The output shows the respective data types for each variable.

```python
a = 10
b = 3.14
c = 2 + 5j

print(type(a))  # Output: <class 'int'>
print(type(b))  # Output: <class 'float'>
print(type(c))  # Output: <class 'complex'>
```

#

**Sequential Data Types**

Sequential data types in Python are fundamental for managing ordered collections of elements. These types include `strings`, `lists`, and `tuples`, each tailored to address specific requirements in data organization and manipulation.

- **Strings:** Represented by the `str` `class`, are utilized for handling textual information. They consist of sequences of characters and support various operations such as **concatenation**, **slicing**, and **indexing**. Strings play a vital role in text processing and are an integral part of any Python program dealing with human-readable data.

- **Lists:** Belonging to the `list` `class`, provide a versatile data structure for storing mutable sequences of elements. Unlike strings, lists can be modified, allowing for the **addition**, **removal**, and **modification** of elements. The flexibility of lists makes them invaluable for dynamic data storage and manipulation. Lists are defined by enclosing elements within brackets, such as `list_names = ["Ana", "John", "Helena"]`

- **Tuples:** Represented by the `tuple` `class`, are similar to lists but with a key distinction – they are **immutable**. Once a tuple is created, its elements cannot be changed. This immutability provides data integrity in situations where the sequence of elements should remain constant throughout the program's execution. Tuples are defined by enclosing elements within parenthesis, such as `tuple_numbers = (1,3,4)`

> ***Note:** The len() function is often employed to determine the length of a sequential data type and sets.*

**Example:** The following code demonstrates the utilization of the `len()` function to ascertain the length of different sequential data types in Python. It showcases a string 'text', a list 'numbers', and a tuple 'values'. By using `len()`, the code reveals the number of elements in each sequential data type, aiding in effective data management.

```python
text = "Python is amazing!"
numbers = [1, 2, 3, 4, 5] 
values = (10, 20, 30)  

print(len(text))     # Output: 18
print(len(numbers))  # Output: 5
print(len(values))   # Output: 3
```

#

**Set Data Type**

The set data type in Python is a powerful tool for handling unordered collections of unique elements. Represented by the set class, sets offer efficient methods for performing operations like **intersection**, **union**, and **difference**, making them invaluable for scenarios where distinct and unordered elements are a priority.

- **Sets:** Belonging to the `set` `class`, are characterized by their unordered nature, ensuring that each element is unique within the collection. This uniqueness property is particularly useful when eliminating duplicate values and performing set operations. Sets are defined by enclosing elements within curly braces, such as `set_colors = {"red", "green", "blue"}`.

> ***Note:** The set() constructor can be employed to create an empty set.*

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

#

**Mapping Data Type**

Mapping data types in Python are essential for associating keys with corresponding values. The primary mapping type in Python is the dictionary, represented by the dict class. Dictionaries allow developers to create flexible and efficient data structures for storing and retrieving information based on unique identifiers.

- **Dictionaries:** Dictionaries, belonging to the dict class, consist of `key-value` pairs. Each key within a dictionary must be **unique**, and it is mapped to a specific value. This mapping allows for quick and direct access to values, making dictionaries efficient for scenarios where fast data retrieval is crucial. Dictionaries are defined using curly braces, with key-value pairs separated by colons, such as `dictionary_people = {"name": "John", "age": 25, "city": "São Paulo"}`.

> ***Note:** The keys() and values() functions are often employed to retrieve the keys and values from a dictionary, respectively.*

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

Python, renowned for its versatility and readability, incorporates a diverse set of operators that play a pivotal role in manipulating data and facilitating decision-making in programs. Let's delve into four primary categories of operators in Python: arithmetic operators, augmented assignments, logical operators, and relational operators.

**Arithmetic Operators**  
Arithmetic operators are fundamental for performing basic mathematical operations. They enable programmers to conduct various calculations efficiently. The key arithmetic operators in Python include:

- `+` **Addition.**
- `-` **Subtraction.**
- `*` **Multiplication.**
- `/` **Division.**
- `%` **Modulus, determining the remainder of a division.**
- `**` **Exponentiation.**
- `//` **Floor division, division rounding down to the nearest whole number.**

```python
# Initializing variables
a = 10
b = 3

# Performing addition and storing the result
sum_result = a + b

# Calculating the remainder of division
remainder = a % b
```

**Reduced Expressions**  
Reduced expressions are a distinctive feature in Python that allows for concise assignment of values using arithmetic operators. These expressions combine an operation and assignment in a single statement.

```python
                  # REDUCED EXPRESSION                                        # NORMAL EXPRESSION
                        A += 5                                                      A = A + 5
                        A -= 5                                                      A = A - 5
                        A *= 5                                                      A = A * 5
                        A /= 5                                                      A = A / 5
                        A %= 5                                                      A = A % 5
```

#

**Relational Operators**  
Relational operators are essential for comparing values and expressing relationships between them. They are instrumental in creating decision structures based on the comparison of variables. The primary relational operators in Python include:

- `==`  Equal To
- `!=`  Not Equal To
- `<`   Less Than
- `>`   Greater Than
- `<=`  Less Than or Equal To
- `>=`  Greater Than or Equal To

> *When using any relational operator, there is always a return value that can either be true or false, otherwsie knokn as a Boolean value.*


#

**Logical Operators**  
Logical operators are indispensable for expressing complex conditions in programs. They are pivotal for decision-making based on multiple criteria. The principal logical operators in Python are:

- `and` Logical **AND**
- `or`  Logical **OR**
- `not` Logical **NOT**

```python
# Defining variables
age = 25
salary = 50000

# Checking if both age is greater than 18 and salary is greater than 30000
if age > 18 and salary > 30000:
    print("Eligible for a loan.")
```


#

### Ternary Operator 

The ternary operator, is a concise way to express conditional statements in a single line. It provides a more compact alternative to traditional *if-else* statements when dealing with simple conditions.

```julia
variable = expression1 if condition1 else expression2 if condition2 (...)
```

The ternary operator allows you to express conditional logic in a compact and readable manner, especially when the resulting code would be simple. It is particularly useful for inline conditionals where you need to assign a value based on a condition without the need for multiple lines of code.

In a scenario where you want to determine if a given number is even or odd and print a corresponding message. Using the ternary operator, you can achieve this in a single line:

```python
number = 15
result = "even" if number % 2 == 0 else "odd"
print(f"The number {number} is {result}.")
```

While the ternary operator can enhance code readability for simple conditions, it's important to use it judiciously. For more complex conditions or multiple statements, traditional *if-else* structures might be more appropriate.

#

### Walrus Operator

The walrus operator, denoted by `:=`, is a unique addition to Python syntax introduced in version 3.8. It provides a concise way to assign a value to a variable as part of an expression. The operator is affectionately named the "walrus" due to its visual resemblance to the eyes and tusks of a walrus.

The walrus operator allows you to perform assignments within expressions. This can result in more compact and readable code, especially in situations where you would otherwise need to repeat a calculation. With the walrus operator, you can assign a value to a variable and use that variable in the same expression, avoiding redundant computations.

Consider a scenario where you want to read lines from a file and print those lines along with their line numbers, but only if the line contains the word "python". Without the walrus operator, the code might look like this:

```python
with open("example.txt", "r") as file:
    lines = file.readlines()
    for i, line in enumerate(lines):
        if "python" in line:
            print(f"Line {i + 1}: {line.strip()}")
```

With the walrus operator, you can achieve the same result more succinctly:

```python
with open("example.txt", "r") as file:
    for i, line in enumerate(lines := file.readlines()):
        if "python" in line:
            print(f"Line {i + 1}: {line.strip()}")
```

In this example, the walrus operator is used to both assign the lines from the file to the `lines` variable and iterate over them in a single line.

While the walrus operator can enhance code readability in certain situations, it's essential to use it judiciously. Overuse may lead to code that is harder to understand, so it's important to strike a balance between conciseness and clarity.

## Lambda Expressions

Lambda expressions are a powerful feature in the Python language, allowing the creation of anonymous functions in a single line. Lambda expressions are often used in situations where simple functions are needed temporarily.

```python
lambda arguments: expression
```

Lambda expressions provide a concise way to create inline functions without the need to define a complete function using the `def` statement. They are particularly useful in contexts where small and specific functions are required, such as in **mapping** and **filtering** operations.

For instance, it is possible to create a lambda function to convert temperatures from Celsius to Fahrenheit:

```python
celsius_to_fahrenheit = lambda celsius: (celsius * 9/5) + 32
temperature_celsius = 25
temperature_fahrenheit = celsius_to_fahrenheit(temperature_celsius)

print(f"{temperature_celsius} degrees Celsius is equal to {temperature_fahrenheit} degrees Fahrenheit.")
```

> ***Note:** The lambda expression creates a function that converts temperatures from Celsius to Fahrenheit.*

Another practical example would be using lambda expressions in **filtering** operations:

```python
numbers = [1, 2, 3, 4, 5, 6, 7, 8, 9, 10]
even_numbers = list(filter(lambda x: x % 2 == 0, numbers))

print(f"Even numbers in the list: {even_numbers}")
```

> ***Note:** The lambda expression is used with the `filter` function to create a list containing only the even numbers from the original list.*

While lambda expressions are useful for simple functions, it's important to note that their excessive use can impact code readability. For more complex functions, it's advisable to use the `def` statement to define functions with a more extensive body.


## Casting Data Types

When an expression combines variables of different data types in Python, the interpreter checks whether conversions between these types are possible. If they are not, the runtime process encounters a TypeError, and an error message is displayed. Otherwise, the interpreter performs all necessary type conversions automatically during runtime.

### **Implicit Type Conversion**  

In Python, when expressions involve variables of different data types, the interpreter automatically performs implicit type conversions to ensure compatibility. If these conversions are not possible, a TypeError will be raised, and the programmer needs to handle it explicitly.

Python follows the following rules for implicit type conversions:

- **Conversion to a Common Type:**  
When combining values of different types, Python automatically converts them to a common type. For example, if the expression involves a combination of int and float, the result is automatically promoted to float.

- **Specific Type Promotion:**  
For pairs of operands with different types, the result takes the type that has higher capacity. For instance, if one operand is of type float and the other is of type int, the result will be of type float.

```python
a = 7
print(type(a))  # <class 'int'>

b = 3.0
print(type(b))  # <class 'float'>

c = a + b  
print(type(c))  # <class 'float'>
```

### **Explicit Type Conversion**  
While Python handles implicit type conversions seamlessly, programmers may sometimes want to explicitly cast the result to a specific type. This can be achieved using cast operators, known as type casting. Here's the syntax:

```python
variable = datatype(expression)
```

Keep in mind that explicit type casting should be used judiciously, considering potential data loss or unexpected behavior. Understanding Python's dynamic typing and implicit conversions is crucial for writing robust and flexible code.

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

You've already encountered two methods for achieving this. The first method involves using commas to insert spaces between each part of the string within a `print()` function:

```python
print(name, "has", str(heads), "heads and", str(arms), "arms")
```

Another approach is to concatenate the strings using the `+` operator:

```python
print(name + " has " + str(heads) + " heads and " + str(arms) + " arms")
```

Both techniques produce code that can be hard to read. Trying to keep track of what goes inside or outside of the quotes can be tough. Fortunately, there’s a third way of combining strings: [formatted string literals](https://docs.python.org/3/reference/lexical_analysis.html#formatted-string-literals), more commonly known as **f-strings**.

The easiest way to understand f-strings is to see them in action. Here’s what the above string looks like when written as an f-string:

```python
>>> f"{name} has {heads} heads and {arms} arms"
'Zaphod has 2 heads and 3 arms'
```

There are two important things to notice about the above examples:

1. The string literal starts with the letter $f$ before the opening quotation mark
2. Variable names surrounded by curly braces (${ \\: \\: }$) are replaced with their corresponding values without using `str()`.

You can also insert Python expressions in between the curly braces. The expressions are replaced with their result in the string:

```python
>>> n = 3
>>> m = 4
>>> f"{n} times {m} is {n*m}"
'3 times 4 is 12'
```

> ***Note:** It is a good idea to keep any expressions used in an f-string as simple as possible.*

For an in-depth guide to f-strings and comparisons to other string formatting techniques, check out the Python 3’s f-Strings: [An Improved String Formatting Syntax (Guide)](https://realpython.com/python-f-strings/) on [realpython.com](https://realpython.com).

### File Handling

In addition to interacting with the user, Python provides features for file handling, allowing you to read from and write to files. This is crucial for more complex data manipulations and persistent storage of information. Here's a basic example:

```python
# Writing to a file
with open("example.txt", "w") as file:
    file.write("This is an example of file handling in Python.")

# Reading from a file
with open("example.txt", "r") as file:
    content = file.read()
    print("File content:", content)
```

## Strings and String Methods

In Python, collections of text are referred to as strings. To manipulate strings, specific functions known as string methods are employed. These methods serve various purposes, including transforming a string from lowercase to uppercase, eliminating whitespace from the beginning or end of a string, substituting portions of a string with different text, and more.

### The String Data Type

Strings represent a fundamental data type in Python, denoting values that signify text. The term "data type" pertains to the kind of data a particular value represents. Strings are classified as a fundamental data type due to their inability to be decomposed into smaller values of a different type. However, not all data types share this fundamental characteristic. 

The string data type in Python is succinctly represented as `str`. For instance:

```python
>>> type("Hello, world")
<class 'str'>
```

> ***Note:** The output `<class 'str'>` signifies that the value "Hello, world" is an instance of the str data type, meaning it is a string.*

It's worth noting that `class` is currently synonymous with `data type` for conceptual purposes at the moment.

The `type()` function is applicable to values assigned to variables as well:

```python
>>> phrase = "Hello, world"
>>> type(phrase)
<class 'str'>
```

Moving forward, the exploration of strings will cover three key properties:

1. **Characters:** Strings consist of characters, which can be individual letters or symbols.
2. **Length:** The length of a string refers to the count of characters it contains.
3. **Sequence:** Characters in a string follow a specific sequence, indicating each character's numbered position within the string.

#

### String Literals

Creating strings in Python involves enclosing text within quotation marks, whether single or double. For instance:

```python
string1 = 'Hello, world'
string2 = "1234"
```

> ***Note:** Either single quotes or double quotes can be used to create a string, as long as both quotation marks are the same type.*

Such text-surrounded strings are referred to as string literals, indicating their literal representation in the code. It's crucial to note that not every string qualifies as a string literal; for instance, user-inputted strings differ as they are not explicitly coded within the program.

The quotes used to surround a string are termed **delimiters**, marking the string's start and end. When one type of quotes is used as the delimiter, the other type of quote can be used inside of the string:

```python
string3 = "We're #1!"
string4 = 'I said, "Put it over by the llama."'
```

> ***Note:** Python recognizes the first delimiter and considers all characters until the matching second delimiter is encountered.*

Attempting to use double quotes within a double-quoted string, however, results in a `SyntaxError`:

```python
>>> text = "She said, "What time is it?""
File "<stdin>", line 1
text = "She said, "What time is it?""
^
SyntaxError: invalid syntax
```

This error occurs because Python interprets the string to end after the second double quote, leading to confusion regarding the rest of the line.

It's important to note that Python strings can encompass any valid [Unicode character](https://home.unicode.org/technical-quick-start-guide/). For instance, the string `"We're #1!"` includes the **pound sign** (`#`), `"1234"` contains numbers, and `"×Pýŧħøŋ×"` is a valid Python string showcasing Unicode characters.

> [!IMPORTANT]
> **A recommended practice is consistency in using either single or double quotes as delimiters throughout a project.**

#

### Determine the Length of a String

The length of a string, encompassing spaces, is referred to as the string's length. For instance, the string `"abc"` has a length of 3, while the string `"Don't Panic"` has a length of 11.

 For a practical demonstration, enter the following into IDLE's interactive window:

```python
>>> len("abc")
3
```

> ***Note:** To determine the length of a string in Python, you can utilize the built-in len() function.*

Moreover, the `len()` function can be employed with strings assigned to variables:

```python
>>> letters = "abc"
>>> num_letters = len(letters)
>>> num_letters
3
```

Here, the string `"abc"` is assigned to the variable `letters`. Subsequently, the `len()` function calculates the length of `letters`, and this result is assigned to the variable `num_letters`. Ultimately, the value of `num_letters` is 3, confirming the string's length, and is displayed.

#

### Multiline Strings


The PEP 8 style guide recommends maintaining a line length of no more than 79 characters, including spaces. While this guideline aids in reading files side by side, it can sometimes be perceived as limiting readability.

When faced with the need for string literals exceeding the chosen limit, the solution lies in creating multiline strings. For instance, consider the following paragraph:

```python
paragraph = "This planet has - or rather had - a problem, which was \
this: most of the people living on it were unhappy for pretty much \
of the time. Many solutions were suggested for this problem, but \
most of these were largely concerned with the movements of small \
green pieces of paper, which is odd because on the whole it wasn't \
the small green pieces of paper that were unhappy."
```

By using a backslash at the end of each line, adhering to PEP 8, the total length of each line, including the backslash, must be 79 characters or less.

Alternatively, multiline strings can be created using triple quotes (`"""` or `'''`). This approach preserves whitespace, displaying the string on multiple lines:

```python
paragraph = """This planet has - or rather had - a problem, which was
this: most of the people living on it were unhappy for pretty much
of the time. Many solutions were suggested for this problem, but
most of these were largely concerned with the movements of small
green pieces of paper, which is odd because on the whole it wasn't
the small green pieces of paper that were unhappy."""
```

Triple-quoted strings serve a special purpose in Python, often used for documenting code, providing descriptions at the top of a `.py` file or documenting custom functions. When printed, triple-quoted strings preserve whitespace, allowing for clear and structured output.

## Concatenation, Indexing, and Slicing

Now that you know what a string is and how to declare string literals in your code, let’s explore some of the things you can do with strings.

### String Concatenation

Strings in Python can be combined, or concatenated, using the `+` operator. For example:

```python
>>> string1 = "abra"
>>> string2 = "cadabra"
>>> magic_string = string1 + string2
>>> magic_string
'abracadabra'
```

> ***Note:** Notice that the two strings are joined without any whitespace between them.*

String concatenation proves useful for combining related strings, such as merging a first and last name to create a full name:

```python
>>> first_name = "Arthur"
>>> last_name = "Dent"
>>> full_name = first_name + " " + last_name
>>> full_name
'Arthur Dent'
```

Here, string concatenation occurs twice on the same line. Firstly, `first_name` is concatenated with a space (`" "`) to create the string "Arthur ". Subsequently, this result is further concatenated with `last_name`, producing the full name "Arthur Dent".

### String Indexing

In a string, each character is assigned a numbered position known as an **index**. To access the character at the $Nth$ position, you can place the number $N$ between two square brackets ($[\\: \\:]$) immediately after the string. For example:

```python
>>> flavor = "apple pie"
>>> flavor[1]
'p'
```

> ***Note:** In this instance, flavor[1] retrieves the character at position 1 in "apple pie," which is 'p'.*

It's important to note that in Python, and most other programming languages, counting starts at zero. Therefore, to obtain the character at the beginning of a string, you need to access the character at position 0:

```python
>>> flavor[0]
'a'
```

A common pitfall is forgetting that counting begins with zero. Attempting to access the first character in a string with the index 1 leads to an off-by-one error. Off-by-one errors are a frequent source of frustration for programmers, both novice and experienced alike.

The following figure shows the index for each character of the string "apple pie":

<table align = "center">
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

Attempting to access an index beyond the end of a string in Python results in an `IndexError`. For example:

```python
>>> flavor[9]
Traceback (most recent call last):
  File "<pyshell#4>", line 1, in <module>
    flavor[9]
IndexError: string index out of range
```

> ***Note:** The largest valid index in a string is always one less than the string's length.*

Strings also support negative indices, where the last character in a string has index -1. For instance:

```python
>>> flavor[-1]
'e'
```

In this case, `flavor[-1]` retrieves the last character in "apple pie," which is the letter 'e'. The second-to-last character 'i' has index -2, and so on. Negative indices provide a convenient way to access characters from the end of the string.

The following figure shows the negative index for each character in the string "apple pie":

<table align = "center">
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

Just like positive indices, attempting to access a negative index less than the index of the first character in the string raises an `IndexError` in Python:

```python
>>> flavor[-10]
Traceback (most recent call last):
  File "<pyshell#5>", line 1, in <module>
    flavor[-10]
IndexError: string index out of range
```

While negative indices might not seem immediately useful, there are situations where they offer a more convenient solution than positive indices. For instance, consider a scenario where a string input by a user is assigned to the variable `user_input`. If you need to retrieve the last character of the string, determining the correct positive index can be cumbersome.

One approach to get the last character is to calculate the final index using `len()`:

```python
final_index = len(user_input) - 1
last_character = user_input[final_index]
```

However, utilizing a negative index simplifies the process and eliminates the need for an intermediate step:

```python
last_character = user_input[-1]
```

> ***Note:** This method is more concise and avoids the additional step of calculating the final index.*

### String Slicing

If you need to obtain the string containing just the first three letters of the string "apple pie," individually accessing each character by index and concatenating them can be done, albeit in a cumbersome manner:

```python
>>> first_three_letters = flavor[0] + flavor[1] + flavor[2]
>>> first_three_letters
'app'
```

However, when dealing with a larger substring, this method becomes impractical. Fortunately, Python provides a more efficient way to achieve this with less code. 

You can extract a portion of a string, known as a **substring**, by inserting a colon between two index numbers inside square brackets:

```python
>>> flavor = "apple pie"
>>> flavor[0:3]
'app'
```

> ***Note:** The [0:3] part of flavor[0:3] is called a slice, which in this case, returns a slice of "apple pie."*

In this example, `flavor[0:3]` returns the first three characters of the string assigned to `flavor`. It starts with the character at index 0 and goes up to, but does not include, the character at index 3. 

String slices may be initially confusing because the substring includes the character at the index of the first number but excludes the character at the index of the second number. To understand slicing, envision a string as a sequence of square slots, each numbered from zero up to the length of the string, and each filled with a character.

Here’s what this looks like for the string "apple pie":

<table align = "center">
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

The slice `[x:y]` in Python returns the substring between the boundaries x and y. For example, for the string "apple pie," the slice `[0:3]` returns the string "app," and the slice `[3:9]` returns the string "le pie."

If you omit the first index in a slice, Python assumes you want to start at index 0:

```python
>>> flavor[:5]
'apple'
```

The slice `[:5]` is equivalent to the slice `[0:5]`, so `flavor[:5]` returns the first five characters in the string "apple pie."

Similarly, if you omit the second index in the slice, Python assumes you want to return the substring that begins with the character whose index is the first number in the slice and ends with the last character in the string:

```python
>>> flavor[5:]
' pie'
```

> ***Note:** The slice [5:] is equivalent to the slice [5:9].*

If you omit both the first and second numbers in a slice, you get a string that starts with the character with index 0 and ends with the last character. In other words, omitting both numbers in a slice returns the entire string:

```python
>>> flavor[:]
'apple pie'
```

Unlike string indexing, Python won’t raise an `IndexError` when you try to slice between boundaries before or after the beginning and ending boundaries of a string:

```python
>>> flavor[:14]
'apple pie'
>>> flavor[13:15]
''
```

In the first example, the slice gets characters from the beginning of the string up to but not including the fourteenth character. Although the string assigned to `flavor` has a length of nine, any non-existent indices are ignored, and the entire string "apple pie" is returned. In the second example, attempting to get a slice where the entire range is out of bounds (`flavor[13:15]`) returns the empty string "".

You can use negative numbers in slices. The rules for slices with negative numbers are exactly the same as slices with positive numbers. It helps to visualize the string as slots with the boundaries labeled by negative numbers:

<table align = "center">
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

Just like before, the slice `[x:y]` returns the substring between the boundaries x and y. For instance, the slice `[-9:-6]` returns the first three letters of the string "apple pie":

```python
>>> flavor[-9:-6]
'app'
```

It's important to note, however, that the right-most boundary in a slice does not have a negative index. While the logical choice might seem to be the number 0, it doesn't work:

```python
>>> flavor[-9:0]
''
```

In this example, `flavor[-9:0]` returns an empty string because the slicing operation assumes that the range includes the character at the index of the left boundary but excludes the character at the index of the right boundary. The right boundary, in this case, is specified as 0, and since 0 is not included, an empty string is returned.

Slicing with three indices, follows a similar principle as slicing with two indices. The third index introduces a step value, indicating the interval between characters to be included in the slice.

<table align = "center">
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

For instance, if we want to slice the word `"pepe"` from the word "apple pie", the resulting slice would be:

```python
>>> flavor[2:9:2]
'pepe'
```

> ***Note:** This slicing starts at index 2, includes the character at that position, and moves forward with a step of 2.*

### Strings Are Immutable

To conclude this section, it's essential to highlight a crucial property of string objects: **immutability**. Strings in Python are immutable, which means that you can’t change them once you’ve created them. For instance, attempting to change a specific character of a string results in an error:

```python
>>> word = "goal"
>>> word[0] = "f"
Traceback (most recent call last):
  File "<pyshell#16>", line 1, in <module>
    word[0] = "f"
TypeError: 'str' object does not support item assignment
```

> ***Note:** The term str is Python’s internal name for the string data type.*

Python raises a `TypeError` and indicates that string objects do not support item assignment.

To modify a string, you need to create an entirely new string. For example, to change the string `"goal"` to `"foal"`, you can use a string slice to concatenate the letter `"f"` with everything but the first letter of the word `"goal"`:

```python
>>> word = "goal"
>>> word = "f" + word[1:]
>>> word
'foal'
```


## Manipulate Strings With Methods

Strings come bundled with special functions called string methods that can be used to work with and manipulate strings. There are numerous string methods available, but we’ll focus on some of the most commonly used ones.

### Converting String Case

In Python, strings are objects, and they come with a variety of built-in methods that you can use to manipulate them. The `.lower()` and `.upper()` methods are two examples of such string methods.

- The `.lower()` method converts all characters in a string to **lowercase**.
- The `.upper()` method converts all characters in a string to **uppercase**.

> ***Note:** The dot (.) signifies to Python that what follows is the name of a method - in this case, the lower() method.*

```python
name = "Jean-luc Picard"
lower_case_name = name.lower()
upper_case_name = name.upper()

print(lower_case_name)  # 'jean-luc picard'
print(upper_case_name)  # 'JEAN-LUC PICARD'
print(name)             # 'Jean-luc Picard'
```


String methods don’t just work on string literals. You can also use the `.lower()` method on a string assigned to a variable:

```python
>>> name = "Jean-luc Picard"
>>> name.lower()
'jean-luc picard'
```


When referring to string methods, we'll use a dot at the beginning of their names. For example, the `.lower()` method is written with a dot instead of just `lower()`. This convention helps distinguish string methods from built-in functions like `print()` and `type()`.

On the other hand, `.upper()` and `.lower()` must be used in conjunction with a string. They do not exist independently.

### Removing Whitespace From a String

Whitespace is any character that is printed as blank space. This includes things like spaces and line feeds, which are special characters that move output to a new line.

Removing whitespace from the beginning or end of a string is essential, particularly when handling strings from user input where inadvertent introduction of extra whitespace characters may occur.

Three string methods are available for removing whitespace:

1. `.rstrip()` : Removes whitespace from the **right side** of a string.
2. `.lstrip()` : Removes whitespace from the **left side** of a string.
3. `.strip()`  : Removes whitespace from both the **left and right sides** of a string.

For example, using `.rstrip()` to remove trailing spaces from the right side of a string:

```python
>>> name = "Jean-luc Picard     "
>>> name.rstrip()
'Jean-luc Picard'
```

In this instance, the string "Jean-luc Picard " has five trailing spaces. Python does not automatically remove these trailing spaces when the string is assigned to a variable. The `.rstrip()` method rectifies this by removing trailing spaces from the right side of the string, resulting in a **new string**, "Jean-luc Picard," without the spaces.

Similarly, `.lstrip()` functions like `.rstrip()`, but it removes whitespace from the left side of the string:

```python
>>> name = "     Jean-luc Picard"
>>> name.lstrip()
'Jean-luc Picard'
```

To remove whitespace from both the left and right sides simultaneously, use the `.strip()` method:

```python
>>> name = "     Jean-luc Picard     "
>>> name.strip()
'Jean-luc Picard'
```

It is important to note that none of the `.rstrip()`, `.lstrip()`, or `.strip()` methods remove whitespace from the middle of the string. In each example, the space between "Jean-luc" and "Picard" is preserved.

### Determine if a String Starts or Ends With a Particular String

When working with text, it's often necessary to ascertain whether a given string starts or ends with specific characters. Two string methods, `.startswith()` and `.endswith()`, are employed for this purpose.

Consider the example with the string "Enterprise." Using `.startswith()` to check if the string starts with the letters 'e' and 'n':

```python
>>> starship = "Enterprise"
>>> starship.startswith("en")
False
```

> ***Note:** The method returns False because "Enterprise" begins with a capital E, and .startswith() is case-sensitive.*

To make it return `True`, you need to provide the method with the correct case:

```python
>>> starship.startswith("En")
True
```

Similarly, the `.endswith()` method is utilized to determine if a string ends with specific characters:

```python
>>> starship.endswith("rise")
True
```

> ***Note:** Like .startswith(), .endswith() is also case-sensitive.*

> [!IMPORTANT]
> **The True and False values are not strings. They are a special kind of data type called a Boolean value.**

## String Methods and Immutability

As mentioned in the previous section, strings in Python are immutable, meaning they cannot be altered once created. 

Many string methods, such as `.upper()` and `.lower()`, do not modify the original string but instead return copies with the desired modifications. It's important to be cautious, as overlooking this fact can lead to subtle bugs in your program. For instance:

```python
>>> name = "Picard"
>>> name.upper()
'PICARD'
>>> name
'Picard'
```

In this example, calling `name.upper()` does not change the original string stored in the `name` variable. To retain the modified result, you must assign it to a variable:

```python
>>> name = "Picard"
>>> name = name.upper()
>>> name
'PICARD'
```

Now, `name.upper()` returns a new string, "PICARD," which is then assigned to the `name` variable, effectively replacing the original string "Picard."

## Working With Strings and Numbers

When obtaining user input using the `input()` function, the result is always a string. Similarly, in various scenarios, input to a program is provided as a string, even when it represents numerical values. This section focuses on handling strings containing numbers, exploring how arithmetic operations behave on strings and the potential for unexpected outcomes. 

### Strings and Arithmetic Operators


Strings in Python can hold various types of characters, including numbers. However, it's crucial not to confuse numerals in a string with actual numbers. Consider the following code:
```python
>>> num = "2"
>>> num + num
'22'
```

> ***Note:** The + operator concatenates two strings together, so the result of 2 + 2 is 22, not 4.*

Strings can be "multiplied" by a number if that number is an integer. For instance:

```python
>>> num = "12"
>>> num * 3
'121212'
```

The expression `num * 3` concatenates the string " $12$ " with itself three times, resulting in the string " $121212$ ". This operation is akin to arithmetic with numbers, where " $12$ " $* \\: 3$ is equivalent to " $12$ " $+$ " $12$ " $+$" $12$ ".

However, attempting to use the $*$ operator between two strings raises a `TypeError`:

```python
>>> "12" * "3"
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
TypeError: can't multiply sequence by non-int of type 'str'
```

Python raises a `TypeError`, indicating that you can't multiply a sequence by a non-integer. When the $*$ operator is used with a string on either the left or the right side, it always expects an integer on the other side.

What happens when you try to add a string and a number?

```python
>>> "3" + 3
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
TypeError: can only concatenate str (not "int") to str
```

Python throws a `TypeError` because the `+` operator expects both things on either side of it to be of the same type. If any one of the objects on either side of `+` is a string, Python tries to perform string concatenation. Addition will only be performed if both objects are numbers. So, to add `"3" + 3` and get `6`, you must first convert the string `"3"` to a number.

### Converting Strings to Numbers

The `TypeError` errors mentioned in the previous section highlight a common challenge when dealing with user input: type mismatches when attempting operations that require a number and not a string.

Consider the following example:

```python
num = input("Enter a number to be doubled: ")
doubled_num = num * 2
print(doubled_num)
```

If you input a number, say $2$, you might expect the output to be $4$. However, the result is $22$. Since `input()` always returns a string, when you input $2$, `num` is assigned the string " $2$ ", not the integer $2$. 

Consequently, the expression `num * 2` concatenates the string " $2$ " with itself, resulting in " $22$ ".

To perform arithmetic on numbers within a string, conversion from string type to a number type is necessary. Two functions, `int()` and `float()`, can be used for this purpose. 
- The `int()` function converts objects into whole numbers.
- The `float()` function converts objects into numbers with decimal points.

```python
>>> num = int(input("Enter a number to be doubled:  "))
>>> doubled_num = num * 2
>>> print(doubled_num)
4
```

> ***Note:** float() adds a decimal point to the number, providing at least one decimal place of precision.*

However, attempting to convert a string resembling a floating-point number into an integer raises a `ValueError`:

```python
>>> int("12.0")
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
ValueError: invalid literal for int() with base 10: '12.0'
```

> ***Note:** This happens because converting 12.0 to 12 would result in the loss of precision.*

### Converting Numbers to Strings

Sometimes you need to convert a number to a string. You might do this, for example, if you need to build a string from some pre-existing variables that are assigned to numeric values.

As demonstrated earlier, attempting to concatenate a number with a string directly results in a `TypeError`:

```python
>>> num_pancakes = 10
>>> "I am going to eat " + num_pancakes + " pancakes."
Traceback (most recent call last):
File "<stdin>", line 1, in <module>
TypeError: can only concatenate str (not "int") to str
```

Since `num_pancakes` is a number, Python cannot concatenate it with the string "I am going to eat." To create the desired string, it's essential to convert `num_pancakes` to a string using `str()`:

```python
>>> num_pancakes = 10
>>> "I am going to eat " + str(num_pancakes) + " pancakes."
'I am going to eat 10 pancakes.'
```

Alternatively, you can directly call `str()` on a number literal or handling arithmetic expressions:

```python
>>> "I am going to eat " + str(10) + " pancakes."
'I am going to eat 10 pancakes.'

>>> total_pancakes = 10
>>> pancakes_eaten = 5
>>> "Only " + str(total_pancakes - pancakes_eaten) + " pancakes left."
'Only 5 pancakes left.'
```

## Find a String in a String

One of the most useful string methods is `.find()`. As its name implies, you can use this method to find the location of one string in another string - commonly referred to as a substring.

To use `.find()`, append it to the end of a variable or a string literal and pass the string you want to find between the parentheses:

```python
>>> phrase = "the surprise is in here somewhere"
>>> phrase.find("surprise")
4
```

The value that `.find()` returns is the index of the first occurrence of the string you pass to it. In this case, "surprise" starts at the fifth character of the string "the surprise is in here somewhere," which has an index of 4 since counting starts at 0.

If `.find()` doesn’t find the desired substring, it will return -1 instead:

```python
>>> phrase = "the surprise is in here somewhere"
>>> phrase.find("eyjafjallajökull")
-1
```

You can call string methods on a string literal directly, so in this case, you don’t need to create a new string:

```python
>>> "the surprise is in here somewhere".find("surprise")
4
```

Keep in mind that this matching is done exactly, character by character, and is case-sensitive. For example, if you try to find "SURPRISE", the `.find()` method returns -1:

```python
>>> "the surprise is in here somewhere".find("SURPRISE")
-1
```

If a substring appears more than once in a string, `.find()` only returns the index of the first appearance, starting from the beginning of the string:

```python
>>> "I put a string in your string".find("string")
8
```

There are two instances of "string" in "I put a string in your string." The first starts at index 8, and the second at index 23. `.find()` returns 8, which is the index of the first instance of "string."

The `.find()` method only accepts a string as its input. If you want to find an integer in a string, you need to pass the integer to `.find()` as a string. If you do pass something other than a string to `.find()`, Python raises a `TypeError`:

```python
>>> "My number is 555-555-5555".find(5)
Traceback (most recent call last):
File "<stdin>", line 1, in <module>
TypeError: must be str, not int
```

```python
>>> "My number is 555-555-5555".find("5")
13
```

Sometimes you need to find all occurrences of a particular substring and replace them with a different string. Since `.find()` only returns the index of the first occurrence of a substring, you can’t easily use it to perform this operation. Fortunately, string objects have a `.replace()` method that replaces each instance of a substring with another string.

Just like `.find()`, you append `.replace()` to the end of a variable or string literal. In this case, though, you need to put two strings inside the parentheses in `.replace()` and separate them with a comma. The first string is the substring to find, and the second string is the string to replace each occurrence of the substring with.

For example, the following code shows how to replace each occurrence of "the truth" in the string "I'm telling you the truth; nothing but the truth" with the string "lies":

```python
>>> my_story = "I'm telling you the truth; nothing but the truth!"
>>> my_story.replace("the truth", "lies")
"I'm telling you lies; nothing but lies!"
```

Since strings are immutable objects, `.replace()` doesn’t alter `my_story`. To change the value of `my_story`, you need to reassign to it the new value returned by `.replace()`:

```python
>>> my_story = my_story.replace("the truth", "lies")
>>> my_story
"I'm telling you lies; nothing but lies!"
```

`.replace()` can only replace one substring at a time, so if you want to replace multiple substrings in a string you need to use `.replace()` multiple times:

```python
>>> text = "some of the stuff"
>>> new_text = text.replace("some of", "all")
>>> new_text = new_text.replace("stuff", "things")
>>> new_text
'all the things'
```











--- 

<!-- 

Função Matemáticas
Em python há função matemáticas nativas para o auxílio de seu programa como a função abs() e a função round()

print(round(3.4)) 

print(abs(-20)) ##Módulo

print(len(var))

max()

min()
Mas além disso, podemos importar o módulo math e utilizar inúmeras funções pertencentes a esse módulo.

import math

math.sqrt(4)

math.pow(2,2)

math.cos(30)

math.ceil(3.4)

#

Expressions x Statements
Statements são declarações de variáveis feitas durante o código.

valor = 1000
Expression são operações matemáticas realizadas com as variáveis ou uma linha inteira de código que realiza uma ação.

idade = (valor / 250) * 8

#

Função Nativas
hello = "hello world"

print(len(hello))

print(hello.upper())

print(hello.lower())

print(hello.capitalize())
  
print(nome.isspace())

print(nome.replace("hello", "ola"))

nome = nome.replace("hello", "ola")

print(nome) 
Acesse w3school e docs python https://docs.python.org/3/library/functions.html

**Lembre `string` são imutáveis**

#

List Unpacking
a,b,c *other, d = [1,2,3,4,5,6,7,8,9]

#

Truthy e Falsy
Quando precisarmos apenas chegar se uma variável não está vazia ou com um valor padrão designada para vazio, como é o casos dos tipos de dados numéricos (0, 0.0), podemos simplesmente verificar se o valor é True ou False.

idade = 22

if idade:
	print(f"Sua idade e: {îdade}")
else:
	print("Digite sua idade")
Casos Falsy
None
False

Numbers that are numerically equal to zero, including:
	0
	0.0
	0j
	decimal.Decimal(0)
	fraction.Fraction(0, 1)
	
Empty sequences and collections, including:
	[] - an empty list
	{} - an empty dict
	() - an empty tuple
	set() - an empty set
	'' - an empty str
	b'' - an empty bytes
	bytearray(b'') - an empty bytearray
	memoryview(b'') - an empty memoryview
	an empty range, like range(0)
	
objects for which
	obj.__bool__() returns False
	obj.__len__() returns 0, given that obj.__bool__ is undefined

 #

Short Circuiting
Em condicionais, nos casos que utilizamos os operadores lógicos and e or poderemos ter casos específicos de execucação de acordo com a seguinte condição.

if True and False:
Quando utilizamos and é checado a condição dos 2 parâmetros para o direcionamento do programa.
if True or False:
Quando utilizamos or se apenas uma das condicionais for válido (True) não é chegado a outra condicional, causando um short circuiting.
Dessa maneira conseguimos economizar tempo de processamento.



#

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

#

Break / Continue / Pass
Break: realiza uma quebra na estrutura de execução de código atual
Continue: realizar uma volta ao topo da condição de loop
Pass: ignora um bloco de execução
while True:
	resp = input("> ")
	if resp in "bye":
		break
while i < 10:
	i += 1
	continue # Nesse exemplo nunca será mostrado o print
	print(i)
for item in lista:
	pass

 #

 Positional Arguments
def pessoa(nome, idade):
	print(f"{nome} {idade}")

Positional Arguments são argumentos que são passados para os parâmetros de uma função em uma determinada ordem, portanto, isso pode afetar a saída de sua função

pessoa("nicholas", 22) 
nicholas 22
		  
pessoa(22, "nicholas")
22 nicholas
Keyword Arguments
def pessoa(nome, idade):
	print(f"{nome} {idade}")

Agora Keyword Arguments são argumentos que direcionamento diretamente os seus valores para a função

pessoa(idade="22", nome="nicholas")
nicholas 22
Default Parameters
def pessoa(nome = "Jojo", idade = 22):  
	print(f"{nome} {idade}")

pessoa()
Jojo 22

pessoa("nicholas", 30)
nicholas 30

#

Argumentos
Para passar um conjunto de elementos em uma função usaremos * ou **
def function(*arg):
	return sum(args)

function(1,2,3,4,5)


def function(arg):  
	total = 0
	for item in args:
	    total += item
	return total

function([1,2,3,4,5])
def function(*arg, **kwargs):
	total = 0
	for item in kwargs.values():
		total += items
	return sum(args) + total

function(1,2,3,4,5, num1=2, num2=1)
Ordem adotada: param, *args, default, **kwargs
**Usar \*args para listas, tuplas, sets, dicionários e conjunto de dados.**

#

Docstrings
Docstrings podem ser utilizadas para comentar uma função.

def teste(a):
	'''
	Info: This function prints a parameter
	'''
	print(a)
Para acessar o docstrings utilizaremos essa linha de comando:
print(test.__doc__)



print(imposto(preco))

##map pega uma lista de valores e aplica uma funcao em cada valor
precos = [1000, 500, 100, 10]
imposto2 = list(map(imposto, precos))
#imposto2 = list(map(lambda preco: preco * 0.3, precos))
print(imposto2)
