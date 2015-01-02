---
layout: lesson
root: ../..
Title: Shortcuts and wildcards
---

# Saving time with shortcuts, tab completion and wild cards

## Shortcuts

There are some shortcuts which you should know about. Dealing with the home directory is very common. So, in the shell the tilde character, `~`, is a shortcut for your home directory. Navigate to the `data` directory in your shell lesson material directory, then enter the command:

```
$ ls ~
```

This prints the contents of your home directory, without you having to type the absolute path. The shortcut `..` always refers to the directory above your current directory. If I'm located at `/Users/barneche/gapminder/data/`, thus:

```
ls ..
```

prints the contents of the `/Users/barneche/gapminder/`. You can chain these together, so:

```
ls ../../
```

prints the contents of `/Users/barneche` which is my home directory. Finally, the special directory `.` always refers to your current directory. So, `ls` and `ls .` do the same thing, they print the contents of the current directory. To summarize, the commands `ls ~`, `ls ~/.` and `ls /Users/barneche` all do exactly the same thing. These shortcuts are not necessary, they are provided for your convenience.

## Tab completion

Bash and most other shell programs have tab completion. This means that you can begin typing in a command name or file name and just hit tab to complete entering the text. If there are multiple matches, the shell will show you all available options.

```
cd
cd gap<tab>
```

What just happened?

Try pressing `d`, then hitting tab?

When you hit the first `tab`, nothing happens. The reason is that there are multiple files and/or directories in the gapminder directory which start with `d`. Thus, the shell does not know which one to fill in. When you hit `tab` again, the shell will list the possible choices.

Tab completion can also fill in the names of programs. For example, type `e<tab><tab>`. You will see the name of every program that starts with an e. One of those is echo. If you enter `ech<tab>`` you will see that `tab` completion works.

## Wildcards

One of the biggest reasons using shell is faster than ever using a GUI file manager is that it allows for wildcards. There are special characters known as wildcards. They allow you to select files based on patterns of characters.

Wildcard examples:
`*`             Matches any character;
`?`             Matches any single character;
`[characters]`  Matches any character in this set;
`![characters]` Matches any character NOT in this set.

Navigate to the `gapminder/data` directory. This directory contains examples of sequencing data. If we type `ls`, we will see that there are a bunch of files which are just four digit numbers. By default, `ls` lists all of the files in a given directory. The `*` character is a shortcut for "everything". Thus, if you enter `ls *`, you will see all of the contents of a given directory. Now try this command:

```
$ ls *1.txt
```

This lists every file that ends with a `1.txt`. This command:

```
$ ls /usr/bin/*.sh
```

lists every file in `/usr/bin` that ends in the characters `.sh`. And this command:

```
$ ls *9*1.txt
```

lists every file in the current directory which contains the number `9`, and ends with the number `1` and the extension `.txt`. There are three such files: `3901.txt`, `7901.txt`, and `9901.txt`.

So how does this actually work? Well...when the shell (bash) sees a word that contains the `*` character, it automatically looks for files that match the given pattern. In this case, it identified four such files. Then, it replaced the `*9*1.txt` with the list of files, separated by spaces. In other the two commands:

```
$ ls *9*1.txt
$ ls 3901.txt 7901.txt 9901.txt
```
are exactly identical. The `ls` command cannot tell the difference between these two things.

## Command History

You can easily access previous commands.  Hit the up arrow. Hit it again.  You can step backwards through your command history. The down arrow takes your forwards in the command history.

* ^-C will cancel the command you are writing, and give you a fresh prompt;
* ^-R will do a reverse-search through your command history. This is very useful.

You can also review your recent commands with the `history` command. Just enter:

```
history
```

to see a numbered list of recent commands, including this just issues `history` command.  You can reuse one of these commands directly by referring to the number of that command.

If your history looked like this:

```
259  cd
260  ls gapminder
261  history
```

then you could repeat command #260 by simply entering:

```
!260
```

(that's an exclamation mark, or `bang`).


## Getting help

* If you're not sure where a program is located, use `which`

e.g.

```
which git
```

***
These lessons were adapted from materials by [Diego Barneche](http://nicercode.github.io/2014-02-13-UNSW/lessons/60-shell/)
