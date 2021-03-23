



# Reproducibility



## Recap

**Prev**: Table operations

- 211 Join operations
- 212 Data pivot
- 213 Read and write data
- 214 Practical session

**Now**: Reproduciblity

- Reproduciblity and software engineering
- Reproduciblity in GIScience
- Guidelines


## Reproduciblity

In quantitative research, an analysis or project are considered to be **reproducible** if:

- *"the data and code used to make a finding are available and they are sufficient for an independent researcher to recreate the finding."* [Christopher Gandrud, *Reproducible Research with R and R Studio*](https://www.crcpress.com/Reproducible-Research-with-R-and-R-Studio/Gandrud/p/book/9781498715379)

That is becoming more and more important in science:

- as programming and scripting are becoming integral in most disciplines
- as the amount of data increases



## Why?

In **scientific research**:

- verificability of claims through replication
- incremental work, avoid duplication

For your **working practice**:

- better working practices
    - coding
    - project structure
    - versioning
- better teamwork
- higher impact (not just results, but code, data, etc.)



## Reproducibility and software engineering

Core aspects of **software engineering** are:

- project design
- software **readibility**
- testing
- **versioning**

As programming becomes integral to research, similar necessities arise among scientists and data analysts.



## Reproducibility and "big data"

There has been a lot of discussions about **"big data"**...

- volume, velocity, variety, ...

Beyond the hype of the moment, as the **amount** and **complexity** of data increases

- the time required to replicate an analysis using point-and-click software becomes unsustainable
- room for error increases

Workflow management software (e.g., ArcGIS ModelBuilder) is one answer, reproducible data analysis based on script languages like R is another.



## Reproducibility in GIScience

[Singleton *et al.*](https://www.tandfonline.com/doi/abs/10.1080/13658816.2015.1137579) have discussed the issue of reproducibility in GIScience, identifying the following best practices:

1. Data should be accessible within the public domain and available to researchers.
2. Software used should have open code and be scrutable.
3. Workflows should be public and link data, software, methods of analysis and presentation with discursive narrative
4. The peer review process and academic publishing should require submission of a workflow model and ideally open archiving of those materials necessary for
replication.
5. Where full reproducibility is not possible (commercial software or sensitive data) aim to adopt aspects attainable within circumstances



## Document everything

In order to be reproducible, every step of your project should be documented in detail

- data gathering
- data analysis
- results presentation

Well documented R scripts are an excellent way to document your project. 



## Document well

Create code that can be **easily understood** by someone outside your project, including yourself in six-month time!

- use a style guide (e.g. [tidyverse](http://style.tidyverse.org/)) consistently
- also add a **comment** before any line that could be ambiguous or particularly difficult or important
- add a **comment** before each code block, describing what the code does
- add a **comment** at the beginning of a file, including
    - date
    - contributors
    - other files the current file depends on
    - materials, sources and other references 



## Workflow

Relationships between files in a project are not simple:

- in which order are file executed?
- when to copy files from one folder to another, and where?

A common solution is using **make files**

- commonly written in *bash* on Linux systems
- they can be written in R, using commands like
    - *source* to execute R scripts
    - *system* to interact with the operative system



## granolarr Mark.R

Section of the [*granolarr*](https://sdesabbata.github.io/granolarr/) project make file [Make.R](https://github.com/sdesabbata/granolarr/blob/master/Make.R) that generates the current slides for the lecture session 221

```{}
cat("\n\n>>> Rendering 221_L_Reproducibility.Rmd <<<\n\n")
rmarkdown::render(
    paste0(
        Sys.getenv("GRANOLARR_HOME"), 
        "/src/lectures/221_L_Reproducibility.Rmd"
    ), 
    quiet = TRUE, 
    output_dir = paste0(
        Sys.getenv("GRANOLARR_HOME"), 
        "/docs/lectures/html"
    )
)
```


## Future-proof formats

Complex formats (e.g., .docx, .xlsx, .shp, ArcGIS .mxd)

- can become obsolete
- are not always portable
- usually require proprietary software

Use the simplest format to **future-proof** your analysis.<br/>**Text files** are the most versatile

- data: .txt, .csv, .tsv
- analysis: R scrpts, python scripts
- write-up: LaTeX, Markdown, HTML



## Store and share

Reproducible data analysis is particularly important when working in teams, to share and communicate your work.

- [Dropbox](https://www.dropbox.com)
    - good option to work in teams, initially free
    - no versioning, branches
- [Git](https://git-scm.com)
    - free and opensource control system
    - great to work in teams and share your work publically
    - can be more difficult at first
    - [GitHub](https://github.com) public repositories are free, private ones are not
    - [GitLab](https://about.gitlab.com/) offers free private repositories



## Summary

Reproduciblity

- Reproduciblity and software engineering
- Reproduciblity in GIScience
- Guidelines

**Next**: RMarkdown

- Markdown
- RMarkdown


