Git How To Guide
================

Core tasks
==========

Initial setup
-------------

To set up your developper credentials on all projects use the following
commands:

\$ git config --global user.name "Paul Bradley"

\$ git config --global user.email git@paulbradley.org

Clone
-----

To get a local copy of a project you simply run the *git clone \[url\]*
command with the URL of the project you want to copy:

\$ git clone git://server.com/owner/project.git

Initialized empty Git repository in /private/tmp/**project**/.git/

remote: Counting objects: 100, done.

remote: Compressing objects: 100% (86/86), done.

remote: Total 100 (delta 35), reused 0 (delta 0)

Receiving objects: 100% (100/100), 9.51 KiB, done.

Resolving deltas: 100% (35/35), done.

This will copy the entire history of that project so you have it locally
and it will give you a working directory of the main branch of that
project so you can look at the code or start editing it. If you change
into the new directory, you can see the *.git* subdirectory - that is
where all the project data is.

Add&Commit&Push
---------------

To add files newly created and remove deleted files in the project first
copy them to the project folder and then call add command. Then use the
commit command with the dash m option to record the comment to the local
git:

\$ git add -A

\$ git commit -m 'add initial project'

To copy your local master and development branch back to the server you
need to use the push command:

\$ git push --all ALMA

Counting objects: 26, done.

Delta compression using up to 2 threads.

Compressing objects: 100% (24/24), done.

Writing objects: 100% (26/26), 9.11 KiB, done.

Total 26 (delta 8), reused 0 (delta 0)

Unpacking objects: 100% (26/26), done.

To //lthtr-alma/Alma/Git/alma\_testing.git

 \* \[new branch\] development -&gt; development

 \* \[new branch\] master -&gt; masterva

Fetch&Merge
-----------

Assuming you have a local copy of a repository and you want to get
updates, you would first run *git fetch \[alias\]* to tell Git to fetch
down all the data it has that you do not, then you would run *git merge
\[alias\]/\[branch\]* to update your local copy to anything new you see
on the server (like if someone else has pushed in the meantime):

\$ git fetch github

remote: Counting objects: 4006, done.

remote: Compressing objects: 100% (1322/1322), done.

remote: Total 2783 (delta 1526), reused 2587 (delta 1387)

Receiving objects: 100% (2783/2783), 1.23 MiB | 10 KiB/s, done.

Resolving deltas: 100% (1526/1526), completed with 387 local objects.

From github.com:schacon/hw

 8e29b09..c7c5a10 master -&gt; github/master

 0709fdc..d4ccf73 c-langs -&gt; github/c-langs

 6684f82..ae06d2b java -&gt; github/java

 \* \[new branch\] ada -&gt; github/ada

 \* \[new branch\] lisp -&gt; github/lisp

Here we can see that since we last synchronized with this remote, five
branches have been added or updated.

Then update the local working copy of the repository:

\$ git merge

... fix any merge conflicts ...

Ignoring files
--------------

By default, Git tracks content changes within all files under a given
project tree. You can tell Git which files to ignore by having a
“.gitignore” file in your projects root folder. The contents of this
file should contain a list of files or file types to ignore.

To create a new blank file in your project folder, use the following
command:

\$ touch .gitignore

Open the “.gitignore” file in a text editor, like Notepad, and enter the
files or complete paths you wish to ignore. Below is an example of what
should be ignored in a Visual Studio project:

/bin

/obj

\*.user

\*.suo

\*.sln.cache

Thumbs.db

Also add any application specific files you don't want to be tracked.
For example I add my error log file.

Protected branches
------------------

Branch *master* is always protected, i.e. you are not able to commit to
it directly. For each task you are working on create a branch with the
name in the following format: *pm\_task\_id-pm\_task\_name*.

All the changes commit into the newly crated branch. Before you deliver
the work, merge the beanch *master* into your branch and then change the
ticket status to *done*.

Afer successful ticket validation your branch will be merged into the
master.

Local copy of remote branch
---------------------------

To keep a synced local copy of a remote branch do:

git checkout --track origin/test\_branch

Good while working on a task in a specific branch.

Branch naming should be in the format:

task\_id-task\_name

Update to a cretain revision
----------------------------

To update local copy of repo to a certain revision/commit, do this:

git checkout \[revision\] .

Replace master with another branch
----------------------------------

Use git branch -m to rename the master branch to another one, then
rename seotweaks branch to master, like this:

git branch -m master old-master

git checkout origin/130-test

git branch master

git branch -m seotweaks master

git push -f origin master

Fix a Git detached head
-----------------------

How to exit (“fix”) detached HEAD state when you already changed
something in this mode and want to save your changes. (That part is
optional though.)

1.  Commit changes you want to keep. If you want to take over any of the
    changes you made in detached HEAD state, commit them. Like:

 git commit -a -m "your commit message"

1.  Discard changes you do not want to keep. The hard reset will discard
    any uncommitted changes that you made in detached HEAD state:

 git reset --hard

 (Without this, step 3 would fail, complaining about modified
uncommitted files in the detached HEAD.)

1.  Check out your branch. Exit detached HEAD state by checking out the
    branch you worked on before, for example:

 git checkout master

1.  Take over your commits. You can now take over the commits you made
    in detached HEAD state by cherry-picking, as shown in my answer to
    another question.

 git reflog

 git cherry-pick &lt;hash1&gt; &lt;hash2&gt; &lt;hash3&gt; …

Delete Last Commit
------------------

If you have committed junk but not pushed:

git reset --soft HEAD\~1

If you already pushed and someone pulled:

git revert HEAD

Checkout file or folder
-----------------------

Checkout the file from master when on the other branch with:

git checkout master -- path/to/the/file/you/want/file.txt

Checkout the folder from master when on the other branch with:

git checkout master -- path/to/the/folder/you/want/

You can use pass the flag --theirs or --ours:

-   Resolve any merge conflicts using the changes being pulled in.

git checkout --theirs file.txt

-   Resolve them by overwriting with your local changes.

git checkout --ours file.txt

For whole branch:

git checkout branchA

git merge -X theirs branchB

If I have deleted a file in branchB, what happens is that when you
checkout branchA the file you deleted in branchB will still be there. To
fix the conflict, just do:

git rm {DELETED-FILE-NAME}

Remote branches
---------------

Show remote repositories:

git remote

Add remote repository:

git remote add pb https://github.com/paulboone/ticgit

Fetch remote repository:

git fetch pb

Push to remote repository:

git push pb master

Rename a remote repository:

git remote rename pb paul

Remove a remote repository:

git remote rm paul

Merging branches
----------------

List branches:

git branch

Create new branch from current one:

git checkout -b iss53

Merge pb/master branch into the current one:

git merge pb/master

Push to remote repository:

Apply changes from one branch to another branch
-----------------------------------------------

Assume the following history exists and the current branch is "topic":

 A---B---C topic

 /

 D---E---F---G master

From this point, the result of either of the following commands:

git rebase master

git rebase master topic

would be:

 A'--B'--C' topic

 /

 D---E---F---G master

Further reading
---------------

Complete manual on how to use git as a part of our development platform
use is here:

<http://wiki.eclipse.org/EGit/User_Guide>


