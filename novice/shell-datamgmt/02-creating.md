---
layout: lesson
root: ../..
Title: Creating, moving, and deleting files and directories
---

## Creating an empty file

Lets create an empty file using the `touch` command. Enter the command:

~~~
$ touch testfile
~~~
{:class="in"}

Then list the contents of the directory again using `ls`. You should see that a new entry, called `testfile`, exists. It does not have a slash at the end, showing that it is not a directory. The `touch` command just creates an empty file.

Some terminals can color the directory entries in this very convenient way. In those terminals, use `ls -G` instead of `ls` if you are on a Mac or `ls --color` if you run on Windows. Now your directories, files, and executables will have different colors.

Now if you use the command `ls -l` you will notice that `testfile` has a size of zero. OK then, let's get rid of `testfile`. To remove a file, just enter the command:

~~~
$ rm -i testfile
~~~
{:class="in"}

When prompted, type:

~~~
$ y
~~~
{:class="in"}

The `rm` command can be used to remove files. The `-i` adds the "are you sure?" message. If you enter `ls` again, you will see that `testfile` is gone.

***Warning: The shell does not have a recycling bin. So any file removed with `rm` is gone forever. Use with caution. Remember the -i argument***

## Manipulating the file system

Make directories with `mkdir`. This will create a new directory within the current directory.

~~~
$ mkdir directory_name
~~~
{:class="in"}

You can create as many folders as you like in a single call.

~~~
$ mkdir directory_name_1 directory_name_2 directory_name_3
~~~
{:class="in"}

To copy and move files, we use the commands `cp` and `mv`, followed by the file you want to copy/move, and then the location that you want to copy/move it to.

~~~
$ cp file1 file2
$ mv file1 file2
~~~
{:class="in"}

So if I am in my data directory and I want to copy or move one of the data files to my desktop, I would do.

~~~
$ cp car-speeds.csv ~/Desktop
$ mv car-speeds.csv ~/Desktop
~~~
{:class="in"}

`cp` and `mv` can also rename files. If you want to rename a file in place, just do:

~~~
$ mv file_oldname file_newname
~~~
{:class="in"}

When we moved `car-speeds.csv` to the Desktop, if we'd wanted to rename it at the same time we could have done:

~~~
$ cp car-speeds.csv ~/Desktop/car-speeds-2.csv
~~~
{:class="in"}

See the `man` command to get help on options you can use with these commands.

Remove files with `rm`

## Let's try out some of the commands above

First create a temporary directory on your desktop.

~~~
$ cd ~/Desktop
$ mkdir scratchpad
$ cd scratchpad
~~~
{:class="in"}

Make a few directories inside `scratchpad`

~~~
$ mkdir dir1 dir2 dir3
$ cp ~/Desktop/swc-data/*.csv .
~~~
{:class="in"}

Use `ls` to view the contents of the current directory. What just happened? *(Ask for a volunteer)*

Why? Can anyone break down the commands we just did? *(Ask again for a volunteer)*

Now try and remove scratchpad.

~~~
rm scratchpad
~~~
{:class="in"}

What just happened? If you want to remove everything within scratchpad no matter what, you will need to add the `-r` argument to function `rm`

~~~
rm -r scratchpad
~~~
{:class="in"}

You can also create an entire directory structure with a single call (unfortunately this shortcut does not work in GitBash). e.g.

~~~
cd
mkdir -p test_project/{R,data,output/{data,figures},doc}
ls test_project/
~~~
{:class="in"}

This will create a project called `test_project` with the following structure:

~~~
|-- R/
|-- data/
|-- output/
|-- |-- data/
|-- |-- figures/
|-- doc/
~~~
{:class="out"}

One could also create lots of subdirectories at once using curly brackets expansions.

~~~
mkdir temp
cd temp
ls
mkdir dir-{0..10}
ls
rm -r temp
~~~
{:class="in"}

## Exercise

Using the shell, create a folder on your desktop for materials from this
workshop that looks like this.

~~~
|-- swc-wise-umich/
|-- |-- data/
|-- |-- |-- (data files here)
|-- |-- R/
|-- |-- |-- (R scripts here)
|-- |-- notes/
~~~
{:class="out"}

***
Acknowledgments: these lessons were adapted by Kara Woo from materials by [Diego Barneche](http://nicercode.github.io/2014-02-13-UNSW/lessons/60-shell/).
