---
layout: lesson
root: ../..
Title: Exploring files and directories
---

## Let's get started

Open your Terminal (i.e. shell prompt)

My Terminal looks like this:

![](prompt.png)

Yours might look different (these can be easily customized). Usually includes something like `username@machinename`, followed by the current working directory and a `$` sign. Note: a "directory" is what you may know as a "folder", and I'll be using these basically interchangeably throughout the lesson.

## Entering commands into the shell

You can just enter commands directly into the shell.

~~~
$ echo Morning People
~~~
{:class="in"}

We just used a command called `echo` and gave it an argument called `Morning People`.

If you enter a command that shell doesn't recognize, it will just report an error

~~~
$ gobbeltdfsf
~~~
{:class="in"}

~~~
-bash: gobbeltdfsf: command not found
~~~
{:class="out"}

---

## How commands work in the shell

Commands are often followed by one or more options that modify their behavior, and further, by one or more arguments, the items upon which the command acts. So most commands look kind of like this:

~~~
$ ls -l ~/
~~~
{:class="in"}

~~~
$ command -letter
~~~
{:class="in"}

**OR**

~~~
$ command --word
~~~
{:class="in"}

## Knowing where you are and seeing what's around

The first thing you want to do when you're somewhere new is get a map or figure out how to obtain directions. Since you're new to the shell, we're going to do just that. This is really easy to do using a GUI (just click on things). Once you learn the basic commands, you'll see that it is really easy to do in the shell too.

Three really imporant commands:

* `pwd` *Acronym for print working directory*. Tell you where you are.
* `cd` *Change directory*. Give it options for where to take you.
* `ls` *Short for list*. List all the files and folders in your current location.

Most operating systems have a hierarchical directory structure. The very top is called the *home* directory. Directories are often called "folders" because of how they are represented in GUIs. Directories are just listings of files. They can contain other files or (sub) directories.

~~~
$ pwd
~~~
{:class="in"}

~~~
/Users/Kara
~~~
{:class="out"}

Note that I'm in my *home* directory. Whenever you start up a terminal, you will start in the home directory. Every user has their own home directory where they have full access to do whatever they want. For example, my user ID is `Kara`, the `pwd` command tells me that I am in the `/Users/Kara` directory. This is the home directory for the `Kara` user. Yours should (hopefully) look different.

### Changing Directories

You can change the working directory at any time using the `cd` command.

~~~
$ cd
$ cd /usr/bin
$ pwd
$ ls
~~~
{:class="in"}

Now change back to your home again

~~~
$ cd ~
~~~
{:class="in"}

Tip: `~` is a shortcut for the HOME directory for any user. My home is `/Users/Kara` and I can get there three ways:

`cd /Users/Kara` OR `cd ~` OR `cd`.

You might be wondering why there is a **standard** shortcut for the home directory. It provides a convenient way of giving a point of access which is independent of machine and username. For instance, `~/Downloads` should work for all Mac users.

### Full versus relative paths

In the command line you can use both full paths (much like someone's street address with post code) OR offer relative directions from one's current location. You can do the same here.

~~~
$ cd /usr
$ pwd
~~~
{:class="in"}

We're now in the `usr/` directory. Now change to `bin/`

~~~
$ cd bin
~~~
{:class="in"}

This is the same as doing:

~~~
$ cd /usr/bin
~~~
{:class="in"}

from **anywhere**.

**An important note:** having spaces in folder names or file names will confuse the computer. Once it sees a space, it will think the path is complete. For this reason it's recommended not to use spaces in your file/folder names. If you do have paths that contain spaces, you can encase the path that you type into the shell with quotation marks, e.g.:

~~~
$ cd "~/Desktop/folder with a space"
~~~
{:class="in"}

*Stop and ask for questions*

### List all the files in this directory

Now we're going to talk about how to view the contents of a folder (directory).

~~~
$ ls
~~~
{:class="in"}

When you enter the `ls` command lists the contents of the current directory. `ls` is extremely useful both for beginners and experts. `ls` can not only list the current directory contents but also contents from anywhere without changing working directories.

e.g.

~~~
$ ls /usr
~~~
{:class="in"}

or even multiple directories at once

~~~
$ ls ~ /usr
~~~
{:class="in"}

### Exercise

1. Using the shell, navigate to the folder of data that you downloaded for Christie's R lesson this morning.
2. List the contents of this directory.
3. Change back into your home directory.
4. Now, without changing your directory (i.e. without using `cd`), list the contents of the data directory again.

~~~
$ cd ~/Desktop/swc-data/
$ ls
$ cd ~
$ ls ~/Desktop/swc-data
~~~
{:class="in"}

### Arguments

Now we can start adding more options. Recall that commands can take both options (with a `-` or `--`) followed by arguments. Let's add some to `ls`.

~~~
$ cd
$ cd ~/Desktop/swc-data
$ ls -l
~~~
{:class="in"}

~~~
total 2288
-rwxr-xr-x@ 1 Kara  staff     1715 Dec 31 09:15 car-speeds.csv
-rwxr-xr-x@ 1 Kara  staff     5374 Dec 31 09:15 inflammation-02.csv
-rwxr-xr-x@ 1 Kara  staff     5403 Dec 31 09:15 inflammation-03.csv
-rwxr-xr-x@ 1 Kara  staff     5427 Dec 31 09:15 inflammation-04.csv
-rwxr-xr-x@ 1 Kara  staff     5405 Dec 31 09:15 inflammation-05.csv
-rwxr-xr-x@ 1 Kara  staff     5390 Dec 31 09:15 inflammation-06.csv
-rwxr-xr-x@ 1 Kara  staff     5402 Dec 31 09:15 inflammation-07.csv
-rwxr-xr-x@ 1 Kara  staff     5412 Dec 31 09:15 inflammation-08.csv
-rwxr-xr-x@ 1 Kara  staff     5387 Dec 31 09:15 inflammation-09.csv
-rwxr-xr-x@ 1 Kara  staff     5402 Dec 31 09:15 inflammation-10.csv
-rwxr-xr-x@ 1 Kara  staff     5423 Dec 31 09:15 inflammation-11.csv
-rwxr-xr-x@ 1 Kara  staff     5400 Dec 31 09:15 inflammation-12.csv
-rwxr-xr-x@ 1 Kara  staff       14 Dec 31 09:15 small-01.csv
-rwxr-xr-x@ 1 Kara  staff       17 Dec 31 09:15 small-02.csv
-rwxr-xr-x@ 1 Kara  staff       14 Dec 31 09:15 small-03.csv
-rwxr-xr-x@ 1 Kara  staff     2115 Jan  2 11:34 species.csv
-rwxr-xr-x@ 1 Kara  staff  1058902 Jan  2 11:01 surveys.csv
~~~
{:class="out"}

By adding `-l` to the command, we changed the output to the long format.

Now let's add more options

~~~
$ ls -lt
~~~
{:class="in"}

The `t` options now sorts by time.

Similarly you can try the following:

Some options: *(list these on the board)*

* `-a`  List all files even those that are hidden. Files starting with a `.` are considered hidden;
* `-F`  All a trailing slash to help identify folders;
* `-l`  Long format;
* `-lh` Make file sizes human readable;
* `-S`  Sort by file size;
* `-t`  Sort by modification time.

Try some of these. Do you see any new files that we have not discussed before? You can even combine several of these options in a single command like we did above with `ls -lt`.

What are all the extra fields in the long format?

~~~
$ ls -l
~~~
{:class="in"}

~~~
total 2288
-rwxr-xr-x@ 1 Kara  staff     1715 Dec 31 09:15 car-speeds.csv
-rwxr-xr-x@ 1 Kara  staff     5374 Dec 31 09:15 inflammation-02.csv
-rwxr-xr-x@ 1 Kara  staff     5403 Dec 31 09:15 inflammation-03.csv
-rwxr-xr-x@ 1 Kara  staff     5427 Dec 31 09:15 inflammation-04.csv
-rwxr-xr-x@ 1 Kara  staff     5405 Dec 31 09:15 inflammation-05.csv
-rwxr-xr-x@ 1 Kara  staff     5390 Dec 31 09:15 inflammation-06.csv
-rwxr-xr-x@ 1 Kara  staff     5402 Dec 31 09:15 inflammation-07.csv
-rwxr-xr-x@ 1 Kara  staff     5412 Dec 31 09:15 inflammation-08.csv
-rwxr-xr-x@ 1 Kara  staff     5387 Dec 31 09:15 inflammation-09.csv
-rwxr-xr-x@ 1 Kara  staff     5402 Dec 31 09:15 inflammation-10.csv
-rwxr-xr-x@ 1 Kara  staff     5423 Dec 31 09:15 inflammation-11.csv
-rwxr-xr-x@ 1 Kara  staff     5400 Dec 31 09:15 inflammation-12.csv
-rwxr-xr-x@ 1 Kara  staff       14 Dec 31 09:15 small-01.csv
-rwxr-xr-x@ 1 Kara  staff       17 Dec 31 09:15 small-02.csv
-rwxr-xr-x@ 1 Kara  staff       14 Dec 31 09:15 small-03.csv
-rwxr-xr-x@ 1 Kara  staff     2115 Jan  2 11:34 species.csv
-rwxr-xr-x@ 1 Kara  staff  1058902 Jan  2 11:01 surveys.csv
~~~
{:class="out"}

* Files begin with a `-` and directories with a `d`.
* Followed by permissions for the user, group, and everyone.
* Permissions are in the order of read, write, and execute. If any * group is missing a permission, you'll see a `-`.
* Ignore second column for now (it's the number of links to the file)
* The owner of the file
* What group this person belongs to
* Size of file in bytes  (Quick question: How do you change this?)
* Date and time the file was last modified
* Name of file.


**Quick exercise:** List the files in your data directory in long format, by file size, with human readable file sizes.

**Arguments**

Most programs take additional arguments that control their exact behavior. For example, `-F` and `-l` are arguments to `ls`.  The `ls` program, like many programs, take a lot of arguments. But how do we know what the options are to particular commands?

Most commonly used shell programs have a manual. You can access the manual using the `man` program. Try entering:

~~~
$ man ls
~~~
{:class="in"}

This will open the manual page for `ls`. Use the space key to go forward and b to go backwards. When you are done reading, just hit `q` to exit.

Unfortunately GitBash for Windows does not have the `man` command. Instead, try using the `--help` flag after the command you want to learn about. For internal bahs commands such as `cd` and  `pwd` you will be able to access the help file by typing `help function`.

~~~
$ ls --help
$ help cd
~~~
{:class="in"}

And you also find the manual pages at many different sites online, e.g. [http://linuxmanpages.com/]().

Programs that are run from the shell can get extremely complicated. To see an example, open up the manual page for the `find` program, which we will use later this session. No one can possibly learn all of these arguments, of course. So you will probably find yourself referring back to the manual page frequently.

### Exploring your file system

Other really important commands

* `file`
* `less`
* `head`

**Determining file type**

~~~
$ file <filename>
~~~
{:class="in"}

e.g.

~~~
$ file surveys.csv
~~~
{:class="in"}

~~~
surveys.csv: ASCII text
~~~
{:class="out"}
Notice that the function `file` is unfortunately not defined in GitBash.

You can have a quick look at the file to see the contents of its first lines using the function `head` (similar to the `head()` function in R).

~~~
$ head <filename>
~~~
{:class="in"}

You can also fully examine files with the `less` command. Keeps the content from scrolling of the screen. You can also use the arrow keys to navigate up or down. Press enter or return to keep scrolling down and the `q` key to quit.

***
Acknowledgments: these lessons were adapted by Kara Woo from materials by [Diego Barneche](http://nicercode.github.io/2014-02-13-UNSW/lessons/60-shell/).
