## File Input and Output

Up until now, your programs have primarily sourced input from either the program code itself or directly from user interaction. Program output has typically been confined to displaying text within IDLE's interactive window. However, these input and output methods prove inadequate in various commonplace scenarios:

- When the input values are indeterminate during program development.
- When the program necessitates more data than a user can reasonably input manually.
- When the output must be disseminated to others after the program execution.

This is where the utilization of files becomes crucial.

### Files and the File System

Chances are, you've been dealing with computer files for quite some time. However, there are aspects of files that programmers should grasp, which may not be as apparent to the general user. In this section, we'll delve into the essential concepts for initiating work with files in Python.

Let's begin by examining what constitutes a file and how computers engage with them.

### The Anatomy of a File

Files come in various types - $text$, $image$, $audio$, $PDF$, and more. Nonetheless, at their core, a file is essentially a sequence of **bytes**, referred to as the **contents** of the file.

Each byte in a file can be conceptualized as an integer ranging from $0$ to $255$, inclusive of both endpoints. These bytes represent the values stored on a physical storage device when a file is saved.

When you access a file on a computer, the contents are read from the disk in the correct sequence of bytes. Crucially, there's nothing intrinsic to the file dictating how its contents should be interpreted.

As a programmer, your responsibility is to interpret the contents appropriately when you open a file. While this might sound intricate, Python simplifies much of this process for you.

For instance, when opening a text file, Python can effortlessly convert the numerical bytes into text characters without requiring you to understand the specifics of the conversion process. The standard library provides tools for working with various file types, including images and audio files.

Accessing a file from a storage device involves several steps, such as determining the device, understanding how to interact with it, and pinpointing the exact location of the file on the device.

This complex task is overseen by a file system. Python interacts with the file system on your computer, enabling the reading, writing, and manipulation of files.

**The File System**  
The file system on a computer serves two primary functions:

1. **It furnishes an abstract representation of the files stored on your computer and connected devices.**
2. **It interfaces with devices to manage the storage and retrieval of file data.**

Python interacts with your computer's file system, and your capabilities in Python are constrained by what your file system permits.

> ***Note:** Different operating systems use distinct file systems, a crucial factor to keep in mind when developing code for diverse platforms.*

The file system manages communication between the computer and the physical storage device. As a programmer, your focus should be on understanding how the file system represents files, leaving the intricate communication aspects to the file system itself.

**The File System Hierarchy**  
File systems employ a hierarchical structure of directories, commonly known as folders. At the apex of this hierarchy sits the root directory, housing all other files and directories within the file system.

Each file within a directory possesses a unique file name distinct from any other file in that same directory. Moreover, directories themselves can harbor additional directories, referred to as subdirectories or subfolders.

Illustrating this hierarchical organization is the following directory tree, portraying the relationships between files and directories within a sample file system:

```
root/
|-- app/
|   |-- program.py
|   |-- data.txt
|
|-- photos/
|   |-- cats/
|   |   |-- cat1.jpg
|   |   |-- cat2.jpg
|
|   |-- dogs/
|       |-- dog1.jpg
|       |-- dog2.jpg
```

In this specific file system, the root folder, denoted as `root/`, is the overarching directory. It contains two subdirectories: `app/` and `photos/`. The `app/` subdirectory accommodates two files, namely `program.py` and `data.txt`. Meanwhile, the `photos/` directory includes two additional subdirectories, `cats/` and `dogs/`, each containing two image files.

**File Paths**  
To pinpoint a file in a file system, you construct a sequence of directories starting from the root directory and culminating with the file's name. This sequence, encapsulated in a string, is termed a file path.

For instance, in the previously outlined file system, the file path for the $jack\\_russel.gif$ file is $root/photos/dogs/jack\\_russel.gif$;

Writing file paths varies based on your operating system. Below are examples of file paths for **Windows**, **macOS**, and **Linux**:

1. **Windows:** `C:\Users\David\Documents\hello.txt`
2. **macOS:** `/Users/David/Documents/hello.txt`
3. **Ubuntu Linux:** `/home/David/Documents/hello.txt`

All these file paths direct to a text file named $hello.txt$ within the $Documents$ subfolder of the user directory for a user named $David$. Evidently, there are significant differences in file paths across operating systems.

On macOS and Ubuntu Linux, a virtual file system organizes all files and directories under a single root directory, commonly denoted by a forward slash symbol (`/`). External storage devices typically reside in a subdirectory named $media/$ .

In Windows, there isn't a universal root directory. Each device possesses a distinct file system with a unique root directory, identified by a drive letter and a colon (`:`) followed by a backslash (`\`). Typically, the hard drive containing the operating system is designated as $C$,  making the root directory for that drive $C:$ . 

Another notable distinction is that directories in a Windows file path are separated by backslashes, while macOS and Ubuntu file paths use forward slashes (`/`).

When programming for multiple operating systems, it's imperative to handle file path differences appropriately. For versions of Python greater than $3.4$, the standard library incorporates a module called `pathlib` to ease the complexity of managing file paths across various operating systems. Continue reading to discover how to leverage `pathlib` for working with file paths in Python.

### Working With File Paths in Python

To handle file paths effectively in Python, the `pathlib` module from the standard library is invaluable. Begin by importing the module:

```python
import pathlib
```

The `pathlib` module encompasses a class called `Path`, which serves to represent a file path.

**Creating Path Objects**  
Path objects can be created in several ways:

1. From a string
2. Utilizing `Path.home()` and `Path.cwd()` class methods
3. Through the `/` operator

The most straightforward method involves creating a Path object from a string:

```python
path = pathlib.Path("/Users/David/Documents/hello.txt")
```

There’s problem, though, with Windows paths. On Windows, directories are separated by back slashes. Python interprets back slashes as the start of an escape sequence that represent a special character in the string, such as the newline character (`\n`).

Attempting to create a Path object with the Windows file path "C:\Users\David\Desktop\hello.txt" raises an exception:

```python
>>> path = pathlib.Path("C:\Users\David\Desktop\hello.txt")
SyntaxError: (unicode error) 'unicodeescape' codec can't decode bytes
in position 2-3: truncated \UXXXXXXXX escape
```

There are two ways to get around this problem:

1. Use forward slashes (`/`) in Windows file paths:

    ```python
    path = pathlib.Path("C:/Users/David/Desktop/hello.txt")
    ```
    Python can interpret this just fine and will translate the path automatically when interfacing with the Windows operating system.

2. Transform the string into a **raw** string by prefixing it with an `r`:

    ```python
    path = pathlib.Path(r"C:\Users\David\Desktop\hello.txt")
    ```
    This tells Python to ignore any escape sequences and just read the string as-is.

**Path.home() and Path.cwd()**  
In addition to creating `Path` objects from strings, the `Path` class provides class methods that yield `Path` objects representing specific directories. Two particularly useful methods are `Path.home()` and `Path.cwd()`.

Every operating system designates a special directory for storing data related to the currently logged-in user, commonly known as the user's **home directory**. The location of this directory varies based on the operating system:

- **Windows:** `C:\Users\<username>`
- **macOS:** `/Users/<username>`
- **Ubuntu Linux:** `/home/<username>`

The `Path.home()` class method generates a `Path` object pointing to the home directory, regardless of the underlying operating system. Here's an example:

```python
home = pathlib.Path.home()
```

Upon inspection, the `home` variable might display something like the following:

```python
home
# WindowsPath("C:\\Users\\David")
```

The Path object created is a subclass of Path called $WindowsPath$. On other operating systems, the $Path$ object returned is a subclass called $PosixPath$.

For example, on **macOS**, inspecting home will display something like the following:

```python
home
PosixPath("/Users/David")
```

Throughout this section, $WindowsPath$ objects will be illustrated in the example output. However, it's important to note that both $WindowsPath$ and $PosixPath$ objects share the same methods and attributes. From a programming perspective, there is no distinction between the two types of `Path` objects.

The `Path.cwd()` class method, on the other hand, returns a `Path` object representing the **current working directory** (**CWD**). The current working directory is a dynamic reference to a directory, contingent on where a process on the computer is presently working. For instance:

```python
pathlib.Path.cwd()
# current_directory = pathlib.Path.cwd()
```

While `Path.cwd()` is valuable, exercise caution when using it, as the current working directory might change during program execution. Ensure that you are aware of the directory to which it refers.

By leveraging these `Path` class methods, you can effortlessly navigate and interact with special directories in a platform-independent manner.

**Using the `/` Operator in Python Path Handling**  
The `/` operator proves instrumental when extending an existing `Path` object with subdirectories or file names. If you have a `Path` object, it enables seamless construction of more complex paths. For instance:

```python
result_path = home / "Desktop" / "hello.txt"
```

This operation creates a `Path` object representing a file named "hello.txt" within the $Documents$ subdirectory of the current user's home directory. Upon inspection, the result might resemble:

```python
WindowsPath('C:/Users/David/Desktop/hello.txt')
```

A crucial rule is that the `/` operator always requires a `Path` object on the left-hand side. On the right-hand side, you can have either a string representing a single file or directory, a string representing a path, or another `Path` object.

This elegant approach simplifies the creation of complex file paths, enhancing readability and maintainability in your Python code. Whether you're navigating through directories or building file paths dynamically, the `/` operator in conjunction with the `Path` class streamlines your path-handling operations.

### Absolute vs. Relative Paths in Python

A file path that commences from the root directory in a file system is termed an absolute path, representing the complete path from the root. Conversely, a file path that is not absolute is known as a relative path, implying that it is defined in relation to another location.

For instance, consider the following examples of `Path` objects representing relative paths:

```python
# Relative Windows path
path_windows = pathlib.Path(r"Photos\image.jpg")

# Relative macOS or Linux path
path_unix = pathlib.Path("Photos/image.jpg")
```

Note that these paths don't commence with `C:\` on Windows or `/` on macOS and Linux, signifying their relativity.

You can determine whether a file path is absolute or not by employing the `.is_absolute()` method:

```python
path_windows.is_absolute()  # Returns False
```

Relative paths find relevance when considered within the context of another directory, often describing the path to a file relative to the current working directory or the user's home directory.

To convert a relative path to an absolute path, use the forward slash (`/`) operator:

```python
home = pathlib.Path.home()  # WindowsPath('C:/Users/David')
absolute_path = home / pathlib.Path(r"Photos\image.png")
```

In this operation, the left side of the forward slash should be an absolute path to the directory containing the relative path, and the relative path should be on the right side.

Once a `Path` object is created, you can explore its various components and inspect the file path it refers to. This distinction between absolute and relative paths is essential for precise file path manipulation and navigation in Python.

### Accessing File Path Components in Python

All file paths contain a list of directories. The $.parents$ attribute of a $Path$ object returns an iterable containing the list of directories in the file path:

```python
>>> path = pathlib.Path.home() / "hello.txt"
>>> path
WindowsPath("C:\\Users\\David")
>>> list(path.parents)
[WindowsPath("C:\\Users\\David"), WindowsPath("C:\\Users"),
WindowsPath("C:\\")]
```

Note that the list of directories is returned in reverse order compared to their appearance in the file path. Iterating over parent directories in a `for` loop reveals this order:

```python
for directory in path.parents:
    print(directory)
```

Notice that the list of the directories are returned in reverse order from how they appear in the file path. That is, the last directory in the path is the first directory in the list of parent directories.

You can iterate over the parent directories in a $for$ loop:
```python
>>> for directory in path.parents:
... print(directory)
...
C:\Users\David
C:\Users
C:\
```

The $.parent$ attribute returns the name of the first parent directory in the file path as a string:

```python
>>> path.parent
'C:\Users\David'
```

If the file path is absolute, you can access the root directory of the file path with the $.anchor$ attribute:

```python
>>> path.anchor
'C:\'
```

Note that $.anchor$ returns a string, and not another Path object. For relative paths, .anchor return an empty string:

```python
>>> path = pathlib.Path("hello.txt")
>>> path.anchor
''
```

The $.name$ attribute returns the name of the file or directory that the path points to:

```python
>>> home = pathlib.Path.home() # C:\Users\David
>>> home.name
'David'
>>> path = home / "hello.txt"
>>> path.name
'hello.txt'
```

The name of a file is broken down into two parts. The part to the left of the dot (`.`) is called the **stem**, and the part to the right of the dot is called the **suffix** or **file extension**.

The $.stem$ and $.suffix$ attributes return strings containing each of these parts of the file name:
```python
>>> path = pathlib.Path.home() / "hello.txt"
>>> path.stem
'hello'
>>> path.suffix
'.txt'
```

You might be wondering at this point how to actually do something with the $hello.txt$ file. You’ll learn how to read and write files in the next section. But before you open a file for reading, it might be a good idea to know whether or not that file exists.

### Checking File Path Existence in Python

Creating a `Path` object for a file path is possible even if the path doesn't currently exist. However, non-existent file paths may not be particularly useful unless you plan to create them later. The `Path` class provides an `.exists()` method that returns `True` or `False` based on whether the file path exists on the machine where the program is executed.

For example, consider the scenario where a file named "hello.txt" is absent in your home directory:

```python
path = pathlib.Path.home() / "hello.txt"
path.exists()
# False
```

Upon creating the file $hello.txt$ in your home directory and re-running the code, the `.exists()` method should now return `True`.

To determine whether a file path refers to a file or a directory, you can utilize the `.is_file()` and `.is_dir()` methods:

```python
# Check if the path is a file
path.is_file()
# True

# Check if the path is a directory
path.is_dir()
# False
```

Note that if the file path refers to a file that doesn't actually exist, `.is_file()` returns `False`. Similarly, for directories, `.is_dir()` returns `True` only if the directory exists.

Working with file paths is a fundamental aspect of programming projects involving data reading or writing from storage devices. Proficiency in handling file paths across different operating systems, along with utilizing `pathlib.Path` objects, ensures that your programs are adaptable to various environments. This skill is valuable for building robust and cross-platform applications.


## Common File System Operations in Python

With a solid understanding of the file system and adeptness in handling file paths using the pathlib module, let's delve into common file operations in Python. In this section, you'll explore how to perform the following operations:

### Creating Directories and Files in Python

Creating directories and files is a fundamental aspect of file system manipulation in Python, and the `pathlib` module simplifies this process. Let's explore how to perform these operations with clarity and efficiency.

**Creating Directories:**  
To create a new directory, use the `.mkdir()` method provided by the `Path` class. For instance:

```python
from pathlib import Path

# Create a new directory in the home folder
new_dir = Path.home() / "new_directory"
new_dir.mkdir()

# Check if the directory exists
print(new_dir.exists())  # True
print(new_dir.is_dir())  # True
```

If the directory already exists, attempting to create it again raises a `FileExistsError`. 

```python
>>> new_dir.mkdir()
Traceback (most recent call last):
  File "<pyshell#32>", line 1, in <module>
    new_dir.mkdir()
File "C:\Users\David\AppData\Local\Programs\Python\
Python38-32\lib\pathlib.py", line 1266, in mkdir
  self._accessor.mkdir(self, mode)
FileExistsError: [WinError 183] Cannot create a file when
that file already exists: 'C:\\Users\\David\\new_directory'
```

When you call the $.mkdir()$ method, Python attempts to create the $new\\_directory/$ folder again. Since it already exists, this operation fails and a `FileExistsError` exception is raised.

If you want to create a new directory if it doesn’t exists, but avoid raising the `FileExistsError` if it does, then you can set the options $exist_ok$ parameter of the $.mkdir()$ method to `True`:

```python
new_dir.mkdir(exist_ok=True)
```

This parameter ensures that the directory is created only if it doesn't exist, preventing an error if it does.


**Creating Files:**  
To create a new file, use the `.touch()` method. For example:

```python
file_path = new_dir / "file1.txt"
file_path.touch()

# Check if the file exists
print(file_path.exists())  # True
print(file_path.is_file())  # True
```

Unlike `.mkdir()`, `.touch()` does not raise an exception if the file already exists. It creates an empty file that can be later written to.

**Handling Nested Directories:**

Creating subdirectories within a directory requires attention to parent directories. If a parent directory doesn't exist, you can use the `parents` parameter:

```python
nested_dir = new_dir / "folder_a" / "folder_b"
nested_dir.mkdir(parents=True)
```

This ensures the creation of all necessary parent directories.

**Handling File Creation in Nested Directories:**

When creating files in nested directories, ensure the parent directories exist:

```python
file_path = new_dir / "folder_c" / "file2.txt"
file_path.parent.mkdir(parents=True)
file_path.touch()
```

This approach guarantees that both the directory and the file are created seamlessly.

By understanding these patterns, you gain a solid foundation for handling directory and file creation in Python, fostering robust and error-resistant code.



### Iterating Over Directory Contents

When working with directories, you often need to process all files within them. The pathlib library provides a convenient way to iterate over directory contents. Processing can encompass various operations like reading files, extracting data, or compressing files. In this discussion, we'll focus on retrieving the contents of a directory using pathlib, leaving file data processing for the next section.

Every item in a directory is either a file or a subdirectory. The `Path.iterdir()` method facilitates iterating over these items by returning an iterator of `Path` objects, each representing an item in the directory.

To employ `iterdir()`, begin by obtaining a `Path` representing the target directory. Consider the example of the previously created "new_directory" folder in your home directory, stored in the `new_dir` variable:

```python
new_dir = Path('C:/Users/David/new_directory')
for path in new_dir.iterdir():
    print(path)
```

The output would display the contents of "new_directory":

```
C:\Users\David\new_directory\file1.txt
C:\Users\David\new_directory\folder_a
C:\Users\David\new_directory\folder_c
```

Currently, "new_directory" contains three items: a file named "file1.txt" and two subdirectories, "folder_a" and "folder_c."

Since `iterdir()` returns an iterable, you can convert it to a list if needed:

```python
list_of_contents = list(new_dir.iterdir())
```

While conversion to a list is not always necessary, it can be useful for specific scenarios. Typically, you'll use `iterdir()` in a for loop, as demonstrated in the initial example.

It's important to note that `iterdir()` only returns items directly contained in the specified directory. Subdirectories' contents are not included in the output. If you need to iterate over the contents of a directory and its subdirectories, a more elaborate approach is required, which we'll address shortly. First, let's discuss how to search for files within a directory.


### Searching For Files In a Directory

When you need to iterate over specific types of files or files with particular naming schemes, the `Path.glob()` method in the pathlib library becomes handy. This method allows you to obtain an iterable over directory contents that meet specified criteria.

Despite its name, `.glob()` is used for file searches. The historical reference to the Unix glob program, which expanded file path patterns to full paths, is the reason behind the naming choice.

To utilize `.glob()`, provide a path representing a directory and pass a string containing a partial pattern with **wildcard characters**. The method then returns a list of file paths that match the specified pattern.

Wildcard characters serve as placeholders in **patterns**, allowing flexibility in matching. For example, in the pattern "\*.txt," the asterisk (*) is a wildcard character that can be replaced with any number of other characters. The resulting pattern matches any file path ending with ".txt."

Here's an example using the "new_directory/" folder assigned to the `new_dir` variable:

```python
for path in new_dir.glob("*.txt"):
    print(path)
```

This code outputs file paths within "new_directory/" that match the "*.txt" pattern.

Like `.iterdir()`, `.glob()` returns an iterable of paths, but this time, only paths matching the specified pattern are included. Keep in mind that `.glob()` returns paths directly contained in the folder on which it is called.

Conversion of the return value of `.glob()` to a list is possible:

```python
list_of_txt_files = list(new_dir.glob("*.txt"))
```

> ***Note:** You will most often use .glob() in a for loop.*

Common wildcard characters and their descriptions are outlined in the following table:

| Wildcard | Character Description         | Example Matches   | Does Not Match   |
|----------|-------------------------------|-------------------|-------------------|
| *        | Any number of characters      | "*b*" (b, ab, bc) | (a, c, ac)        |
| ?        | A single character            | "?bc" (abc, bbc)  | (bc, aabc, abcd)  |
| [abc]    | Matches one character in brackets | [CB]at (Cat, Bat) | (at, cat, bat)    |


Before delving into examples of how `.glob()` works with wildcard characters, let's enrich the $new\\_directory/$ folder with additional files. The following code snippet creates a more diverse set of files and directories within $new\\_directory/$:

```python
# Creating additional files in the "new_directory/" folder
paths = [
    new_dir / "program1.py",
    new_dir / "program2.py",
    new_dir / "folder_a" / "program3.py",
    new_dir / "folder_a" / "folder_b" / "image1.jpg",
    new_dir / "folder_a" / "folder_b" / "image2.png",
]

for path in paths:
    path.touch()
```

After executing this code, the structure of the "new_directory/" folder becomes more interesting, containing a mix of Python files and images in various subdirectories.


Desculpe pela confusão anterior. Aqui está o diagrama ajustado com os arquivos de `new_directory` no final:

```
new_directory/
|___folder_a/
│   |
|   |___folder_b/
│   |    │
│   |    └── image1.jpg
│   |    └── image2.png
|   └── program3.py
├── folder_c
│   └── file2.txt
|
├── file1.txt
├── program1.py
└── program2.py
```

Now, let's explore how the `.glob()` method works with each of the wildcard characters, leveraging this enhanced folder structure. We'll provide examples for the '*' (any number of characters), '?' (a single character), and '[abc]' (matches one character in brackets) wildcards.


**The \* Wildcard**  
The * wildcard matches any number of characters in a file path pattern. For example, the patter "*.py" matches all file paths that end in `.py`:

```python
>>> list(new_dir.glob("*.py"))
[WindowsPath('C:/Users/David/new_directory/program1.py'),
WindowsPath('C:/Users/David/new_directory/program2.py')]
```

You can use the * wildcard multiple times in a single pattern:

```python
>>> list(new_dir.glob("*1*"))
[WindowsPath('C:/Users/David/new_directory/file1.txt'),
WindowsPath('C:/Users/David/new_directory/program1.py')]
```

The pattern "*1*" matches any file path containing the number $1$ with any number of characters before and after it. The only files in $new\\_directory/$ that contain the number $1$ are $file1.txt$ and program1.py.


If you leave off the first * from the patter "*1*" to get the pattern "1*", then nothing gets matched:

```python
>>> list(new_dir.glob("1*"))
[]
```

The pattern "1*" matches files paths that start with the number $1$ and are followed by any number of characters after it. There are no files in the $new\\_directory/$ folder that match this, so `.glob()` doesn’t return anything.


**The ? Wildcard**  
The $?$ wildcard character matches a single character in a pattern. For example, the pattern "program?.py" will match any file path that starts with the word program followed by a single character and then .py:

```python
>>> list(new_dir.glob("program?.py"))
[WindowsPath('C:/Users/David/new_directory/program1.py'),
WindowsPath('C:/Users/David/new_directory/program2.py')]
```

You can use multiple instances if ? in a single pattern:

```python
>>> list(new_dir.glob("?older_?"))
[WindowsPath('C:/Users/David/new_directory/folder_a'),
WindowsPath('C:/Users/David/new_directory/folder_c')]
```

The pattern "?older_?" matches paths that start with any letter followed by older_ and some other character. In the $new\\_directory/$ folder, those paths are the $folder\\_a/$ and $folder\\_b/$ directories.

You can also combine the * and ? wildcards:
```python
>>> list(new_dir.glob("*1.??"))
[WindowsPath('C:/Users/David/new_directory/program1.py')]
```

The pattern "*1.??" matches any file path that contains a $1$ followed by a dot (.) and two more characters. The only path in $new\\_directory/$ matching this pattern is $program1.py$. Notice that $file1.txt$ doesn’t match the pattern because the dot is followed by three characters

**The [] Wildcard**  

The $[\\: \\:]$ wildcard works kind of like the $?$ wildcard because it matches only a single character. The difference is that instead of matching any single character like $?$ does, $[\\: \\:]$ only matches characters that are included between the square brackets.

For example, the pattern "program[13].py" matches any path containing the word program, followed by either a $1$ or $3$ and the extension `.py`. In the new_directory/ folder, program1.py is the only path matching this pattern:

```python
>>> list(new_dir.glob("program[13].py"))
[WindowsPath('C:/Users/David/new_directory/program1.py')]
```

As with the other wildcards, you can use multiple instances of the $[\\: \\:]$ wildcard, as well as combine it with any of the others.

### Recursive Matching With The \*\* Wildcard 

A limitation observed with both `.iterdir()` and `.glob()` is their exclusive return of paths directly contained in the specified folder. For instance, `new_dir.glob("*.txt")` only yields the path for "file1.txt" in "new_directory/" but overlooks "file2.txt" in the "folder_c/" subdirectory, despite it matching the "*.txt" pattern.

To address this limitation, the double asterisk (\*\*) wildcard comes into play, making the pattern recursive. The conventional way to implement this is by prefixing your pattern with "**/". This instructs `.glob()` to match the pattern in the current directory and any of its subdirectories.

For example, the pattern "**/*.txt" captures both "file1.txt" and "folder_c/file2.txt":

```python
list_txt_files_recursive = list(new_dir.glob("**/*.txt"))
[WindowsPath('C:/Users/David/new_directory/file1.txt'),
WindowsPath('C:/Users/David/new_directory/folder_c/file2.txt')]
```

Similarly, the pattern "**/*.py" encompasses any .py files in "new_directory/" and its subdirectories:

```python
list_python_files_recursive = list(new_dir.glob("**/*.py"))
[WindowsPath('C:/Users/David/new_directory/program1.py'),
WindowsPath('C:/Users/David/new_directory/program2.py'),
WindowsPath('C:/Users/David/new_directory/folder_a/program3.py')]
```

An alternative shorthand for recursive matching is `.rglob()`. Use it by passing the pattern without the "**/" prefix:

```python
list_python_files_rglob = list(new_dir.rglob("*.py"))
[WindowsPath('C:/Users/David/new_directory/program1.py'),
 WindowsPath('C:/Users/David/new_directory/program2.py'),
 WindowsPath('C:/Users/David/new_directory/folder_a/program3.py')]
```

The "r" in `.rglob()` signifies "recursive," offering a slightly shorter alternative to prefixing patterns with "**/". Both approaches are valid, but for simplicity, this guide will favor the use of `.rglob()` over the "**/" prefix.

### Moving and Deleting Files and Folders

Performing operations like moving or deleting files and directories requires utmost caution to avoid data loss. The `pathlib` library provides methods for such operations, but careful consideration is crucial.

To move a file or directory, leverage the `.replace()` method. For instance, moving "file1.txt" from "new_directory/" to "folder_a/":

```python
source = new_dir / "file1.txt"
destination = new_dir / "folder_a" / "file1.txt"
source.replace(destination)
```

If the destination already exists, `.replace()` overwrites it without raising exceptions, potentially causing data loss. To mitigate this, check if the destination file exists before moving:

```python
if not destination.exists():
    source.replace(destination)
```

For directory renaming or moving, use `.replace()` similarly. For example, renaming "folder_c" to "folder_d":

```python
source = new_dir / "folder_c"
destination = new_dir / "folder_d"
source.replace(destination)
```

To delete a file, use the `.unlink()` method:

```python
file_path = new_dir / "program1.py"
file_path.unlink()
```

Ensure its deletion with `.exists()`:

```python
file_path.exists()
```

To handle potential `FileNotFoundError` exceptions, set the optional `missing_ok` parameter to `True`:

```python
file_path.unlink(missing_ok=True)
```

Remember, deleting a file is irreversible; ensure it's intended. `.unlink()` only works for files. To remove an empty directory, use the `.rmdir()` method:

```python
folder_d = new_dir / "folder_d"
folder_d.rmdir()
```

For non-empty directories, you must delete the contained files first. To delete an entire directory, use the `shutil.rmtree()` function:

```python
import shutil
folder_a = new_dir / "folder_a"
shutil.rmtree(folder_a)
```

This function handles non-empty directories, ensuring their complete deletion. Exercise caution when working with the file system to prevent unintended data loss. Always verify file paths before operations and obtain user confirmation when necessary.

## Reading and Writing Files
In the realm of programming, files serve as the cornerstone for storing and transferring digital data. This section delves into the essential skills of reading and writing files using Python, with a focus on plain text files.

**What Is a File?**  
A file is essentially a sequence of bytes, with each byte being a number between 0 and 255. These bytes must be decoded to make sense of the file's contents. Python offers standard library modules for handling text, CSV, and audio files, along with various third-party packages for diverse file types. While advanced file types will be explored later, this section concentrates on plain text files.

**Understanding Text Files**  
Text files, consisting solely of text, are straightforward to work with. Yet, two potential challenges arise: character encoding and line endings.

1. **Character Encoding:** 
2. **Line Endings:**  


**Character Encoding**

Text files, when stored on disk, are essentially a sequence of bytes, with each byte or group of bytes representing a character within the file. Encoding is the process of converting characters typed on a keyboard into bytes during file creation, and decoding is the reverse process when reading a text file.

The association between a character and its corresponding integer value is determined by the file's character encoding. Some widely used character encodings include:

1. ASCII
2. UTF-8
3. UTF-16
4. UTF-32

While certain character encodings, like ASCII and UTF-8, encode characters in a similar manner (e.g., numbers and English letters), the crucial difference lies in the expanded capability of UTF-8 to encode a broader range of characters, including those not covered by ASCII, such as "ñ" or "ü". It's important to note that while you can decode ASCII-encoded text with UTF-8, the reverse is not always true.

Serious problems may arise when different encodings are used for encoding and decoding text. For example, decoding text encoded as UTF-8 with UTF-16 may result in the interpretation of an entirely different language than originally intended. A comprehensive guide to character encodings can be found in Real Python’s "Unicode & Character Encodings in Python: A Painless Guide."

Identifying the encoding used by a file is crucial, though it may not always be apparent. Typically, on modern Windows computers, `.txt` files are encoded with UTF-16 or UTF-8, while on macOS and Ubuntu Linux, the default encoding is usually UTF-8.

Throughout the examples in this section, it is assumed that the character encoding of all text files is UTF-8. If issues arise, consider adjusting the examples to use a different encoding.

**Line Endings**

Each line in a text file concludes with one or two characters indicating the line's end. These characters, not typically visible in a text editor, exist as bytes in the file data. The two characters employed for representing line endings are the carriage return (`\r`) and line feed (`\n`).

On Windows, line endings are represented by both a carriage return and a line feed by default. Conversely, on macOS and most Linux distributions, line endings are represented with a single line feed character.

When reading a Windows file on macOS or Linux, extra blank lines may be observed between text lines due to the interpretation of carriage returns as line endings on these platforms.

In practice, differences in line endings between various operating systems are rarely problematic. Python has built-in capabilities to handle line ending conversions automatically, alleviating concerns in most scenarios.

### Python File Objects
In Python, files are represented as file objects, instances of classes designed to handle various file types. There are two main types of file objects in Python:

1. **Text file objects**: Used for interacting with text files, handling encoding and decoding bytes.

2. **Binary file objects**: Used for directly working with the bytes contained in files, without performing encoding or decoding.

File objects can be created in Python using either the `Path.open()` method or the built-in `open()` function.

**Using the Path.open() Method**  
To utilize the `Path.open()` method, you'll first need a `Path` object. The following example demonstrates its usage in an interactive window like IDLE:

```python
from pathlib import Path

# Creating a Path object for the hello.txt file
path = Path.home() / "hello.txt"

# Creating the file in the home directory
path.touch()

# Opening the file in read mode with UTF-8 encoding
file = path.open(mode="r", encoding="utf-8")
```

In this example:
- A `Path` object for the "hello.txt" file is created and assigned to the `path` variable.
- `path.touch()` creates the file in your home directory.
- `path.open()` returns a new file object representing "hello.txt" and assigns it to the `file` variable.

Two essential keyword parameters are used to open the file:

1. **mode parameter:** Determines in which mode the file should be opened. The "r" argument opens the file in read mode.
2. **encoding parameter:** Determines the character encoding used to decode the file. The argument "utf-8" represents the UTF-8 character encoding.

You can inspect the `file` variable to see that it is assigned to a text file object:

```python
>>> file
<_io.TextIOWrapper name='C:\Users\David\hello.txt' mode='r' encoding='utf-8'>
```

Text file objects are instances of the `TextIOWrapper` class. You don't need to instantiate this class directly since you can create them with the `Path.open()` method.

Here are some commonly used modes for opening a file:

| Mode | Description |
| ---- | ----------- |
| "r"  | Creates a text file object for reading and raises an error if the file can't be opened. |
| "w"  | Creates a text file object for writing and overwrites all existing data in the file. |
| "a"  | Creates a text file object for appending data to the end of a file. |
| "rb" | Creates a binary file object for reading and raises an error if the file can't be opened. |
| "wb" | Creates a binary file object for writing and overwrites all existing data in the file. |
| "ab" | Creates a binary file object for appending data to the end of the file. |

Remember to explicitly close the file using the `file.close()` method to avoid leaving unnecessary waste in the system:

```python
>>> file.close()
```

Using `Path.open()` is the preferred way to open a file when you have an existing `Path` object. However, there is also a built-in function called `open()` that you can use for the same purpose.

**Using the open() Built-in**  
The built-in `open()` function is quite similar to the `Path.open()` method, but its first parameter is a string containing the path to the file you want to open. Here's how you can use the `open()` function:

First, create a new variable called `file_path` and assign to it a string containing the path to the "hello.txt" file (you should adjust the path to match the location on your own computer):

```python
file_path = "C:/Users/David/hello.txt"
```

Next, create a new file object using the `open()` built-in function and assign it to the variable `file`:

```python
file = open(file_path, mode="r", encoding="utf-8")
```

In this example:
- The first parameter of `open()` must be a path string.
- The `mode` and `encoding` parameters are the same as the parameters for the `Path.open()` method. Here, `mode` is set to "r" for read mode, and `encoding` is set to "utf-8".

Just like the file object returned by `Path.open()`, the file object returned by `open()` is a `TextIOWrapper` instance:

```python
>>> file
<_io.TextIOWrapper name='C:/Users/David/hello.txt' mode='r' encoding='utf-8'>
```

To close the file, use the file object’s `.close()` method:

```python
>>> file.close()
```

For the most part, you’ll use the `Path.open()` method when opening a file from an existing `pathlib.Path` object. However, if you don’t need all of the functionality of the `pathlib` module, then `open()` is a great way to quickly create a file object.

**Using the with Statement**  
When you open a file, your program establishes a connection between itself and the physical file, and the operating system manages this connection. It's crucial to close this connection to release system resources. If your program crashes between opening and closing a file, these resources might linger until the operating system recognizes they are no longer needed.

To ensure proper cleanup, you can open a file within a `with` statement. The pattern for using the `with` statement is as follows:

```python
with path.open(mode="r", encoding="utf-8") as file:
    # Do something with the file
```

The `with` statement has two parts: a header and a body. The header starts with the `with` keyword and ends with a colon. The return value of `path.open()` is assigned to the variable name after the `as` keyword. The indented block of code following the header is executed, and when it's exited, the file object assigned to `file` is closed automatically, even if an exception is raised during the block's execution.

This `with` statement pattern also works with the `open()` built-in:

```python
with open(file_path, mode="r", encoding="utf-8") as file:
    # Do something with the file
```

Using the `with` statement is considered the Pythonic way of working with files, as it ensures proper resource management. Throughout this book, this pattern will be consistently used whenever opening a file.

### Reading Data From a File

To begin, open the hello.txt file in your home directory using a text editor. Add the text "Hello World" and save the file.

In IDLE's interactive window, execute the following commands:

```python
>>> path = Path.home() / "hello.txt"
>>> with path.open(mode="r", encoding="utf-8") as file:
...     text = file.read()
...
>>>
```

The file object created by `path.open()` is assigned to the variable `file`. Within the `with` block, the `file.read()` method reads the text from the file, and the result is assigned to the variable `text`.

The value returned by `file.read()` is a string object with the value "Hello World":

```python
>>> type(text)
<class 'str'>
>>> text
'Hello World'
```

The `file.read()` method reads the entire text in the file and returns it as a string value. If there are multiple lines, each line is separated by a newline character `\n`. To demonstrate, open hello.txt in a text editor, add the text "Hello again" on the second line, and save the file.

Back in IDLE, read the text from the file again:

```python
>>> with path.open(mode="r", encoding="utf-8") as file:
...     text = file.read()
...
>>> text
'Hello World\nHello again'
```

> ***Note:** The \n character between the text from each line.*

Instead of reading the entire file at once, you can process each line one at a time:

```python
>>> with path.open(mode="r", encoding="utf-8") as file:
...     for line in file.readlines():
...         print(line, end="")
...
Hello World
Hello again
```

The `file.readlines()` method returns an iterable of lines from the file. Setting the `print()` function's optional `end` parameter to an empty string removes the extra blank line:

```python
>>> with path.open(mode="r", encoding="utf-8") as file:
...     for line in file.readlines():
...         print(line, end="")
...
Hello World
Hello again
```

Use `readlines()` when each line in the file represents a single record.

If you attempt to read from a non-existent file, both `path.open()` and `open()` raise a `FileNotFoundError`:

```python
>>> path = Path.home() / "new_file.txt"
>>> with path.open(mode="r", encoding="utf-8") as file:
...     text = file.read()
...
Traceback (most recent call last):
  ...
FileNotFoundError: [Errno 2] No such file or directory: 'C:\\Users\\David\\new_file.txt'
```

### Writing Data To a File

To write data to a plain text file, utilize the `write()` method of a file object, passing a string to it. Ensure that the file object is opened in write mode by specifying "w" as the value for the `mode` parameter.

For example, the following writes the text "Hi there!" to the hello.txt file in your home directory:

```python
>>> with path.open(mode="w", encoding="utf-8") as file:
...     file.write("Hi there!")
...
9
>>>
```

The integer 9 displayed after the `with` block indicates that the `write()` method returns the number of characters written. The string "Hi there!" contains nine characters, so the `write()` method returns 9.

When using `write()`, any existing contents of the file are overwritten. It is equivalent to deleting the old hello.txt file and creating a new one. Note that when `mode="w"` is set in `open()`, the original data in the file is lost.

You can verify the file's content by reading and displaying it:

```python
>>> with path.open(mode="r", encoding="utf-8") as file:
...     text = file.read()
...
>>> print(text)
Hi there!
```

To append data to the end of a file, open the file in append mode ("a"):

```python
>>> with path.open(mode="a", encoding="utf-8") as file:
...     file.write("\nHello")
...
6
```

In append mode, new data is added to the end of the file, leaving the existing data intact. The newline character at the beginning of the string ensures that "Hello" is printed on a new line.

Verify the addition by opening and reading from the file:

```python
>>> with path.open(mode="r", encoding="utf-8") as file:
...     text = file.read()
...
>>> print(text)
Hi there!
Hello
```

To write multiple lines to a file simultaneously, use the `writelines()` method. Create a list of strings and open the file in write mode, then use `writelines()` to write each string to the file:

```python
>>> lines_of_text = [
...     "Hello from Line 1\n",
...     "Hello from Line 2\n",
...     "Hello from Line 3 \n",
... ]
>>> with path.open(mode="w", encoding="utf-8") as file:
...     file.writelines(lines_of_text)
...
>>>
```

Each string in the `lines_of_text` list is written to the file. Note that each string ends with the newline character (`\n`).

If you attempt to open a non-existent path in write mode, Python will attempt to create the file. If all parent folders in the path exist, the file is created without issues:

```python
>>> path = Path.home() / "new_file.txt"
>>> with path.open(mode="w", encoding="utf-8") as file:
...     file.write("Hello!")
...
6
```

However, if a parent directory does not exist, `open()` will raise a `FileNotFoundError`. To address this, call the `.mkdir()` method with the `parents` parameter set to `True` before opening the file in write mode:

```python
>>> path = Path.home() / "new_folder" / "new_file.txt"
>>> path.parent.mkdir(parents=True)
>>> with path.open(mode="w", encoding="utf-8") as file:
...     file.write("Hello!")
...
6
```

In this section, you covered various aspects, including the nature of files as sequences of bytes, character encodings, differences in line endings across operating systems, and the methods for reading and writing text files using the `Path.open()` method and the `open()` built-in function.

## Read and Write CSV Data

Let's consider a scenario where you have a temperature sensor in your house that records the temperature every four hours, resulting in six temperature readings per day. To store these readings, you can create a list and write the values to a CSV (Comma-Separated Values) file, where each day's readings are on a new line, separated by commas.

```python
from pathlib import Path

# Example temperature readings for a day
temperature_readings = [68, 65, 68, 70, 74, 72]

# File path for the CSV file
file_path = Path.home() / "temperatures.csv"

# Writing to the CSV file in append mode
with file_path.open(mode="a", encoding="utf-8") as file:
    file.write(str(temperature_readings[0]))
    for temp in temperature_readings[1:]:
        file.write(f",{temp}")
```

In this example, a file named `temperatures.csv` is created in your home directory, and each day's temperature readings are appended as a new line. The values are separated by commas.

To read the content of the CSV file:

```python
with file_path.open(mode="r", encoding="utf-8") as file:
    text = file.read()

# Displaying the content of the CSV file
print(text)
```

The content of the file will be `'68,65,68,70,74,72'`.

CSV files are a common format for storing sequential data, allowing you to recover each row as a list. For instance:

```python
# Recovering the list from the CSV file
temperatures = text.split(",")
print(temperatures)  # Output: ['68', '65', '68', '70', '74', '72']
```

Keep in mind that values read from a text file are always read as strings. To convert them back to integers, you can use a list comprehension:

```python
# Converting the strings to integers
int_temperatures = [int(temp) for temp in temperatures]
print(int_temperatures)  # Output: [68, 65, 68, 70, 74, 72]
```

This example illustrates that a CSV file is essentially a plain text file. By utilizing file reading and writing techniques, you can store and retrieve sequences of values in CSV files.

Moreover, the Python standard library includes a module called `csv` to simplify working with CSV files. In the upcoming sections, we'll explore how to use the `csv` module for writing and reading CSV files.

### The csv Module

The `csv` module in Python simplifies the process of reading and writing CSV files. In this section, we'll demonstrate how to use the `csv` module to rewrite the previous example, showcasing its capabilities and the operations it handles.

To start, import the `csv` module in the IDLE's interactive window:

```python
>>> import csv
```

Now, let's create a new CSV file containing temperature data for several days.

**Writing CSV Files With csv.writer**  
Create a list of lists containing temperature readings from three days:

```python
>>> daily_temperatures = [
...     [68, 65, 68, 70, 74, 72],
...     [67, 67, 70, 72, 72, 70],
...     [68, 70, 74, 76, 74, 73],
... ]
```

Now, open the `temperatures.csv` file in write mode:

```python
>>> file_path = Path.home() / "temperatures.csv"
>>> file = file_path.open(mode="w", encoding="utf-8")
```

Instead of using a `with` statement, a file object is created to inspect each step of the writing process. Create a new CSV writer object by passing the file object `file` to `csv.writer()`:

```python
>>> writer = csv.writer(file)
```

The `csv.writer()` method returns a CSV writer object with methods for writing data to the CSV file. For example, use the `writer.writerow()` method to write a list to a new row in the CSV file:

```python
>>> for temp_list in daily_temperatures:
...     writer.writerow(temp_list)
...
```

Just like a file object’s `.write()` method, `.writerow()` returns the number of characters written to the file. Now, close the file:

```python
>>> file.close()
```

If you open the `temperatures.csv` file in a text editor, you'll see the following content:

```plaintext
68,65,68,70,74,72
67,67,70,72,72,70
68,70,74,76,74,73
```

In practice, you would typically use a `with` statement to write to the file. Here's how the code looks using the `with` statement:

```python
with file_path.open(mode="w", encoding="utf-8") as file:
    writer = csv.writer(file)
    for temp_list in daily_temperatures:
        writer.writerow(temp_list)
```

The main advantage of using `csv.writer` is that you don’t need to worry about converting values to strings before writing them to the file. The `csv.writer` object handles this for you, resulting in shorter and cleaner code.

The `.writerow()` method writes a single row to the CSV file, but you can write multiple rows at once using the `.writerows()` method. This shortens the code even more when your data is already in a list of lists:

```python
with file_path.open(mode="w", encoding="utf-8") as file:
    writer = csv.writer(file)
    writer.writerows(daily_temperatures)
```

Now let’s proceed to read from the `temperatures.csv` file to recover the `daily_temperatures` list of lists.

**Reading CSV Files With csv.reader**  
To read a CSV file using the `csv` module, you can utilize the `csv.reader` class. Similar to `csv.writer` objects, `csv.reader` objects are instantiated from a file object:

```python
>>> file = file_path.open(mode="r", encoding="utf-8")
>>> reader = csv.reader(file)
```

The `csv.reader()` method returns a CSV reader object, which allows you to iterate over the rows of the CSV file:

```python
>>> for row in reader:
...     print(row)
...
['68', '65', '68', '70', '74', '72']
['67', '67', '70', '72', '72', '70']
['68', '70', '74', '76', '74', '73']
>>> file.close()
```

Each row of the CSV file is returned as a list of strings. To recover the `daily_temperatures` list of lists, you'll need to convert each list of strings to a list of integers using a list comprehension.

Here's a complete example that opens the CSV file in a `with` statement, reads each row in the CSV file, converts the list of strings to a list of integers, and stores each list of integers in a list of lists called `daily_temperatures`:

```python
# Create an empty list
daily_temperatures = []
with file_path.open(mode="r", encoding="utf-8") as file:
    reader = csv.reader(file)
    for row in reader:
        # Convert row to list of integers
        int_row = [int(value) for value in row]
        # Append the list of integers to daily_temperatures list
        daily_temperatures.append(int_row)
```

The resulting `daily_temperatures` list will be:

```python
[[68, 65, 68, 70, 74, 72], [67, 67, 70, 72, 72, 70], [68, 70, 74, 76, 74, 73]]
```

Working with CSV files using the `csv` module is much more straightforward than using the standard tools for reading and writing plain text files. In more complex scenarios, CSV files may represent records with various fields, and the first row may serve as a header row with the names of the fields. The `csv` module provides functionalities to handle such cases efficiently.

**Reading and Writing CSV Files With Headers**  
Let's delve into an example of a CSV file with a header row, encompassing multiple data types:

```plaintext
name,department,salary
Lee,Operations,75000.00
Jane,Engineering,85000.00
Diego,Sales,80000.00
```

The initial line of the file comprises field names, and each subsequent line signifies a record with a value for each field.

Although it's feasible to read CSV files like the one above using `csv.reader()`, it necessitates keeping track of the header row, and each row is returned as a list without the field names. A more intuitive approach is to return each row as a dictionary, where keys are the field names, and values are the field values in the row. This is precisely what `csv.DictReader` objects accomplish!

Let's create a new CSV file named `employees.csv` and demonstrate how to work with `csv.DictReader`:

```python
>>> file_path = Path.home() / "employees.csv"
>>> file = file_path.open(mode="r", encoding="utf-8")
>>> reader = csv.DictReader(file)
>>> reader.fieldnames
['name', 'department', 'salary']

>>> for row in reader:
...     print(row)
...
{'name': 'Lee', 'department': 'Operations', 'salary': '75000.000'}
{'name': 'Jane', 'department': 'Engineering', 'salary': '85000.00'}
{'name': 'Diego', 'department': 'Sales', 'salary': '80000.00'}
>>> file.close()
```

Upon creating a `DictReader` object, the first row of the CSV file is presumed to contain the field names, stored in a list assigned to the `DictReader` instance’s `.fieldnames` attribute.

Just like `csv.reader` objects, `DictReader` objects are iterable:

```python
>>> def process_row(row):
...     row["salary"] = float(row["salary"])
...     return row
...
>>> with file_path.open(mode="r", encoding="utf-8") as file:
...     reader = csv.DictReader(file)
...     for row in reader:
...         print(process_row(row))
...
{'name': 'Lee', 'department': 'Operations', 'salary': 75000.0}
{'name': 'Jane', 'department': 'Engineering', 'salary': 85000.0}
{'name': 'Diego', 'department': 'Sales', 'salary': 80000.0}
```

The `process_row()` function converts the "salary" key to a floating-point number for each row dictionary read from the CSV file. Understanding how to read and process CSV files with headers using `csv.DictReader` is a valuable skill.

You can efficiently write CSV files with headers using the `csv.DictWriter` class. Here's an example using a list of dictionaries representing a small database of people and their ages:

```python
>>> people = [
...     {"name": "Veronica", "age": 29},
...     {"name": "Audrey", "age": 32},
...     {"name": "Sam", "age": 24},
... ]

>>> file_path = Path.home() / "people.csv"
>>> file = file_path.open(mode="w", encoding="utf-8")
>>> writer = csv.DictWriter(file, fieldnames=["name", "age"])
```

When instantiating a new `DictWriter` object, the first parameter is the file object for writing the CSV data. The `fieldnames` parameter, which is required, is a list of strings containing the field names.

In the example above, the string literal `["name", "age"]` is passed to the `fieldnames` parameter, but you can also use `people[0].keys()`. This approach is useful if the field names are not known when writing the program or if there are many fields, making a list literal impractical.

Now, let's write the data to the CSV file. The `writeheader()` method writes the header row to the CSV file:

```python
>>> writer.writeheader()
10
```

The `writeheader()` method returns the number of characters written to the file, which is 10 in this case. Writing the header row is optional but recommended. It helps define the data contained in the CSV file and makes it easy to read the rows from the CSV file as dictionaries using the `csv.DictReader` class.

Now that the header is written, you can proceed to write the data from the `people` list to the CSV file using the `.writerows()` method. Finally, close the file.

```python
>>> writer.writerows(people)
>>> file.close()
```

This code snippet writes the content of the `people` list to the CSV file. The resulting `people.csv` file, located in your home directory, will contain the following data:

```
name,age
Veronica,29
Audrey,32
Sam,24
```

CSV files provide a flexible and convenient way of storing data, making them widely used in businesses worldwide. Acquiring the skills to work with CSV files is valuable for handling and managing data effectively.
