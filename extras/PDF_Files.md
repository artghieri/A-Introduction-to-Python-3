## Creating and Modifying PDF Files

The Portable Document Format (PDF) stands out as one of the most widely used formats for document sharing over the internet. PDF files have the capability to encapsulate text, images, tables, forms, and even multimedia elements such as videos and animations, all within a single file.

The diverse range of content types that PDFs can encompass sometimes poses challenges when working with them. Opening a PDF file involves decoding a plethora of data. Fortunately, the Python ecosystem offers excellent packages specifically designed for reading, manipulating, and creating PDF files.

### Extracting Text from a PDF

In this section, you will discover how to read a PDF file and extract its text using the PyPDF2 package. To begin, ensure you have [PyPDF2](https://pypi.org/project/PyPDF2/) installed by executing the following pip command:

```bash
$ python3 -m pip install PyPDF2
```

Verify the successful installation by running the following command in your terminal:

```bash
$ python3 -m pip show PyPDF2
Name: PyPDF2
Version: 1.26.0
Summary: PDF toolkit
Home-page: http://mstamy2.github.com/PyPDF2
Author: Mathieu Fenniak
Author-email: biziqe@mathieu.fenniak.net
License: UNKNOWN
Location: c:\users\david\python38-32\lib\site-packages
Requires:
Required-by:
```

Ensure that the version information matches the latest release (at the time of writing, it is version 1.26.0). Pay attention to this detail, and if you have IDLE open, restart it to enable the use of the PyPDF2 package.

Now that PyPDF2 is installed, let's delve into working with PDF files!

### Opening a PDF File

To begin, let's open a PDF file and retrieve information from it. We will utilize the "Pride_and_Prejudice.pdf" file.

Open the IDLE's interactive window and import the PdfFileReader class from the PyPDF2 package:

```python
>>> from PyPDF2 import PdfFileReader
```

> ***Note:* If you haven't done so yet, you can obtain the exercise solutions and practice files [here](https://github.com/artghieri/A-Introduction-to-Python-3/blob/main/files/Pride_and_Prejudice.pdf).*

Creating a new instance of the PdfFileReader class requires specifying the path to the PDF file you want to open. Let's obtain that path using the pathlib module:

```python
>>> from pathlib import Path
>>> pdf_path = (
...     Path.home() /
...     "python-basics-exercises" /
...     "ch13-interact-with-pdf-files" /
...     "practice_files" /
...     "Pride_and_Prejudice.pdf"
... )
```

Now, the `pdf_path` variable contains the path to a PDF version of Jane Austen’s Pride and Prejudice.

> ***Note:* You might need to adjust pdf_path to match the location of the "python-basics-exercises/" folder on your computer.*

Next, create the PdfFileReader instance:

```python
>>> pdf = PdfFileReader(str(pdf_path))
```

The `pdf_path` is converted to a string because PdfFileReader doesn’t support reading directly from a pathlib.Path object.

As a reminder from **File Input and Output**, it's essential to close all open files before a program terminates. However, the PdfFileReader object takes care of this automatically, so you don't need to worry about manually opening or closing the PDF file!

Now that you've instantiated a PdfFileReader, you can extract information about the PDF. For instance, the `.getNumPages()` method provides the number of pages in the PDF file:

```python
>>> pdf.getNumPages()
234
```

The "Pride_and_Prejudice.pdf" file consists of 234 pages.

It's worth noting that `.getNumPages()` is written in camelCase, not snake_case, in accordance with [PEP8](https://pep8.org). However, PEP8 is a set of guidelines, not strict rules. In Python, camelCase is acceptable.

PyPDF2 is a derivative of the PyPDF package, which was developed in 2005, just four years after the publication of PEP 8. During that time, many Python programmers were transitioning from languages where camelCase is more prevalent.

You can also access document information using the `.documentInfo` attribute:

```python
>>> pdf.documentInfo
{'/Title': 'Pride and Prejudice, by Jane Austen', '/Author': 'Chuck', '/Creator':...}
```

While the object returned by `.documentInfo` resembles a dictionary, it's not exactly the same. Each item in `.documentInfo` can be accessed as an attribute. For example, to retrieve the title, use the `.title` attribute:

```python
>>> pdf.documentInfo.title
'Pride and Prejudice, by Jane Austen'
```

The `.documentInfo` object contains the PDF **metadata**, which is set when a PDF is created.

In summary, the PdfFileReader class serves as the gateway to working with PDF files in Python, providing the necessary methods and attributes to access data within a PDF file.

### Extracting Text from a Page

In PyPDF2, PDF pages are represented by the PageObject class. These instances allow you to interact with pages in a PDF file, and you can obtain them through a PdfFileReader object. Let's illustrate how to extract text from the first page of the "Pride_and_Prejudice.pdf" file.

There are two steps to extract text from a single PDF page:

1. Obtain a PageObject using `PdfFileReader.getPage()`.
2. Extract the text as a string with the `PageObject` instance’s `extractText()` method.

Given that "Pride_and_Prejudice.pdf" has 243 pages with indices ranging from 0 to 242, you can get an object representing a specific page by passing the page’s index to the `PdfFileReader.getPage()` method:

```python
>>> first_page = pdf.getPage(0)
```

The `.getPage()` method returns a `PageObject`:

```python
>>> type(first_page)
<class 'PyPDF2.pdf.PageObject'>
```

Now, you can extract the page’s text with the `PageObject.extractText()` method:

```python
>>> first_page.extractText()
'\n \nThe Project Gutenberg EBook of Pride and Prejudice, by Jane Austen\n \n\nThis eBook is for the use of anyone anywhere at no cost and with\n \nalmost no restrictions whatsoever. You may copy it, give it away or\n \nre\n-\nuse it under the terms of the Project Gutenberg License included\n \nwith this eBook or online at www.gutenberg.org\n \n \n \nTitle: Pride and Prejudice\n \n\nAuthor: Jane Austen\n \n \nRelease Date: August 26, 2008 [EBook #1342]\n\n[Last updated: August 11, 2011]\n \n \nLanguage: Eng\nlish\n \n \nCharacter set encoding: ASCII\n \n \n*** START OF THIS PROJECT GUTENBERG EBOOK PRIDE AND PREJUDICE ***\n \n \n \n \n \nProduced by Anonymous Volunteers, and David Widger\n \n \n \n \n \n \n \nPRIDE AND PREJUDICE \n \n \nBy Jane Austen \n \n\n \n \nContents\n \n'
```

Note that the output displayed here has been formatted for better readability on this page. The output you observe on your computer may be formatted differently.

To extract all the text from the entire PDF, you'll need a way to iterate over all the pages in the document. Every PdfFileReader object has a `.pages` attribute, which provides an iterable of PageObject objects for each page in the PDF. This iterable is ordered, so the first PageObject corresponds to the first page of the PDF, the second PageObject to the second page, and so forth.

Here’s how you can use a for loop to iterate over all the pages in the PDF and print their text:

```python
for page in pdf.pages:
    print(page.extractText())
```

Now, let's combine everything you’ve learned and write a program that extracts all the text from the "Pride_and_Prejudice.pdf" file and saves it to a .txt file.

### Putting It All Together

Open a new script window in IDLE and type out the following script:

```python
from pathlib import Path
from PyPDF2 import PdfFileReader

# Change the path below to the correct path for your computer.
pdf_path = (
    Path.home() /
    "python-basics-exercises" /
    "ch13-interact-with-pdf-files" /
    "practice-files" /
    "Pride_and_Prejudice.pdf"
)

# 1
pdf_reader = PdfFileReader(str(pdf_path))
output_file_path = Path.home() / "Pride_and_Prejudice.txt"

# 2
with output_file_path.open(mode="w") as output_file:
    # 3
    output_file.write(
        f"{pdf_reader.documentInfo.title}\n"
        f"Number of pages: {pdf_reader.getNumPages()}\n\n"
    )

    # 4
    for page in pdf_reader.pages:
        text = page.extractText()
        output_file.write(text)
```

Now, let’s break down the script:

1. A new PdfFileReader instance is assigned to the `pdf_reader` variable, and a new Path object for the file "Pride_and_Prejudice.txt" in your home directory is assigned to the `output_file_path` variable.
2. The script opens the `output_file_path` in write mode.
3. Inside the `with` block, the PDF title and the number of pages are written to the text file using `output_file.write()`.
4. Following that, each PageObject in the `pdf_reader.pages` iterable is looped over in a `for` loop. At each step, the text from each page is extracted with `page.extractText()` and written to the `output_file`.

When you save and run this script, a new file named "Pride_and_Prejudice.txt" containing the full text of the "Pride_and_Prejudice.pdf" document is created in your home directory. Open it up and check it out!

## Extracting Pages From a PDF

In the preceding section, you acquired the knowledge of extracting all text from a PDF file and storing it in a .txt file. Now, we'll delve into the process of extracting a single page or a range of pages from an existing PDF and subsequently saving them to a new PDF.

The `PdfFileWriter` class is employed for creating a new PDF file. Let's delve into this class and comprehend the essential steps involved in generating a PDF using PyPDF2.

### The PdfFileWriter Class 
The `PdfFileWriter` class serves the purpose of creating new PDF files. In the interactive window of IDLE, import the `PdfFileWriter` class and instantiate a new object named `pdf_writer`:

```python
>>> from PyPDF2 import PdfFileWriter
>>> pdf_writer = PdfFileWriter()
```

`PdfFileWriter` objects act as containers for pages. To craft a new PDF, you need to append `PageObject` instances to the `PdfFileWriter` and subsequently write those pages to a file.

Let’s initiate the process by adding a blank page to the `pdf_writer` object:

```python
>>> page = pdf_writer.addBlankPage(width=72, height=72)
```

The `.addBlankPage()` method incorporates a blank page into the PDF writer object. Since there are no existing pages, this becomes the first page. The parameters `width` and `height` are mandatory and determine the dimensions of the page in points, with one point equating to 1/72 inches. Consequently, the above code introduces a one-inch square blank page to `pdf_writer`.

`.addBlankPage()` returns a new `PageObject` instance representing the page added to the `PdfFileWriter`:

```python
>>> type(page)
<class 'PyPDF2.pdf.PageObject'>
>>> page
{'/Type': '/Page', '/Parent': IndirectObject(1, 0), '/Resources': {},
'/MediaBox': RectangleObject([0, 0, 72, 72])}
```

Although in this example, the `PageObject` instance returned by `.addBlankPage()` is assigned to the `page` variable, typically, this assignment is unnecessary. Usually, you call `.addBlankPage()` without assigning the return value:

```python
>>> pdf_writer.addBlankPage(width=72, height=72)
```

With at least one page added to `pdf_writer`, you can write the contents to a new PDF file. To achieve this, pass a binary write mode file object to the `PdfFileWriter.write()` method:

```python
>>> from pathlib import Path
>>> with Path("blank.pdf").open(mode="wb") as output_file:
...     pdf_writer.write(output_file)
...
>>>
```

This process generates a new file named "blank.pdf" in your current working directory. Upon opening the file with a PDF reader, such as Adobe Acrobat, you'll observe a document containing a single blank one-inch square page.

Take notice that when saving the PDF file, you utilize the PdfFileWriter object’s `.write()` method with the file object, not the file object’s `.write()` method directly. The correct approach is as follows:

```python
>>> with Path("blank.pdf").open(mode="wb") as output_file:
...     pdf_writer.write(output_file)
```

Avoid the following incorrect syntax:

```python
>>> with Path("blank.pdf").open(mode="wb" as output_file):
...     output_file.write(pdf_writer)
```

This distinction is crucial, so be cautious to prevent this mistake.

While PdfFileWriter objects can write to new PDF files, they are limited in creating new content from scratch, except for blank pages. Despite this limitation, in many scenarios, there is no need to generate entirely new content. Typically, you will work with pages extracted from PDF files opened with a PdfFileReader instance.

The example above demonstrated three key steps to create a new PDF file using PyPDF2:

1. Create a `PdfFileWriter` instance.
2. Add one or more pages to the `PdfFileWriter` instance.
3. Write to a file using the `PdfFileWriter.write()` method.

This pattern will be recurrent as you explore various methods to add pages to a `PdfFileWriter` instance.

### Extracting a Single Page From a PDF

Let’s revisit the Pride and Prejudice PDF from the previous section. In this exercise, you'll open the PDF using a `PdfFileReader` class instance, extract the first page, and create a new PDF file that includes only this single extracted page.

Open IDLE’s interactive window and import both `PdfFileReader` and `PdfFileWriter` from PyPDF2, along with the `Path` class from the `pathlib` module:

```python
>>> from pathlib import Path
>>> from PyPDF2 import PdfFileReader, PdfFileWriter
```

Now, open the "Pride_and_Prejudice.pdf" file with a `PdfFileReader` instance:

```python
>>> pdf_path = (
...     Path.home() /
...     "python-basics-exercises" /
...     "ch13-interact-with-pdf-files" /
...     "practice_files" /
...     "Pride_and_Prejudice.pdf"
... )
>>> input_pdf = PdfFileReader(str(pdf_path))
```

Remember to adjust the file path if necessary for your system.

The first page in the PDF is at index 0. Extract it as a `PageObject` by passing the argument 0 to `.getPage()`:

```python
>>> first_page = input_pdf.getPage(0)
```

Now, create a new `PdfFileWriter` instance and add the extracted page to it:

```python
>>> pdf_writer = PdfFileWriter()
>>> pdf_writer.addPage(first_page)
```

The `.addPage()` method adds a page to the set of pages in the `pdf_writer` object, similar to `.addBlankPage()`. The difference is that you must pass a `PageObject` to `.addPage()`.

Finally, write the contents of `pdf_writer` to a new file called "first_page.pdf":

```python
>>> with Path("first_page.pdf").open(mode="wb") as output_file:
...     pdf_writer.write(output_file)
...
>>>
```

You now have a new PDF file saved in your current working directory with the name "first_page.pdf," containing only the cover page of the "Pride_and_Prejudice.pdf" file. Quite neat!

### Extracting Multiple Pages From a PDF File

Using for loops, you can extract multiple pages from a PDF file and save them to a new PDF. Let’s extract the first chapter from "Pride_and_Prejudice.pdf." If you open the PDF file with a PDF viewer, you can see that the first chapter is on the second, third, and fourth pages in the PDF. Since pages are indexed starting with 0, we’ll need to extract the pages at the indices 1, 2, and 3.

Let's set everything up by importing the necessary classes and opening the PDF file:

```python
>>> from PyPDF2 import PdfFileReader, PdfFileWriter
>>> from pathlib import Path
>>> pdf_path = (
...     Path.home() /
...     "python-basics-exercises" /
...     "ch13-interact-with-pdf-files" /
...     "practice_files" /
...     "Pride_and_Prejudice.pdf"
... )
>>> input_pdf = PdfFileReader(str(pdf_path))
```

Our goal is to extract the pages at indices 1, 2, and 3, add these to a new `PdfFileWriter` instance, and then write them to a new PDF file. One way to do this is to loop over the range of numbers starting at 1 and ending at 3, extracting the page at each step of the loop and adding it to the `PdfFileWriter` instance. Here’s what that looks like in code:

```python
>>> pdf_writer = PdfFileWriter()
>>> for n in range(1, 4):
...     page = input_pdf.getPage(n)
...     pdf_writer.addPage(page)
...
>>>
```

Now `pdf_writer` has three pages added to it, which you can check with the `.getNumPages()` method:

```python
>>> pdf_writer.getNumPages()
3
```

Finally, you can write the extracted pages to a new PDF file:

```python
>>> with Path("chapter1.pdf").open(mode="wb") as output_file:
...     pdf_writer.write(output_file)
...
>>>
```

Now you can open the "chapter1.pdf" file in your current working directory to read just the first chapter of "Pride and Prejudice."

Another way to extract multiple pages from a PDF is to take advantage of the fact that the iterable returned by `PdfFileReader.pages` supports slice notation. Let’s redo the previous example using `.pages` instead of looping over a range object. Since you’ve already imported the necessary classes and set-up file paths, start by initializing a new `PdfFileWriter` object:

```python
>>> pdf_writer = PdfFileWriter()
```

Now loop over a slice of the `.pages` iterable from indices starting at 1 and ending at 3:

```python
>>> for page in input_pdf.pages[1:4]:
...     pdf_writer.addPage(page)
...
>>>
```

Recall that the values in a slice range from the item at the first index in the slice and up to, but not including, the item at the second index in the slice. So `.pages[1:4]` returns an iterable of the pages with indices 1, 2, and 3.

Finally, write the contents of `pdf_writer` to the output file:

```python
>>> with Path("chapter1_slice.pdf").open(mode="wb") as output_file:
...     pdf_writer.write(output_file)
...
>>>
```

Now open the "chapter1_slice.pdf" file in your current working directory and compare it to the "chapter1.pdf" file you made by looping over the range object. They contain the same pages!

Sometimes you need to extract every page from a PDF. You can use the methods illustrated above to do this, but PyPDF2 provides a shortcut. `PdfFileWriter` instances have an `.appendPagesFromReader()` method that is used to append pages from a `PdfFileReader` instance.

To use `.appendPagesFromReader()`, pass a `PdfFileReader` instance to its `reader` parameter. For example, the following copies every page from the "Pride and Prejudice" PDF to a `PdfFileWriter` instance:

```python
>>> # Assume pdf_reader contains the opened "Pride_and_Prejudice.pdf"
>>> pdf_writer = PdfFileWriter()
>>> pdf_writer.appendPagesFromReader(pdf_reader)
```

Now `pdf_writer` contains every page in `pdf_reader`!

## Concatenating and Merging PDFs

Two common tasks when working with PDF files are concatenating and merging several PDFs together into a single file.

**Concatenating PDFs:**  
When you concatenate two or more PDFs together, you join the files into a single document one after another. For instance, a company may concatenate several daily reports into one monthly report at the end of a month.

**Merging PDFs:**  
Merging two PDFs together also combines them into a single file, but instead of joining the second PDF at the end of the first, it can be inserted after a specific page in the first PDF, pushing all following pages in the first PDF to the end of the second one.

In this section, you’ll learn how to concatenate and merge PDFs using the PyPDF2 package’s `PdfFileMerger`.

### The PdfFileMerger Class

The `PdfFileMerger` class is similar to the `PdfFileWriter` class discussed in the previous section. Both classes are used to write PDF files. In both cases, pages are added to instances of the class and then written to a file.

The main difference is that `PdfFileWriter` can only append pages to the end of the list of pages already contained in the writer, whereas `PdfFileMerger` can insert pages at any location.

Let’s create our first `PdfFileMerger` instance. In IDLE’s interactive window, type the following:

```python
>>> from PyPDF2 import PdfFileMerger
>>> pdf_merger = PdfFileMerger()
```

First, import the `PdfFileMerger` class from the PyPDF2 package. Then, create a new `PdfFileMerger` instance and assign it to the `pdf_merger` variable. `PdfFileMerger` objects are empty when first instantiated. We’ll need to add some pages to it before we can do anything.

There are a couple of ways to add pages to the `pdf_merger` object, and how you do that depends on what you need to accomplish:

- `.append()` concatenates every page in an existing PDF document to the end of the pages currently in the `PdfFileMerger`.
- `.merge()` is used to insert all of the pages in an existing PDF document after a specific page in the `PdfFileMerger`.

We’ll look at both methods in this section, starting with `.append()`.

### Concatenating PDFs With .append()

In the Files directory, there is a subdirectory called [Expense Reports](https://github.com/artghieri/A-Introduction-to-Python-3/tree/main/files/Expense%20Reports) with three expense reports for an employee named Peter Python. Peter needs to concatenate these three PDFs together and submit them to his employer as a single PDF file for reimbursement of work-related expenses.

Let’s start by using the `pathlib` module to get a list of `Path` objects for each of the three expense reports in the `expense_reports/` folder:

```python
>>> from pathlib import Path
>>> reports_dir = (
... Path.home() /
... "python-basics-exercises" /
... "ch13-interact-with-pdf-files" /
... "practice_files" /
... "expense_reports"
... )
```

Once you have the path to the `expense_reports/` directory assigned to the `reports_dir` variable, you can use `.glob()` to get an iterable of paths to PDF files in the directory.

Let’s take a look at what’s in the directory:

```python
>>> for path in reports_dir.glob("*.pdf"):
...     print(path.name)
...
```

The names of the three files are listed, but they aren’t in order. Furthermore, the order of the files you see on your computer may not match the output shown here.

In general, the order of paths returned by `.glob()` is not guaranteed, so you’ll need to order them yourself. You can do this by creating a list containing the three file paths, and then calling the `.sort()` method on that list:

```python
>>> expense_reports = list(reports_dir.glob("*.pdf"))
>>> expense_reports.sort()
```

Recall that `.sort()` sorts a list in place, so you don’t need to assign the return value to a variable. After calling `.sort()`, the `expense_reports` list is sorted by file name in alphabetical order.

Let’s check that the sorting worked by looping over `expense_reports` again and printing out the file names:

```python
>>> for path in expense_reports:
...     print(path.name)
...
```

Now we can concatenate the three PDFs together using the `PdfFileMerger.append()` method, which requires a single string argument representing the path to a PDF file. Each path in `expense_reports/` is converted to a string with `str()` before being passed to `pdf_merger.append()`.

```python
>>> from PyPDF2 import PdfFileMerger
>>> pdf_merger = PdfFileMerger()
```

Now loop over the paths in the sorted `expense_reports` list and append them to `pdf_merger`:

```python
>>> for path in expense_reports:
...     pdf_merger.append(str(path))
...
```

With all of the PDF files in the `expense_reports/` directory concatenated together in the `pdf_merger` object, the last thing you need to do is write everything to an output PDF file. `PdfFileMerger` instances have a `.write()` method that works just like the `PdfFileWriter.write()`.

Open a new file in binary write mode, then pass the file object to `pdf_merger.write()`:

```python
>>> with Path("expense_reports.pdf").open(mode="wb") as output_file:
...     pdf_merger.write(output_file)
...
```

Now you have a PDF file called `expense_reports.pdf` in your current working directory. Open it up with a PDF reader, and you’ll find all three expense reports together in the same PDF file.

### Merging PDFs With .merge()

To merge two or more PDFs together, use the `PdfFileMerger.merge()` method. This method is similar to the `.append()` method, except that you must specify where in the output PDF to insert all of the content of the PDF you are merging.

Let’s look at an example. Google, Inc has prepared a quarterly report, but forgot to include a table of contents. Peter Python noticed the mistake and quickly created a PDF with the missing table of contents. Now he needs to merge that PDF into the original report.

The first thing you need to do is import everything you need from PyPDF2 and pathlib:

```python
>>> from pathlib import Path
>>> from PyPDF2 import PdfFileMerger
```

The report PDF and table of contents PDF can be found in the `quarterly_report/` subfolder of the Chapter 14 Practice Files folder. The report is in a file called `report.pdf`, and the table of contents is in a file `toc.pdf`.

Let’s go ahead and get the paths to both of those files:

```python
>>> report_dir = (
...     Path.home() /
...     "python-basics-exercises" /
...     "ch13-interact-with-pdf-files" /
...     "practice_files" /
...     "quarterly_report"
... )
>>> report_path = report_dir / "report.pdf"
>>> toc_path = report_dir / "toc.pdf"
```

The first thing we’ll do is append the report PDF to a new `PdfFileMerger` instance using the `.append()` method:

```python
>>> pdf_merger = PdfFileMerger()
>>> pdf_merger.append(str(report_path))
```

Now that `pdf_merger` has some pages in it, we can merge the table of contents PDF into it at the correct location. If you open the `report.pdf` file with a PDF reader, you’ll see that the first page of the report is a title page. The second is an introduction, and the remaining pages have different report sections in them.

We want to insert the table of contents after the title page and just before the introduction section. Since PDF pages are indexed starting with 0 in PyPDF2, this means that we need to insert the table of contents after the page at index 0 and before the page at index 1.

To do that, call `pdf_merger.merge()` with two arguments: first the integer 1 indicating the index of the page where the table of contents should be inserted, and second a string containing the path the PDF file for the table of contents.

Here’s what that looks like:

```python
>>> pdf_merger.merge(1, str(toc_path))
```

Every page in the table of contents PDF is inserted before the page at index 1. Since the table of contents PDF is only one page, it gets inserted at index 1 and the page currently at index 1 gets shifted to index 2, the page currently at index 2 gets shifted to index 3, and so on.

Now write the merged PDF to an output file:

```python
>>> with Path("full_report.pdf").open(mode="wb") as output_file:
...     pdf_merger.write(output_file)
...
```

You now have a `full_report.pdf` file in your current working directory. Open it up with a PDF reader and check that the table of contents was inserted at the correct spot.

Concatenating and merging PDFs are common operations. While the examples in this section are admittedly somewhat contrived, you can imagine how useful a program would be for merging thousands of PDFs or for automating routine tasks that would otherwise take a human lots of time to complete.

## Rotating and Cropping PDF Pages

So far, you’ve learned how to extract text from PDF files, extract pages, and concatenate and merge PDF files. These are all common operations with PDF files, but PyPDF2 has many other useful features.

In this section, you’ll learn how to rotate and crop pages in a PDF file.

### Rotating Pages

Let’s start by learning how to rotate pages. For this example, we’ll use the `ugly.pdf` file in the Chapter 14 Practice Files folder. The `ugly.pdf` file contains a lovely version of Hans Christian Andersen’s The Ugly Duckling, except that every odd-numbered page is rotated counterclockwise by ninety degrees.

Let’s fix that. In a new IDLE interactive window, start by importing the `PdfFileReader` and `PdfFileWriter` classes from PyPDF2, as well as the `Path` class from the `pathlib` module:

```python
from pathlib import Path
from PyPDF2 import PdfFileReader, PdfFileWriter
```

Now create a `Path` object for the `ugly.pdf` file:

```python
pdf_path = (
    Path.home() /
    "python-basics-exercises" /
    "ch13-interact-with-pdf-files" /
    "practice_files" /
    "ugly.pdf"
)
```

Finally, let’s create new `PdfFileReader` and `PdfFileWriter` instances:

```python
pdf_reader = PdfFileReader(str(pdf_path))
pdf_writer = PdfFileWriter()
```

Our goal is to create a new PDF file using `pdf_writer` that has all of the pages in the PDF rotated correctly. The even-numbered pages in the PDF are already properly oriented, but the odd-numbered pages in the PDF file are rotated counterclockwise by ninety degrees.

To correct the problem, you’ll use the `PageObject.rotateClockwise()` method. This method takes an integer argument, in degrees, and rotates a page clockwise by that many degrees. For example, `.rotateClockwise(90)` rotates a PDF page clockwise by ninety degrees.

> ***Note**: In addition to the .rotateClockwise() method, the PageObject class also has a .rotateCounterClockwise() method for rotating pages counterclockwise.*

There are several ways you can go about rotating the pages in the PDF.

We’ll discuss two different ways of rotating pages. Both of them rely on the `.rotateClockwise()` method, but they take different approaches to determining which pages get rotated.

The first method is to loop over the indices of the pages in the PDF. During each iteration, check if the index corresponds to a page that needs to be rotated and call `.rotateClockwise()` to rotate the page if needed. Then add the page to `pdf_writer`.

Here’s what that looks like:

```python
for n in range(pdf_reader.getNumPages()):
    page = pdf_reader.getPage(n)
    if n % 2 == 0:
        page.rotateClockwise(90)
    pdf_writer.addPage(page)
```

Notice that the page gets rotated if the index is even. That might seem odd because it’s the odd pages in the PDF that are rotated incorrectly. However, page numbers in the PDF start with 1, while page indices start with 0. That means odd PDF pages have even indices.

*Note: When you execute the for loop above, you’ll see a bunch of output in IDLE’s interactive window. That’s because `.rotateClockwise()` returns a `PageObject` instance. You can ignore this output for the time being. When you execute programs from IDLE’s script window, this output won’t be visible.*

Now that you’ve rotated all the pages in the PDF, you can write the content of `pdf_writer` to a new file and check that everything worked:

```python
with Path("ugly_rotated.pdf").open(mode="wb") as output_file:
    pdf_writer.write(output_file)
```

You should now have a file called `ugly_rotated.pdf` in your current working directory with the pages from the `ugly.pdf` file all rotated correctly.

The problem with the approach we just used to rotate the pages in the `ugly.pdf` file is that it depends on knowing ahead of time which pages need to be rotated. In a real-world scenario, it isn’t practical to go through an entire PDF taking note of the page numbers of pages to rotate.

In fact, you can determine which pages need to be rotated without prior knowledge. Well, sometimes you can. Let’s see how by getting a new `PdfFileReader` instance:

```python
pdf_reader = PdfFileReader(str(pdf_path))
```

We need to do this because we altered the pages in the old `PdfFileReader` by rotating them. So by creating a new instance, we’re starting fresh.

`PageObject` instances maintain a dictionary of values containing information about the page:

```python
pdf_reader.getPage(0)
```

Output:
```plaintext
{'/Contents': [IndirectObject(11, 0), IndirectObject(12, 0),
  IndirectObject(13, 0), IndirectObject(14, 0), IndirectObject(15, 0),
  IndirectObject(16, 0), IndirectObject(17, 0), IndirectObject(18, 0)],
 '/Rotate': -90, '/Resources': {'/ColorSpace': {'/CS1':
   IndirectObject(19, 0), '/CS0': IndirectObject(19, 0)}, '/XObject':
   {'/Im0': IndirectObject(21, 0)}, '/Font': {'/TT1':
   IndirectObject(23, 0), '/TT0': IndirectObject(25, 0)}, '/ExtGState':
   {'/GS0': IndirectObject(27, 0)}}, '/CropBox': [0, 0, 612, 792],
 '/Parent': IndirectObject(1, 0), '/MediaBox': [0, 0, 612, 792],
 '/Type': '/Page', '/StructParents': 0}
```

Yikes! Mixed in with all that nonsensical looking stuff is a key called `/Rotate`, which you can see on the fourth line of output above. The value of this key is -90.

You can access the `/Rotate` key on a `PageObject` using subscript notation, just like you can on a Python dict object:

```python
page = pdf_reader.getPage(0)
page["/Rotate"]
# -90
```

If you look at the `/Rotate` key for the second page in `pdf_reader`, you’ll see that it has a value of 0:

```python
page = pdf_reader.getPage(1)
page["/Rotate"]
# 0
```

What all this means is that the page at index 0 has a rotation value of -90 degrees, meaning it has been rotated ninety degrees counterclockwise. The page at index 1 has a rotation value of 0, so it has not been rotated at all.

What all this means is that the page at index 0 has a rotation value of -90 degrees, meaning it has been rotated ninety degrees counterclockwise. The page at index 1 has a rotation value of 0, so it has not been rotated at all.

If you rotate the first page using `.rotateClockwise()`, the value of `/Rotate` changes from -90 to 0:

```python
page = pdf_reader.getPage(0)
page["/Rotate"]  # Output: -90
page.rotateClockwise(90)
page["/Rotate"]  # Output: 0
```

Now that we know how to inspect the `/Rotate` key, let’s use it to rotate the pages in the `ugly.pdf` file.

The first thing we need to do is re-initialize our `pdf_reader` and `pdf_writer` objects so that we get a fresh start:

```python
pdf_reader = PdfFileReader(str(pdf_path))
pdf_writer = PdfFileWriter()
```

Now, write a loop that loops over the pages in the `pdf_reader.pages` iterable, checks the value of `/Rotate`, and rotates the page if that value is -90:

```python
for page in pdf_reader.pages:
    if page["/Rotate"] == -90:
        page.rotateClockwise(90)
    pdf_writer.addPage(page)
```

Not only is this loop slightly shorter than the loop in the first solution, but it doesn’t rely on any prior knowledge of which pages need to be rotated. You could use a loop like this to rotate pages in any PDF without ever having to open it up and look at it.

To finish out the solution, write the contents of `pdf_writer` to a new file:

```python
with Path("ugly_rotated2.pdf").open(mode="wb") as output_file:
    pdf_writer.write(output_file)
```

Now you can open the `ugly_rotated2.pdf` in your current working directory and compare it to the `ugly_rotated.pdf` you generated earlier. They should look identical.

One word of warning about the `/Rotate` key: it is not guaranteed to exist on a page.

If the `/Rotate` key doesn’t exist, this usually means that the page has not been rotated. However, that isn’t always a safe assumption. If a `PageObject` has no `/Rotate` key, then a `KeyError` is raised when you try to access it. You can catch this exception with a `try...except` block.

The value of `/Rotate` may not always be what you expect. For example, if you scan a paper document with the paper page rotated ninety degrees counterclockwise, then the contents of the PDF will appear rotated. However, the `/Rotate` key may have the value 0.

This is one of many things that can make working with PDF files frustrating. Sometimes, you will just need to open a PDF in a PDF reader program and manually figure some things out.

### Cropping Pages

A common PDF operation involves cropping pages, either to split a single page into multiple sections or to extract a specific portion such as a signature or figure. For instance, consider the file "half_and_half.pdf" within the "practice_files/" subdirectory of the "ch13-interact-with-pdf-files/" directory, containing a segment from Hans Christian Andersen’s The Little Mermaid.

Each page in this PDF consists of two columns. Our objective is to split each page into two, each dedicated to a separate column. To initiate the process, import the PdfFileReader and PdfFileWriter classes from PyPDF2, along with the Path class from the pathlib module:

```python
from pathlib import Path
from PyPDF2 import PdfFileReader, PdfFileWriter
```

Now, create a Path object for the "half_and_half.pdf" file:

```python
pdf_path = Path.home() / "python-basics-exercises" / "ch13-interact-with-pdf-files" / "practice_files" / "half_and_half.pdf"
```

Next, create a PdfFileReader object and retrieve the first page of the PDF:

```python
pdf_reader = PdfFileReader(str(pdf_path))
first_page = pdf_reader.getPage(0)
```

To crop the page, an understanding of page structure is necessary. PageObject instances, like `first_page`, possess a `.mediaBox` attribute representing a rectangular area defining page boundaries.

Let's explore the `.mediaBox` attribute using IDLE’s interactive window before proceeding with cropping:

```python
first_page.mediaBox
```

Note that the `.mediaBox` attribute returns a RectangleObject, representing a rectangular area on the page. The output, like [0, 0, 792, 612], consists of four numbers: the x- and y-coordinates of the lower-left corner, width, and height. It's important to recognize that the width and height values are in points, with one point equal to 1/72 inches.

For example, RectangleObject([0, 0, 792, 612]) signifies a rectangular region starting at the origin, with a height of 792 points (11 inches) and a width of 612 points (8.5 inches), corresponding to standard letter-sized page dimensions.

Additionally, a RectangleObject has four attributes, namely `.lowerLeft`, `.lowerRight`, `.upperLeft`, and `.upperRight`, providing coordinates of the rectangle's corners in points.

Utilize these four properties to retrieve the coordinates of each corner of the RectangleObject:

```python
first_page.mediaBox.lowerLeft  # (0, 0)
first_page.mediaBox.lowerRight  # (792, 0)
first_page.mediaBox.upperLeft  # (0, 612)
first_page.mediaBox.upperRight  # (792, 612)
```

Each property returns a tuple with the coordinates of the specified corner. Individual coordinates can be accessed using square brackets, similar to accessing elements in any other Python tuple:

```python
first_page.mediaBox.upperRight[0]  # 792
first_page.mediaBox.upperRight[1]  # 612
```

To modify the coordinates of a mediaBox, assign a new tuple to one of its properties:

```python
first_page.mediaBox.upperLeft = (0, 480)
first_page.mediaBox.upperLeft  # (0, 480)
```

When altering the .upperLeft coordinates, the .upperRight attribute adjusts automatically, maintaining a rectangular shape:

```python
first_page.mediaBox.upperRight  # (792, 480)
```

Changing the coordinates of the RectangleObject obtained from .mediaBox effectively crops the page. The `first_page` object now contains information only within the boundaries of the new RectangleObject.

Proceed to write the cropped page to a new PDF file:

```python
pdf_writer = PdfFileWriter()
pdf_writer.addPage(first_page)

with Path("cropped_page.pdf").open(mode="wb") as output_file:
    pdf_writer.write(output_file)
```

If you open the "cropped_page.pdf" file in your current working directory, you'll observe that the top portion of the page has been removed.

To crop the page and display only the text on the left side, cutting the horizontal dimensions in half, you can achieve this by modifying the `.upperRight` coordinates of the `.mediaBox` object. Follow these steps:

First, obtain new PdfFileReader and PdfFileWriter objects as we have altered the first page in `pdf_reader` and added it to `pdf_writer`:

```python
pdf_reader = PdfFileReader(str(pdf_path))
pdf_writer = PdfFileWriter()
```

Now, retrieve the first page of the PDF:

```python
first_page = pdf_reader.getPage(0)
```

To preserve the original page, work with a copy using the `copy` module:

```python
import copy
left_side = copy.deepcopy(first_page)
```

Now, alter `left_side` without changing the properties of `first_page`. This ensures the ability to use `first_page` later to extract the text on the right side of the page.

Perform the following steps to crop the page to show only the text on the left side:

```python
# Get the current coordinates of the upper right corner of the .mediaBox.
current_coords = left_side.mediaBox.upperRight

# Create a new tuple with the first coordinate equal to half of the original value.
new_coords = (current_coords[0] / 2, current_coords[1])

# Assign the new coordinates to the .upperRight property.
left_side.mediaBox.upperRight = new_coords
```

Now, the original page is cropped to contain only the text on the left side. To extract the right-hand side of the page, obtain a new copy of `first_page`:

```python
right_side = copy.deepcopy(first_page)
```

To crop the page to only the right-hand side, move the `.upperLeft` corner instead of the `.upperRight` corner:

```python
right_side.mediaBox.upperLeft = new_coords
```

Now, `right_side.mediaBox` represents a rectangle with the upper-left corner at the top center of the page and the upper-right corner at the top right of the page.

Finally, add the `left_side` and `right_side` pages to `pdf_writer` and write them to a new PDF file:

```python
pdf_writer.addPage(left_side)
pdf_writer.addPage(right_side)
with Path("cropped_pages.pdf").open(mode="wb") as output_file:
    pdf_writer.write(output_file)
```

Now, open the "cropped_pages.pdf" file with a PDF reader. You should observe a file with two pages: the first containing the text from the left-hand side of the original first page, and the second containing the text from the original right-hand side.

## Encrypting and Decrypting PDFs

Occasionally, PDF files come with password protection. The PyPDF2 package facilitates working with encrypted PDF files and adding password protection to existing PDFs.

To work with password-protected PDFs, PyPDF2 provides functionality for both encryption and decryption. 


### PDF Encryption

The `.encrypt()` method of a `PdfFileWriter()` instance is employed to apply password protection to a PDF file, with two primary parameters:

1. `user_pwd`: Sets the user password, allowing opening and reading the PDF.
2. `owner_pwd`: Sets the owner password, enabling opening the PDF without any restrictions, including editing.

Let's utilize `.encrypt()` to add a password to a PDF file. Initially, open the "newsletter.pdf" file in the Chapter 14 Practice Files directory:

```python
from pathlib import Path
from PyPDF2 import PdfFileReader, PdfFileWriter

pdf_path = Path.home() / "python-basics-exercises" / "ch13-interact-with-pdf-files" / "practice_files" / "newsletter.pdf"
pdf_reader = PdfFileReader(str(pdf_path))
```

Create a new `PdfFileWriter` instance and append the pages from `pdf_reader`:

```python
pdf_writer = PdfFileWriter()
pdf_writer.appendPagesFromReader(pdf_reader)
```

Add the password "SuperSecret" using the `pdf_writer.encrypt()` method:

```python
pdf_writer.encrypt(user_pwd="SuperSecret")
```

When setting only `user_pwd`, the `owner_pwd` argument defaults to the same string, setting both the user and owner passwords.

Finally, write the encrypted PDF to an output file named "newsletter_protected.pdf" in your home directory:

```python
output_path = Path.home() / "newsletter_protected.pdf"
with output_path.open(mode="wb") as output_file:
    pdf_writer.write(output_file)
```

When you open the PDF with a PDF reader, you'll be prompted to enter a password ("SuperSecret" in this case) to access the document.

If you need to set a separate owner password for the PDF, provide a second string to the `owner_pwd` parameter. For instance:

```python
pdf_writer.encrypt(user_pwd="SuperSecret", owner_pwd="ReallySuperSecret")
```

This sets the user password to "SuperSecret" and the owner password to "ReallySuperSecret." Adjust these passwords according to your security requirements.

### PDF Decryption

When dealing with password-protected files programmatically, you must decrypt them before accessing any of the contents. To decrypt an encrypted PDF file, use the `.decrypt()` method of a `PdfFileReader` instance, which takes a single parameter called `password`. Let's illustrate the process using the previously created "newsletter_protected.pdf" file.

First, create a new `PdfFileReader` instance with the path to the protected PDF:

```python
from pathlib import Path
from PyPDF2 import PdfFileReader, PdfFileWriter

pdf_path = Path.home() / "newsletter_protected.pdf"
pdf_reader = PdfFileReader(str(pdf_path))
```

Before decrypting the PDF, attempt to get the first page to observe the behavior:

```python
try:
    pdf_reader.getPage(0)
except Exception as e:
    print(f"Exception: {e}")
```

Executing this code will raise a `PdfReadError` exception, indicating that the PDF file has not been decrypted.

Now, proceed to decrypt the file by providing the password:

```python
pdf_reader.decrypt(password="SuperSecret")
```

The `.decrypt()` method returns an integer representing the success of the decryption:

- 0 indicates an incorrect password.
- 1 indicates a successful match with the user password.
- 2 indicates a successful match with the owner password.

Once the file is successfully decrypted, you can access the contents of the PDF, for example, by getting the first page:

```python
page_content = pdf_reader.getPage(0)
print(page_content)
```

Now, you have the ability to extract text, crop, or rotate pages as needed. The decryption process allows you to interact with the PDF content programmatically.

## Creating a PDF File From Scratch with ReportLab

While the PyPDF2 package is excellent for reading and modifying existing PDF files, it doesn't support the creation of new PDF files. In this section, you'll use the ReportLab toolkit to generate PDF files from scratch. ReportLab is a comprehensive PDF creation solution, and it offers both a commercial version and a limited-feature open source version.

> ***Note:** This introduction to ReportLab is not exhaustive but serves as a sample to demonstrate its capabilities.*

### Install reportlab

To install ReportLab, open your terminal or command prompt and run the following command:

```bash
python3 -m pip install reportlab
```

You can verify the installation by using the following command:

```bash
python3 -m pip show reportlab
```

This should display information about the installed ReportLab package, including its version, summary, author details, and license.

For example:

```bash
Name: reportlab
Version: 3.5.34
Summary: The Reportlab Toolkit
Home-page: http://www.reportlab.com/
Author: Andy Robinson, Robin Becker, the ReportLab team and the community
Author-email: reportlab-users@lists2.reportlab.com
License: BSD license (see license.txt for details), Copyright (c) 2000-2018, ReportLab Inc.
Location: c:usersdaveavenvlibsite-packages
Requires: pillow
Required-by:
```

Ensure that you have the latest version of ReportLab installed. If you have IDLE open, restart it to make sure the package is recognized.

### Using the Canvas Class

The primary interface for creating PDFs with ReportLab is the `Canvas` class, located in the `reportlab.pdfgen.canvas` module. Open a new IDLE interactive window and import the `Canvas` class:

```python
from reportlab.pdfgen.canvas import Canvas
```

Create a new `Canvas` instance for the file "hello.pdf":

```python
canvas = Canvas("hello.pdf")
```

This creates a `Canvas` instance associated with a file called "hello.pdf" in your current working directory.

Add some text to the PDF using the `drawString()` method:

```python
canvas.drawString(72, 72, "Hello World")
```

The first two arguments specify the location on the canvas where the text is written. The first argument is the distance from the left edge of the canvas, and the second is the distance from the bottom edge.

To save the PDF to a file, use the `Canvas` object's `save()` method:

```python
canvas.save()
```

Now, you have a PDF file called "hello.pdf" in your current working directory. Open it with a PDF reader to see the text "Hello World" at the bottom of the page.

> ***Note:** The default page size is A4, and the font defaults to Helvetica with a font size of 12 points, but you can customize these settings as needed.*

### Setting the Page Size in ReportLab

When creating a `Canvas` object in ReportLab, you have the flexibility to adjust the page size using the optional `pagesize` parameter. This parameter accepts a tuple of floating-point values representing the width and height of the page in points.

For instance, if you wish to set the page size to 8.5 inches width by 11 inches tall, you can instantiate the `Canvas` as follows:

```python
canvas = Canvas("hello.pdf", pagesize=(612.0, 729.0))
```

Here, the tuple (612, 729) denotes letter-sized paper, as 8.5 times 72 equals 612, and 11 times 72 equals 729.

For those who find the conversion of points to inches or centimeters cumbersome, the `reportlab.lib.units` module provides assistance. This module offers convenient objects such as `inch` and `cm` that simplify unit conversions.

Let's import the `inch` and `cm` objects:

```python
from reportlab.lib.units import inch, cm
```

Now, let's inspect each object:

```python
cm  # 28.346456692913385
inch  # 72.0
```

Both `cm` and `inch` are floating-point values representing the number of points in each unit. Specifically, `inch` is equivalent to 72.0 points, and `cm` is approximately 28.35 points.

To utilize these units, multiply the unit name by the desired number of units to obtain the conversion to points. For instance, setting the page size to 8.5 inches wide by 11 inches tall using `inch`:

```python
canvas = Canvas("hello.pdf", pagesize=(8.5 * inch, 11 * inch))
```

While you can create a page of any size by passing a tuple to `pagesize`, ReportLab includes some standard page sizes for convenience. These sizes are conveniently located in the `reportlab.lib.pagesizes` module. For example, to set the page size to letter:

```python
from reportlab.lib.pagesizes import LETTER
canvas = Canvas("hello.pdf", pagesize=LETTER)
```

Inspecting the `LETTER` object reveals that it is a tuple of floats:

```python
LETTER  # (612.0, 792.0)
```

The `reportlab.lib.pagesize` module contains many standard page sizes.

Here are some of them and their dimensions:

| Page Size | Dimensions        |
|-----------|-------------------|
| A4        | 210 mm x 297 mm   |
| LETTER    | 8.5 in x 11 in     |
| LEGAL     | 8.5 in x 14 in     |
| TABLOID   | 11 in by 17 in     |

In addition to these, the module contains definitions for all of the [ISO 216 standard paper sizes](https://en.wikipedia.org/wiki/ISO_216).

### Setting Font Properties in ReportLab

In ReportLab, you have the flexibility to customize font properties such as the font type, font size, and font color when adding text to the canvas. The `Canvas` class provides methods to achieve this customization.

To change the font and font size, use the `setFont()` method. Here's an example demonstrating how to set the font to Times New Roman with a size of 18 points:

```python
from reportlab.lib.pagesizes import LETTER
from reportlab.pdfgen.canvas import Canvas
from reportlab.lib.units import inch

# Create a new Canvas instance with letter page size
canvas = Canvas("font-example.pdf", pagesize=LETTER)

# Set the font to Times New Roman with a size of 18 points
canvas.setFont("Times-Roman", 18)

# Write the string to the canvas and save it
canvas.drawString(1 * inch, 10 * inch, "Times New Roman (18 pt)")
canvas.save()
```

In this example, the text is positioned one inch from the left side of the page and ten inches from the bottom.

ReportLab provides three default fonts:
1. "Courier"
2. "Helvetica"
3. "Times-Roman"

Each font has bold and italicized variants. Here is a list of all available font variations in ReportLab:

- "Courier"
- "Courier-Bold"
- "Courier-BoldOblique"
- "Courier-Oblique"
- "Helvetica"
- "Helvetica-Bold"
- "Helvetica-BoldOblique"
- "Helvetica-Oblique"
- "Times-Bold"
- "Times-BoldItalic"
- "Times-Italic"
- "Times-Roman"

You can also set the font color using the `setFillColor()` method. Here's an example of creating a PDF with blue text:

```python
from reportlab.lib.colors import blue
from reportlab.lib.pagesizes import LETTER
from reportlab.lib.units import inch
from reportlab.pdfgen.canvas import Canvas

canvas = Canvas("font-colors.pdf", pagesize=LETTER)
canvas.setFont("Times-Roman", 12)
canvas.setFillColor(blue)
canvas.drawString(1*inch, 10*inch, "Blue text")
canvas.save()
```

Note that the color "blue" is an object imported from the `reportlab.lib.colors` module, which contains common named colors.

These examples demonstrate the basics of working with fonts and colors in ReportLab. The possibilities go beyond, allowing you to create tables, forms, and high-quality graphics from scratch. If you're eager to delve deeper, the ReportLab User Guide is an excellent resource, offering a plethora of examples for generating PDF documents from scratch. It provides valuable insights for anyone interested in mastering PDF creation with Python.
