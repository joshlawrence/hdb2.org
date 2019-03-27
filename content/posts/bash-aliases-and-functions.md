---
title: "Bash Aliases and Functions"
date: 2019-03-26T20:31:02-05:00
draft: false
toc: false
images:
tags:
  - bash
  - linux
  - scripting
  - macos
---

Using aliases and functions can make working on the command line more efficient and fun. There are no shortage of examples on the Internet; here are a few I've found to be useful.

_For more on the difference between an alias and a function, check out this thread on Stackexchange [here](https://unix.stackexchange.com/questions/30925/in-bash-when-to-alias-when-to-script-and-when-to-write-a-function)._

---

## Writing with nano

    alias nano="nano -m -u -W --tabsize=4 --fill=80 --autoindent --smooth"

While vim and emacs are great text _editors_, it's not always easy to configure them for simple writing.  This alias starts the nano editor with sane defaults (observing the 80 column rule, of course).

## Merging PDF files

    # macOS specific
    alias mergepdf="/System/Library/Automator/Combine\ PDF\ Pages.action/Contents/Resources/join.py"

Did you know that macOS comes with python script for joining PDF files?  It does, and this alias makes it easy to use it.  Using it is pretty easy:

    mergepdf -o outputfile.pdf inputfile1.pdf inputfile2.pdf ...

It can also shuffle the input files; take a look at the `join.py` source for more information.

## Pretty man pages

```bash
pman () {
  man -t $1 | open -fa /Applications/Preview.app
}
```

This one isn't necessarily all that useful, but it's _very_ cool...make man pages pretty!

## Create and enter a directory

```bash
mkcd() {
  mkdir -p $1; cd $1
}
```

From pretty to pragmatic, this one is my personal favorite due to it's simplicity and usefulness: Create a directory then cd into it.  

## Use

On my macOS machine, my aliases and functions are defined in `~/.bash_profile` (look for `~/.bashrc` on a Linux machine).  I only have a few functions so I just keep those in the profile file, but I split out the aliases in a separate file (`.bash_aliases`).  In your `.bash_profile` you can source the aliases file like so:

```bash
if [ -f ~/.bash_aliases ]; then
  source ~/.bash_aliases
fi
```

Enjoy!