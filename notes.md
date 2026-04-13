# Git Course

# Introduction

## What Exactly is Git?

- a Version Control System, commonly shortened to **"VCS"**
    - software that tracks and manages changes to a set of files over time
    - revisit older versions of files, compare changes between versions, undo changes, and etc.
- git is just one of many different vcs options out there
    - cvs, mercurial, subversion are some others to look into

## Visualizing Git

- save points in a video game is the simplest way to describe it to newbies

## History o' Git

- Linus Torvalds, dev behind Linux and Git
- in 2005 on Linux, he got annoyed with current VCS options cause they were paid, closed-source crap
    - April 2005 is basically when it was created by Linus
    - he called it "stupid content tracker" lol
    - "global information tracker" is the corpo cleaned up meaning
    - "goddamn idiot truckload" of shit when you get a problem

## Who uses Git?

- engineers, devs, coders, and such
- tech-adjacent roles, like folks who work with devs or dev teams
- governments
    - used in drafting of laws
    - washington dc city council uses git and github
- scientists
- writers
- anyone really lmao

## Git vs. GitHub

- they ain't the same, but closely related
- git is the vcs that runs on someone's machine
    - no account needed
    - no internet needed
    - can use it without ever touching github
- github is a service, a web service specifically
    - takes repositories (aka projects) that stores them in cloud
    - helps with collab online
    - need internet and an account
    - takes your local repo and hosts it online for others to see or collab
    - aka the connecting tissue of group work

# Installtion and Setup

## Terminal vs. GUIs

- git is primarily a terminal tool
    - run various git commands in a unix shell of some kind
    - not user friendly, but the core of how git works
    - **pros**
        - all documentation and resources online refer to the command line
        - way faster if you're comfortable
        - advanced features only doable with commands
        - commands are univeral across all machines
    - **cons**
        - not beginner friendly at all
        - even for experienced folks, the text-based output can be a difficult experience :(
- GUIs have grown in popularity to visualize interaction with git
    - GitHub Desktop, GitKraken, SourceTree, and many more
    - **pros**
        - way lower barrier of entry for newbies
        - friendlier to use when it works
        - some peeps gotta have a visual experience
    - **cons**
        - a lot of "magic" involved behind the scenes which obfuscates git core
        - leads to dependance on a particular software
        - if things go really fuckin' sideways you can't really fix without the command line
        - GUIs vary a lot between each so "skills" don't translate easily

## Windows Install

- a tad more complicated than mac install
- designed to run in a unix-based interface
- windows don't come with a unix-based prompt by default
    - uses command prompt instead ugh
- **git bash** is typically the solution
    - emulates a window's bash experience with git stuff built in
- can just do the git installer for windows with _git-scm.com_
- output a test with `git --version`

## Mac Install

- some come with git already installed
- want to use version **2.23.x** and above
- installer from _git-scm.com_ with binary installer

## Configuring Git Name & Email

- use a name people that know you by
- use the email linked to your github account
- can be re-configured whenever you want :D

```bash
# configure it
git config --global user.name "blah"
git config --global user.email "blah@blah.com"

# test it
git config user.name
git config user.email
```

## GitKraken

- free tier is solid, paid tier is not needed
- [https://www.gitkraken.com/](https://www.gitkraken.com/)
- register, preferably with your github account as the option, but not technically necessary

# Basics of Git: Adding & Committing

## What is a Git Repo?

- repository, aka repo, is a workspace which tracks and manages files within a folder

## First Commands `git init` & `git status`

- `git status` is a command to report the status in current repo
- `git init` initializes a new repo wherever you are in your command line
    - one-time per project, yo
    - a `.git` directory added with subs for objects, red/heads, and ref/tags

### The Mysterious `.git` Folder

- remember `ls -a` shows hidden files, too, when you wanna explore and goof in the `.git` dir

### Common Early Mistakes

- when you initialize a git repo, it's one directory
- git will watch anything happening in that directory, including _any nested directories_
    - it's top-down tracked by git
- **do not** initialize a git repo inside another existing repo
    - not end of the world, but it will go wrong at some point
- always just check with `git status` first and confirm you're not in a git repo already before using `git init`

## The Committing Workflow Overview

- a git commit is basically a "checkpoint" or a "snapshot" of a moment in time
- not the same as saving a file, think of it as something "on top of" saving a file
    - we can group saved changes together to a single commit rather than each "saving" of each file
- TL;DR Workflow
    - Work on Stuff
    - Add Changes
    - Commit
- working directory > git add > staging area > git commit > repo

### The `git add` Command

- allows us to separate specific changes we made to group them together
    - this places them from our working dir into staging
        - (commit moves them to the local repo)
- location: working directory
    - the place we're actually working on our project
- location: repository
    - the actual `.git` folder itself
        - the `git commit` adds commits to this folder, this is what is updated during the workflow
- location: staging area (the intermediate area)
    - where we add our changes to before we make a commit
- `git add file1 file2 ...`
    - separate files by spaces, globbing patterns do work here e.g. `git add src/types/*.ts`
- `git add .`
    - stages all changes at once

### The `git commit` Command

- the command we use to actually make a commit to whatever changes we have staged
- commit expects us to include a message that describes or summarizes the changes in that given commit snapshot
- `git commit` simple as
    - it will use default editor e.g. VIM to write a message
- `git commit -m "my message"` lets us just add the message at the same time
- working tree clean means everything we've done in our main working folder and git knows about is in sync

### The `git log` Command

- doesn't do anything really, just retreives info for us
- retrieves log of commits for our local repo
- the commit hash reported, good reference point
- untracked files and modified files
    - modified means git has been tracking that file already
    - untracked means its a new file not been comitted before