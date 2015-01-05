---
layout: lesson
root: ../..
Title: Shortcuts and wildcards
---

# Saving time with shortcuts, tab completion and wild cards

## Shortcuts

There are some shortcuts which you should know about. Dealing with the home
directory is very common. So, in the shell the tilde character, `~`, is a
shortcut for your home directory. Navigate to the `data` directory in your
workshop directory, then enter the command:

~~~
$ ls ~
~~~
{:class="in"}

This prints the contents of your home directory, without you having to type the
absolute path. The shortcut `..` always refers to the directory above your
current directory. If I'm located at `/Users/Kara/Desktop/swc-wise-umich/data/`, thus:

~~~
$ ls ..
~~~
{:class="in"}

prints the contents of the `/Users/Kara/Desktop/swc-wise-umich/`. You can chain
these together, so:

~~~
$ ls ../../
~~~
{:class="in"}

prints the contents of `/Users/Kara/Desktop`. Finally, the special directory `.` always refers to your current directory. So, `ls` and `ls .` do the same thing, they print the contents of the current directory. To summarize, the commands `ls ~`, `ls ~/.` and `ls /Users/Kara` all do exactly the same thing. These shortcuts are not necessary, they are provided for your convenience.

## Tab completion

Bash and most other shell programs have tab completion. This means that you can begin typing in a command name or file name and just hit tab to complete entering the text. If there are multiple matches, the shell will show you all available options.

~~~
$ cd ~/Desktop/swc-wise-umich
$ cd d<tab>
~~~
{:class="in"}

What just happened?

Let's say we want to view the `head` of some data. Try pressing `head i`, then hitting tab?

When you hit the first `tab`, it fills in `inflammation-` because files starting with `inflammation-` are the only things beginning with `i` in this directory. When you hit `tab` again, the shell will list all the files that begin with `inflammation-` in this directory. In this case after the first tab you could type the number of the file you wanted to view the head of, and then hit `tab` again.

~~~
$ head i<tab>06<tab>
~~~
{:class="in"}

Tab completion can also fill in the names of programs. For example, type `e<tab><tab>`. You will see the name of every program that starts with an e. One of those is echo. If you enter `ech<tab>` you will see that `tab` completion works.

## Wildcards

One of the biggest reasons using shell is faster than ever using a GUI file manager is that it allows for wildcards. There are special characters known as wildcards. They allow you to select files based on patterns of characters.

Wildcard examples:

* `*` Matches any character;
* `?` Matches any single character;
* `[characters]` Matches any character in this set;
* `![characters]` Matches any character NOT in this set.

By default, `ls` lists all of the files in a given directory. The `*` character is a shortcut for "everything". Thus, if you enter `ls *`, you will see all of the contents of a given directory. Now try this command:

~~~
$ ls *.csv
~~~
{:class="in"}

This lists every file that ends with a `.csv`. This command:

~~~
$ ls /usr/bin/*.sh
~~~
{:class="in"}

lists every file in `/usr/bin` that ends in the characters `.sh`. And this command:

~~~
$ ls s*.csv
~~~
{:class="in"}

Lists all csv files in the current directory whose names begin with the letter s.

**Exercise:** View the head of all of the inflammation data files using one command.

*Ask for several learners' examples - there are many ways to do accomplish this exercise, e.g.*

~~~
$ head i*
$ head i*.csv
$ head inflammation*.csv
~~~
{:class="in"}

What if there were also a file called `influenza.csv`? Or `inflammation.doc`? Which examples would still work?

## Command History

You can easily access previous commands.  Hit the up arrow. Hit it again.  You can step backwards through your command history. The down arrow takes your forwards in the command history.

* ^-C will cancel the command you are writing, and give you a fresh prompt;

You can also review your recent commands with the `history` command. Just enter:

~~~
$ history
~~~
{:class="in"}

to see a numbered list of recent commands, including this just issues `history` command.  You can reuse one of these commands directly by referring to the number of that command.

If your history looked like this:

~~~
259  cd
260  ls gapminder
261  history
~~~
{:class="out"}

then you could repeat command #260 by simply entering:

~~~
!260
~~~
{:class="in"}

(that's an exclamation mark, or `bang`).


## Getting help

* If you're not sure where a program is located, use `which`

e.g.

~~~
$ which git
~~~
{:class="in"}

***
Acknowledgments: these lessons were adapted by Kara Woo from materials by [Diego Barneche](http://nicercode.github.io/2014-02-13-UNSW/lessons/60-shell/).
