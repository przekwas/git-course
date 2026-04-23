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

# Commits in Detail

## Atomic Commits

- keeping each commit focused on a single thing
- makes it easier to undo changes or rollback stuff later on in the project lifespan
- makes code and project easier to review, too

## Commit Messages

- git docs specifically advocate for describing changes in imperative mood
    - "make fizz do buzz" instead of "this patch makes fizz do buzz" or "i changed fizz to do buzz"
    - kinda' like giving orders to the codebase
- present tense imperative or past tense imperative are two main schools of thougt
    - obviously follow what your team/company/org are doing
- extra links on topic:
    - https://medium.com/@corrodedlotus/which-tense-should-be-used-on-a-git-commit-message-121cb641134b
    - https://www.danclarke.com/git-tense/
    - https://www.quora.com/Which-tense-should-be-used-in-a-git-commit-message-past-present-and-why
    - https://stackoverflow.com/questions/3580013/should-i-use-past-or-present-tense-in-git-commit-messages
- on larger or open source projects sometimes we'll have paragraphs and bullets for the message
    - `git config core.editor` to output what it is
        - `code --wait` is the VS Code output
            - the wait flag basically waiting for us to edit the text commit message in VS Code before it continues on, save, and close it
    - so either get good at using VIM or just default to VS Code using links below in [The Git Docs](#the-git-docs)

### A Lil' Extra Look at `git log`

- if we got long commit messages they can clog the terminal/gui with lots of texts
- `git log --online`
    - shortrhand actually for `git log --pretty=oneline --abbrev-commit`
    - shorter version of that commit hash to quick search
    - the oneline shorthands each commit message to oneline with the hash
        - e.g. `<commit hash> fix fizz in buzz` as the output

## Amend Commits

- forgot to include a file or perhaps a typo or shitty commit message
- basically lets you "redo" the _previous_ commit only, not some commit 10 updates ago
- in the forgot a file to previous commit case:
    - `git add missing-file.txt`
    - `git commit --amend` which opens your editor with the previous commit message
        - if you just save and close it will include whatever you staged with `git add`

## Ignorin' Shit with `.gitignore`

- certain things you want not tracked ever by git
    - secrets, api keys, credentials
    - operating system files (looking at you `.DS_Store`)
    - log files
    - deps and packages
- just create a `.gitignore` file in the root of a repo
    - `folderName/`
    - `fileName.ext`
    - `*.log` glob patterns work
- [http://gitignore.io/](http://gitignore.io/)

### The Git Docs

- [https://git-scm.com/docs](https://git-scm.com/docs)
    - reference manual or book works
- [Git Commit Docs](https://git-scm.com/docs/git-commit)
- [Git Commands for Default Editor Setup](https://git-scm.com/book/en/v2/Appendix-C%3A-Git-Commands-Setup-and-Config)

# Workin' with Branches

## Introduction to Branches

- each commit gets a hash (SHA1)
- each commit references a parent commit that came before it
- so on large projects we work in multiple contexts e.g. one person on overhauling layout, one on new feature, one on bug fix, and etc.
    - if we only did linear commits this would never work and could break other folk's code
    - this is what branches are for
- branches are alternative timelines for projects
    - what we do on one branch will not affect other branches
        - until we merge :)
- you always work on a branch even if you don't create any new contexts
    - e.g. master or main
    - the main branch as the "source of truth" like the official working codebase
        - but it's a choice we get to make
        - git don't really care which branch is your main/production codebase

## What is the HEAD?

- it's a pointer that refers to the current "location" in a repo
- it points to a particular branch reference
- if a branch is a bookmark in a book
    - at any point in time we can only open the book to one bookmark
    - think of HEAD as the current location or the place we're viewing or checking out a particular bookmark
- the HEAD will default to the main/master branch's latest commit
    - (tip is the last commit)
- term originates on the "playhead" of an old analog tape deck

## Branching Commands

- `git branch` gives us a list of current branches in a repo
    - `*` indicates which branch you're currently on
    - type `q` to exit terminal stuffs lols
- `git branch <branch-name>`
    - makes a new branch based upon the current HEAD
        - _important_ the current branch we're on affects the newly created branch
    - just creates the branch, it does **not** switch you to that branch aka HEAD stays the same
- `git switch <branch-name>`
    - newer command, actually
        - `git checkout` the old school way
    - HEAD will now point to the tip of the branch you switched to
- `git checkout <branch-name>`
    - does the same as switch, but with a bunch of additional things
        - can restore working tree files and such
    - switch was added because it was a standalone simple command
- `git switch -c <branch-name>` the shorthand to create and switch in oneline
- `git branch -d <branch-name>` must be fully merged in its upstream branch before it will delete
    - can't delete one you're checked out at
    - can't delete it till it's fully merged but you can do the `-D` flag which is same as `-d --force` lol
- `git branch -m <branch-name>` to rename a branch
    - the `-m` flag is for "move" similar to the idea of how bash `mv` works for renaming something i guess
    - to rename you have to be _on that branch_ to rename it, again, how `mv` renaming works
- `git branch -v` outputs some additional info, like the shorthand commit hash and the oneline commit message
    - good way to see where HEAD is and what commit is the tip of that branch

## Unstaged Changes and Branches

- example: do some changes on a tracked file on one branch but do not commit
- try to switch branches
    - error "Please commit your changes or stash them"
- example: do some changes on an untracked file in a new branch with no conflict
- try to switch branches
    - untracked/unstaged file **WILL COME WITH YOU** to the new branch omg
- **REMEMBER**
    - sometimes you'll have merge conflicts so you get an error on branch switches
    - sometimes it'll bring over unstaged new stuff on branch switches
    - GENERALLY commit or stash to avoid this biggity-bullshit
- **REMEMBER**

### How Git Stores HEAD & Branches

- literally just files and folders references
- collections of bookmarks from that previous analogy
- inside of `.git` you can check the `HEAD` file
    - `cat HEAD` will tell you the `ref: refs/heads/<branch>` it's pointing to
    - the HEAD file just references a branch
- so like `refs/heads/master` is a file and is just a commit hash
- if `HEAD` points to a branch reference e.g. master, we get that `refs/heads/master`
    - and `refs/heads/master` is a file with a commit hash inside of it, and it's just the tip of that branch!

# Merging Branches

## Introduction to Merging

- incorporates one branch context into another
    - we do this via `git merge` oh boy!
    - you can also abandon a branch and not merge it
- common workflow is to treat master/main as the "trunk" aka source of truth or stable working code
    - add new feature on new branch
    - and then merge feature into master when tested and ready
- **two priciples** to remember:
    - we merge branches, not specific commits
    - we always merge to the current HEAD branch
- two basic steps:
    - switch to or checkout the branch you want to merge changes into (the receiving branch)
    - use the `git merge` command to merge changes from a specific branch into the current branch
- the simple merge with nothing else is a **fast forward** merge
    - and it contains the commits and works from the merged branch
    - the FF merge is just moving a branch pointer up to a new commit hash, that's basically it!

### Merge Commits

- let's say master gets a commit while we're on a bugfix branch
    - now master is 1 commit ahead of where our merge occurred so we cannot just do a fast forward merge
    - git can still resolve it for us _if_ there is no conflict :)
- a merge commit generated for us by git that moves master ahead
    - the first kind of commit that has **two** parents unlike a normal commit!!

## Merge Conflicts

- same as previous section example, but what if there's a conflict on lines of code?
- the files where there are conflicts are decorated to indicate the conflict itself
    - <<<<<<<<<<<<< HEAD
        - content on the recipient branch that we're mering into
    - =============
    - \>>>>>>>>>>>>> branch-name
        - this is from the branch we're trying to merge in
- **resolving conflict tl;dr steps**
    -   1. open the files with merge conflicts
    -   2. edit the files to remove the conflicts, deciding which branch's content you want to keep in each conflict
        - or keep content from both!
    -   3. remove the conflict marker symbols
    -   4. add your changes and make a commit
- vs code as your editor has some quick and nifty tools to help resolve conflicts, too

### Practice

- create a ff merge
- create a merge with no conflict that generates a merge commit
- create a merge with conflict

# Comparin' Changes with Git Diff

## Introduction to Diffing

- all about showing changes with git
- a command to view changes between commits, branches, files, our working dir, and lots more
- `git diff` can be overwhelming, but often used along with `git status` and `git log`
    - purely informative command
- `git diff`
    - no additional options lists all the changes in our working dir that are **NOT** staged for the next commit

### Guide to Reading Diffs

- the output from the diff follows a similar pattern for every output
- `diff --git a/file.example b/file.example`
    - files that are being compared, usually the same aka old and new version
        - could be different files if you diff it yourself
- next line doesn't matter too much, but it's meta data about the files compared
- `--- a/file.example`
- `+++ b/file.example`
    - just indicators for how changes will be marked
- chunks, the diff only shows us a lil' context before and after and just our changes
- chunk header `@@ -[set1 numbers] +[set2 numbers] @@`
    - numbers are how many lines extracted and what part of a file they start from
        - `-3,4` from file `a` 4 lines have been extracted starting from line 3

### Different Ways to Use Diffs

- `git diff`
    - all changes in working directory that are _not_ staged for the next commit
        - compares staging (index) and the working directory
        - the differences are what we _could_ tell git that we have to add to the stating area
- `git diff HEAD`
    - lists all changes in the working tree since your last commit
    - includes staged and unstaged changes
- `git diff --staged` or `--cached` (same just an alias)
    - show me what will be included in my commit staging area
- `git diff HEAD [filename]`
- `git diff --staged [filename]`
    - both commands just allow us to diff specific files and not all if it's a ton of work on a big project
    - can separate files by spaces to get multiple e.g. `git diff --staged file1.txt file2.txt`
- `git diff branch1..branch2`
    - diffs all files between branches, but we can narrow it down to specific files if we want
    - space or two dots works in the syntax e.g. `git diff branch1 branch2`
    - the order of the branches diff'ed DOES matter, so bear in mind the `+` and `-` markers for your a/b diff
- `git diff commit1..commit2`
    - changes between 2 commits in history, can be any you want not just between HEAD and some commit are
    - you'll need the commit hash to do the comparison though so it can be tedious lol

# Ins and Outs of Stashing

## Introduction to Stashing

- if we have a bunch of work unstaged and uncomitted one one branch and we, for whatever reason, need to switch back to our main branch
    - what happens? Either all our changes come with us to the destination branch
        - or `git` won't let us switch if there are potential conflicts
- it's not used by everyone, there's no situation where you _have_ to use it
- basically it's a quality of life topic to know about
- we can stash uncommited changes so that we can return to them later without having to make unecessary commits

### Basics of Stash

- `git stash`
    - takes all uncommited changes (staged and unstaged) and stash them, reverting the changes in your working copy
    - `git stash stave` also works
- `git stash pop`
    - **removes** the most recently stashed changes in your stash and re-apply them to your working copy
- `git stash apply`
    - apply whatever is stashed away, _without removing them from the stash_
    - can be useful if you want to apply stashed changes to multiple branches!!!
    - rarely used, though, lol
- multiple stashes can be done as you work
    - they add in order on top the current stash
- `git stash list`
    - can view what we have in our stash
    - also provides a lil' stash id we can use to apply specific stashed changes
- `git stash apply stash@{2}`
    - git assumes you want to apply the most recent stash, but you can specify a particular stash using the id
- `git stash drop stash@{2}`
    - to delete a particular stash using the id
    - if you use apply you may need to use this command
- `git stash clear`
    - clears the whole stash out

# Undoing Changes & Time Traveling

## Introduction Stuff

- checkout out commits
    - important to know
- "escaping" detached HEAD
    - important to know
- discarding changes with checkout
- `git restore`
- `git reset`
- `git revert`

## Checking Out Old Commits

- `git checkout`
    - it's like a swiss army knife, because it's pretty overloaded which is why git switch and git restore were made
- `git checkout <commit hash>`
    - this let's us view a previous commit
    - we see a message like `detached HEAD` state letting us know we traveled to see that commit and our history till then
    - we time travel in commit history so a `git log` will only show the commits UP UNTIL THAT COMMIT HASH
- usually a HEAD points to a branch reference
    - it usually DOES NOT refer to a specific commit, normally a branch reference does
    - so a detached HEAD makes it point to a specific commit!

### Detached HEAD State

- we can do a few things in this state
    - stay in detached HEAD to examine the contents of the old commit, poke around, view files, and etc
    - leave and go back to wherever you were before, aka reattach the HEAD
    - create a new branch and switch to it
        - we can now make and save changes since HEAD is no longer detached
- if we have a detached head and we switch to a brainch e.g. `git switch main`
    - this moves the HEAD back to the branch reference aka we reattached the HEAD

## Reference Commits Relative to HEAD

- we can checkout stuff for referencing previous commits relative to a partiular one
- `git checkout HEAD~1`
    - `HEAD~1` refers to a parent aka the commit before HEAD
    - `HEAD~2` refers to a grandparent aka the 2nd commit before HEAD
    - kinda' think about it as "HEAD - n" back "n" commits in history to checkout
        - but commit hashes still work and can be easier or more specific if needed
- other than switching back to our branch reference we can just do `git switch -`
    - this takes us back to our last left off branch :)

## Discard Changes

### Git Checkout

- `git checkout HEAD <file(s)>`
    - if you make changes to a file but don't want to keep them, you can revert back to whatever it looked like when you last committed
    - discard any changes in that file, reverting back to the HEAD
- `git checkout -- <file(s)>`
    - another shorthand way to do the same thing
- remember `checkout` is the "old-school" command to do a lot of this but is considered overloaded hence the new command restore in the next section

### Git Restore

- brand new command that helps with undoing operations
- worth knowing despite not being mentioned in a lot of tutorials
- `git restore <file(s)>`
    - restores back to the HEAD
    - note: this command is not "undoable" so if you have uncommitted changes in the file, they will be lost!
- `git restore --source HEAD~1 <file(s)>`
    - restores the files to its state from a prior commit to HEAD
    - you can use a commit hash as the source if you want
- has another use other than un-modifying
    - it can also un-stage changes
- `git restore --staged <file(s)>`
    - if you accidentally added a file to the staging area with `git add` and you _don't_ want to include it in the next commit, this removes it from staging

## Undoing Commits with Git Reset

- suppose we've made a couple commits on main branch, but we actually wanted to make them on a separate branch instead
    - we can undo these commits with a reset!
    - there's a regular reset and a hard reset
- `git reset <commit-hash>`
    - will reset the repo back to a specific commit
    - the commits are gone
    - this is the PLAIN RESET
        - THE CHANGES ARE STILL IN THE WORKING DIRECTORY
    - **we don't lose the changes, we just lose the commit history**
        - we want to keep the work, but we just wanted it on a different brach
- `git reset --hard <commit-hash>`
    - the hard reset
    - removes the commit history **and** the work/changes

## Reverting Commits with Git Revert

- similar to reset
- `git reset` actually moves the branch pointer backwards eliminating commits
- `git revert <commit-hash>` instead creates a brand new commit which reverses/undos the changes from a commit
    - because it results in a new commit, you will be prompted to enter a new commit message
-   if you need to reverse some commits that other people have on their machines, you should use revert
    -   because reset nukes the history which could fuck with other people
    -   you can use reset if you only have the bad commits on your local machine only before it is on other's
-   sometimes revert can cause some merge conflicts that we'd have to do like we'd do regularly
