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

#lesson 3 : Sequences of Numbers#
* 1:10 gives 1  to 10
* pi:10 gives 3.14 to 9.14 (increment by 1)
* 15:1 gives 15 to 1 decrement by 1
* for functions related help, we give ?functionname for operator, we need to give ?<backtick>:<backtick> (ie, the operator in between two backticks (left of 1 key in the keyboard).
* seq(1,10, by 0.5) will start with 1 , increment by .5 and end with 10. So, seq() function can be used for custom intervals. 
* seq(1,10, length = 30) will split the range into 30 items seperated by equal intervals
* seq(along.with =20) and seq_along(20) give 1 to 20 values.
* rep() function is to replicate. rep(0, times = 40) will give 40 zeros. rep(c(1,2,3), times = 10) will repeat 1,2,3 ten times. rep(c(1,2,3), each =10) will given 10 is, 10 2s and then 10 3s.

#Lesson 4 : Vectors#
* the simplest and most common data structure in R is vector. 
* two types of vectors : Atomic and Lists (Atomic have same dataType, Lists can have Multiple data Type)
* Types of Atomic Vectors (Numeric, logical, Character, Integer, complex)
* Logical Vectors (TRUE, FALSE, NA (for Not available))
* a <- C(1,2,3) and then b<- a <  2. the value of b wil be (TRUE,FALSE,FALSE) and Not (1)
* Logical Operators are >, <, >=, <=, == (for exact equality) and != 
* A|B is A OR B. A&B is A AND B. !A is Negation of A.
* just like in bodmAS, AND takes precedence over OR (think of AND as Addition and OR as Subtraction just for the sake of remembering)
* for character vector, we need to give objects in doube quotes (single quotes also worked).
* paste() function concatenates values in a vector. Example paste(c("My","Name","is"), collapse="-") will give My-Name-is as a result. paste(1:3,c("a","b","c"), sep = '-') will give a vector with 3 objects "1-a" "2-b" "3-c" in this example, the numeric values 1,2,3 are COERCED into character values so that they can be combined with a,b,c.
* LETTERS is an inbuilt variable in R containing character vector of all 26 alphabets in english

#Lesson 5: Missing Values#
* NA in R is for Not Available or Missing (in Statistics)
* Any Operation involving NA genrally yeilds NA
* NA == NA give NA. is.na(NA) gives TRUE. just like NULL in SQL.
* a<- 1:3 and b <- a <2 now b is TRUE, FALSE, FALSE. SUM(b) will be 1 because SUM() function will treat TRUE as 1 and FALSE as 0.
* NaN means Not a Number. (example 0/0)
* Inf means Infinity . Inf+1 = Inf . Inf - Inf will also give NaN

#Lesson 6: Subsetting vectors#
* The way you tell R that you want to select some particular elements (i.e. a 'subset') from a vector is by placing an 'index vector' in square brackets immediately following the name of the vector.
*  x[1:10] to view the first ten elements of x. Many programming languages use what's called 'zero-based indexing', which means that the first element of a vector is considered element 0. R uses 'one-based indexing', which (you guessed it!) means the first element of a vector is considered element 1. x[c(3,5,7)] will give 3rd 5th and 7th elements of the vector x.
*  four type of index vectors : Logical Vectors, vectors of Postitve Integers, vectors of Negative integers, vectors of Character Strings. 
*  x[is.NA(x)] will give all NA elements of x. x[x>0] will give all elements in x which are +ve and also all NA values.This is Unlike in SQL , where if we give x>0 , we get only +values and no NULL values. The R equivalent of SQL's x>0 is x[!is.na() & x>0 ] -- These are Logical indexes. x[1:10] or x[c(5,7)] are examples of Positive integer indexes
*  if a vector x has 4 numeric elements, if we give x[0] , we get numeric(0) which is not useful. if you give x[5], we get NA. only x[1:4] will give us the actual values.
*  x[c(-2,-10)] will give all elements of th vector except 2nd and 10th . THis is and example of Negative integer index. Short cut way for this syntax is x[-c(2,10)]
*  vect <- c(foo = 11, bar = 2, norf = NA) will create a vector named vect with NAMED ELEMENTS. now names(vect) will give the element names. alternatively, you can first create a vector and add names to elements later like this vect2<- c(11,2,NA) and then names(vect2) <- c("foo","bar", "norf"). Now if you want to check if vect and vect2 are identical, we can use identical(vect,vect2) function which gives Boolean TRUE as result.
*  Now, in the above example vect["bar"] will give the 2nd element of the vector. Now we have to give the bar value in quotes here because this is index and not a function and bar is not a vector and just an element name. vect[c("bar","foo")] will give 2nd and 1st elements of the vector vect.

#Lesson 7 Matrices and Dataframes : #
*  Matirces and Data Frames are rectangular data types which contain tabular data with rows and columns. 
*  Matrices can contain only single class of data while data Frames can contain many different classes of data. 
* A matrix is a atomic vector with a dimension attribute. example a<-1:20 and dim(a) will give nothing. dim(a) <- c(4,5) will change this vector 'a' to a matrix with 4 rows and 5 columns. Now if you give dim(a) you can see the result as 4 and 5. Observe here that dim function can be used to both assign a dimension attribute and to extract the dimension attribute information like we have seen in the preceding example. attributes() funtion will also give the dimension attribute information. 
* matrix() function can be used to create a matrix directly . Example : my_matrix2 <- matrix(1:20, nrow = 4, ncol = 5, byrow = FALSE). byrow = FALSE means that the data will be filled column wise. identical() function can be used to compare two vectors /matrices
* cbind() function will bind a character vector to a matrix which means if there is a matrix (a) with 4x5, and a character vector (b) with 4 patient names, then if we do cbind(a,b) then a new matrix will be created which is of 4x6 and the 6th column will have attrribute name as b. In this example we can also observe the difference between dimension and attribute. if we store the value new matrix in c and give dim(c), we get only 4x6. if we give attrributes(c) we get dimension 4x6 as well as dimension names which are all null for rows and all null except b for columns. 
* Also, if a decimal vector is cbind()'ed with character matrix, the resulting matrix will be implicity COERCED as character since character takes precedence. This is because, as we discuseed in the definition of matrix, the matrix can have only single class of data. -- try how to do explicit coersion.
* if we want to avoid coersion and have multiple classes of data, we can go for data.frames() function. in this case, if we use data.frames(a,b) then even if a is decimal vector and b is character matrix, the resulting data frame will not be coerced and the elements will retain their origional class of data types. 
* you can check if a variable is a vector or matrix or a data.frame by using class() function. 
* we can use colnames() function to assign dimension names to the data.frames just like how we used dim() function to assingn dimension name to a matrix earlier. 

#Lesson 8 : Logic#
* Logical operators are ==, <, >, <=, >=, !, &, &&, |, || 
* the difference between & and && is that & applies to all elements of the operands and && applies to first element alone. 
* example: TRUE & c(TRUE,FALSE,FALSE) will give TRUE, FALSE ,FALSE (since this is equivalent to c(TRUE, TRUE, TRUE) & c(TRUE, FALSE, FALSE) after rotation is applied due to unequal elements in the two vectors). But if you give TRUE && c(TRUE, FALSE, FALSE), the result is only TRUE. Here, though rotation is applied, only the first element is evaluated. remaining all are ignored.
* same applies to | (OR) operator and | and || have the same difference. 
* & is called vectorised version and && is called non vectorised version of AND operator due to obvious reason that && will return only one element. same with | and ||
* & has precedence over | if no brackets are provided. 
* isTRUE() function will return TRUE if argument is TRUE ELse, will return FALSE. i tried to pass numeric argument to this function instead of  a logical TRUE or FALSE argument. example isTRUE(3) and it returned false. check why?
* identical('hello','Hello') will give FALSE since R is case sensitive. i tried identical(xor,'xor') and it returned FALSE but i thought it would return an error since first argument did not have quotes. but since xor is a function in R, it returned some value (may be character) and it did not match with 'xor' and hence false. if i give identical(abc,'abc') i will get an error saying abc is not recognised.
* xor() function is the R version for mathematically available Exclusive-OR. it returns TRUE only when one operand evalutaes to TRUE and other to FALSE.
* sample() function gives random sampling of integers with out replacement. ie, if you give sample(10), you will get 1 to 10 numbers but in random order.
* the which() function takes logical VECTOR as an argument and returns indices (aka dimensions?) of that vector that are true. example: which(c(TRUE, FALSE, TRUE)) would return c(1,3)
* the any() and all() functions also take logical vectors as arguments. any() retruns TRUE if any of the elements in the vector is TRUE and all() returns TRUE when ALL the elements in the vector are TRUE.
* At the end of this lesson, this message came "That's all for this introduction to logic in R. If you really want to see what you can do with logic, check out the control flow lesson!". But there is no control Flow lesson in swirl R programming course. Check 'take me to the swirl course repository' option to see if it exists. Else check R programming course in Coursera if any such chapter exists. --update: Control Flow is nothing but IF, ELSE, REPEAT, FOR, APPLY etc in R. THere is a seperate chapter in R Plural Sight course - Notes. Pls check.

#Lesson: 9 Functions#
* Sys.Date() function will give date in 'YYYY-MM-DD' Fromat (Based on your computers environment). 
* mean() function takes vector as an input (argument) and gives the mean value of all elements in the vector. Example: mean(c(2,3,5)) will give 3.3333
* syntax : boring_function <- function(x) {x} will create a function called boring_function() with one argument x and will return the value of x. you can also put additional logic in those {} . The last expression to be evaluated with in {} will be returned as an output
* To understand computations in R, two slogans are helpful: 1. Everything that exists is an object. 2. Everything that happens is a function call.
*  if you want to see the source code for any function, just type the function name with out any parenthesis. 
*  consider this function. remainder <- function (num, divisor = 2) { num %% divisor}. Now what can learn from this is: 1) for remainder, use %%. 2) divisor has a default value. so you can just give remainder(5) and you will get 1 as result. You can also give remainder(8,3) and get 2 as answer where default value is overwritten by 3. you can give remainder(8,3) OR remainder(divisor = 3, num =8) OR remainder(3, num =8) so the order of arguments is not relevant once you explicity mention the argument names while calling the function. you can also use the first letters of argument names and assign value while calling functions like in powershell. But stay away from it since its not a good practice. 
*  Also, you can give args(remainder) to get the argument details of the function remainder() that you created. THis is interesting! args() is a function, remainder() is a function, yet remainder was an argument for args(). Yes it's true: you can pass functions as arguments! This is a very powerful concept.
*  while passing function as an argument to another function, we should not put that argument in quotes. Example:  some_func <- function(abc, val) {abc(val)} here, if you give some_func(sum,c(1,5)), you will get 6. But if you give some_func("sum",c(1,5)), you will get an error since the function definition is to return abc(val) and hence it is expecting a function as parameter and not a character value. This idea of passing a function as an argument to another function is an important concept in programming.
* you can pass a function as an argument without first defining the passed function. Functions that are not named are appropriately known as anonymous functions. Example: using the somee_func function that has been created in the above step, we can do this some_func(function(x){x+1},6), the result is 7. This function(x){x+1} is an anonymous function because , it is not defined (doesnt have a name), but we still executed that function as a part of evaluate function. 
* if ellipses(...) is an argument in a function (example paste() function), then all the arguments after ellipses MUST have default value. So, as a good practice, if you want to have ellipses as an argument in your custom defined functions, have the ellipse as the last argument so that you dont have to bother about the default values of argumnets after it. 
* consider this function telegram <- function(...){ paste("START",... ,"STOP" )}. Now telegram() function can take any number of arguments (as a part of ellipses) and it will just paste those arguments as a character vector with space in between and place START at the begining and STOP at the end of that chacter vector. 
* if you want to create a function with ellipses as parameters, then we need to unpack the arguments in the function logic. Also, we have to explicitly use the argument names while calling the function. These argument names can be found in the definition of the function (where we define them while unpacking) Example: 
mad_libs <- function(...){
  args <- list(...)  ##args is just a variable name and not any syntax here.
  place <- args[["place"]]
  adjective <- args[["adjective"]]
  noun <- args[["noun"]]
  paste("News from", place, "today where", adjective, "students took to the streets in protest of the new", noun, "being installed on campus.")
}

Now, to call this mad_libs() function, we need to explicitly give argument names defined in the function.
like this : mad_libs(place = "Newyork", adjective = "good", noun = "bar")
--check how we are able to call paste function with out explicitly mentioning the argument names eventhough the paste function has ellipses as an argument. check the code of paste() function
* +,-,*,/ are examples of binary operators (because they have two operands - left and right). In R, we can define our own operators. Example: "%p%" <- function(left, right){  paste(left,right)} See the syntax, the new operator should start and end with % also it should be enclosed in quotes while defining. Now to use it, we can do this : "I" %p% "Love" %p% "R"  this will give the result "I Love R"

#lesson 10 : lapply and sapply#
-- Try this lesson in swirl . only theory is here.
* lapply() and sapply() are the two most important members of R's *apply family of functions, also known as loop functions
*  These powerful functions, along with their close relatives (vapply() and tapply(), among others) offer a concise and convenient means of implementing the Split-Apply-Combine strategy for data analysis.
*  Each of the *apply functions will SPLIT up some data into smaller pieces, APPLY a function to each piece, then COMBINE the results. A more detailed discussion of this strategy is found in Hadley Wickham's Journal of Statistical Software paper titled 'The Split-Apply-Combine Strategy for Data Analysis'.
* Throughout this lesson, we'll use the Flags dataset from the UCI Machine Learning Repository. This dataset contains details of various nations and their flags. More information may be found here: http://archive.ics.uci.edu/ml/datasets/Flags
* I've (creator of swirl) stored the dataset in a variable called flags. Type head(flags) to preview the first six lines (i.e. the 'head') of the dataset.
* The 'l' in 'lapply' stands for 'list'. lapply() will always return a list.
* x <- as.character(listname) will change the list vector (with the name listname) to character vector x.
* sapply will return a vector or matrix (which have data elements of same class) if it understands that the result can be arranged as a matrix or a vector. If it cannot understand if the result can be arranged as a matrix or avector, it will give the result as a list. lapply will return a list always. 
* unique() will give the unique values as an output.
* Anonymous functions (check in previous lesson 'functions') can also be used in lapply and sapply. 

#Lesson 10 : vapply and tapply #
* in this lesson also we use the flags dataset that was used in the previous lesson.
* str() function . take a look. -> Structure function a very important function. 
* sapply() tries to 'guess' the correct format of the result, vapply() allows you to specify it explicitly. If the result  doesn't match the format you specify, vapply() will throw an error, causing the operation to stop. This can prevent significant problems in your code that might be caused by getting unexpected return values from sapply()
* You might think of vapply() as being 'safer' than sapply(), since it requires you to specify the format of the output in  advance, instead of just allowing R to 'guess' what you wanted. In addition, vapply() may perform faster than sapply() for large datasets. However, when doing data analysis interactively (at the prompt), sapply() saves you some typing and will often be good enough.
* table() function will do basic profiling(counts) of various values in the input.
* tapply kind of brings the GroupBy clause into picture??
* summary() function gives mean, meadian, min , max and 1st and 3rd Quartiles(whats this?) values. 
* summary()will give table() kind of output if input is character?? - this is only my assumption. check this. -- checked it. THis is true . THe only differenc is summary() just shows few values and categorizes rest into OTHERS if the dataset is big. but Table() will show counts of all the values.

#Lesson 12 : looking at Data#
* We'll be using a dataset constructed from the United States Department of Agriculture's PLANTS Database (http://plants.usda.gov/adv_search.html).
* It's very common for data to be stored in a data frame. It is the default class for data read into R using functions like  read.csv() and read.table()
* dim() function to see number of rows and columns. nrow() for rows ncol() for columns. Rows and Columns are called Observations and Variables respectively in R. 
* object.size() to know how much space the object is occupying. 
* names() will give the character vector of column names 
* head(x) by default shows top 6 rows. if you want top 10 rows give head(x,10). Same way you can use tail() function to get last rows
* check how R will determine wheter a colum is a FACTOR type of element. ?? factor is like Gender: M/F
* the beauty of str()  function is that it combines features of other metadata functions (like dim, head, class) and gives output in a nice and readable format
* str() is actually a very general function that you can use on most objects in R. Any time you want to understand the structure of something (a dataset, function, etc.), str() is a good place to start.

#Lesson 13: Simulation#
* sample()- to randomly pick data from input. replace = TRUE argument means if we are picking 4 elements from six elements. The element already picked (lets say as first element) can again be picked as 2nd element. If replace = FALSE then the same element cannot be picked. Its like if picking 4 balls from a bag of 6 balls. when replace = true, we can pick 6*6*6*6 combinations. if replace = false, we can pick 6*5*4*3 combinations. we can aslo make use of another argument in the same function which is prob and set the probablility of picking any element while the function randomly picks elements. 
* Each probability distribution in R has an r*** function (for "random"), a d*** function (for "density"), a p*** (for "probability"), and q*** (for "quantile"). We are most interested in the r*** functions in this lesson, but I encourage you to explore the others on your own. examples: rbinom, dbinom, pbinom, qbinom
* Similar to rbinom() we can use R to simulate random numbers from many other probability distributions. we can use rnorm() for this.
* rpois() function can generate random values from poisson distribution.
* there are different funcitons like hist() colMeans() functions covered in the course. have a look.
*  All of the standard probability distributions are built into R, including exponential (rexp()), chi-squared (rchisq()), gamma (rgamma()), .... Well, you see the pattern.

#Lesson 14 : Dates and Times#
* Dates are represented by the 'Date' class and times are represented by the 'POSIXct' and 'POSIXlt' classes. Internally, dates are stored as the number of days since 1970-01-01 and times are stored as either the number of seconds since 1970-01-01 (for 'POSIXct') or a list of seconds, minutes, hours, etc. (for 'POSIXlt').
* do d1<-Sys.Date() now class(d1) and then unclass(d1)  and see how date is internally stored as number of dates since Jan 1 1970. but if you see the value of d1 by just giving d1, you will see the date as proper date.
* what about dates before 1970? try this: d2 <- as.Date("1969-01-01") and then unclass(d2) now you can see a negative integer which means it is that many days before 1970 jan 1.
* Sys.time() will give time (along with date)
* t1 <- Sys.time() then print t1 and then class(t1) and then see the result. As mentioned earlier, POSIXct is just one of two ways that R represents time information. (You can ignore the second value above, POSIXt, which just functions as a common language between POSIXct and POSIXlt.) Use unclass() to see what t1 looks like internally -- the (large) number of seconds since the beginning of 1970. By default, Sys.time() returns an object of class POSIXct, but we can coerce the result to POSIXlt with as.POSIXlt(Sys.time()). Give it a try and store the result in t2. then try printing it, then class(t2) and then unclass(t2) and str(unclass(t2)). After seeing the results of str function, we understand that we just need to give t2$min to get minutes value. 
* there are date and time related functions to get date parts like weekdays(), months(), quarters().
* Often, the dates and times in a dataset will be in a format that R does not recognize. The strptime() function can be helpful in this situation. strptime() converts character vectors to POSIXlt. In that sense, it is similar to as.POSIXlt(), except that the input doesn't have to be in a particular format (YYYY-MM-DD). Here we have to give the syntax for which value in the input corresponds to year, date, hours and sec etc). 
* Finally, there are a number of operations that you can perform on dates and times, including arithmetic operations (+ and -) and comparisons (<, ==, etc.)
* if you give t1 - t2 then time difference will be shown in random units ?? but if you want the diffence to be shown in particular units, we can use difftime() function.
* In this lesson, you learned how to work with dates and times in R. While it is important to understand the basics, if you find yourself working with dates and times often, you may want to check out the lubridate package by Hadley Wickham. --check this.

#Lesson 15 : Base Graphics#
* We do not cover the more advanced portions of graphics in R in this lesson. These include lattice, ggplot2 and ggvis. There is a school of thought that this approach is backwards, that we should teach ggplot2 first. See http://varianceexplained.org/r/teach_ggplot2_to_beginners/ for an outline of this view.
* data(cars) loads the included data frame 'cars' (does this mean cars is an in-built dataframe in R-> check). Once loaded if we give ?cars, we get the help page for cars. So may be it is inbuilt -- check anyway.
* if you give plot(cars), As always, R tries very hard to give you something sensible given the information that you have  provided to it. First, R notes that the data frame you have given it has just two columns, so it assumes that you want to plot one column versus the other. Second, since we do not provide labels for either axis, R uses the names of the columns. Third, it creates axis tick marks at nice round numbers and labels them accordingly. Fourth, it uses the other defaults supplied in plot().
* We will now spend some time exploring plot, but many of the topics covered here will apply to most other R graphics functions. Note that 'plot' is short for scatterplot. for plot function do not type plot(cars$speed, cars$dist), although that will work. Instead, use plot(x = cars$speed, y = cars$dist).
* Note that there are other ways to call the plot command, i.e., using the "formula" interface. For example, we get a similar plot to the above with plot(dist ~ speed, cars). However, we will wait till later in the lesson before using the formula interface.
* The plot help page (?plot) only covers a small number of the many arguments that can be passed in to plot() and to other graphical functions. To begin to explore the many other options, look at ?par. Let's look at some of the more commonly used ones. Continue using plot(cars, ...) as the base answer to these questions.
* Go through the course in Swirl console. there are examples about many parameters.
* boxplot() is one more kind of plot. this kind of plot is there in Qlikview as well i dont remember the exact name there.
* Note that we can use the same set of arguments that we explored with plot() above to add axis labels, titles and so on in boxplot() as well 
* When looking at a single variable, histograms are a useful tool. hist() is the associated R function. Like plot(), hist() is best used by just passing in a single vector. Example hist(mtcars$mpg)
* In this lesson, you learned how to work with base graphics in R. The best place to go from here is to study the ggplot2 package. If you want to explore other elements of base graphics, then this web page (http://www.ling.upenn.edu/~joseff/rstudy/week4.html) provides a useful overview.

END of SWIRL Course - check if you can find anything useful in https://github.com/swirldev/swirl_courses which is the repository for this courses








