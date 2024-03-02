## Graphical User Interfaces

In the course of this book, you have predominantly focused on crafting command-line applications—programs initiated and generating output within a terminal window. While command-line apps are effective for developing tools primarily intended for usage by developers or yourself, it is essential to acknowledge that most software users prefer not to engage with a terminal.

Graphical User Interfaces (GUIs), commonly referred to as "gooeys," offer a distinct paradigm. Unlike command-line interfaces, GUIs present windows equipped with components such as buttons and text fields. This approach affords users a familiar and visual means to interact with a program, steering away from the traditional reliance on terminal-based interactions.

### Adding GUI Elements With EasyGUI

To swiftly incorporate a graphical user interface into your program, EasyGUI is a handy library. While somewhat limited, EasyGUI excels in simplifying the integration of GUI elements, making it suitable for uncomplicated tools requiring minimal user input.

In this segment, we'll utilize EasyGUI to develop a brief GUI program enabling users to select a PDF file from their hard drive and rotate its pages by a specified angle.

#### Installing EasyGUI

Begin by installing EasyGUI using the following pip3 command:

```python
$ pip3 install easygui
```

After installing EasyGUI, you can inspect specific details about the package using the `pip3 show` command:

```python
$ pip3 show easygui
```

The output provides information such as the version (0.98.1), a brief summary, the home page link, authors, license, and installation location.

Please note that the code in this chapter is based on EasyGUI version 0.98.1, as indicated in the provided information.

### Your First EasyGUI Application

EasyGUI excels in presenting dialog boxes to gather user input and display output, making it an effective tool for simpler applications. However, it may not be the most suitable choice for developing extensive applications with multiple windows, menus, and toolbars. Instead, consider EasyGUI as a replacement for the traditional `input()` and `print()` functions, providing a visual interface for user interaction.

The typical program flow with EasyGUI involves:

1. Displaying a visual element on the user's screen at a specific point in the code.
2. Pausing code execution until the user provides input through the visual element.
3. Resuming code execution once the user's input is received.

To gain an understanding of EasyGUI's functionality, open a new interactive window in IDLE and execute the following code:

```python
import easygui as gui
gui.msgbox(msg="Hello!", title="My first message box")
```

When executed, this code on a Windows system will result in a window similar to the one depicted below:

<img src="https://github.com/artghieri/A-Introduction-to-Python-3/assets/102708433/e5966236-3e34-4ffb-bac3-f695cfbda888"></img>

> ***Note:** This is a window’s appearance on Windows system.*

Both EasyGUI and IDLE leverage the Tkinter library, which you'll delve into in the upcoming section. However, this shared dependency occasionally leads to execution issues, causing dialog boxes to become unresponsive or frozen.

If you encounter such problems, consider running your code from a terminal. Initiate an interactive Python session using the `python` command on Windows and `python3` on macOS/Ubuntu.

Now, let's dissect the elements of the dialog box generated with the provided code:

1. The string "Hello!" passed to the `msg` parameter of `msgbox()` is presented as the message in the dialog box.
2. The string "My first message box," supplied to the `title` parameter, acts as the title of the message box.
3. A single button labeled "OK" is visible in the message box.

Upon clicking the OK button, inspect IDLE’s interactive window. The string 'OK' is displayed beneath the last line of code:

```python
>>> gui.msgbox(msg="Hello, EasyGUI!", title="My first message box")
'OK'
```

The `msgbox()` function returns the button label upon closing the dialog box. If the dialog box is closed without pressing the OK button, the return value is `None`.

You have the flexibility to customize the button label using a third optional parameter called `ok_button`. For instance, the following code creates a message box with a button labeled "Click me":

```python
>>> gui.msgbox(msg="Hello!", title="Greeting", ok_button="Click me")
```

While `msgbox()` serves well for displaying messages, it offers limited interaction options. EasyGUI provides several functions that present diverse dialog box types. Let’s explore some of these functions now!

### EasyGUI’s Ensemble of GUI Elements

Besides `msgbox()`, EasyGUI has several other functions for displaying different kinds of dialog boxes. The following table summarizes some of the available functions:

| Function      | Description                                      | Returns                                    |
|---------------|--------------------------------------------------|--------------------------------------------|
| `msgbox()`    | Display a message with a single button           | Label of the button                        |
| `buttonbox()` | Dialog box with several buttons                  | Label of the selected button               |
| `indexbox()`  | Dialog box with several buttons                  | Index of the selected button               |
| `enterbox()`  | Dialog box with a text entry box                 | Text entered                               |
| `fileopenbox()`| Dialog box for selecting a file to be opened     | Absolute path to the selected file         |
| `diropenbox()` | Dialog box for selecting a directory to be opened| Absolute path to the selected directory    |
| `filesavebox()`| Dialog box for saving a file                     | Absolute path to the location for saving  |


**buttonbox()**  
The `buttonbox()` function in EasyGUI showcases a dialog box containing a message and multiple clickable buttons. Your program receives the label of the clicked button as a return value.

Similar to `msgbox()`, `buttonbox()` entails parameters such as `msg` and `title` for configuring the displayed message and dialog box title. Additionally, it introduces a third parameter, `choices`, utilized to define the button labels.

For instance, the following code snippet generates a dialog box featuring three buttons labeled "Red", "Yellow", and "Blue":

```python
gui.buttonbox(
msg="What is your favorite color?",
title="Choose wisely...",
choices=("Red", "Yellow", "Blue"),
)
```

The resulting dialog box is depicted below:

![image](https://github.com/artghieri/A-Introduction-to-Python-3/assets/102708433/5135d581-fc30-4304-9354-2176ed8ce37e)

Upon clicking any of the buttons in the `buttonbox()` dialog box, the corresponding button label is returned as a string. For instance, pressing the "Yellow" button will display the string `'Yellow'` in the output of the interactive window, immediately below the `buttonbox()` function:

```python
gui.buttonbox(
msg="What is your favorite color?",
title="Choose wisely...",
choices=("Red", "Yellow", "Blue"),
)
'Yellow'
```

Similar to `msgbox()`, if the dialog box is closed without selecting any button, the value `None` is returned. This feature allows you to handle scenarios where the user decides to close the dialog without making a choice.

**indexbox()**  

The `indexbox()` function presents a dialog box similar in appearance to the one generated by `buttonbox()`. In fact, creating an `indexbox()` follows the same pattern as creating a `buttonbox()`:

```python
gui.indexbox(
msg="What's your favorite color?",
title="Choose wisely...",
choices=("Red", "Yellow", "Blue"),
)
```

Here's a visual representation of the dialog box:


![image](https://github.com/artghieri/A-Introduction-to-Python-3/assets/102708433/8b4a9405-3de2-419e-a888-ffd0f5f351a2)


The primary distinction between `indexbox()` and `buttonbox()` lies in the return value. While `buttonbox()` returns the label of the selected button, `indexbox()` returns the index corresponding to the chosen option in the list or tuple specified in the `choices` parameter.

For instance, clicking the "Yellow" button would yield the integer `1`:

```python
gui.indexbox(
msg="What's your favorite color?",
title="Favorite color",
choices=("Red", "Yellow", "Blue"),
)
```

Given that `indexbox()` returns an index rather than a string, it is advisable to define the tuple for `choices` outside the function. This way, you can later reference the label using the obtained index in your code:

```python
colors = ("Red", "Yellow", "Blue")
choice = gui.indexbox(
msg="What's your favorite color?",
title="Favorite color",
choices=colors,
)
choice  # Output: 1
colors[choice]  # Output: 'Yellow'
```

Both `buttonbox()` and `indexbox()` are valuable for gathering input when users need to choose from a predetermined set of options. However, these functions are less suitable for obtaining information like a user's name or email address. For such cases, you can utilize `enterbox()`.

**enterbox()**  
The `enterbox()` function serves the purpose of gathering text input from the user:

```python
gui.enterbox(
msg="What is your favorite color?",
title="Favorite color",
)
```

The resulting dialog box includes an input box where the user can type their response:


![image](https://github.com/artghieri/A-Introduction-to-Python-3/assets/102708433/16dae5f7-c632-4edb-bc69-74ae1549c5b7)


Type in a color name, such as "Yellow," and press "OK." The text you entered is then returned as a string:

```python
gui.enterbox(
msg="What is your favorite color?",
title="Favorite color",
)
# Output: 'Yellow'
```

Frequently, dialog boxes are employed to enable users to choose files or directories in their filesystem. For these specific scenarios, EasyGUI provides dedicated functions.

**fileopenbox()**  
The `fileopenbox()` function presents a dialog box allowing the user to choose a file for opening:

```python
gui.fileopenbox(title="Select a file")
```

The resulting dialog box mirrors the appearance of the standard system file open dialog box:


![image](https://github.com/artghieri/A-Introduction-to-Python-3/assets/102708433/a7386f4f-2ce6-4f4f-9520-e6ad414ea87b)


Select a file and click the "Open" button. A string containing the full path to the selected file is then returned.

`fileopenbox()` solely provides the file selection dialog; it does not actually open the file. To open the selected file, you need to use the `open()` built-in function, as demonstrated in Chapter 12.

Similar to `msgbox()` and `buttonbox()`, the function returns `None` if the user presses "Cancel" or closes the dialog box without selecting a file.

**diropenbox()  and  filesavebox()**  
EasyGUI provides two additional functions that create dialogs similar to `fileopenbox()`:

1. **`diropenbox()`**
- Opens a dialog to select a folder instead of a file.
- Returns the full path to the selected directory when the user presses "Open."

2. **`filesavebox()`**
- Opens a dialog to choose a location for saving a file.
- Confirms whether the user wants to overwrite the file if the chosen name already exists.
- Returns the file path when the user presses "Save."

**Important Points:**
- Neither `diropenbox()` nor `filesavebox()` actually opens a directory or saves a file. They only provide the absolute path to the directory to be opened or the file to be saved.
- You must implement the code yourself to perform the actual directory opening or file saving.
- Both functions return `None` if the dialogs are closed without pressing "Open" or "Save." This can potentially lead to program crashes if not handled carefully.

**Example:**
```python
# Raises a TypeError if the dialog box is closed without making any selection
path = gui.fileopenbox(title="Select a file")
open_file = open(path, "r")
```

How you handle such situations significantly impacts the user experience with your program.

### Exiting Your Program Gracefully

Suppose you are developing a program for extracting pages from a PDF file, and the first step is to allow the user to select a PDF file using `fileopenbox()`.

What should your program do if the user decides not to proceed and presses the "Cancel" button? It's essential to handle such situations gracefully, ensuring that your program doesn't crash or produce unexpected outputs.

In scenarios like the one described above, it's appropriate to stop the program from running. Python provides the built-in `exit()` function as a means to achieve this.

Here's an example demonstrating the use of `exit()` to terminate the program when the user presses the "Cancel" button in a file selection dialog box:

```python
import easygui as gui

# Allow the user to select a file
path = gui.fileopenbox(title="Select a file")

# Check if the user pressed "Cancel"
if path is None:
exit()
```

In this code snippet:
- If the user closes the file open dialog box without pressing "OK," the `path` variable becomes `None`.
- In such cases, the program executes the `exit()` function within the `if` block, leading to program termination.

> ***Note:* When running the program in IDLE, `exit()` also closes the current interactive window.*

Now that you have the ability to create dialog boxes using EasyGUI, you can integrate these concepts into a comprehensive real-world application.

## Introduction to Tkinter

Python offers numerous GUI frameworks, but Tkinter stands out as the sole framework integrated into the Python standard library. Tkinter boasts several strengths, with its cross-platform compatibility being a prominent feature. This implies that the same code seamlessly operates on Windows, macOS, and Linux. Tkinter leverages native operating system elements for rendering visual components, resulting in applications that blend seamlessly with the platform on which they run.

While Tkinter holds the position of the de facto Python GUI framework, it is not immune to criticism. One notable critique is that GUIs developed with Tkinter may appear outdated. If your preference is for a sleek, modern interface, Tkinter might not align with your expectations.

However, Tkinter compensates with its lightweight nature and relative simplicity compared to other frameworks. This simplicity makes it an attractive choice for constructing GUI applications in Python, particularly for scenarios where achieving functionality and cross-platform compatibility promptly takes precedence over creating a cutting-edge appearance.

As mentioned in the previous section, IDLE, the Python IDE, is constructed using Tkinter. Users might encounter challenges when running their own GUI programs within IDLE. If your GUI window unexpectedly freezes or seems to disrupt IDLE's behavior, try executing your script from a command prompt or terminal.

### Your First Tkinter Application

At the core of a Tkinter Graphical User Interface (GUI) is the window, serving as the container for all other GUI elements. These elements, including text boxes, labels, and buttons, are collectively referred to as widgets, residing within windows.

Let's initiate the creation of a window containing a single widget. Start by opening a new interactive window in IDLE.

Begin by importing the Tkinter module:

```python
import tkinter as tk
```

In Tkinter, a window is an instance of the `Tk` class. Create a new window and assign it to the variable `window`:

```python
window = tk.Tk()
```

Upon executing this code, a new window will appear on your screen. Its appearance is contingent on your operating system.

![image](https://github.com/artghieri/A-Introduction-to-Python-3/assets/102708433/bc9139e8-afd8-4ca0-9a99-dadff40eac2e)

> ***Note:** Windows, macOS, Ubuntu respectively.*
abel Widget to the Tkinter Window

Now that we've established a window, let's incorporate a widget. The `tk.Label` class is employed to introduce text into a window.

Create a `Label` widget displaying the text "Hello, Tkinter" and assign it to a variable named `greeting`:

```python
greeting = tk.Label(text="Hello, Tkinter")
```

The window you created earlier remains unchanged at this point. Although you've fashioned a `Label` widget, it has not been integrated into the window yet.

Various methods exist for adding widgets to a window. Presently, we will employ the `Label` widget's `.pack()` method:

```python
greeting.pack()
```

The window now adopts the appearance shown below:

![image](https://github.com/artghieri/A-Introduction-to-Python-3/assets/102708433/dc37c817-1bf6-4096-8205-d62b3b263252)

When utilizing `.pack()` to embed a widget into a window, Tkinter automatically adjusts the window size to be as compact as possible while still encompassing the entire widget.

Now, execute the following Python code:

```python
window.mainloop()
```

While it might seem uneventful, observe that a new prompt does not appear in the shell.

`window.mainloop()` directs Python to execute the Tkinter application, halting any subsequent code from running until the associated window is closed. Once you close the window you've created, a new prompt will be displayed in the shell.

When working with Tkinter from a REPL (Read-Eval-Print Loop), such as IDLE's interactive window, window updates occur as each line is executed. This behavior differs when a Tkinter program is executed from a Python file. If you omit `window.mainloop()` at the end of a program in a Python file, the Tkinter application won't run, and nothing will be displayed.

Creating a fundamental window in Tkinter involves just a few lines of code. Nevertheless, blank windows lack practicality. In the next section, you'll delve into some of the widgets offered by Tkinter and discover how to tailor them to meet your application's specific needs.

### Working With Widgets

Widgets serve as the cornerstone of Tkinter, representing the elements with which users engage in your program. Each widget in Tkinter is characterized by a specific class. Below are descriptions of some available widgets:

| Widget Class | Description                                       |
|--------------|---------------------------------------------------|
| Label        | Displays text on the screen.                      |
| Button       | A clickable button that may execute an action.    |
| Entry        | Permits the entry of a single line of text.       |
| Text         | Enables the input of multiline text.              |
| Frame        | A rectangular region grouping related widgets or providing padding between them. |

In the upcoming sections, you will gain insights into working with each of these widgets. It's worth noting that Tkinter encompasses more widgets than those highlighted here. For an exhaustive list, refer to the [Basic Widgets](https://tkdocs.com/tutorial/widgets.html) and [More Widgets](https://tkdocs.com/tutorial/morewidgets.html) articles in the [TkDocs](https://tkdocs.com/tutorial/index.html) tutorial.

### Label Widgets

Label widgets serve the purpose of displaying static text or images, and the text they present cannot be edited by the user; it is strictly for display. As illustrated in the initial example of this chapter, you can instantiate a Label widget by using the Label class and providing a string to the `text` parameter:

```python
label = tk.Label(text="Hello, Tkinter")
```

By default, Label widgets exhibit text with the system's default text color and background color, usually black and white, respectively. However, you might observe different colors if you've adjusted these settings in your operating system.

To govern Label text and background colors, utilize the `foreground` and `background` parameters:

```python
label = tk.Label(
text="Hello, Tkinter",
foreground="white",   # Set the text color to white
background="black"    # Set the background color to black
)
```

Several valid color names are available, such as "red," "orange," "yellow," "green," "blue," and "purple." Additionally, many HTML color names are compatible with Tkinter.

Refer to a comprehensive chart of valid color names [here](https://www.tcl.tk/man/tcl8.4/TkCmd/colors.htm#M11). For an exhaustive reference, including macOS and Windows-specific system colors dictated by the current system theme, consult [this list](https://www.tcl.tk/man/tcl8.4/TkCmd/colors.htm#M17).

You can specify colors using [hexadecimal RGB](https://en.wikipedia.org/wiki/Web_colors#Hex_triplet) values as well:

```python
label = tk.Label(text="Hello, Tkinter", background="#34A2FE")
```

This sets the label background to a pleasant light blue color. Although hexadecimal RGB values might seem cryptic compared to named colors, they offer greater flexibility. Luckily, various tools can assist in obtaining hexadecimal color codes with minimal effort.

To streamline the process, if you prefer brevity, you can use the shorthand `fg` and `bg` parameters instead of `foreground` and `background`:

```python
label = tk.Label(text="Hello, Tkinter", fg="white", bg="black")
```

You can also manage the width and height of a label using the `width` and `height` parameters:

```python
label = tk.Label(
text="Hello, Tkinter",
fg="white",
bg="black",
width=10,
height=10
)
```

Here's a visual representation of this label within a window:

![image](https://github.com/artghieri/A-Introduction-to-Python-3/assets/102708433/e26d102e-75ad-47f8-89cb-5fc2d144ec93)

It might appear peculiar that the label in the window isn't square, even though both width and height are set to 10. This anomaly occurs because the height and width are measured in text units.

In Tkinter, one horizontal text unit corresponds to the width of the character "0" (the number zero) in the default system font. Similarly, one vertical text unit is determined by the height of the character "0".

Tkinter employs text units for width and height measurements, as opposed to units like inches, centimeters, or pixels. This ensures consistent behavior across platforms, allowing the application to adapt to the default font size on a user's machine.

By basing measurements on the width of a character, Tkinter guarantees that the widget size is relative to the default font. This ensures proper text fit within labels and buttons, regardless of the application's execution environment.

While labels excel in displaying text, they do not facilitate user input. The upcoming three widgets are specifically designed for gathering user input.

### Exploring Button Widgets

Button widgets serve as clickable elements that can be configured to execute a function upon being clicked. The process of calling functions from button clicks will be covered in the upcoming section. For now, let's focus on creating and styling a Button.

Button and Label widgets share many similarities, with a Button essentially functioning as a clickable Label. The same keyword arguments utilized for creating and styling a Label can be applied to Button widgets.

For instance, the following code snippet generates a Button featuring a blue background, yellow text, and dimensions set to 10 text units in height and 5 text units in width:

```python
button = tk.Button(
text="Click me!",
width=25,
height=5,
bg="blue",
fg="yellow",
)
```

Here's a visual representation of the button within a window:

![image](https://github.com/artghieri/A-Introduction-to-Python-3/assets/102708433/92a0d701-91ba-4181-8e6e-18d8cf111a61)

The next two widgets we’ll see are used to collect text input from a user.

### Understanding Entry Widgets

When you require a small amount of text input from a user, such as a name or email address, Entry widgets prove useful. They present a compact text box where users can input text.

Creating and styling an Entry widget closely follows the process for Label and Button widgets. For instance, the following code snippet generates an Entry widget with a blue background, yellow text, and a width of 50 text units:

```python
entry = tk.Entry(fg="yellow", bg="blue", width=50)
```

However, the unique aspect of Entry widgets lies in how they are used to obtain user input. There are three primary operations with Entry widgets:

1. Retrieving text with the `.get()` method
2. Deleting text with the `.delete()` method
3. Inserting text with the `.insert()` method

To gain a better understanding of Entry widgets, let's create one and interact with it. Open IDLE's interactive window and follow along with the examples.

Begin by importing tkinter and creating a new window:

```python
import tkinter as tk
window = tk.Tk()
```

Next, create a Label and an Entry widget:

```python
label = tk.Label(text="Name")
entry = tk.Entry()
```

While the Label doesn't enforce any requirements on the Entry, it provides a description of the expected text. To make the widgets visible, use the `.pack()` method:

```python
label.pack()
entry.pack()
```

Here's how it looks:

![image](https://github.com/artghieri/A-Introduction-to-Python-3/assets/102708433/2288556e-e463-44ec-bbb1-5d19e0b7dcaa)

Notice that Tkinter automatically centers the Label above the Entry widget in the window. This is a feature of the `.pack()` method, which you’ll learn more about in later sections.

Click inside the Entry widget with your mouse and type "Real Python":

![image](https://github.com/artghieri/A-Introduction-to-Python-3/assets/102708433/2a0443f9-ad67-4946-8328-a584951aab35)

Now that you've entered some text into the Entry widget, it's time to retrieve that text for use in your program.

Utilize the Entry widget’s `.get()` method to fetch the text and assign it to a variable, let's call it `name`:

```python
name = entry.get()
```

After executing this code, the variable `name` will hold the retrieved text. For instance:

```python
>>> name
'Real Python'
```

If you wish to delete text from the Entry widget, you can use the `.delete()` method. This method takes an integer argument specifying which character to remove. For example, calling `.delete(0)` removes the first character from the Entry:

```python
>>> entry.delete(0)
```

After this operation, the text remaining in the widget would be "eal Python":

![image](https://github.com/artghieri/A-Introduction-to-Python-3/assets/102708433/3443ccb6-3509-44ca-aa51-eaa7f96d9c68)

Similar to Python string objects, the indexing of text in an Entry widget starts from 0. If you intend to remove multiple characters from an Entry, you can provide a second integer argument to the `.delete()` method. This second argument indicates the index of the character where the deletion should stop.

For instance, if you want to delete the first four letters in the Entry, you can execute the following:

```python
>>> entry.delete(0, 4)
```

Following this operation, the remaining text in the Entry would be "Python":

![image](https://github.com/artghieri/A-Introduction-to-Python-3/assets/102708433/1e133b3b-54c5-4c02-8acd-0ae239ba7270)


The `.delete()` method in Entry widgets functions similarly to string slices. The first argument specifies the starting index, and the deletion extends up to, but does not include, the index provided as the second argument.

To remove all text in an Entry, you can use the special constant `tk.END` as the second argument:

```python
>>> entry.delete(0, tk.END)
```

This operation results in an empty text box.

![image](https://github.com/artghieri/A-Introduction-to-Python-3/assets/102708433/ee2af684-2dde-4fe6-80ff-46689a1b11cd)

To insert text into an Entry widget, use the `.insert()` method:
```python
>>> entry.insert(0, "Python")
```

The window now looks like this:

![image](https://github.com/artghieri/A-Introduction-to-Python-3/assets/102708433/57b46f0d-ac9e-4a8a-9de4-c59904f16b7d)


The `.insert()` method in Entry widgets takes two arguments. The first argument specifies the position where the text should be inserted. If the Entry is empty, the new text will always be inserted at the beginning, regardless of the first argument.

For instance, using `.insert(100, "Real ")` would yield the same result as using `.insert(0, "Real ")` if the Entry is initially empty.

If there is already existing text in the Entry, the `.insert()` method will insert the new text at the specified position and shift the existing text to the right. For example:

```python
>>> entry.insert(0, "Real ")
```

This results in the Entry widget displaying the text "Real Python".

![image](https://github.com/artghieri/A-Introduction-to-Python-3/assets/102708433/adc6de4c-5795-4afd-8ac6-ef8261c0820f)

Entry widgets are great for capturing small amounts of text from a user, but because they are only displayed on a single line, they are not ideal for gathering large amounts of text. That’s where Text widgets come in!

### Text Widgets

Text widgets in Tkinter serve the purpose of handling multiline text, enabling users to input substantial amounts of text, ranging from paragraphs to multiple pages.

Similar to Entry widgets, Text widgets support three primary operations:

1. **Retrieve Text:** Employ the `.get()` method.
2. **Delete Text:** Use the `.delete()` method.
3. **Insert Text:** Utilize the `.insert()` method.

While the method names align with those used for Entry widgets, their functionality varies slightly. Let's delve into the capabilities of Text widgets by creating an example.

**Note:**
If the window from the previous section is still open, you can close it with the following command in IDLE's interactive window:

```python
>>> window.destroy()
```

Alternatively, close it manually by clicking the "Close" button on the window.

In IDLE's interactive window, establish a new empty window and add a Text widget using `.pack()`:

```python
>>> window = tk.Tk()
>>> text_box = tk.Text()
>>> text_box.pack()
```

Text boxes are inherently larger than Entry widgets by default. The resulting appearance of the window is as described above.

![image](https://github.com/artghieri/A-Introduction-to-Python-3/assets/102708433/7df37dce-9019-49ce-a8ec-992f8d972c5f)

Click anywhere inside the window to activate the text box. Type in the word "Hello". Then press Enter and type "World" on the second line.

The window should now look like this:

![image](https://github.com/artghieri/A-Introduction-to-Python-3/assets/102708433/66b3447b-a1e1-4aa6-bf7c-a856a6f28f51)

Similar to Entry widgets, Text widgets in Tkinter enable the retrieval of text using the `.get()` method. However, it's crucial to note that calling `.get()` without any arguments raises an exception. Unlike Entry widgets, Text widgets require two indices to define a range for text retrieval, as they can contain multiple lines.

Here's an explanation of how indices work in Text widgets:

1. Line numbers start from 1.
2. Character positions start from 0 on each line.

To create an index, use the format `<line>.<char>`, where `<line>` is the line number, and `<char>` is the character position.

Examples:

- "1.0": First character on the first line.
- "2.3": Fourth character on the second line.

Using the created index, retrieve text:

```python
>>> text_box.get("1.0")
'H'
```

To get the word "Hello" from the text box:

```python
>>> text_box.get("1.0", "1.5")
'Hello'
```

To get the word "World" from the second line:

```python
>>> text_box.get("2.0", "2.5")
'World'
```

To retrieve all text:

```python
>>> text_box.get("1.0", tk.END)
'Hello\nWorld\n'
```

Notice that newline characters are included in the retrieved text. Every line in a Text widget, including the last one, has a newline character at the end.

The `.delete()` method is employed to delete characters, and it works similarly to Entry widgets:

- With a single argument: Deletes a single character.

```python
>>> text_box.delete("1.0")
```

The first line of text becomes "ello".

![image](https://github.com/artghieri/A-Introduction-to-Python-3/assets/102708433/54a077d4-12f4-4651-a111-84db5b926d88)

In the two-argument version of the `.delete()` method for Text widgets, you specify two indices to eliminate a range of characters. This deletion starts at the first index and extends up to, but does not include, the second index.

For instance, consider deleting the remaining "ello" on the first line of the text box using the indices "1.0" and "1.4":

```python
>>> text_box.delete("1.0", "1.4")
```

Upon executing this command, observe that the text is removed from the first line, resulting in a blank line followed by the word "World" on the second line. This capability provides precise control over the content within a Text widget, facilitating dynamic manipulation of text entries.

![image](https://github.com/artghieri/A-Introduction-to-Python-3/assets/102708433/bf0b6435-f117-4ddd-b1d5-6b3bb36bd9c7)

Even when not visible, a newline character remains on the first line of the text in the Text widget. This invisible character can be confirmed using the `.get()` method:

```python
>>> text_box.get("1.0")
'\n'
```

Upon deletion of this newline character, the content in the text box undergoes a shift, moving "World" up to the first line:

```python
>>> text_box.delete("1.0")
```

Now, "World" occupies the first line of the text box. Managing newline characters becomes crucial when manipulating the text content in Text widgets, ensuring accurate alignment and formatting.


![image](https://github.com/artghieri/A-Introduction-to-Python-3/assets/102708433/5731d99c-51b6-4d06-8b34-0fa395c58f79)

To clear out the entire text in the Text widget, you can use the `.delete()` method with "1.0" as the start index and `tk.END` as the second index:

```python
>>> text_box.delete("1.0", tk.END)
```

Executing this command results in an empty text box, effectively removing all the content. This operation is useful when you want to reset or clear the Text widget for new input or display purposes.


![image](https://github.com/artghieri/A-Introduction-to-Python-3/assets/102708433/db1e7900-c11a-4956-8417-d63021bc18e6)

To add text to a Text widget, the `.insert()` method is used. The format for the method is:

```python
text_box.insert("index", "text to insert")
```

For example, to insert the word "Hello" at the beginning of the Text widget, you can use:

```python
>>> text_box.insert("1.0", "Hello")
```

This command places the specified text at the given position within the Text widget. The index is specified in the format "<line>.<column>", similar to the format used by `.get()` to retrieve text.


![image](https://github.com/artghieri/A-Introduction-to-Python-3/assets/102708433/08eed7f3-9d33-4964-a7c8-b93081e21b5d)

When attempting to insert text into a new line, it's important to note that the format for the index is crucial. To insert the word "World" on the second line, you should use an index with a line number greater than 1. However, to start a new line, it's common to use the index format "<line>.0", indicating the beginning of a line.

Here's an example:

```python
>>> text_box.insert("2.0", "World")
```

In this case, the text "World" is inserted at the beginning of the second line, creating a new line in the Text widget.


![image](https://github.com/artghieri/A-Introduction-to-Python-3/assets/102708433/6f51f999-a461-4327-a6a6-94e95dab705a)

When aiming to insert text onto a new line in a Text widget, it's essential to explicitly include a newline character (`\n`) in the string being inserted. This signals the start of a new line.

Here's an example:

```python
>>> text_box.insert("2.0", "\nThis goes on the second line")
```

By incorporating `\n`, the text "This goes on the second line" is inserted on a new line in the Text widget.

![image](https://github.com/artghieri/A-Introduction-to-Python-3/assets/102708433/2e6da75d-130b-4813-be3d-c1c7e5fae19f)

So, `.insert()` will either insert text at the specified position, if there is already text at that position, or append text to the specified line if the character number is greater than the index of the last character in the text box.

It’s usually impractical to try and keep track of what the index of the last character is. The best way to insert text at the end of a Text widget is pass `tk.END` to the first parameter of `.insert()`:

```python
text_box.insert(tk.END, "Put me at the end!")
```

Don’t forget to include the newline character \n at the beginning of the text if you want to put it on a new line:

```python
text_box.insert(tk.END, "\nPut me on a new line!")
``` 

Label, Button, Entry, and Text widgets are just a few of the widgets available in Tkinter. There are several others, including widgets for checkboxes, radio buttons, scroll bars, and progress bars. For more information on the other widgets available, check out the tutorial on tkdocs.com.

In this chapter, we’re going to work with only five widgets: the four you have seen so far plus the Frame widget. Frame widgets are important for organizing the layout of your widgets in an application.

Before we get into the details about laying out the visual presentation of your widgets, let’s take a closer look at how Frame widgets work, and how you can assign other widgets to them

### Framing Your Widgets in Tkinter

In Tkinter, utilizing Frame widgets is crucial for organizing and structuring the layout of your application. Below is a simple script that creates a basic Frame widget and integrates it into the main application window:

```python
import tkinter as tk

window = tk.Tk()
frame = tk.Frame()
frame.pack()

window.mainloop()
```

The `frame.pack()` method efficiently integrates the frame into the window, prompting the window to resize itself to the smallest possible dimensions required to enclose the frame.

Upon executing the script, you'll observe a rather unremarkable output, as the frame doesn't contain any widgets yet. This is merely the initial step in understanding how to incorporate Frame widgets into your Tkinter applications. Let's further explore how you can assign other widgets to these frames and enhance the visual appeal of your GUI.

![image](https://github.com/artghieri/A-Introduction-to-Python-3/assets/102708433/ec24b694-0d36-4fa1-b073-c38cc45e2ccb)


An empty Frame widget might seem invisible, but it serves as a container for other widgets. You can assign a widget to a frame by setting the widget’s `master` attribute. Here's an example:

```python
import tkinter as tk

frame = tk.Frame()
label = tk.Label(master=frame)
```

To illustrate this concept, let’s create a script that involves two Frame widgets named `frame_a` and `frame_b`. `frame_a` will contain a label with the text "I'm in Frame A," while `frame_b` will hold the label "I'm in Frame B." Here's how you can achieve that:

```python
import tkinter as tk

window = tk.Tk()
frame_a = tk.Frame()
frame_b = tk.Frame()

label_a = tk.Label(master=frame_a, text="I'm in Frame A")
label_a.pack()

label_b = tk.Label(master=frame_b, text="I'm in Frame B")
label_b.pack()

frame_a.pack()
frame_b.pack()

window.mainloop()
```

Notice that `frame_a` is packed into the window before `frame_b`. When you run the script, the resulting window displays the label in `frame_a` above the label in `frame_b`. This showcases how frames act as organizational containers for widgets within Tkinter applications.

![image](https://github.com/artghieri/A-Introduction-to-Python-3/assets/102708433/301db33a-7e73-48dc-8a87-24025a61e2ca)

Let's explore the impact of swapping the order of `frame_a.pack()` and `frame_b.pack()` in a Tkinter script. The following example demonstrates the change:

```python
import tkinter as tk

window = tk.Tk()

frame_a = tk.Frame()
label_a = tk.Label(master=frame_a, text="I'm in Frame A")
label_a.pack()

frame_b = tk.Frame()
label_b = tk.Label(master=frame_b, text="I'm in Frame B")
label_b.pack()

# Order of `frame_a` and `frame_b` is swapped
frame_b.pack()
frame_a.pack()

window.mainloop()
```

Executing this script will result in the labels appearing in the reverse order in the window. The label from `frame_b` will now be displayed above the label from `frame_a`. This demonstrates the significance of the order in which frames are packed into the window and how it influences the layout of widgets.

![image](https://github.com/artghieri/A-Introduction-to-Python-3/assets/102708433/61a0ae40-9183-455b-b56f-5c89f4feaec0)

Now, with `label_b` on top, it's noteworthy that its position follows the placement of `frame_b`.

Each of the widget types you've encountered—Label, Button, Entry, and Text—incorporates a `master` attribute during instantiation. This allows you precise control over which Frame a widget is associated with.

Frame widgets prove to be invaluable for structuring other widgets in a coherent manner. By grouping related widgets within the same frame, you ensure that they remain together, maintaining cohesion even if the frame is repositioned within the window.

Beyond logical organization, Frame widgets can also enhance the visual appeal of your application. Continue reading to explore how to implement various borders for Frame widgets.

### Enhancing Frame Appearance with Reliefs in Tkinter

In Tkinter, you can enhance the visual appeal of Frame widgets by configuring the `relief` attribute, which creates distinctive borders around the frame. The `relief` attribute can be set to one of the following values:

- `tk.FLAT`: No border effect (default).
- `tk.SUNKEN`: Creates a sunken effect.
- `tk.RAISED`: Creates a raised effect.
- `tk.GROOVE`: Creates a grooved border effect.
- `tk.RIDGE`: Creates a ridged effect.

To implement the border effect, you need to set the `borderwidth` attribute to a value greater than 1, adjusting the width of the border in pixels.

Below is a script that demonstrates these effects by packing five Frame widgets into a window, each with a different `relief` value:

```python
import tkinter as tk

# Dictionary of relief effects
border_effects = {
    "flat": tk.FLAT,
    "sunken": tk.SUNKEN,
    "raised": tk.RAISED,
    "groove": tk.GROOVE,
    "ridge": tk.RIDGE,
}

window = tk.Tk()

for relief_name, relief in border_effects.items():
    # Create a new Frame with specified relief and borderwidth
    frame = tk.Frame(master=window, relief=relief, borderwidth=5)
    
    # Pack the Frame into the window
    frame.pack(side=tk.LEFT)
    
    # Create a Label to display the relief name and pack it into the Frame
    label = tk.Label(master=frame, text=relief_name)
    label.pack()

window.mainloop()
```

This script creates a dictionary (#1) with relief names as keys and their corresponding Tkinter objects as values. Then, a loop iterates over the dictionary items, creating Frame widgets with different reliefs and displaying them in the window.

The resulting window showcases the distinct border effects applied to each Frame.

![image](https://github.com/artghieri/A-Introduction-to-Python-3/assets/102708433/4eac6aa0-a4b8-4605-8877-c4ae759a8b41)

In this image, you can observe that:
- `tk.FLAT` creates a flat-looking frame.
- `tk.SUNKEN` adds a border that gives the frame the appearance of being sunk into the window.
- `tk.RAISED` gives the frame a border that makes it appear to protrude from the screen.
- `tk.GROOVE` adds a border that appears as a sunken groove around an otherwise flat frame.
- `tk.RIDGE` gives the appearance of a raised lip around the edge of the frame.


### Widget Naming Conventions

When creating widgets, you have the flexibility to name them as you wish, provided the name adheres to valid Python identifier rules. However, it is advisable to include the widget class name in the variable name assigned to the widget instance.

For instance, if a Label widget displays a user's name, consider naming the widget `label_user_name`. Similarly, an Entry widget collecting a user's age could be named `entry_age`. Including the widget class name in the variable name enhances code readability, making it clear which type of widget the variable refers to.

Using the full widget class name may result in lengthy variable names. Therefore, adopting a shorthand for each widget type can be helpful. Throughout this chapter, the following prefixes will be used to name widgets:

Classe do Widget | Prefixo Variável | Exemplo
--- | --- | ---
Label | `lbl` | `lbl_name`
Button | `btn` | `btn_submit`
Entry | `ent` | `ent_age`
Text | `txt` | `txt_notes`
Frame | `frm` | `frm_address`

With this knowledge, you can create windows, utilize widgets, and manage frames. While you can now construct windows displaying messages, the next section will delve into Tkinter's potent geometry managers, allowing you to control the layout of your applications more effectively.

## Controlling Layout With Geometry Managers

Up until now, you’ve been adding widgets to windows and Frame widgets using the `.pack()` method, but you haven’t been told what exactly this method does. Let’s clear things up!

Application layout in Tkinter is controlled with geometry managers. `.pack()` is an example of a geometry manager, but it isn’t the only one. Tkinter has two others: `.place()` and `.grid()`.

Each window and Frame in your application can use only one geometry manager. However, different frames can use different geometry managers, even if they are assigned to a frame or window using another geometry manager.

Let’s start by taking a closer look at `.pack()`.

### The .pack() Geometry Manager

The `.pack()` method utilizes a packing algorithm to place widgets in a Frame or window in a specified order. The packing algorithm consists of two primary steps:

1. Computes a rectangular area, known as a parcel, that is just tall (or wide) enough to hold the widget and fills the remaining width (or height) in the window with blank space.
2. Centers the widget in the parcel, unless a different location is specified.

`.pack()` is a powerful tool but can be challenging to visualize. The best way to understand it is to explore some examples.

Let’s observe what happens when you use `.pack()` to arrange three Label widgets within a Frame:

```python
import tkinter as tk

window = tk.Tk()

frame1 = tk.Frame(master=window, width=100, height=100, bg="red")
frame1.pack()

frame2 = tk.Frame(master=window, width=50, height=50, bg="yellow")
frame2.pack()

frame3 = tk.Frame(master=window, width=25, height=25, bg="blue")
frame3.pack()

window.mainloop()
```

By default, `.pack()` positions each Frame below the previous one, in the order they are assigned to the window.

![image](https://github.com/artghieri/A-Introduction-to-Python-3/assets/102708433/b8e6410d-b946-468a-80da-ad46d1c26570)

### Understanding Widget Placement with `.pack()`

Each Frame is positioned at the top-most available position. The red Frame is at the window's top, followed by the yellow Frame just below it, and the blue Frame below the yellow one.

For each Frame, there is an invisible parcel containing it. Each parcel is as wide as the window and as tall as the corresponding Frame it contains. Since no anchor point was specified when `.pack()` was called for each Frame, they are all centered inside their parcels. This is why each Frame appears centered in the window.

`.pack()` accepts keyword arguments for more precise widget placement. For instance, you can use the `fill` keyword argument to specify the direction in which the frames should fill. Options include `tk.X` to fill horizontally, `tk.Y` to fill vertically, and `tk.BOTH` to fill in both directions.

Here’s an example of stacking the three frames to fill the entire window horizontally:

```python
import tkinter as tk

window = tk.Tk()

frame1 = tk.Frame(master=window, height=100, bg="red")
frame1.pack(fill=tk.X)

frame2 = tk.Frame(master=window, height=50, bg="yellow")
frame2.pack(fill=tk.X)

frame3 = tk.Frame(master=window, height=25, bg="blue")
frame3.pack(fill=tk.X)

window.mainloop()
```

Notice that the width is not set on any of the Frame widgets because the `.pack()` method on each frame is set to fill horizontally, overriding any width that may be set. The resulting window looks like this:

![image](https://github.com/artghieri/A-Introduction-to-Python-3/assets/102708433/bc382556-c798-4a0e-a3ac-f0d664a9f4f7)

### Responsive Filling and Side Placement with `.pack()`

An advantage of using `.pack()` to fill the window is its responsiveness to resizing. You can try widening the window generated by the previous script to observe how it works. As you widen the window, the width of the three Frame widgets grows to fill the window.

However, notice that the Frame widgets do not expand in the vertical direction. The `side` keyword argument of `.pack()` specifies on which side of the window the widget should be placed. Options include `tk.TOP`, `tk.BOTTOM`, `tk.LEFT`, and `tk.RIGHT`. If `side` is not set, `.pack()` automatically uses `tk.TOP` and places new widgets at the top of the window or at the top-most portion of the window that isn’t already occupied by a widget.

For instance, the following script places three frames side by side from left to right and expands each frame to fill the window vertically:

```python
import tkinter as tk

window = tk.Tk()

frame1 = tk.Frame(master=window, width=200, height=100, bg="red")
frame1.pack(fill=tk.Y, side=tk.LEFT)

frame2 = tk.Frame(master=window, width=100, bg="yellow")
frame2.pack(fill=tk.Y, side=tk.LEFT)

frame3 = tk.Frame(master=window, width=50, bg="blue")
frame3.pack(fill=tk.Y, side=tk.LEFT)

window.mainloop()
```

This time, you have to specify the `height` keyword argument on at least one of the frames to force the window to have some height. The resulting window adapts to the set configuration.

![image](https://github.com/artghieri/A-Introduction-to-Python-3/assets/102708433/14565297-9ae1-4186-8160-72d98e323c4f)

Just as setting `fill=tk.X` made the frames resize responsively when the window is resized horizontally, setting `fill=tk.Y` makes the frames resize responsively when the window is resized vertically. Feel free to try it out!

For a truly responsive layout, you can set an initial size for your frames using the `width` and `height` attributes. Then, set the `fill` keyword argument of the `.pack()` method to `tk.BOTH` and the `expand` keyword argument to `True`:

```python
import tkinter as tk

window = tk.Tk()

frame1 = tk.Frame(master=window, width=200, height=100, bg="red")
frame1.pack(fill=tk.BOTH, side=tk.LEFT, expand=True)

frame2 = tk.Frame(master=window, width=100, bg="yellow")
frame2.pack(fill=tk.BOTH, side=tk.LEFT, expand=True)

frame3 = tk.Frame(master=window, width=50, bg="blue")
frame3.pack(fill=tk.BOTH, side=tk.LEFT, expand=True)

window.mainloop()
```

Now, when you run the script, you'll see a window that initially looks the same as the one generated in the previous example. However, the difference is that now you can resize the window however you want, and the frames expand and fill the window responsively. Pretty cool!

### Precise Widget Placement with .place()

You can use the `.place()` method of a widget to precisely control its location within a window or frame. Provide the `x` and `y` keyword arguments to specify the top-left corner's x- and y-coordinates. Both `x` and `y` are measured in pixels, not text units.

Keep in mind that the origin, where `x` and `y` are both 0, is the top-left corner of the frame or window. Therefore, consider the `y` argument of `.place()` as the number of pixels from the top of the window and the `x` argument as the number of pixels from the left of the window.

Here's an example illustrating how the `.place()` geometry manager works:

```python
import tkinter as tk

window = tk.Tk()

# Create a new Frame widget (frame1) that is 150 pixels wide and 150 pixels tall, and pack it into the window
frame1 = tk.Frame(master=window, width=150, height=150)
frame1.pack()

# Create a new Label (label1) with a yellow background and place it in frame1 at position (0, 0)
label1 = tk.Label(master=frame1, text="I'm at (0, 0)", bg="red")
label1.place(x=0, y=0)

# Create a second Label (label2) with a red background and place it in frame1 at position (75, 75)
label2 = tk.Label(master=frame1, text="I'm at (75, 75)", bg="yellow")
label2.place(x=75, y=75)

window.mainloop()
```

This code creates a window with a frame and two labels placed at specific coordinates within the frame. The result is displayed in the window produced by the script.

![image](https://github.com/artghieri/A-Introduction-to-Python-3/assets/102708433/55737dc8-e884-4ee7-8536-69548d8f7405)

While the `.place()` method can be effective in specific scenarios, it is not commonly used due to two main drawbacks:

1. **Complex Layout Management:** Managing layouts with `.place()` can be challenging, especially in applications with numerous widgets.

2. **Non-Responsiveness:** Layouts created with `.place()` are not responsive, meaning they don't adapt to changes when the window is resized.

Cross-platform GUI development faces the challenge of creating layouts that appear appealing across different platforms. `.place()` is not an ideal choice for achieving responsive and cross-platform layouts.

However, this doesn't imply that `.place()` should never be used. In certain cases, such as developing a GUI for a map, `.place()` might be the perfect choice to ensure widgets are correctly positioned relative to each other on the map.

`.pack()` is often a more preferred choice than `.place()`, but it also has some drawbacks. Widget placement depends on the order in which `.pack()` is called, making it challenging to modify existing applications without a thorough understanding of the layout-controlling code.

The `.grid()` geometry manager provides a solution to many of these issues, offering a more versatile and intuitive approach, as you'll discover in the next section.

### The Versatile .grid() Geometry Manager

One of the most commonly used geometry managers is the `.grid()` geometry manager. Offering the flexibility of `.pack()` in a more comprehensible and maintainable format, `.grid()` simplifies the process of organizing widgets.

The functioning of `.grid()` revolves around dividing a window or Frame into rows and columns. By calling `.grid()` and providing the row and column indices to the respective keyword arguments, you can specify the location of a widget. Both row and column indices start at 0. For instance, a row index of 1 and a column index of 2 would instruct `.grid()` to position a widget in the third column of the second row.

To illustrate, consider the following script that generates a 3 × 3 grid of frames, each containing Label widgets:

```python
import tkinter as tk

window = tk.Tk()

for i in range(3):
    for j in range(3):
        frame = tk.Frame(
            master=window,
            relief=tk.RAISED,
            borderwidth=1
        )
        frame.grid(row=i, column=j)
        
        label = tk.Label(master=frame, text=f"Row {i}\nColumn {j}")
        label.pack()

window.mainloop()
```

The resulting window displays a 3 × 3 grid of frames with labeled content:

![image](https://github.com/artghieri/A-Introduction-to-Python-3/assets/102708433/63bfaa3c-750b-42a1-8f4c-93cfd207aea4)

In this example, both the `.grid()` and `.pack()` geometry managers are employed. While each Frame is associated with the window through the `.grid()` manager, the layout of individual frames is governed by the `.pack()` manager.

It's crucial to note that although `.grid()` is invoked on each Frame object, the geometry manager's application extends to the window object. Simultaneously, the layout specifics of each frame are managed using the `.pack()` geometry manager.

In the previous example, the frames were positioned closely adjacent to each other. To introduce some spacing around each Frame, you can define the padding for each cell in the grid. Padding comprises both external and internal padding. External padding adds space around the outside of a grid cell and can be adjusted using two `.grid()` keyword arguments:

1. `padx`: Adds padding in the horizontal direction.
2. `pady`: Adds padding in the vertical direction.

Both `padx` and `pady` are measured in pixels, offering precise control over the amount of padding. Setting both to the same value ensures consistent padding in both directions.

Let's enhance the previous example by incorporating some padding around the frames:

```python
import tkinter as tk

window = tk.Tk()

for i in range(3):
    for j in range(3):
        frame = tk.Frame(
            master=window,
            relief=tk.RAISED,
            borderwidth=1
        )
        frame.grid(row=i, column=j, padx=5, pady=5)
        
        label = tk.Label(master=frame, text=f"Row {i}\nColumn {j}")
        label.pack()

window.mainloop()
```

The resulting window displays a well-organized grid of frames with adequate spacing:

![image](https://github.com/artghieri/A-Introduction-to-Python-3/assets/102708433/1d9e88f7-ea33-4737-b28b-2ec07241822a)


In the following code, a subtle modification has been made to the previous example by introducing extra padding around each Label. This refinement provides each cell in the grid with a bit of breathing room, creating a visually appealing separation between the Frame border and the text within the Label:

```python
import tkinter as tk

window = tk.Tk()

for i in range(3):
    for j in range(3):
        frame = tk.Frame(
            master=window,
            relief=tk.RAISED,
            borderwidth=1
        )
        frame.grid(row=i, column=j, padx=5, pady=5)
        
        label = tk.Label(master=frame, text=f"Row {i}\nColumn {j}")
        label.pack(padx=5, pady=5)

window.mainloop()
```

In this version, both `.grid()` and `.pack()` geometry managers are employed to optimize the layout. The additional padding around the Label widgets contributes to a more aesthetically pleasing and well-organized grid, enhancing the overall visual presentation of the window.

![image](https://github.com/artghieri/A-Introduction-to-Python-3/assets/102708433/495a1ecb-c9b0-4d09-9d79-68a123a57f6e)


The design looks quite appealing! However, if you attempt to expand the window in any direction, you'll observe that the layout lacks responsiveness. The entire grid remains anchored at the top-left corner as the window enlarges.

To address this, you can regulate how the rows and columns of the grid expand when the window is resized by employing the `.columnconfigure()` and `.rowconfigure()` methods on the window object. It's important to note that the grid is associated with the window, even though you invoke `.grid()` on each Frame widget.

Both `.columnconfigure()` and `.rowconfigure()` require three essential arguments:

1. The index of the grid column or row that you intend to configure. You can also specify a list of indices to configure multiple rows or columns simultaneously.
2. A keyword argument named weight, determining how the column or row should respond to window resizing relative to the other columns and rows.
3. A keyword argument named minsize, setting the minimum size of the row height or column width in pixels.

By default, weight is set to 0, signifying that the column or row does not expand as the window resizes. If every column and row is assigned a weight of 1, they all grow at the same rate. Alternatively, if one column has a weight of 1 and another a weight of 2, the second column expands at twice the rate of the first.

Let's enhance the previous script to better handle window resizing:

```python
import tkinter as tk

window = tk.Tk()

for i in range(3):
    window.columnconfigure(i, weight=1, minsize=75)
    window.rowconfigure(i, weight=1, minsize=50)

for j in range(3):
    frame = tk.Frame(
        master=window,
        relief=tk.RAISED,
        borderwidth=1
    )
    frame.grid(row=i, column=j, padx=5, pady=5)
    
    label = tk.Label(master=frame, text=f"Row {i}\nColumn {j}")
    label.pack(padx=5, pady=5)

window.mainloop()
```

The `.columnconfigure()` and `.rowconfigure()` methods are positioned within the body of the outer for loop. While you could explicitly configure each column and row outside of the for loop, this would necessitate writing an additional six lines of code.

During each iteration of the loop, the i-th column and row are configured to have a weight of 1. This ensures that each row and column expands at the same rate whenever the window is resized.

The `minsize` argument is set to 75 for each column and 50 for each row. This guarantees that the Label widget always displays its text without cutting off any characters, even if the window size is extremely small.

Feel free to run the script to get a sense of how it operates! Experiment with the `weight` and `minsize` parameters to observe their impact on the grid.

By default, widgets are centered in their grid cells. For instance, the following code generates two Label widgets and positions them in a grid with one column and two rows:

```python
import tkinter as tk

window = tk.Tk()
window.columnconfigure(0, minsize=250)
window.rowconfigure([0, 1], minsize=100)

label1 = tk.Label(text="A")
label1.grid(row=0, column=0)

label2 = tk.Label(text="B")
label2.grid(row=1, column=0)

window.mainloop()
```

Each grid cell is 250 pixels wide and 100 pixels tall. The labels are centered within each cell, as depicted in the following figure: [Include an image if available.]

![image](https://github.com/artghieri/A-Introduction-to-Python-3/assets/102708433/df5f4fca-231a-4b00-abf4-6e9fb8b2e343)

You can adjust the placement of each label inside the grid cell using the `.grid()` method's `sticky` parameter. The `sticky` parameter accepts a string containing one or more of the following letters:

- "n" or "N" to align to the top center of the cell
- "e" or "E" to align to the right center side of the cell
- "s" or "S" to align to the bottom center of the cell
- "w" or "W" to align to the left center side of the cell

These letters correspond to the cardinal directions: north, south, east, and west.

For instance, setting `sticky` to "n" on both labels in the previous code positions each label at the top center of its grid cell:

```python
import tkinter as tk

window = tk.Tk()
window.columnconfigure(0, minsize=250)
window.rowconfigure([0, 1], minsize=100)

label1 = tk.Label(text="A")
label1.grid(row=0, column=0, sticky="n")

label2 = tk.Label(text="B")
label2.grid(row=1, column=0, sticky="n")

window.mainloop()
```

The output will reflect this adjustment in label placement.


![image](https://github.com/artghieri/A-Introduction-to-Python-3/assets/102708433/f0530260-2db8-4cf6-94b6-30ca1d9fa68d)


Certainly! You can combine multiple letters in a single string to position each label in a corner of its grid cell. Here's an example:

```python
import tkinter as tk

window = tk.Tk()
window.columnconfigure(0, minsize=250)
window.rowconfigure([0, 1], minsize=100)

label1 = tk.Label(text="A")
label1.grid(row=0, column=0, sticky="ne")

label2 = tk.Label(text="B")
label2.grid(row=1, column=0, sticky="sw")

window.mainloop()
```

In this instance, the `sticky` parameter of `label1` is set to "ne," which situates the label at the top right corner of its grid cell. Meanwhile, `label2` is positioned in the bottom left corner by passing "sw" to the `sticky` parameter.

The resulting window will reflect these adjustments in label positioning.

![image](https://github.com/artghieri/A-Introduction-to-Python-3/assets/102708433/8e575016-1025-4822-8cdf-eb56f3c78103)

When a widget is positioned with `sticky`, its size is only large enough to contain the text and other contents inside it. It won't fill the entire grid cell.

To fill the grid cell, you can specify "ns," which forces the widget to fill the cell in the vertical direction, or "ew" to fill the cell in the horizontal direction. To fill the entire cell, set `sticky` to "nsew."

Here's an example illustrating each of these options:

```python
import tkinter as tk

window = tk.Tk()
window.rowconfigure(0, minsize=50)
window.columnconfigure([0, 1, 2, 3], minsize=50)

label1 = tk.Label(text="1", bg="black", fg="white")
label2 = tk.Label(text="2", bg="black", fg="white")
label3 = tk.Label(text="3", bg="black", fg="white")
label4 = tk.Label(text="4", bg="black", fg="white")

label1.grid(row=0, column=0)
label2.grid(row=0, column=1, sticky="ew")
label3.grid(row=0, column=2, sticky="ns")
label4.grid(row=0, column=3, sticky="nsew")

window.mainloop()
```

The resulting output will demonstrate the impact of each sticky option on the widgets within the grid cells.


![image](https://github.com/artghieri/A-Introduction-to-Python-3/assets/102708433/865a23f6-ddc9-4bd5-9465-7ca565563740)


What the above example illustrates is that the `.grid()` geometry manager's `sticky` parameter can be employed to achieve effects similar to the `.pack()` geometry manager's `fill` parameter.

The correspondence between the `sticky` and `fill` parameters is summarized in the following table:

- `.grid()`:
  - `sticky="ns"` corresponds to `fill=tk.Y`
  - `sticky="ew"` corresponds to `fill=tk.X`
  - `sticky="nsew"` corresponds to `fill=tk.BOTH`

`.grid()` is a powerful geometry manager. It is often more straightforward to understand than `.pack()` and provides much greater flexibility than `.place()`. When creating new Tkinter applications, it's advisable to consider using `.grid()` as your primary geometry manager.

`.grid()` offers much more flexibility than demonstrated here. For instance, you can configure cells to span multiple rows and columns. For additional information, refer to the [Grid Geometry Manager](https://tkdocs.com/tutorial/grid.html) section of the [TkDocs](https://tkdocs.com/tutorial/index.html) tutorial.

Now that you've grasped the basics of Tkinter's geometry managers, the next step is to assign actions to buttons to bring your applications to life.


## Creating Interactive Applications

By this point, you likely have a solid grasp of creating windows using Tkinter, incorporating widgets, and managing application layouts – fantastic! However, it's crucial for applications not only to appear aesthetically pleasing but also to serve a functional purpose.

In this section, we will delve into the process of infusing life into your applications by executing actions in response to specific events.

### Events and Event Handlers

When developing a Tkinter application, the initiation of the event loop is imperative, and this is accomplished by calling the `window.mainloop()` method. Within the event loop, your application constantly monitors for occurring events. If an event takes place, the corresponding code can be executed in response.

The event loop is seamlessly provided by Tkinter, sparing you from the need to code event-checking mechanisms. However, the responsibility falls on you to write the code that responds to these events. Tkinter requires the creation of functions known as event handlers, which are responsible for handling the events used in your application.

So, what exactly constitutes an event, and what unfolds when an event is triggered? An event encompasses any action within the event loop that might induce specific behavior in the application, such as pressing a key or a mouse button.

Upon an event occurrence, an event object is emitted, indicating the instantiation of a class that represents the event. The creation of these event classes is automatically managed by Tkinter, relieving you of the burden of crafting them.

To gain a clearer understanding of Tkinter's event loop, let's construct our own event loop to discern its integration into your application and identify the components necessitating manual input.

Imagine a fictional scenario where there's a list named `events_list` holding event objects. Each time an event transpires, a new event object is automatically added to `events_list` in this hypothetical example.

In an infinite loop, we can continually examine if there are any event objects in `events_list`:

```python
# Assume that this list gets updated automatically
events_list = []

# Run the event loop
while True:
    # If events_list is empty, then no events have occurred, and we skip to the next iteration
    if events_list == []:
        continue

    # If execution reaches this point, there is at least one event object in events_list
    event = events_list[0]
```

Currently, our event loop doesn't perform any actions with the event. Let's modify that.

Suppose our application necessitates responding to key presses. In this case, we need to verify that the event was generated by a user pressing a key on their keyboard. If affirmative, we pass the event to an event handler function designed for key presses.

Let's assume that the `event` object has a `.type` attribute set to the string "keypress" if it represents a keypress event and a `.char` attribute containing the character of the pressed key.

Now, let's introduce a `handle_keypress()` function and update our event loop:

```python
events_list = []

# Create an event handler
def handle_keypress(event):
    """Print the character associated with the pressed key"""
    print(event.char)

while True:
    if events_list == []:
        continue
    event = events_list[0]
    # If the event is a keypress event object
    if event.type == "keypress":
        # Call the keypress event handler
        handle_keypress(event)
```

When you invoke Tkinter’s `window.mainloop()` method, a loop similar to the one described above is executed for you. `mainloop()` takes care of two critical aspects of the loop: it manages a list of occurred events and executes an event handler each time a new event is added to that list.

Let's enhance our event loop by utilizing `window.mainloop()` instead of our custom loop:

```python
import tkinter as tk

# Create a window object
window = tk.Tk()

# Create an event handler
def handle_keypress(event):
    """Print the character associated with the pressed key"""
    print(event.char)

# Run the event loop
window.mainloop()
```

Although `.mainloop()` simplifies many aspects, there's a crucial element missing in the provided code. How does Tkinter determine when to utilize `handle_keypress()`? Tkinter widgets employ a `.bind()` method precisely for this purpose.

### The .bind() Method: Enabling Event Handling

To invoke an event handler whenever an event occurs on a widget, utilize the widget’s `.bind()` method. This method establishes a binding between the event and the corresponding event handler, triggering the handler each time the event takes place.

Continuing with the keypress example from the previous section, let’s apply `.bind()` to associate `handle_keypress()` with the keypress event:

```python
import tkinter as tk

window = tk.Tk()

def handle_keypress(event):
    """Print the character associated with the pressed key"""
    print(event.char)

# Bind keypress event to handle_keypress()
window.bind("<Key>", handle_keypress)

window.mainloop()
```

Here, `handle_keypress()` is bound to a "<Key>" event using the `window.bind()` method. Each time a key is pressed during the application's runtime, the corresponding character will be printed.

`.bind()` consistently requires two arguments:

1. An event, represented as a string of the form "<event_name>", where `event_name` can be any of Tkinter’s events.
2. An event handler, denoting the function to be called upon the event occurrence.

The event handler is bound to the widget on which `.bind()` is applied. When the handler is invoked, the event object is passed to the event handler function.

In the given example, the event handler is attached to the window itself, but you have the flexibility to bind an event handler to any widget in your application. For instance, you can associate an event handler with a Button widget, enabling it to execute a specific action upon button press:

```python
def handle_click(event):
    print("The button was clicked!")

button = tk.Button(text="Click me!")
button.bind("<Button-1>", handle_click)
```

In this scenario, the "<Button-1>" event on the button widget is linked to the `handle_click` event handler. This event occurs whenever the left mouse button is pressed while positioned over the widget. Other mouse button click events include "<Button-2>" for the middle mouse button (if available) and "<Button-3>" for the right mouse button.

For a comprehensive list of commonly used events, refer to the Event types section of the Tkinter 8.5 reference.

While `.bind()` provides a versatile method to attach event handlers to widgets, for button clicks, a more straightforward approach exists using the Button widget’s `command` attribute.


### The command Attribute

Each Button widget in Tkinter comes equipped with a `command` attribute that can be linked to a function. When the associated button is pressed, the assigned function is automatically executed.

Let’s examine an example to illustrate this concept. Initially, we will create a window featuring a Label widget displaying a numerical value. Two buttons, positioned on the left and right of the label, will be employed. The left button is designed to decrease the displayed value in the Label, while the right one increases it.

Here's the code for creating the window:

```python
import tkinter as tk

window = tk.Tk()

window.rowconfigure(0, minsize=50, weight=1)
window.columnconfigure([0, 1, 2], minsize=50, weight=1)

btn_decrease = tk.Button(master=window, text="-")
btn_decrease.grid(row=0, column=0, sticky="nsew")

lbl_value = tk.Label(master=window, text="0")
lbl_value.grid(row=0, column=1)

btn_increase = tk.Button(master=window, text="+")
btn_increase.grid(row=0, column=2, sticky="nsew")

window.mainloop()
```

The resulting window will appear as follows:

![image](https://github.com/artghieri/A-Introduction-to-Python-3/assets/102708433/f38bfb72-b152-4a06-a64e-e1ef049c9334)

Now that the application layout is defined, let's infuse life into it by assigning commands to the buttons.

Beginning with the left button, when it is pressed, the intention is to decrease the value in the label by 1. To achieve this, there are two essential tasks: understanding how to retrieve the text from a Label and how to update the text within it.

Unlike Entry and Text widgets, Label widgets lack a `.get()` method. However, you can access the text from the label using dictionary-style subscript notation:

```python
label = tk.Label(text="Hello")
# Retrieve a Label's text
text = label["text"]
# Set new text for the label
label["text"] = "Goodbye"
```

Now, equipped with the knowledge of fetching and modifying a label's text, let’s create a function `increase()` that elevates the value in `lbl_value` by 1:

```python
def increase():
    value = int(lbl_value["text"])
    lbl_value["text"] = f"{value + 1}"
```

The `increase()` function extracts the text from `lbl_value`, converts it to an integer using `int()`, increments this value by 1, and sets the label’s text attribute to this updated value.

Similarly, we need a `decrease()` function to decrement the value in `lbl_value` by 1:

```python
def decrease():
    value = int(lbl_value["text"])
    lbl_value["text"] = f"{value - 1}"
```

Ensure to place the `increase()` and `decrease()` functions in your code immediately after the import statement.

To associate the buttons with these functions, assign the respective function to each button’s `command` attribute during instantiation. For example, to link the `increase()` function to `btn_increase`, update the button instantiation line as follows:

```python
btn_increase = tk.Button(master=window, text="+", command=increase)
```

Similarly, assign the `decrease()` function to `btn_decrease`:

```python
btn_decrease = tk.Button(master=window, text="-", command=decrease)
```

By binding the buttons to the `increase()` and `decrease()` functions through the `command` attribute, your program becomes fully functional. Save your changes and run the application to witness the interactive behavior in action!

Here's the full code for your reference:

```python
import tkinter as tk

def increase():
    value = int(lbl_value["text"])
    lbl_value["text"] = f"{value + 1}"

def decrease():
    value = int(lbl_value["text"])
    lbl_value["text"] = f"{value - 1}"

window = tk.Tk()

window.rowconfigure(0, minsize=50, weight=1)
window.columnconfigure([0, 1, 2], minsize=50, weight=1)

btn_decrease = tk.Button(master=window, text="-", command=decrease)
btn_decrease.grid(row=0, column=0, sticky="nsew")

lbl_value = tk.Label(master=window, text="0")
lbl_value.grid(row=0, column=1)

btn_increase = tk.Button(master=window, text="+", command=increase)
btn_increase.grid(row=0, column=2, sticky="nsew")

window.mainloop()
```

While this app may not have a specific purpose, the skills you've acquired here are fundamental and applicable to any application you create:

- Use widgets to craft user interface components.
- Employ geometry managers to regulate the layout of the application.
- Develop functions that interact with various components to capture and manipulate user input.

In the upcoming sections, you will apply these skills to construct more practical applications: a temperature converter that transforms Fahrenheit to Celsius and a text editor capable of opening, editing, and saving text files.

## Example App: Temperature Converter

Let's build the Temperature Converter app step by step. Open up IDLE's script window and follow along. Before we dive into the code, let's design the app with three essential elements:

1. An Entry widget called `ent_temperature` to input the Fahrenheit value.
2. A Label widget called `lbl_result` to display the Celsius result.
3. A Button widget called `btn_convert` that, when clicked, reads the value from `ent_temperature`, converts it from Fahrenheit to Celsius, and sets the text of `lbl_result` to the result.

We'll arrange these widgets in a grid with a single row and one column for each widget. However, for a more user-friendly interface, we'll add helpful labels to clarify the purpose of each element.

Let's enhance the design of the Temperature Converter app as described. We'll add labels to provide helpful information to the user and improve the visual appeal of the interface. Specifically:

1. A label directly to the right of the `ent_temperature` widget containing the ℉ symbol.
2. Give `btn_convert` a visual flair by setting its text to "\N{RIGHTWARDS BLACK ARROW}".
3. Ensure that `lbl_result` always displays the ℃ symbol "\N{DEGREES CELSIUS}" at the end.

Here’s what the final window will look like:


![image](https://github.com/artghieri/A-Introduction-to-Python-3/assets/102708433/639af9ea-5348-48b1-b84b-e070fd4d9b81)

Let's start coding the Temperature Converter app by creating the necessary widgets and defining their relationships. We'll import the `tkinter` module, create a new window, and set its title. Then, we'll set up the `ent_temperature` widget with a label (`lbl_temp`) and place them within a frame (`frm_entry`) for organization.

```python
import tkinter as tk

# Step 1: Create the main window
window = tk.Tk()
window.title("Temperature Converter")

# Step 2: Create and organize widgets
frm_entry = tk.Frame(master=window)
ent_temperature = tk.Entry(master=frm_entry, width=10)
lbl_temp = tk.Label(master=frm_entry, text="\N{DEGREE FAHRENHEIT}")
```

Here, `ent_temperature` is where the user will input the Fahrenheit value, and `lbl_temp` is a label for `ent_temperature`, displaying the ℉ symbol. `frm_entry` acts as a container, grouping `ent_temperature` and `lbl_temp` together.

Continuing with the setup of the Temperature Converter app, we want to position `lbl_temp` directly to the right of `ent_temperature`. This can be achieved by using the `.grid()` geometry manager on `frm_entry` with one row and two columns. Here's the code for this part:

```python
ent_temperature.grid(row=0, column=0, sticky="e")
lbl_temp.grid(row=0, column=1, sticky="w")
```

In this snippet, the `sticky` parameter is set to "e" for `ent_temperature` to ensure it always sticks to the right-most edge of its grid cell. For `lbl_temp`, setting `sticky` to "w" ensures it remains stuck to the left-most edge of its grid cell. This positioning ensures that `lbl_temp` is always immediately to the right of `ent_temperature`.

Now, let's create `btn_convert` and `lbl_result` to handle the conversion and display the results:

```python
btn_convert = tk.Button(
    master=window,
    text="\N{RIGHTWARDS BLACK ARROW}"
)
lbl_result = tk.Label(master=window, text="\N{DEGREE CELSIUS}")
```

Both `btn_convert` and `lbl_result` are assigned to the `window`. These three widgets collectively form the main application grid. We will use `.grid()` to lay them out:

```python
frm_entry.grid(row=0, column=0, padx=10)
btn_convert.grid(row=0, column=1, pady=10)
lbl_result.grid(row=0, column=2, padx=10)
```

This organization establishes the basic structure of the Temperature Converter app. Now, we can proceed with the implementation of the conversion functionality.

To finalize the Temperature Converter app and make the conversion button functional, follow these steps:

Add a function called `fahrenheit_to_celsius()` just below the import line. This function reads the value from `ent_temperature`, converts it from Fahrenheit to Celsius, and displays the result in `lbl_result`:

```python
def fahrenheit_to_celsius():
    """Convert the value from Fahrenheit to Celsius and insert the result into lbl_result."""
    fahrenheit = ent_temperature.get()
    celsius = (5/9) * (float(fahrenheit) - 32)
    lbl_result["text"] = f"{round(celsius, 2)} \N{DEGREE CELSIUS}"
```

Go to the line where you define `btn_convert` and set its `command` parameter to `fahrenheit_to_celsius`:

```python
btn_convert = tk.Button(
    master=window,
    text="\N{RIGHTWARDS BLACK ARROW}",
    command=fahrenheit_to_celsius  # Add this line
)
```

Finally, run the application:

```python
window.mainloop()
```

Now, the button will trigger the conversion when clicked, thanks to the `fahrenheit_to_celsius()` function. With just 26 lines of code, you've created a fully functional temperature converter app! Great job!

Here’s the full script for your reference:

```python
import tkinter as tk

def fahrenheit_to_celsius():
    """Convert the Fahrenheit value to Celsius and insert the result into lbl_result."""
    fahrenheit = ent_temperature.get()
    celsius = (5/9) * (float(fahrenheit) - 32)
    lbl_result["text"] = f"{round(celsius, 2)} \N{DEGREE CELSIUS}"

# Set up the window
window = tk.Tk()
window.title("Temperature Converter")
window.resizable(width=False, height=False)

# Create the Fahrenheit entry frame with an Entry
# widget and label in it
frm_entry = tk.Frame(master=window)
ent_temperature = tk.Entry(master=frm_entry, width=10)
lbl_temp = tk.Label(master=frm_entry, text="\N{DEGREE FAHRENHEIT}")

# Layout the temperature Entry and Label in frm_entry
# using the .grid() geometry manager
ent_temperature.grid(row=0, column=0, sticky="e")
lbl_temp.grid(row=0, column=1, sticky="w")

# Create the conversion Button and result display Label
btn_convert = tk.Button(
    master=window,
    text="\N{RIGHTWARDS BLACK ARROW}",
    command=fahrenheit_to_celsius
)
lbl_result = tk.Label(master=window, text="\N{DEGREE CELSIUS}")

# Set up the layout using the .grid() geometry manager
frm_entry.grid(row=0, column=0, padx=10)
btn_convert.grid(row=0, column=1, pady=10)
lbl_result.grid(row=0, column=2, padx=10)

# Run the application
window.mainloop()
```
