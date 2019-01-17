# Parnassus Format Editor's Guide
Last Edit: 11/17/19, Zach Sowerby

This document is to serve as a guide for Parnassus' Format Editor. It explains how to use Github, Git bash, a text editor, Markdown syntax, Pandoc, LaTeX, Alphabetum, and CSS to create and format works in the Parnassus database for publication.

## Github
### What is Github?
Github is a free cloud-based version control platform. A Github repository is where the Parnassus database and its associated documentation will be primarily maintained. Lest you worry that the entire database is stored remotely by a service over which we have no control, never fear - Github facilitates local copies (clones) of all of the information stored there.

To edit the Parnassus database, the Format Editor must have an account with Github. The Format Editor must also obtain write access to (i.e. the ability to edit) the official Parnassus repository. Write access can be granted via the account which created the repository.

### Using Github
To properly use Github, the Format Editor must use Git bash (see Downloads). Git bash is a bash shell specifically designed to bring Git functionality to a local machine. It will be primarily used to track changes and coordinate different users for version control. On a Windows machine, it will have its own interface; on a Mac, Git commands will be incorporated directly into the Terminal.

The Git functionality required for Parnassus will consist of just a few commands;
1. `cd <insert file path here>`
2. `git clone <insert clonign address here>`
3. `git pull`
4. `git status`
5. `git add <insert file name here>`
6. `git commit -m"<insert commit message here>"`
7. `git push`

`cd` (change directory) is a command which is used to navigate your operating system's hierarchy. Changing the directory changes the part of the hierarchy in which subsequent commands will operate. For example, `C:\users\Zach Sowerby\Desktop` describes the Desktop of my computer. I can navigate to a specific file on my Desktop with the command `cd <insert file path here>`. Other useful commands to assist in navigating your operating system are `cd ..` (navigates backwards one directory), `pwd` (prints in the Shell the full file path to your current location), and `ls` (lists the possible sub-directories contained within your current directory). These are standard commands, not added by Git bash.

To work with Git, you must create a local copy (clone) of the Parnassus Github repository on your machine. Navigate into the directory, using `cd`, where you would like to edit the Parnassus repository (for convenience's sake, I usually use the Desktop, but it doesn't really matter where as long as you are consistent). At the Parnassus repository on the Github website, find the cloning address. It is accessible via a green button on the right-hand side of the page ("Clone or Download"). It should look something like "https://github.com/zachsowerby/Parnassus_Temporary.git". Copy this to your clipboard, and in the Shell, enter the following command: `git clone <insert cloning address here>`. This will create the local clone. This may only be a one-time action; once the repository is cloned to your machine, you can sync your local clone with the Github repository using the other commands.

`git pull` searches the Github repository for any updates which are not yet downloaded on your local clone and downloads them. This is especially important if you are not the only one working in a repository. Since both the Web Editor and Format Editor will have write access to this repository, `git pull` is a crucial step every time you start working. Conflicts between different branches of the repository can be tricky to resolve, and the situation is best avoided entirely by good Git hygiene.

After you edit whatever files in the repository you wish (see Text Editor, below), the remaining Git functionality syncs your local clone with the Github repository. `git status` does nothing but print in the Shell a list of files in the current directory and their statuses. (Changes are only detected by Git if they have already been saved locally! Make sure all changes have been saved in your text editor.) Files you have edited will appear red in the status list. Feel free to use the command `git status` as much as necessary throughout the syncing process - it does not affect the process, and only provides helpful information.

To sync, first stage the files you wish to commit. This is done with the command `git add <insert file name here>`. You can easily copy and paste the path of a file you've edited straight from the list you printed with `git status`. Files staged to commit will appear green instead of red when printed with `git status`.

Once you have given Git this list of files, use `git commit -m"<insert commit message here>"`. This takes changes you've staged and saves them to your local repository. The commit message is a human-readable summary description of the edits committed to the repository with this commit. The commit will fail if there is no commit message added.

The final command, `git push`, simply saves the commit from your local repository to the Github repository. These changes will now be accessible to anyone else via the command `git pull`.


1. Github
2. Git bash
3. Text Editor (preferably Atom)
4. Markdown
5. Pandoc
6. LaTeX
7. Alphabetum
8. CSS

## Downloads
1. Git bash
2. Atom (optional but recommended)
3. Pandoc
4. MiKTeX
5. Alphabetum
