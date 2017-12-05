# Intro to Pandoc

## Garret Christensen

[Pandoc](http://pandoc.org/) is a command line tool to convert documents from one type to another. Kind of like [Professor Farnsworth](https://youtu.be/wGKxWatPkd0).
![](http://www.futurama-madhouse.net/bios/bioFarnsworth.jpg)

### Installing Pandoc

Pandoc is included when you install RStudio, and likely other things too (like the Anaconda installation of Python).
To make sure you have it, type `which pandoc` or `pandoc --version` in the command line. If it's not installed, download it [here](https://pandoc.org/installing.html).

### Using the Command Line
The command line is the way to type commands directly to your computer. On a Mac, look in ./Applications/Utilities/Terminal. Windows usually comes with 'Powershell' installed, but I like [Git Bash](https://git-scm.com/download/win).
If you're using Linux, I'm going to assume you know what you're doing.

We'll go over some basic commands, a more complete list is [here](https://lifehacker.com/5633909/who-needs-a-mouse-learn-to-use-the-command-line-for-almost-anything). Software Carpentry has a nice tutorial [here](http://swcarpentry.github.io/shell-novice/).

Just a few of the very basics:
* `whoami` to check the current user
* `cd` to change directory. Follow with `directoryname` to go down into a directory, or `..` to go up a level
* `pwd` to see the present working directory
* `ls` lists the contents of the current directory.

### Reproducibility
What does this have to do with transparency or reproducibility?

It can help you automate stuff! If you routinely produce a report, and want to put it on the web, or you wrote in LaTeX and a journal doesn't accept that so you need to submit in Word, or if you hate the Microsoft Word Equation Editor (because who doesn't?) Pandoc is your friend.

### Simple Conversion

`pandoc --help` to see all the options. The general setup is `pandoc <existingfile.type> <newfile.type>`.


#### Change Output Format
By default output is html.

So type `pandoc militaryrecruiting.tex`. But this just outputs the file to the command line.

To save the output to a new html file: `pandoc militaryrecruiting.tex -o militaryrecruiting.html`

(The easiest way to open any of your output files is just type `open <filename>`.)

Just change the extension to get whatever output file you like.
`pandoc militaryrecruiting.tex -o militaryrecruiting.docx`

`pandoc militaryrecruiting.tex -o militaryrecruiting.odt`

You'll notice some labels and references don't look so hot immediately, but footnotes are great, and a lot (but not all) of the math is nice.

To try Markdown, try converting the README file to html. To go from MS Word to LaTeX, send the Word paper back to TeX. How are the original and re-converted different?

#### References
To get the references, tell pandoc where the .bib file is.
 `pandoc militaryrecruiting.tex -o militaryrecruiting.docx --bibliography=military_bib.bib --csl=chicago-author-date.csl`

Note that you also have to tell it about the citation style file.

#### Make a Script
If you wanted to really automate this, you could make the conversion part of a shell script. Put the command into a text file, which you can do directly, or with the `echo` command:

`echo "pandoc militaryrecruiting.tex -o militaryrecruiting.docx --bibliography=military_bib.bib --csl=chicago-author-date.csl">>shellscript.sh`

Then you can run that script by typing:

`bash shellscript.sh`

Or you could run that in Stata with:

`!bash shellscript.sh`


### Issues
Do you have issues? Pandoc is open source and [on GitHub](https://github.com/jgm/pandoc).

I haven't been able to get complicated tables to work. That's potentially a big limitation.

Non-ASCII characters can screw things up. (Apparently, BibTeX doesn't support Unicode.) For example, try converting my "Manual of Best Practices" into HTML.

`pandoc Manual.tex -o Manual.html --bibliography=test.bib`

There definitely is a way to fix this!

One way would be to use `iconv` to clean up the .bib file. This should convert a UTF-8 file to ASCII. F is for from, t is for to, and c discards any unconvertable characters.

`iconv -c -f utf-8 -t ascii  test.bib>clean.bib`

(You could also try using `sed`, the stream editor: `sed -i 's/[\d128-\d255]//g' MYFILE.txt` to remove all the non-ASCII characters.)

### Harness the Full Power of Pandoc
Test your powers by seeing if you can convert Jake Bowers & Martin Voors paper "[How to improve your relationship with your future self (V 2.0)](https://github.com/jwbowers/workflow)"
![](https://i.pinimg.com/originals/25/e1/0a/25e10a98cf2dd1659dbb9f364343d7f4.jpg)
