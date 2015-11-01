getwd() - shows the working directory
R-help and R-devel mailing lists and StackOverFlow.--Sources for R Forums.
R is divided into BASE (that we download from CRAN) and OTHERS (Util, stats, datasets, graphics etc). The 'Others' keep adding every day. http://bioconductor.org --R packages associated with bio-genome??
Resources Available on R Cran website(http://cran.r-project.org):
An Introduction of R
Writing R Extensions
R Data Import/Export
R Installation and Administration (Mostly for Building R from Sources).
R internals (Advanced - Not for the faint hearted)

You can also find other books on https://www.r-project.org/
<- is assignment operator.
auto printing - just give the vector name and enter
vector take decimal by default if you give number. for giving integer, we need to give like 1L
A vector can have elements of same class (data type) if you need elements to be from different classess, then you need to create a LIST
as.numeric(x) changes the data type of x to numeric
is LIST like a table?? elements ofa list will have double brackets when printed.

swirl: -- Its already installed (from swirlstats.com)
When you want to invoke Swirl, type library("swirl") and then swirl()

You can exit swirl and return to the R prompt (>) at any time by pressing the Esc key. If you are already at the prompt, type bye() to exit and save your progress.
| When you exit properly, you'll see a short message letting you know you've done so.

| When you are at the R prompt (>):
| -- Typing skip() allows you to skip the current question.
| -- Typing play() lets you experiment with R on your own; swirl will ignore what you do...
| -- UNTIL you type nxt() which will regain swirl's attention.
| -- Typing bye() causes swirl to exit. Your progress will be saved.
| -- Typing main() returns you to swirl's main menu.
| -- Typing info() displays these options again.

If at any point you'd like more information on a particular topic related to R, you can type help.start() at the prompt, which will open a menu of resources (either
| within RStudio or your default web browser, depending on your setup).

 Anytime you have questions about a particular function, you can access R's built-in help files via the `?` command. For example, if you want more information on the
| c() function, type ?c without the parentheses that normally follow a function name.

Using the args() function on a function name is also a handy way to see what arguments a function can take. Example args(list.files) will give the details about arguments to be used for list.files() function.

type rm(list=ls()) to clear your workspace.








