# Intro to Pandoc

## Garret Christensen

[Pandoc](http://pandoc.org/) is a command line tool to convert documents from one type to another.

### Installing Pandoc

Pandoc is included when you install RStudio, and likely other things too (like the Anaconda installation of Python).
To make sure you have it, type `which pandoc` in the command line. If it's not installed, download it [here](https://pandoc.org/installing.html).

### Using the Command Line
The command line is the way to type commands directly to your computer. On a Mac, look in ./Applications/Utilities/Terminal. Windows usually comes with 'Powershell' installed, but I like [Git Bash](https://git-scm.com/download/win).
If you're using Linux, I'm going to assume you know what you're doing.

We'll go over some basic commands, a more complete list is [here](https://lifehacker.com/5633909/who-needs-a-mouse-learn-to-use-the-command-line-for-almost-anything). Software Carpentry has a nice tutorial [here](http://swcarpentry.github.io/shell-novice/).

Just a few of the very basics:
* `whoami` to check the current user
* `cd` to change directory. Follow with `directoryname` to go down into a directory, or `..` to go up a level
* `pwd` to see the present working directory.

### Simple Conversion
