---
layout: page
title: "Instructor Notes"
permalink: /guide/
---

## Setup

### Build the docker image

``` bash
cd r-novice-gapminder/files
docker build -t r-novice-gapminder:dev .
```

### View your changes locally @ [localhost:4000](http://localhost:4000) and build site for pushing

Need to re-run each time you want to render `_episodes_rmd/*.rmd` -> `_episodes/*.md`

``` bash
cd r-novice-gapminder
make docker-serve
```

### Run RStudio in browser [localhost:8787](http://localhost:8787)

This is good for modifying / executing the `.rmd` files using the build environment.

``` bash
docker run --rm  -dP -e PASSWORD=secret123 -e USERID=$UID -v  $(pwd):/r_novice -p 8787:8787 r-novice-gapminder:dev
```

Login with username: `rstudio` and password: `secret123`, then navigate to `/r_novice` from RStudio's interface to see the repo.

### Run RStudio on MyBinder

[![Binder](https://mybinder.org/badge_logo.svg)](https://mybinder.org/v2/gh/ycrc/r-novice-gapminder/binder?urlpath=rstudio)

This is a nice place to test interactive code with just the data for the lessons. The url is `https://mybinder.org/v2/gh/ycrc/r-novice-gapminder/binder?urlpath=rstudio`



## Timing

Leave about 30 minutes at the start of each workshop and another 15 mins
at the start of each session for technical difficulties like WiFi and
installing things (even if you asked students to install in advance, longer if
not).

## Setting up git in RStudio

There can be difficulties linking git to RStudio depending on the
operating system and the version of the operating system. To make sure
Git is properly installed and configured, the learners should go to
the Options window in the RStudio application.

* **Mac OS X:**
  * Go RStudio -> Preferences... -> Git/SVN
  * Check and see whether there is a path to a file in the "Git executable" window. If not, the next challenge is figuring out where Git is located.
  * In the terminal enter `which git` and you will get a path to the git executable. In the "Git executable" window you may have difficulties finding the directory since OS X hides many of the operating system files. While the file selection window is open, pressing "Command-Shift-G" will pop up a text entry box where you will be able to type or paste in the full path to your git executable: e.g. /usr/bin/git or whatever else it might be.
* **Windows:**
  * Go Tools -> Global options... -> Git/SVN
  * If you use the Software Carpentry Installer, then 'git.exe' should be installed at `C:/Program Files/Git/bin/git.exe`.

To prevent the learners from having to re-enter their password each time they push a commit to GitHub, this command (which can be run from a bash prompt) will make it so they only have to enter their password once:

~~~
$ git config --global credential.helper 'cache --timeout=10000000'
~~~
{: .bash}

## Pulling in Data

The easiest way to get the data used in this lesson during a workshop is to have
attendees download the raw data from [gapminder-data][gapminder-data] and
[gapminder-data-wide][gapminder-data-wide].

Attendees can use the `File - Save As` dialog in their browser to save the file.

## Overall

Make sure to emphasize good practices: put code in scripts, and make
sure they're version controlled. Encourage students to create script
files for challenges.

If you're working in a cloud environment, get them to upload the
gapminder data after the second lesson.

Make sure to emphasize that matrices are vectors underneath the hood
and data frames are lists underneath the hood: this will explain a
lot of the esoteric behaviour encountered in basic operations.

Vector recycling and function stacks are probably best explained
with diagrams on a whiteboard.

Be sure to actually go through examples of an R help page: help files
can be intimidating at first, but knowing how to read them is tremendously
useful.

Be sure to show the CRAN task views, look at one of the topics.

There's a lot of content: move quickly through the earlier lessons. Their
extensiveness is mostly for purposes of learning by osmosis: so that their
memory will trigger later when they encounter a problem or some esoteric behaviour.

Key lessons to take time on:

* Data subsetting - conceptually difficult for novices
* Functions - learners especially struggle with this
* Data structures - worth being thorough, but you can go through it quickly.

Don't worry about being correct or knowing the material back-to-front. Use
mistakes as teaching moments: the most vital skill you can impart is how to
debug and recover from unexpected errors.

[gapminder-data]: https://docs.ycrc.yale.edu/r-novice-gapminder/data/gapminder_data.csv

[gapminder-data-wide]: https://docs.ycrc.yale.edu/r-novice-gapminder/data/gapminder_wide.csv
