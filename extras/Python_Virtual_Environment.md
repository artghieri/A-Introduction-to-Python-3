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

## 

### Running Pip as a Module

When using your system's `pip` directly, the command may not indicate the Python version it is associated with. This ambiguity can lead to packages being installed in the `site-packages` directory of an unintended Python version. To avoid this, it is recommended to run `pip` as a Python module using the following command:  

```bash
python3 -m pip
```  

The `-m` switch instructs Python to run a module as an executable using the `python3` interpreter. This ensures that the pip command is executed with your system's default Python 3 version. For more details about this approach, you can read Brett Cannon’s insightful article on [the advantages of using python3 -m pip](https://snarky.ca/why-you-should-use-python-m-pip/).  

In some cases, you may want to limit package installations to a specific project. To achieve this, you should use pip within a **virtual environment**.  

## 

### Using pip in a Python Virtual Environment

To avoid installing packages directly into your system Python installation and to maintain project independence, it’s highly recommended to use a virtual environment. A virtual environment provides an isolated Python interpreter and package directory for your project. This setup ensures that your project’s dependencies remain separate from both the system environment and other projects.  

Using `pip` within a virtual environment offers several benefits:  

1. Ensures that the correct Python version is used for your project.  
2. Guarantees that the appropriate `pip` instance is referenced.  
3. Allows you to manage specific package versions without impacting other projects.  

Python 3 includes the built-in [venv](https://docs.python.org/3/library/venv.html) module, which simplifies the creation of virtual environments. Once activated, the environment isolates your installed packages, ensuring no overlap with other environments or the system-wide installation.  

Follow these steps to create and activate a virtual environment, then verify the pip installation:  

### **Windows:**  
```bash  
python3 -m venv venv  
.\venv\Scripts\activate  
(venv) pip --version  
```  

### **Linux/macOS:**  
```bash  
python3 -m venv venv  
source venv/bin/activate  
(venv) pip3 --version  
```  

Here, a virtual environment named `venv` is created using Python’s built-in `venv` module. The environment is activated with the `activate` command, as indicated by the `(venv)` prefix in the shell prompt.  

Finally, check the versions of `pip` or `pip3` within the activated virtual environment. Both commands refer to the same pip module, allowing you to use either interchangeably once the environment is active.  

## 

### Upgrading pip to the Latest Version

Before proceeding, ensure that you have the latest version of `pip` installed. You can do this by running the following command in your terminal:  

```bash
python3 -m pip install --upgrade pip
```  

Press `Enter` to execute the command. If an updated version is available, it will be downloaded and installed. Otherwise, you will see a message like "Requirement already satisfied," indicating that you already have the latest version.  

## 

### Listing All Installed Packages

To view a list of all the packages installed on your system, run the following command in your terminal:  

```bash
python3 -m pip list
```  

If you haven’t installed any additional packages, the output should look something like this:  

```
Package    Version  
---------- -------  
pip        19.3.1  
setuptools 41.2.0  
```  

In this example, `pip` and `setuptools` are listed. `pip` is itself a package manager, while `setuptools` is a library used by `pip` for setting up and installing other packages.  

This command is particularly useful for checking the packages currently installed and their corresponding versions on your system.  

## 

### Using the Python Package Index (PyPI)

One of the many packages hosted on PyPI is `requests`. The `requests` library simplifies interaction with web services by abstracting the complexities of [HTTP](https://en.wikipedia.org/wiki/Hypertext_Transfer_Protocol) requests. You can learn more about `requests` in its official [documentation](https://requests.readthedocs.io/).  

To use the `requests` package in your project, you must first install it into your Python environment. If you want to avoid installing it globally in your system’s Python site-packages, consider creating a virtual environment as explained earlier.  

Once your virtual environment is created and activated, the command-line prompt will display the environment's name in parentheses, indicating that any `pip` commands you run will operate within this environment.  

To install a package, `pip` provides the `install` command. Use it to install the `requests` package as follows:  

```bash  
python3 -m pip install requests  
```  

During the installation process, you’ll see output similar to this:  

```bash  
Collecting requests  
  Downloading https://.../requests-2.22.0-py2.py3-none-any.whl (57kB)  
  |................................| 61kB 2.0MB/s  
Collecting urllib3!=1.25.0,!=1.25.1,<1.26,>=1.21.1  
  Downloading https://...urllib3-1.25.7-py2.py3-none-any.whl (125kB)  
  |................................| 133kB 3.3MB/s  
Collecting certifi>=2017.4.17  
  Downloading https://...certifi-2019.11.28.py3-none-any.whl (156kB)  
  |................................| 163kB ...  
Collecting chardet<3.1.0,>=3.0.2  
  Downloading https://...chardet-3.0.4-py2.py3-none-any.whl (133kB)  
  |................................| 143kB 6.8MB/s  
Collecting idna<2.9,>=2.5  
  Downloading https://...idna-2.8-py2.py3-none-any.whl (58kB)  
  |................................| 61kB 3.8MB/s  
Installing collected packages: urllib3, certifi, chardet, idna, requests  
Successfully installed certifi-2019.11.28 chardet-3.0.4 idna-2.8 requests-2.22.0 urllib3-1.25.7  
```  

Here, `pip` looks for the package in PyPI, resolves its dependencies, and installs everything necessary for `requests` to function in your environment.  

By default, the `pip install <package>` command retrieves and installs the latest version of the specified package. It also checks for dependencies listed in the package metadata and installs them to ensure compatibility.  

After installation, you can verify that `requests` and its dependencies have been installed by running the `pip list` command. The version numbers may vary depending on the latest available releases.  

## 

### Using a Custom Package Index

By default, `pip` uses PyPI as its package index. However, `pip` also allows you to specify a custom package index, which can be useful in several scenarios:

- When the PyPI domain is blocked on your network.
- If you need to work with private packages not publicly available.
- For environments where system administrators maintain an internal package index to control available package versions.

To function with `pip`, a custom package index must adhere to the [PEP 503 – Simple Repository API](https://peps.python.org/pep-0503/). You can explore the structure of this API by visiting the [PyPI Simple Index](https://pypi.org/simple/). Be aware that this page contains a large amount of raw, hard-to-parse content. Custom indexes following this API can be specified using the `--index-url` option or its shorthand `-i`.

## 

### Installing from a Custom Index

For example, to install the `rptree` tool from the [TestPyPI](https://test.pypi.org) index, use:

```bash
(venv) C:\> python -m pip install -i https://test.pypi.org/simple/ rptree
```

Here, `-i` instructs `pip` to use TestPyPI instead of the default PyPI index. TestPyPI is particularly useful for testing the publishing process of your Python packages without affecting the production PyPI.

##

### Setting a Permanent Custom Index

To permanently use a custom index, configure `pip` via its settings file (`pip.conf`). Identify its location using:

```bash
(venv) C:\> python -m pip config list -vv
```

Once you locate the configuration file, add the following:

```plaintext
# pip.conf
[global]
index-url = https://test.pypi.org/simple/
```

With this setup, `pip` will default to the specified index, eliminating the need to repeatedly use `--index-url` in commands.

## 

### Installing Packages from GitHub Repositories

`pip` also supports installing packages directly from GitHub or other Git repositories. For instance, you can install the `rptree` package directly from its repository:

```bash
(venv) C:\> python -m pip install git+https://github.com/realpython/rptree
```

This uses the `git+https` scheme to fetch the package. You can verify its installation in an interactive Python session:

```python
>>> import rptree
>>> rptree.__version__
"x.y.z"
```

Installing from Git repositories is especially useful for accessing packages not hosted on PyPI or for using custom or pre-release versions directly from source.

## 

### Editable Mode Installation for Development

When developing your own package, you can install it in **editable mode**. This allows you to work on the package source while using it in your environment. The typical workflow involves cloning the repository, setting up a virtual environment, and installing the package as editable:

```bash
C:\> git clone https://github.com/realpython/rptree
C:\> cd rptree
C:\rptree> python3 -m venv venv
C:\rptree> venv\Scripts\activate.bat
(venv) C:\rptree> python -m pip install -e .
```

Here’s what each step does:
1. Clone the repository.
2. Change to the package directory.
3. Create and activate a virtual environment.
4. Install the package in editable mode with `pip install -e .`.

Installing in editable mode links the package source directory to your environment’s `site-packages`, allowing real-time updates as you modify the code.

## 

### Installing Specific Package Versions

You can control package versions during installation using version specifiers:

1. **Latest version greater than or equal to a specific version**:
   ```bash
   $ python3 -m pip install requests>=2.0
   ```

2. **Latest version less than or equal to a specific version**:
   ```bash
   $ python3 -m pip install requests<=3.0
   ```

3. **An exact version**:
   ```bash
   $ python3 -m pip install requests==2.25.0
   ```

Specifiers:
- `>=`, `<=`: Inclusive greater than or less than.
- `<`, `>`: Exclusive greater than or less than.
- `==`: Exact version.

These options ensure precise dependency management across projects.

##

### Viewing Package Details

To get detailed information about an installed package, use:

```bash
$ python3 -m pip show requests
```

Sample output:

```plaintext
Name: requests
Version: 2.22.0
Summary: Python HTTP for Humans.
Home-page: http://python-requests.org
Author: Kenneth Reitz
Author-email: me@kennethreitz.org
License: Apache 2.0
Location: c:\users\David\...\python\python38-32\lib\site-packages
Requires: chardet, idna, certifi, urllib3
Required-by:
```

This output provides key details, including dependencies (`Requires`) and installation location, enabling you to manage and debug your Python environments more effectively.

##

### Uninstalling Packages With pip

Occasionally, you'll need to uninstall a package. This might happen because you've found a better library or simply no longer need the package. While the process is straightforward, dependencies can make it slightly more complex.

#### Inspect Dependencies Before Uninstalling

When you installed `requests`, `pip` also installed its dependencies. As you add more packages to your environment, some of these dependencies may be shared by multiple libraries. To avoid breaking your environment, always inspect a package's dependency tree before uninstalling it.

Use the `pip show` command to gather details about a package:

```bash
(venv) $ python3 -m pip show requests

Name: requests
Version: 2.26.0
Summary: Python HTTP for Humans.
Home-page: https://requests.readthedocs.io
Author: Kenneth Reitz
Author-email: me@kennethreitz.org
License: Apache 2.0
Location: .../python3.9/site-packages
Requires: certifi, idna, charset-normalizer, urllib3
Required-by:
```

Here, the `Requires` field lists the dependencies of `requests`, and the `Required-by` field shows packages that depend on `requests`. Since no packages depend on `requests`, it's safe to uninstall it.

Repeat the `pip show` command for the dependencies listed in `Requires` to ensure that no other packages rely on them.

## 

### Uninstalling Packages

Once you've confirmed the dependency tree, use the `pip uninstall` command to remove the package:

```bash
(venv) $ python3 -m pip uninstall requests
```

`pip` will display the files to be removed and prompt for confirmation. If you're certain about uninstalling the package, use the `-y` switch to skip the confirmation dialog:

```bash
(venv) $ python3 -m pip uninstall urllib3 -y
```

## 

### Uninstalling Multiple Packages

You can uninstall multiple packages in a single command:

```bash
(venv) $ python3 -m pip uninstall -y charset-normalizer idna requests
```

Here, the `-y` switch suppresses the confirmation prompts for each package.

If you have a list of packages in a `requirements.txt` file, you can uninstall them all at once:

```bash
(venv) $ python3 -m pip uninstall -r requirements.txt -y
```

This is especially useful for decluttering your environment or resetting dependencies for a project.

## 

### Virtual Environments and System Installations

When using a virtual environment, it might be easier to create a new environment and reinstall only the necessary packages rather than manually uninstalling unused ones. However, `pip uninstall` is invaluable for removing packages from your **system-wide Python installation**. This helps clean up your system and prevents accidental clutter caused by globally installed packages.

## 

### Tips for Safe Uninstallation

1. **Inspect dependencies**: Always check the `Requires` and `Required-by` fields of a package to avoid breaking other installations.
2. **Use virtual environments**: They isolate dependencies, making cleanup and maintenance easier.
3. **Uninstall dependencies**: After uninstalling a package, consider removing its unused dependencies.
4. **Backup requirements**: Before major changes, export your package list with `pip freeze > requirements.txt`.

By following these guidelines, you can manage your Python environment effectively and avoid potential issues caused by broken dependencies.

##

### Exploring Alternatives to pip

While `pip` is the default package manager for Python, there are several other tools available that provide enhanced functionality and simplify package management. Here are some of the most popular alternatives:

| Tool    | Description             |
|---------|-------------------------|
| [**Conda**](https://conda.io/en/latest/)        | **Conda** is a package, dependency, and environment manager for multiple languages, including Python. Originating from [Anaconda](https://www.anaconda.com/), Conda is particularly popular in the data science and [machine learning](https://realpython.com/python-windows-machine-learning-setup/) communities. It has its own [package index](https://repo.continuum.io/) to host compatible packages and is widely used for managing complex environments.                                                                                                           |
| [**Poetry**](https://python-poetry.org/)        | **Poetry** is a modern package management tool that will feel familiar if you're coming from JavaScript and [npm](https://www.npmjs.com/). Poetry not only manages packages but also helps with building and distributing Python applications, making it an all-in-one solution for dependency management, packaging, and deployment to PyPI. You can learn more about it in the guide on [dependency management with Poetry](https://realpython.com/dependency-management-python-poetry/). |
| [**Pipenv**](https://github.com/pypa/pipenv)    | **Pipenv** merges virtual environment management and package management into a single tool. It automatically creates and manages a virtual environment for your projects, ensuring that the right dependencies are installed. To learn more, check out [Pipenv: A Guide to the New Python Packaging Tool](https://realpython.com/pipenv-guide/).                                                                                                           |
