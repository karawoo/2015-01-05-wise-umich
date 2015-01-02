---
layout: lesson
root: ../..
Title: Exploring files and directories
---

## Let's get started

Open your Terminal (i.e. shell prompt)

My Terminal looks like this:

![](shell_prompt.png)

Yours might look different (these can be easily customized). Usually includes something like `username@machinename`, followed by the current working directory (more about that soon) and a `$` sign

## Entering commands into the shell

You can just enter commands directly into the shell.

```
echo Morning People
```

We just used a command called `echo` and gave it an argument called `Morning People`.

If you enter a command that shell doesn't recognize, it will just report an error

```
$ gobbeltdfsf
-bash: gobbeltdfsf: command not found
```

Now let's enter something useful. Let's navigate to the home directory of your computer (more on navigation very shortly)

```
cd ~
pwd
```

What does it say?

---

## How commands work in the shell

Commands are often followed by one or more options that modify their behavior, and further, by one or more arguments, the items upon which the command acts. So most commands look kind of like this:

```
e.g. ls -l ~/
```

```
command -letter
```

**OR**

```
command --word
```

## Knowing where you are and seeing what's around

The first thing you want to do when you're somewhere new is get a map or figure out how to obtain directions. Since you're new to the shell, we're going to do just that. This is really easy to do using a GUI (just click on things). Once you learn the basic commands, you'll see that it is really easy to do in the shell too.

Three really imporant commands:

* `pwd` *Acronym for print working directory*. Tell you where you are.
* `cd` *Change directory*. Give it options for where to take you.
* `ls` *Short for list*. List all the files and folders in your current location.

Most operating systems have a hierarchical directory structure. The very top is called the *home* directory. Directories are often called "folders" because of how they are represented in GUIs. Directories are just listings of files. They can contain other files or (sub) directories.

```
$ pwd
/Users/barneche
```

Note that I'm in my *home* directory. Whenever you start up a terminal, you will start in the home directory. Every user has their own home directory where they have full access to do whatever they want. For example, my user ID is `barneche`, the `pwd` command tells me that I am in the `/Users/barneche` directory. This is the home directory for the `barneche` user. Yours should (hopefully) look different.

**Changing Directories**

You can change the working directory at any time using the `cd` command.

```
cd
cd /usr/bin
pwd
ls
```
Now change back to your home again

```
cd ~
```

Tip: `~` is a shortcut for the HOME directory for any user. My home is `/Users/barneche` and I can get there three ways:

`cd /Users/barneche` OR `cd ~` OR `cd`.

You might be wondering why there is a **standard** shortcut for the home directory. It provides a convenient way of giving a point of access which is independent of machine and username. For instance, `~/Downloads` should work for all Mac users.

**Full versus relative paths**

In the command line you can use both full paths (much like someone's street address with post code) OR offer relative directions from one's current location. You can do the same here.

```
cd /usr
pwd
```

We're now in the `usr/` directory. Now change to `bin/`

```
cd bin
```

This is the same as doing:

```
cd /usr/bin
```

from **anywhere**.

**List all the files in this directory**

```
$ ls
Applications    Documents   Dropbox     Library     Music       Public      Desktop     Downloads         Movies      Pictures
```

When you enter the `ls` command lists the contents of the current directory. `ls` is extremely useful both for beginners and experts. `ls` can not only list the current directory contents but also contents from anywhere without changing working directories.

e.g.

```
ls /usr
```

or even multiple directories at once

```
ls ~ /usr
```

Now we can start adding more options. Recall that commands can take both options (with a `-` or `--`) followed by arguments. Let's add some to `ls`.

```
cd
cd gapminder
ls -l
SCI-5052:gapminder barneche$ ls -l
total 48
drwxr-xr-x  4 barneche  staff   136  7 Feb 14:14 R
-rw-r--r--  1 barneche  staff    20  7 Feb 10:55 README.md
-rw-r--r--  1 barneche  staff   476  7 Feb 10:55 analysis.R
drwxr-xr-x  4 barneche  staff   136  7 Feb 10:55 data
-rwxr-xr-x  1 barneche  staff    47  7 Feb 11:48 executable.R
-rwxr-xr-x  1 barneche  staff    38  7 Feb 11:49 executable.sh
drwxr-xr-x  3 barneche  staff   102  7 Feb 15:56 figures
-rw-r--r--  1 barneche  staff   204  7 Feb 10:55 gapminder.Rproj
-rw-r--r--  1 barneche  staff  3150  7 Feb 10:55 rich-for-functions.R
```

By adding `-l` to the command, we changed the output to the long format.

Now let's add more options

```
ls -lt
```

The `t` options now sorts by time.

Similarly you can try the following:

Some options:
`-a`  List all files even those that are hidden. Files starting with a `.` are considered hidden;
`-F`  All a trailing slash to help identify folders;
`-l`  Long format;
`-lh` Make file sizes human readable;
`-S`  Sort by file size;
`-t`  Sort by modification time.

Try some of these. Do you see any new files that we have not discussed before? You can even combine several of these options in a single command.

What are all the extra fields in the long format?

```
$ ls -l
total 48
drwxr-xr-x  4 barneche  staff   136  7 Feb 14:14 R
-rw-r--r--  1 barneche  staff    20  7 Feb 10:55 README.md
-rw-r--r--  1 barneche  staff   476  7 Feb 10:55 analysis.R
drwxr-xr-x  4 barneche  staff   136  7 Feb 10:55 data
-rwxr-xr-x  1 barneche  staff    47  7 Feb 11:48 executable.R
-rwxr-xr-x  1 barneche  staff    38  7 Feb 11:49 executable.sh
drwxr-xr-x  3 barneche  staff   102  7 Feb 15:56 figures
-rw-r--r--  1 barneche  staff   204  7 Feb 10:55 gapminder.Rproj
-rw-r--r--  1 barneche  staff  3150  7 Feb 10:55 rich-for-functions.R
```
* Files begin with a `-` and directories with a `d`.
* Followed by permissions for the user, group, and everyone.
* Permissions are in the order of read, write, and execute. If any * group is missing a permission, you'll see a `-`.
* Ignore second column for now (it's the number of links to the file)
* The owner of the file
* What group this person belongs to
* Size of file in bytes  (Quick question: How do you change this?)
* Date an time the file was last modified
* Name of file.

One last argument for the function `ls` now.

```
$ ls -F
R/    		 data/			 executable.sh*	   messy-folder/
README.md	 dplyr.R		 figures/		   repeating.R
analysis.R	 executable.R*   gapminder.Rproj   rich-for-functions.R
```

The `-F` flag tells the computer to list the files in a way that shows their file type. There are (probably) several items in your home directory, notice that many have a slash at the end. This tells us that all of these items are directories as opposed to files. If a file has an asterisk at the end, it is *executable*.

**Arguments**

Most programs take additional arguments that control their exact behavior. For example, `-F` and `-l` are arguments to `ls`.  The `ls` program, like many programs, take a lot of arguments. But how do we know what the options are to particular commands?

Most commonly used shell programs have a manual. You can access the manual using the `man` program. Try entering:

```
$ man ls
```

This will open the manual page for `ls`. Use the space key to go forward and b to go backwards. When you are done reading, just hit `q` to exit.

Unfortunately GitBash for Windows does not have the `man` command. Instead, try using the `--help` flag after the command you want to learn about. For internal bahs commands such as `cd` and  `pwd` you will be able to access the help file by typing `help function`.

```
ls --help
help cd
```

And you also find the manual pages at many different sites online, e.g. [http://linuxmanpages.com/]().

Programs that are run from the shell can get extremely complicated. To see an example, open up the manual page for the `find` program, which we will use later this session. No one can possibly learn all of these arguments, of course. So you will probably find yourself referring back to the manual page frequently.

---
## Exploring your file system

Other really important commands

* `file`
* `less`
* `head`

**Determining file type**

```
file <filename>
```

e.g.

```
file Location.md
Location.md: ASCII English text
```

Notice that the function `file` is unfortunately not defined in GitBash. Alternatively, Windows users can have a quick look at the file to see the contents of its first lines using the function `head`

```
head <filename>
```

you can also fully examine files with the `less` command. Keeps the content from scrolling of the screen. You can also use the arrow keys to navigate up or down. Press enter or return to keep scrolling down and the `q` key to quit.

***
These lessons were adapted from materials by [Diego Barneche](http://nicercode.github.io/2014-02-13-UNSW/lessons/60-shell/)
