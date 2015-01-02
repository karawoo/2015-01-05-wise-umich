---
layout: lesson
root: ../..
Title: Creating, moving, and deleting files and directories
---

## Creating an empty file

Lets create an empty file using the `touch` command. Enter the command:

```
$ touch testfile
```

Then list the contents of the directory again using `ls`. You should see that a new entry, called `testfile`, exists. It does not have a slash at the end, showing that it is not a directory. The `touch` command just creates an empty file.

Some terminals can color the directory entries in this very convenient way. In those terminals, use `ls -G` instead of `ls` if you are on a Mac or `ls --color` if you run on Windows. Now your directories, files, and executables will have different colors.

Now if you use the command `ls -l` you will notice that `testfile` has a size of zero. OK then, let's get rid of `testfile`. To remove a file, just enter the command:

```
$ rm -i testfile
```

When prompted, type:

```
$ y
```

The `rm` command can be used to remove files. The `-i` adds the "are you sure?" message. If you enter `ls` again, you will see that `testfile` is gone.

***Warning: The shell does not have a recycling bin. So any file removed with `rm` is gone forever. Use with caution. Remember the -i argument***

## Manipulating the file system

Make directories with `mkdir`

```
mkdir directory_name
```

You can create as many folders as you like in a single call.

```
mkdir directory_name_1 directory_name_2 directory_name_3
```

Copy files with `cp`

```
cp file1 file2
```

Move files with `mv`

```
mv file1 file2
```

See the `man` command to get help on options you can use with these commands.

Remove files with `rm`

## Let's try out some of the commands above

First go home `cd`.
Next create a temporary directory.

```
cd
mkdir scratchpad
cd scratchpad
```

Make a few directories inside `scratchpad`

```
mkdir dir1 dir2 dir3
cp ../gapminder/R/*.R .
```

What did just happened?

```
ls -l
```

Now try and remove scratchpad

```
rm scratchpad
```

What did just happened? If you want to remove everything within scratchpad no matter what, you will need to add the `-r` argument to function `rm`

```
rm -r scratchpad
```

You can also create an entire directory structure with a single call. e.g.

```
cd
mkdir -p test_project/{R,data,output/{data,figures},doc}
ls test_project/
rm -r test_project/
```

This will create a project called `test_project` with the following structure:

|-- R/
|-- data/
|-- output/
|-- |-- data/
|-- |-- figures/
|-- doc/

One could also create lots of subdirectories at once using curly brackets expansions.

```
echo Experiment-{A,B,C}-master
echo {01..15}
# nest these patterns
echo a{A{1,2},B{3,4}}b
```

Notice that this shortcut using curly brackets does not work in GitBash.

```
mkdir temp
cd temp
ls
mkdir dir-{0..10}
ls
rm -r temp
```



***
These lessons were adapted from materials by [Diego Barneche](http://nicercode.github.io/2014-02-13-UNSW/lessons/60-shell/)
