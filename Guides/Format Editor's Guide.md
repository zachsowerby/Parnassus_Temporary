# Parnassus Format Editor's Guide
Last Edit: 11/17/19, Zach Sowerby

This document is to serve as a guide for Parnassus' Format Editor. It explains how to use Github, Git bash, a simple text editor, Markdown syntax, Pandoc, LaTeX, Alphabetum, and CSS to create and format works in the Parnassus database for publication.

## Github
### What is Github?
Github is a free cloud-based version control platform. A Github repository is where the Parnassus database and its associated documentation will be primarily maintained. Lest you worry that the entire database is stored remotely by a service over which we have no control, never fear - Github facilitates local copies (clones) of all of the information stored there.

To edit the Parnassus database, the Format Editor must have an account with Github. The Format Editor must also obtain write access to (i.e. the ability to edit) the official Parnassus repository. Write access can be granted via the account which created the repository.

### Using Github
To properly use Github, the Format Editor must use Git bash (see the "Downloads" section at the end of this document). Git bash is a bash shell specifically designed to bring Git functionality to a local machine. It will be primarily used to track changes and coordinate different users for version control. On a Windows machine, it will have its own interface; on a Mac, Git commands will be incorporated directly into the Terminal.

The Git functionality required for Parnassus will consist of just a few commands;
1. `cd <insert file path here>`
2. `git clone <insert cloning address here>`
3. `git pull`
4. `git status`
5. `git add <insert file name here>`
6. `git commit -m"<insert commit message here>"`
7. `git push`

`cd` (change directory) is a command which is used to navigate your operating system's hierarchy. Changing the directory changes the part of the hierarchy in which subsequent commands will operate. For example, `C:\users\Zach Sowerby\Desktop` describes the Desktop of my computer. I can navigate to a specific file on my Desktop with the command `cd <insert file path here>`. Other useful commands to assist in navigating your operating system are `cd ..` (navigates backwards one directory), `pwd` (prints in the Shell the full file path to your current location), and `ls` (lists the possible sub-directories contained within your current directory). These are standard commands, not added by Git bash.

To work with Git, you must create a local copy (clone) of the Parnassus Github repository on your machine. Navigate into the directory, using `cd`, where you would like to edit the Parnassus repository (for convenience's sake, I usually use the Desktop, but it doesn't really matter where as long as you remember). At the Parnassus repository on the Github website, find the cloning address. It is accessible via a green button on the right-hand side of the page ("Clone or Download"). It should include the name of the repository and end in ".git". Copy this to your clipboard, and in the Shell, enter the following command: `git clone <insert cloning address here>`. This will create the local clone. This may only be a one-time action; once the repository is cloned to your machine, you can sync your local clone with the Github repository using the other commands.

`git pull` searches the Github repository for any updates which are not yet downloaded on your local clone and downloads them. This is especially important if you are not the only one working in a repository. Since both the Web Editor and Format Editor will have write access to this repository, `git pull` is a crucial step every time you start working. Conflicts between different branches of the repository can be tricky to resolve, and the situation is best avoided entirely by good Git hygiene.

After you edit whatever files in the repository you wish (see Text Editor, below), the remaining Git functionality syncs your local clone with the Github repository. `git status` does nothing but print in the Shell a list of files in the current directory and their statuses. (Changes are only detected by Git if they have already been saved locally! Make sure all changes have been saved in your text editor.) Files you have edited will appear red in the status list. Feel free to use the command `git status` as much as necessary throughout the syncing process - it does not affect the process, but only provides helpful information.

To sync, first stage the files you wish to commit. This is done with the command `git add <insert file name here>`. You can easily copy and paste the path of a file you've edited straight from the list you printed with `git status`. Files staged to commit will appear green instead of red when printed with `git status`.

Once you have given Git this list of files, use `git commit -m"<insert commit message here>"`. This takes changes you've staged and saves them to your local repository. The commit message is a human-readable summary description of the edits in this commit. The commit will fail if there is no commit message added.

The final command, `git push`, simply saves the commit from your local repository to the Github repository. These changes will now be accessible to anyone else via the command `git pull`.

### Keychain
Some Mac computers use a program called Keychain. Keychain is designed to automatically fill in your password.

When you push, you will be asked for your Github username and password; your push will be denied if your account does not have write access to the repository. Keychain will save this information and automatically fill it in.

However, on public computers such as those in the St. Isidore of Seville Computer Lab, multiple people may be committing to different Github repositories; Keychain will supply the Github login information of the last person to enter their Github username and password. If that person does not have write access to your repository, the push will be denied. This is fixable by deleting the "Github" entry in Keychain, attempting the push again, and supplying your own information when prompted.


## Editing Files
### Text Editor
There is nothing wrong with using a Microsoft Word file or a PDF - however, file types such as these are quite technology-dependent. They require machines which can read these specific file types. There are many different types of operating systems, not all of which can read every type of file - and as technology evolves, certain file types may no longer be supported. Furthermore, the formatting in something such as Microsoft Word causes the textual data to be technologically dependent on the Microsoft Word format.

Using a simple text editor, perhaps as simple as Notepad or TextEdit, avoids these problems by separating the concerns of formatting and content. Every functional computer now and likely in the distant future will be able to read a file consisting only of strings of Unicode. These strings of Unicode are also not wholly dependent on the file format in which they were first written.

There are several excellent simple text editors, with far more functionality than Notepad and TextEdit. Atom is the recommended choice for several reasons (not the least of which being that it was designed with built-in Git functionality). Sublime Text is another excellent option. See the "Downloads" section at the end of this document.

### Markdown Syntax
Markdown syntax is a way to include those rich text elements into the simple text format. It is technically a simple coding language, but in practice it is just a way to mark up a plain text document with extra information (such as emphasis, section information, etc).

Markdown only uses Unicode characters incorporated into the data of the document to achieve this. For example, to add emphasis to a word in your document, simply surround it with * . This is equivalent to marking a word in italics, and the representation of Markdown syntax will likely represent it as such.

Markdown can be used to express quite complex information, such as tables or pictures. Full guides and cheat sheets are easily available online.

## Generating Files
### Pandoc
Pandoc is a free in-line document conversion tool. It has the capability to convert a document from one of any number of file formats to one of any number of others. It is freely available online (see the "Downloads" section at the end of this document). For Parnassus, it can be used to easily generate files in HTML, in .docx, or in .pdf all from a single Markdown file, without altering or harming the original file in any way.

First, navigate into the folder which contains the file you wish to convert. `pandoc` starts a Pandoc command; specify the existing file name first, with extension, and then specify the desired output file name with desired extension (here HTML). `-s` tells Pandoc to produce a standalone file (as opposed to a fragment, which is the default). `-o` specifies output. A full command to convert a file in Markdown to a file in HTML would look something like this:

`pandoc example.md -s -o example.html`

### Beautiful PDF Generation with LaTeX
Pandoc can not, however, generate a PDF by itself. It instead must produce a document in a PDF typesetting format called LaTeX, which it can subsequently convert into a PDF. This requires LaTeX to be installed in addition to Pandoc. (See the "Downloads" section at the end of this document for MiKTeX, a basic TeX/LaTeX package.) Converting to PDF will probably be the most important conversion used by Parnassus, since CrossWorks only publishes PDFs.

LaTeX, however, has some trouble with non-standard Unicode characters; amongst these non-standard characters is basic Ancient Greek, which is an obvious problem for Parnassus. Thus, two things need to be taken into consideration when converting into a PDF. First of all, you must specify a special version of LaTeX (XeLaTeX, or Extended LaTeX) which can handle these characters. If this is not specified, PDF conversion will fail when LaTeX encounters its first unknown character and no document will be produced. The second thing to take into consideration is that the typeface must be specified, to be one which supports the characters in question. If the typeface used in the PDF generation does not support the characters in question, the document will be produced with blank white space where the non-standard characters would be. Please pay attention to the Shell, as any failure to render a character in the PDF will be reported there.

For this reason and others, I would recommend using a standard typeface for all Parnassus publications - Alphabetum (see the "Downloads" section at the end of this document). Alphabetum is an ideal candidate because its breadth of coverage (everything from Ugaritic to Meroitic to Linear B to Old Nordic) allows for its use as one standard typeface. Unlike other options, such as Avdira or New Athena Unicode (which lack Alphabetum's breadth), Alphabetum is non-offensive, sober, and visually consistent.

PDF generation with Pandoc is similar to standard Pandoc conversion, with just a few added specifications in code:

`pandoc --pdf-engine=xelatex -V mainfont="ALPHABETUM" example.md -o example.pdf`

After download, you may or may not have to set MiKTeX as an environment variable.

### Formatting
That's all well and good, but how does one specify formatting? Pandoc interprets the rich text aspects of Markdown in standard formatting ways which are alterable. How they are altered is different for different outputs.

If the output is a Microsoft Word document, your best bet is probably generating the document and editing it in Word. The CSS file (Cascading Style Sheet) is designed to integrate into HTML; a file written in CSS language can be specified during the Pandoc generation of your HTML.

Pandoc uses a template written in LaTeX when generating a PDF. (The `-V` command in the above code changes a variable in template, in that case the main font.) You can write your own template in LaTeX and specify it in the generation of the PDF. (This of course means you will not have to specify a font, as font is included as a variable in the template.) This means learning the LaTeX coding language (resources available online).

To create a new template, you can run the code `pandoc -D latex > templateExample.latex`. After editing your .latex file, you can specify it in PDF generation with a command like `pandoc --pdf-engine=xelatex --template=templateExample.latex example.md -o example.pdf`.

## Downloads
Ideally, all of these will soon be available on computers in the St. Isidore of Seville Computer Lab. All of these programs except for Alphabetum are free. I will try to get funding for a license for Alphabetum in the Lab.

1. [Git bash](https://git-scm.com/downloads)
2. [Atom (optional but highly recommended)](https://atom.io/)
3. [Pandoc](https://pandoc.org/installing.html)
4. [MiKTeX (basic TeX/LaTeX functionality)](https://miktex.org/download)
5. Alphabetum
