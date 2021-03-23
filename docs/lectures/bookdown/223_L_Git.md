



# Git


## Recap

RMarkdown

- Markdown
- RMarkdown

**Next**: Git and Docker

- Git operations
- Git and RStudio
- Docker



## What's git?

**Git** is a free and opensource version control system

- commonly used through a server
    - where a master copy of a project is kept
    - can also be used locally
- allows storing versions of a project
    - syncronisation
    - consistency
    - history
    - multiple branches



## How git works

A series of snapshots

- each commit is a snapshot of all files
- if no change to a file, link to previous commit
- all history stored locally

<center>
![](images/git_snapshots.png){width=80%}

<br/>
<font size="4">
<a href="https://git-scm.com/book/en/v2/Getting-Started-What-is-Git%3F">by Scott Chacon and Ben Straub</a>, licensed under <a href="https://creativecommons.org/licenses/by-nc-sa/3.0/">CC BY-NC-SA 3.0</a>
</font>
</center>



## Three stages

When working with a git repository

- first checkout the latest version
- select the edits to stage
- commit what has been staged in a permanent snapshot

<center>
![](images/git_three_stages.png){width=60%}

<br/>
<font size="4">
<a href="https://git-scm.com/book/en/v2/Getting-Started-What-is-Git%3F">by Scott Chacon and Ben Straub</a>, licensed under <a href="https://creativecommons.org/licenses/by-nc-sa/3.0/">CC BY-NC-SA 3.0</a>
</font>
</center>


## Basic git commands

- `git clone`
    - copy a repository from a server
- `git fetch`
    - get the latest version from a branch
- `git pull`
    - incorporate changes from a remote repository
- `git add`
    - stage new files
- `git commit`
    - create a commit
- `git push`
    - upload commits to a remote repository



## Git and RStudio

Git can be used

- from the system terminal or shell, using the `git` command
- dedicated apps such as [GitHub Desktop](https://desktop.github.com/)
- RStudio git plug-in (top-right panel, `Git` tab)

All approaches allow to

- clone R projects from repositories
- stage and commit changes
- push to remote copy 
- pull changes from remote copy



## What's Docker?


:::::: {.cols data-latex=""}
::: {.col data-latex="{0.5\textwidth}"}


Docker allows to encapsulate and share computational environments

- First released in 2013
- Similar to virtual machines
  - simulates a guest operative system
  - within a host operative system
- Lightweight
  - doesn't simulate an entire system
  - only the *"user space"* is simulated
  
:::
::: {.col style="width: 40%;" data-latex="{0.5\textwidth}"}

![](images/DockerDiagram_VM.png)
<br/><br/>
![](images/DockerDiagram_Docker.png)

:::
::::::


## Virtual machines

:::::: {.cols data-latex=""}
::: {.col style="width: 100%;" data-latex="{0.5\textwidth}"}

Virtual machines software (e.g., VMWare) simulate a computer on top of your operative system

- allows **virtual machine** to access physical resources (e.g., disk, keyboard) of a **host**
- allows to run full operative systems
- e.g., run a full Windows virtual machine on a Mac host
- have been around since the 1970s
- can be *heavy* to run

:::
::: {.col style="width: 80%; text-align: right;" data-latex="{0.5\textwidth}"}
![](images/DockerDiagram_VM.png)
:::
::::::



## Docker containers

:::::: {.cols data-latex=""}
::: {.col style="width: 100%;" data-latex="{0.5\textwidth}"}

Docker runs *containers*

- developed for flexible deployment of (web) services
  - compartimentalised
  - lightweight
  - (frequently) transient
- **kernel** is not simulated
  - kernels are the bulk of operative systems
  - containers share host's kernel
  - can also share binaries and libraries

:::
::: {.col style="width: 80%; text-align: right;" data-latex="{0.5\textwidth}"}
![](images/DockerDiagram_Docker.png)
:::

::::::



## Docker and reproducibility

Why are dockers useful for reproducibility?

One of the key issues of reproducing a study is replicating the computational environment used

- e.g., all the libraries in their correct version 

Creating a Docker image (from which a container is instantiated)

- defined using a [*Dokerfile*](https://docs.docker.com/engine/reference/builder/)
- requires to list a full system configuration
  - version of programming language, libraries, etc
- once created / defined
  - other researchers or developers can run your script **in the exact same computational environment**


## granolarr Dockerfile

```{}
# Base image https://hub.docker.com/r/rocker/ml
FROM rocker/geospatial:4.0.2

# create an R user
ENV USER rstudio

## Install additional required R libraries
COPY ./DockerConfig/Requirements.R /tmp/Requirements.R
RUN Rscript /tmp/Requirements.R

## Install additional required TeX libraries
RUN tlmgr install amsmath
RUN tlmgr install latex-amsmath-dev
RUN tlmgr install iftex
RUN tlmgr install euenc
RUN tlmgr install fontspec
```

[... continues]



## Summary

Git and Docker

- Git operations
- Git and RStudio
- Docker

**Next**: Practical

- Reproducibile data analysis
- RMarkdown
- Git


