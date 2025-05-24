---
sticker: lucide//newspaper
---
# Introduction
In the previous session we've talked about essentials of git. What is a Version Control System, why do we nee it, and how to use git locally on our computer in one branch. Let's recap really quickly.

We first have to initialize a repository on some directory on our computer. We use the following command to do so:

```bash
git init
```

Then we do our normal work. We write documents, edit them, make new files, and other things that one would do. When we are at a point were something seems to be done, we stage it, make the git notice the change and track it. 

```bash
git add <name-of-the-files-to-stage>
```

or more simply

```bash
git add .
```

And our last step as for writing a new page in the history of our repository is to commit our changes so that git adds them to the finalized history:

```bash
git commit -m"A message"
```

or if the message is long 

```bash
git commit 
```

And you'll be heading towards the editor automatically. Use `:wq` to save the message and quit.

We've also learned to check our project status by:

```bash
git status
```

and the timeline of commits using:

```bash
git log
```

If you accidentally staged something and wanted to get back you'd simply use:

```bash
git restore --staged <file>
```

## Branches: Parallel Stories
Now we would talk about making a new branch, a parallel history of works that could later be added to the main branch or not.

We start by creating a new branch:

```bash
git branch <name-of-branch>
```

and then going into the branch

```bash 
git switch <name-of-branch>
```
everything else is now the same, this is just a parallel workflow, you can still add, commit, and go forward.

Most of branches are created for specific tasks and are to be added to the main repository later. For this we can do to things: `merge` and `rebase`

## Merging
To Merge means to add all the commits of the branch as a single commit to another branch. The history would still contain the repositories branches and their histories, but after merging the branch that's being merged to has a new commit, which contains last version of the repository in the merging branch.

To do so:
```bash
git switch <name-of-the-main-branch>
git merge <name-of-the-merging-branch>
```

It is optional to delete the branch that you merged afterwards, this does nothing to history but permits from faulty commits to the out-dated branch.


## Rebasing
To rebase is to put all the commits of the branch on top of the commits of the main branch. you're commits would be added to the other branch while rebasing.

To rebase we would write:

```bash
git rebase <rebased-on-top-of> <the-branch-tobe-rebased>
```

Assume the following history exists and the current branch is "topic":

                     A---B---C topic
                    /
               D---E---F---G master

From this point, the result of either of the following commands:

```bash
git rebase master
git rebase master topic
```
       would be:

                             A'--B'--C' topic
                            /
               D---E---F---G master



#git #range #software