Example of porting LaTeX notes to Reveal

**Background**

For three years I've taught a course on Linear Algebra for Computer Science students. It assumes that the students don't know any prior Linear Algebra and the emphasis is on showing the practical consequences of the field in CS. 

I've created a series of PDF's based on a set of topics that have been written in LaTeX. I make extensive use of RHUL's VLE moodle with in-class tests, multiple choice tests and creating slidecasts of every lecture (using Quicktime and then uploading to the Panopto service). There are a set of labs that make use of Jupyter but I won't talk about that any further here.

**Challenges**

With *the great COVID-19 disruption* I need to move this course into a blended learning experience. In particular, the parts where I go through problems use the lecture whiteboard.

So I need to convert the LaTeX notes into a series of chunked videos where I can not only create videos but also do live writing on a board. 

**Resources**

In the [LaTeX](./LaTeX) folder is a fragment of my first topic notes along with the input files. The figures used are in the [Figures](./Figures) folder. 

**What you will need installed**

- A [LaTeX](https://www.latex-project.org/) distribution. 
- [pandoc](https://pandoc.org/) (I used V2.9.1.1). I have a version installed with conda which is V2.2 and that doesn't work.
- [Rstudio](https://rstudio.com/) and [R](https://www.r-project.org/) with [revealJs](https://github.com/rstudio/revealjs) installed. There is a sessionInfo file [here](./sessionInfo.txt). You can do this all just with R but I haven't explored that option. 



**Porting LaTeX to markdown**

First we can convert the LaTeX to markdown with the following command in the LaTeX folder.

`pandoc -f latex short.tex -t markdown -o short.md`

and move `short.md` to the main folder. Note you get errors if files have spaces in them.



**Inspecting the R markdown file**

There is extensive documentation on R and RStudio so I won't go into how to get things set up. Once you started Rstudio you can open [testReveal.Rmd](./testReveal.Rmd) (you can also just open the equivalent [html file](./testReveal.html) to see what it looks like first). 

The top material between the three dashes are instructions to configure revealJs. These are more or less copy-pasted from the GitHub resource. *The chalkboard option is important here - on the lower left hand corner of the web pages there is an icon to fire up a whiteboard you can write on.* 

The `<script>` business gives instructions to the [MathJax](https://www.mathjax.org/) server which renders all the Maths. The piece of put in there allows one to ensure that equations get numbers. More could go in here but I haven't explored MathJax sufficiently. 

The actual markdown part is copy-pasted from short.md. To note, all occurences of

`###`

have been replaced by

`#`

and the path to the figures have been updated.

**What's next**

There is much tweaking that can be done here.

- Adjusting size of figures.
- Making more use of the navigation options.
- Fiddling to make it all look better.
- Making links to quizzes better.
- Figuring out how to export to PDF.
- Figuring out how to save and/or upload drawings on chalkboard.

