**Editors:**
An editor is what you use to manipulate a text file, such as program code or a batch script.

Command:
* gedit: Easy to use Notepad-like text editor. Recommended for new users. Requires [X Forwarding (http://www.bu.edu/tech/support/research/system-usage/getting-started/x-forwarding/).

* emacs: Programming text editor. Extremely extensible and configurable by advanced users. The default version requires X Forwarding but you can use the **-nw** (no windows) option to avoid this.

* vi, vim, gvim: Visual text editor. Only **gvim** requires X Forwarding

* nano: GNU text editor with command-line interface.

**Image and Document Viewers and Editors:**
These tools are used to display images and documents in formats more complex than ASCII text, such as PDF, HTML, and .CSV files. Most of these tools require X Forwarding.

Command:
* firefox: Web browser. View HTML files.

* evince: View PDF (Adobe’s Portable Document Format) files.

* pdftk: Command-line tool for manipulating PDF documents.

* soffice: Open source suite with much of the functionality of Microsoft Office. Requires first running module load libreoffice and then executing the command soffice

* xv: Display and modify images; simple to use.

* display, convert, etc..  : [ImageMagick](https://www.imagemagick.org/script/command-line-tools.php) suite of command-line tools. There are many tools to display, convert formats of, resize, and otherwise manipulate image files. Operations can be easily automated to process many files.

* gwenview: Image viewer. Easy viewing of all of the images in a directory.

* gimp: GNU Image Manipulation Program; similar to Photoshop but open source.

* tiff: Manipulate TIFF (Tag Image File Format) files. Use module load **tiff** to access this tool.

**Interactive Development Environments (IDEs):**

An [integrated development environment](https://en.wikipedia.org/wiki/Integrated_development_environment) (IDE) is a software application that provides comprehensive facilities to computer programmers for software development. An IDE normally consists of a source code editor, build automation tools and a debugger.

Command:
* [codeblocks](http://www.codeblocks.org/): Cross-platform IDE for C, C++, and Fortran that is built around wxWidgets. It is designed to be extensible and configurable. Use module load codeblocks to access this tool.

* geany: Text editor using the GTK+ toolkit with the basic features of an IDE. [Geany](https://www.geany.org/) supports many different [filetypes](https://www.geany.org/Main/AllFiletypes) including C, Java, PHP, HTML, Python, and Perl.

* eclipse: IDE used in computer programming mostly for Java, C, and C++.
