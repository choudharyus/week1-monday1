# The CLI (Command Line Interface)

[![Build Status](https://travis-ci.org/ga-wdi-lessons/cli-intro.svg?branch=master)](https://travis-ci.org/ga-wdi-lessons/cli-intro)

## Learning Objectives

### Concepts

- Compare and contrast CLIs / GUIs
- Explain how command line usage can increase efficiency
- Describe the anatomy of a command (statement, flags, arguments)
- Explain what a path is, and why the 'current path' is important in the CLI
- Explain the difference between an absolute path and a relative path

### Mechanics

- Setup your working directory / environment for WDI
- List common commands to
  - View the path of the current directory
  - View the contents of a directory
  - Navigate to different directories
  - Manage files and directories
- Open files and directories with Atom
- List unsafe commands

## Framing(5/5)

As developers, we need a tool to interface with our computers. OS's generally provide a graphical user interface or GUI so that we can interface with our computer. They also provide a UI that is strictly text based.

Turn & Talk: Given your exposure to the command line so far (prework and
installfest), discuss the following questions:

* How is the CLI different from the GUI?
* What do you like / dislike about using it?
* It what ways might it be better or worse for Developers? (Compared to a GUI)

![](http://coding-journal.com/wp-content/uploads/2013/10/Screen-Shot-2013-10-30-at-12.02.14.png)

---------------------------------------------------------------------------

### Why The CLI? (10/15)

Why? Because if you want to learn to code, then you must learn how to use the CLI. Programming languages are advanced ways to control your computer with language. Learning the command line teaches you to control the computer using language. Once you get past that, you can then move on to writing code and feeling like you actually can make the hunk of metal in front of you do what you want.

The CLI has many benefits over a GUI:

**Speed**
While it may not seem so yet, over time, most developers can achieve common
tasks much faster using the command line. Features such as tab completion,
history searching / modifying, and piping commands all contribute to this speed.

**Precision**
Because of its nature as a text-based interface, the command line provides us
with a lot more precision. We can look at the commands we're about to enter
and understand exactly what they will do. This also allows:

**Repeatability / Scriptability**
The precision of commands and their text-based nature means we can easily save
them and re-use them, or share them with others when appropriate. If you think
back to the commands you ran during installfest, those were basically a set of
scripts that we had you run.

**Tools**
There are a very large number of tools available on the command line, to help
us achieve almost any task. Most of them are built in, but we can download
almost any others using `brew` on a mac, or `apt-get` on linux.

Additionally, tools built for the command line usually follow something called
the ['unix philosophy'](http://catb.org/esr/writings/taoup/html/#id2807216), which is that each tool should do ~1 thing, and do it
well. Complex tasks can be achieved by chaining tools together.

## DEMO: JS - Hello World Program using GUI vs CLI

> Note: There's nothing wrong with combining the powers of both the CLI and a GUI!

We might be thinking to ourselves, "These differences are negligible! Which in this contrived example, it's a difference of MAYBE 5 seconds. But in the span of our careers as developers, becoming proficient with the command line is extremely important. It will end up saving us lots of time.
--------------------------------------------------------------------------------

## Basics of CLI (45/60)

You may already be familiar with some of these concepts, but it's worth
reviewing them now, cementing the concepts and getting some more practice in.

### Everything is a command

First things first, on the command line, everything we enter into the command
line is a **command**. When we hit enter, the command is executed.

### Commands have output and side effects

Some commands have **output**, which is displayed on the screen for us to see.
Examples of commands that have output might be:

* `pwd`
* `ls`
* `telnet towel.blinkenlights.nl`

Other commands primarily exist to have a *side-effect*, or in other words, to
make some change, usually on our system. An example might be `touch`, which
creates a new file.

Note that often times, a command whose main job is a side effect may not provide
any output if it succeeds. If there is an error it will provide output.

Rarely, some commands may provide both an output and side effects.

### Command Syntax (Flags and Arguments)

**See `haircut` command for demo.**

    $ ./haircut --mohawk adrian

Commands generally consist of three parts, the command, followed by flags (aka
options), and finally arguments.


The **command** is the first 'word', e.g. `ls`, `cd`, or `touch`. It is like the
verb, which says generally, 'what do we want to do'.

Next come the **flags** or **options**. These are optional; you may not use them
for some commands. As the name implies, they set options to tell the command
**how** to do what it's about to do. There may be zero or more options. Options
usually start with one or two dashes. Usually one dash is for a short one letter
abbreviation, while two dashes is for long name for the option.

http://catb.org/esr/writings/taoup/html/ch10s05.html#id2948149

Finally come the arguments. These are what you want to do the action to. Usually
these are file names, but they could be URLs, or other things.

#### Common Patterns

The commands given to a CLI shell are often in one of the following forms:

- `doSomething how toFiles`
- `doSomething how sourceFile destinationFile`

Where *doSomething* is, in effect, a verb, *how* an adverb (for example, should the command be executed "verbosely" or "quietly") and *toFiles* an object or objects (typically one or more files) on which the command should act.

Let's take a look at something we did for installfest.

```
$ brew install git
```

> When we type this command and hit enter , we're saying, "Computer, we're about to do something with homebrew. The thing were going to do is install something. What we want to do is install it.

It should be noted that all commands follow this pattern, but many do.

### Commands run in an 'environment'

We won't go deep into environments yet, but everytime a command is run, it may
choose to look at what are called `environment variables`. These are essentially
variables that are semi-permanent and can provide information or options to help
a command do its job.

--------------------------------------------------------------------------------

## BREAK (10/70)

--------------------------------------------------------------------------------

## Paths (35/105)
### What is a 'path'?

A path is the description that tells us (or a computer) where a file or folder
is on our computer.

Our terminal (shell) is always working out of a single path at a time. Commands
that are run will take action in the current path (directory) unless we tell
them to do otherwise.

Before we get too deep into paths. Let's review a couple of important commands that we'll be using frequently through the course.

- `pwd` - outputs the current working directory(print working directory)
- `cd` - changes directories(change directory)
- `ls` - lists folders and files(list)

### Relative vs Absolute Paths

All paths point to a single file or folder, but we can write paths to be either
**relative** or **absolute**.

#### Absolute Paths

An absolute path will always tell us exactly where the file or folder is. An example in the real world would be a mailing address:

GA
8th Floor
1133 15th St NW
Washington, DC 20003
USA
Earth
Solar System
Milky Way

Absolute paths start with a `/` and go from top down (least specific to more specific):

```bash
/Milky_Way/Solar_System/Earth/USA/Washington_DC/1133_15th_St_NW/8th_Floor/GA
# or a realistic example
/Users/adambray/code/work/general_assembly/courses/wdi/dc/dc8/lessons/cli-intro/
```

The first slash essentially means "start at the root of the computer's file system".

Some absolute paths instead start with a `~`. This is a shortcut to the absolute
path of our home directory. So the above absolute path could also be written as

```
~/code/work/general_assembly/courses/wdi/dc/dc7/curriculum/01-front-end/
```

#### Relative Paths

Relative paths are interpreted starting from the directory we're in (aka the
current working directory).

They start with anything but a slash `/` or a tilde `~`.

So if we were in our home directory, the path to our work folder could be written

```bash
code/work                     # relative
~/code/work                   # absolute
/users/adambray/code/work/    # absolute
```

If we were in a different folder, then the relative path would point to an
entirely different folder/file.

Periods or dots are special in relative paths:
* One dot means "relative to the current directory"
* Two dots means "go up to the parent directory"

So if we're in `~/code/work` then the relative path `../personal_projects` means "go up one level to the code folder, then down into my `personal_projects` directory.

**Note**: We can use multiple `..` to go up multiple levels:

`../../documents/top_secret/lol_cats/favorites/so_many_kittenz.jpg` would go up two levels, from `~/code/work` to `~` (my home directory), and then down into my favorite lolcat picture.

--------------------------------------------------------------------------------

## Common Commands

### Getting help / info (5/110)

There are three general ways to get help with a command.

* add `--help` or `-h` to the end of the command. e.g. `brew --help`
* use the `man` tool (manual), e.g. `man brew`
* search google

### Common Command Teachbacks (15/125)

Form groups of ~3 and spend 15 minutes researching and preparing a short demo
of your command. Focus on:

* what it does
* common uses
* common flags or arguments
* any 'gotchas'?

#### Commands

1. tab completion
2. ls
3. cd
4. touch / mkdir
5. cp
6. mv
7. rm
8. atom

--------------------------------------------------------------------------------

## BREAK (10/130)

--------------------------------------------------------------------------------

## Unsafe Commands (10/140)

### sudo

`sudo` runs the command that follows as the SuperUser, aka 'root' or 'admin'.
This means the command could potentially have destructive effects.

Generally, you shouldn't need to run commands with sudo in this course. If
you're not sure, ask an instructor.


### rm

`rm` deletes files with no confirmation, and there's no `trash` to recover them
from. Use `rm`, and especially `rm -rf` with caution.

## WDI Environment (10/150)

### Directory Structure

Here's the suggested structure for your WDI folder. Please create the following
folders if they do not exist.

  * ~/wdi
    * sandbox
    * exercises
    * lessons
    * projects

--------------------------------------------------------------------------------

## If time allows - aliases in your bash profile

You may have noticed during installfest that the instructors messed with the `~/.bash_profile` file. During installfest, we changed the  `~/.bash_profile` to change your prompt to a better one! Turns out, there's a lot you can do with the  `~/.bash_profile`.

There will be commands that you'll find yourself doing frequently it may become a pain to continue to type commands out all the time. It would be really nice if we could shorten some of these commands... enter aliasing. Aliasing is really quite simple!

Let's open our  `~/.bash_profile` in atom and type in the following:

```
alias greeting="echo 'hello world'"
alias gs='git status'
```

### You do - Make an alias
Take the next 5 minutes to create your own alias and test it!

Try and alias something you think you'll find yourself doing frequently!

## Homework
### To OZ

[To Oz](https://github.com/ga-wdi-exercises/to_oz)

To Submit:

1. Go to the [issues page for the oz exercise](https://github.com/ga-wdi-exercises/to_oz/issues)
2. Click 'New Issue’.
3. For the title, just put “Day 1 HW” or something similar
4. For the description, copy paste the commands you used to complete the oz exercise.

### Further Practice (Optional)

- [Command Line Fu](https://github.com/ga-wdi-exercises/command_line_fu)
- [Kitchen Organizer](https://github.com/ga-wdi-exercises/kitchen_organizer)


--------------------------------------------------------------------------------

## Sample Quiz Questions

- Why would a developer prefer the command line over a GUI?
- Write a command to list only files beginning with your first name.  Label the parts of the command.
- Where can we find help for shell commands?
- Describe 4 bash commands for managing folders and files.
- Describe 2 unsafe commands
- You are currently in the "code" folder in the below file tree. How would you get to the folder that contains "beach.png" using the command line?
```
home
├── documents
│   └── code
├── photos
│   ├── headshot.jpg
│   └── summer_vacation_2014
│       └── beach.png
└── videos
```

## Hungry for More?

Here are some advanced commands worth checking out that we may not explicitly go over in class:

* grep
* cat
* less
* find
* tmux
* cal
* vim
  * vimtutor

## Feeling Adventurous?

Bash isn't the only option. Check out zsh (http://code.joejag.com/2014/why-zsh.html) or fish (http://fishshell.com/)

## Glossary

- **Prompt** — is a sequence of (one or more) characters used in a command-line interface to indicate readiness to accept commands. Its intent is to literally prompt the user to take action. A prompt usually ends with one of the characters `$`, `%`, `#`, `:`, `>` and often includes other information, such as the path of the current working directory.

- **Arguments(Parameters)** — are items of information provided to a program or command when it is started. A program can have many command-line arguments that identify sources or destinations of information, or that alter the operation of the program.

- **Flags(Options)** — modify the operation of a command; the effect is determined by the command's program. Options follow the command name on the command line, separated by spaces. 

- **Path** - is the description that tells us (or a computer) where a file or folder is on our computer.
