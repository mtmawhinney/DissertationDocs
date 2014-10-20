# Drexel Dissertation Template Files

This repository (hereafter, "repo") is a collection of all documents
and template files needed for the completion of a Ph.D. in physics at
Drexel University. Attempts will be made to keep this repo
comprehensive and up-to-date.

## General Template

The LaTeX dissertation template file entitled [`example.tex`](Templates/example.tex) contains a bare bones example of a dissertation. 
A PDF version of this example can be generated by running from the [`Templates`](Templates/) directory:

``` bash
$ pdflatex example.tex
```

The LaTeX class file, [`drexel-thesis.cls`](Templates/drexel-thesis.cls), required for styling and arrangement, has also been included here.

## Dissertation Requirements

A PDF document entitled, [`thesismanual.pdf`](Templates/thesismanual.pdf?raw=true) has also been included and contains all requirements for formatting and arrangement of
a Drexel Dissertation, according to the Drexel University [Office of Research and Graduate Studies](http://www.drexel.edu/graduatestudies/).
The dissertation templates, should in principle, always be up-to-date to reflect these formatting and arrangement requirements.

## Purpose of this repository

This repo serves as a central (public) location for hosting references and templates to aid in the formatting of a Drexel dissertation. 
All Drexel University graduate physics students are allowed and encouraged to use this repo. 
Additionally, completed thesis by former students can be hosted here.
These accepted thesis are often considerably more complex than the bare template provided and may serve as a better starting point.

Below are a few rules to ensure that this resource remains useful for everyone:

  * All users are granted full privileges to this repo; no exceptions.
  * All users are very much encouraged (but not required) to upload their own personal dissertations as examples for less senior students.
  * All users should refrain from deleting files, unless it has been determined (and ideally confirmed by a qualified person) that something is either out-of-date or incorrect. 
  * Users should not modify others uploaded thesis without _explict_ permission.

### Examples:

+ **Travis Hoppe**: [_On the Role of Entropy in the Protein Folding Process_](Examples/TravisHoppe)


## Getting Started

Git/Github has a bit of a steep learning curve. The first step is to
create a complete copy of the DrexelPhysics/DissertationDocs
repo to associate with your own Github account. If you do not already
have a Github account, now would be a good time to [create one](https://github.com/join). 
Creating a new (and personal) remote copy of this repo is called
"forking", and only needs to be done once.

To fork the DrexelPhysics/DissertationDocs repo, simply navigate to
the project repository on Github, and click on `Fork`, most likely
located in the upper right corner of the page. Make sure to select
your own account as the location.

After the repo has been forked, you now have two versions of
DissertationDocs. The first is the public project (owner:
DrexelPhysics), and the other is your own personal copy
(UNAME/DissertationDocs); 
**WARNING**: this repo is likely still public. 
Avoid putting any sensitive information here.  

It is now time to create a local copy of your own repo,
DissertationDocs. In the command line, navigate to some location 
on your local machine, and create a directory called, `drexelphysics`.
Within this directory, create another directory called,
`dissertationdocs`. Now clone your remote repo into this repository:

``` bash
$ git clone https://github.com/UNAME/DissertationDocs.git
```

where `UNAME` is your Github username. This also only needs to be done
once. You are now free to create or modify files within this new local
git directory.

The last thing one needs to do, is to tell git where "upstream" is
located. Upstream should always point to the larger
DrexelPhysics/DissertationDocs repo. This ensures that updating your
personal remote and local repos will always pull from the correct
location. In order to set upstream, do the following within your local
git directory (inside of DissertationDocs):

``` bash
$ git remote add upstream git@github.com:DrexelPhysics/DissertationDocs.git
```
If this has worked, a simple:

``` bash
$ git remote -v
```

will show the following: 

``` bash
$ origin	https://github.com/UNAME/DissertationDocs.git (fetch)
$ origin	https://github.com/UNAME/DissertationDocs.git (push)
$ upstream	git@github.com:DrexelPhysics/DissertationDocs.git (fetch)
$ upstream	git@github.com:DrexelPhysics/DissertationDocs.git (push)
```

The process of setting your upstream only needs to be done once.

#### Adding/Modifying Files

As an example of how to update local and remote repos, let's try
adding a specific thesis folder which contains all relevant thesis
files. In the command line, navigate to the git directory
`DissertationDocs`. Within this repository, create a new directory
`FirstLast` (where `First` is your first name, and `Last` is your last
name). 

``` bash
$ mkdir FirstLast
```

First, let's add a readme file, which describes and lists all files
(and perhaps non-standard LaTeX packages used) which will exist in
this sub-directory. Now let's tell git to begin tracking this file.

``` bash
$ cd FirstLast
$ touch README.md 
$ git add README.md 
```

Now git knows about this file, and all modifications to it will
be tracked as well. The next step is to bring our own remote repo up
to speed with our local repo containing new content.

``` bash
$ git commit -am "Added README.rst."
$ git push
```

#### Pushing changes upstream

Once thesis files have been added to your local git repo (and these
changes have been pushed to your remote repo), the last step will be
to push them upstream. Pushing content upstream will be done through
'pull requests'. Navigate to the DrexelPhysics page, and click on 'Pull
Request'. At the very top, click on 'New Pull Request'. Then select 'compare
across forks', with the base fork as
DrexelPhysics/DissertationDocs:master; the head fork should always be
your version of this repo (the one that contains modified content:
UNAME/DissertationDocs:first-last-thesis). Step-by-step instructions
are included below:

> A Note About Branches:
> You will notice that the above discussion of submitting a pull
> request does not have you using the 'master' branch of your
> DissertationDocs repo. This is intentional, and requires a word on
> branching. In general, pushing content upstream should be done by
> creating a branch off of your own master branch, separating out the
> development of a single feature from the rest of the current working
> project. **One feature, one branch.**

Let's create a new branch. For this example we're pushing thesis
documents upstream.


Which branch are we currently on?

``` bash
$ git branch
$ >>> * master
```

Creating a new branch will effectively create a new copy of the entire
local repository:

``` bash
$ git branch first-last-thesis
$ git branch
$ >>> first-last-thesis
$ >>> * master
$
$ git checkout first-last-thesis
$ git branch
$ >>> * first-last-thesis
$ >>>  master
$ git push --set-upstream origin first-last-thesis
```

Now let's make some changes. First let's create a new folder in the
Examples directory.

``` bash
$ cd DissertationDocs/Examples
$ mkdir FirstLast
$ cd FirstLast
```

Next, move all relevant files into this directory through the command
line. Git doesn't know they exist yet, so we'll have to tell it to
begin tracking them. We'll also 

``` bash
$ git add .
$ git commit -am "Adding First Last thesis files."
$ git push
```

The above commit/push commands are necessary because we are submitting
a pull request to DrexelPhysics through out remote repo, which needs
to be up to date. We are now good to follow the above instructions for
submitting a pull request:

> Navigate to the DrexelPhysics page, and click on 'Pull Request'. At
> the very top, click on 'New Pull Request'. Then select 'compare
> across forks', with the base fork as
> DrexelPhysics/DissertationDocs:master; the head fork should always
> be your version of this repo (the one that contains modified content:
> UNAME/DissertationDocs:first-last-thesis).

Next, click on 'Create pull request'. Once this has been done,
navigate to the pull request you've just submitted, and if it tells
you that it is ready to merge, do so. Now all users can pull down
these changes from upstream.

A last word on cleaning up: The 'first-last-thesis' branch is no
longer needed. First, checkout your master branch, and pull in changes
from upstream:

``` bash
$ git checkout master
$ git fetch upstream
$ git merge upstream/master
$ git push
```

** Check to make sure that your changes are present before contining
   on to the next step. **

Now, we can delete the feature branch:

``` bash
$ git branch -d first-last-thesis
```

You now have successfully added all of your thesis documents to your
local, remote, and upstream repositories.


#### I need help

Luckily, most things in git can be un-done. Even if you think you've
done irreparable damage to your repo, chances are, you haven't. For
questions, comments, and concerns, contact:

* Austen Groener:
  austen.m.groener@drexel.edu/austen.groener@gmail.com * 

