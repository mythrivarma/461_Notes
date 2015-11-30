#IDE and Help(on local machine)#
* All notes corresponds to R-Studio (especially shortcuts ).
* many IDEs are present for R. Rstudio is free best version.
* In RStudio IDE, Help menu will give 
* Help(), Demo(), Vignette() inbuilt Help commands for R.
* ?searchterm and Help(searchterm) are same. ??searchterm and Help("searchterm") are same. ?? will give related searches (? takes only exact searchterm)
* example(searchterm) will run the examples present in Help file for searchterm
* Ctrl+Enter will run the line where cursor is placed and then moves the cursor to next line.
* demo() will give all available as demos. Demo(package = "graphics") will give demos in graphics package.
* vignette() give usually PDFs which have detailed information about attached pacakges. syntax is similar to demo()

#Web Search, blogs and forums#
* RSiteSearch() - uses search engine at search.r-project.org
* RSiteSearch("arithematic mean") and RSiteSearch("{arithematic mean}") -- see the difference. 
* sos package can be installed from web and loaded to the library. the findFn() funtion in the sos package will work in the same way as RSiteSearch() but it is more appleaing to the eyes and also have some additional functionality. To install sos package, install.packages("sos") and then library("sos").
* If we want to search in web Search engines, using [R] will be more relevant.
* Help Communities : Mailing List, forums, Blogs
* Mailing List: you can subscribe to R-help (for generic) , R-devel (for technical), Special Interest Groups : (R-sig-finance, R-sig-hpc -> for high performance computing etc) check https://www.r-project.org/mail.html for all.
* Forums: http://bit.ly/stackoverflowR  (for R) http://bit.ly/crossvalidatedR (for Statistics) http://bit.ly/nabbleR (Very active form)
* Blogs : http://bit.ly/rbloggers http://bit.ly/revolutionAnalyticsR http://bit.ly/rstatistics http://bit.ly/rdatamining

# R Variables and Operators#
* x <- 10 here x is a Variable. R variables are case sensitive so x and X are different variables.
* Variables names can contain letter, number, dot, underline characters.
* Variable names should start with a letter. They can also start with a dot if the dot is not followed by a number. 
* We should not use reserve key words as variable names. Examples of reserved key words are NaN, Inf, TRUE, FALSE, NA_integer, function, if, for, break, while, repeat, etc. 
* Google R style Guide. http://bit.ly/googleRguide
* x <- 10 is not the only way to assign 10 value to x. we can also use assign() function. assign("x",10) will do the same. 
* In R we can use single or double quotes interchangebly in MOST cases.
* Environment is a bag which holds variables. Environments Use in lexical scoping (check this). There are custom environments and Global environment. as variable x can have different values in custom and Global environment. You can see Environment tab in the right top quadrant of RStudio.
* syntax to create new environment my.environment <- new.env() To add a variable to a custom environment that we created now, we have to give assign("x",10,my.environment)  other way of doing this is my.environment[["x"]] <- 10 other way is my.environment$x <- 10 (note that my.environment is just a variable name and not any syntax)
* To get the value of a variable from any custom environment, we can use get("x",my.environment) OR my.environment[["x"]] OR my.environment$x when we use $ sign, quotes are optional
* global environment is globalenv() function. So, if we want to get a value of variable from Global environment we can use get("x", globalenv())
* when we use new.env() to create a new environment, example: my.env <- new.env() then the default parent environment for the my.env environment will be Global environment. You can also get the parent environment details of any environment by using the function parent.env() so if we give parent.env(my.env) , we get R_GlobalEnv as a result.
* to run multiple line in R script of R studio, select the multiple lines and click Run button just like in ssms.
* Operators work on one or more Operands and return a result. 
* Arithmetic and Logical operators. 
* Arithmentic- will operate on numeric values . they are : +,-,*,/, ^ OR ** (exponent), %% (Modulos or remainder), %/% (for integer division - just like Greatest integer function). 10^5 will give the result as 1e+05. This is a scientic notation for exponential results. If you dont want to see scientific notation, use format function format(10 ^ 5, scientific = FALSE) this will return "100000" which is a character value. So, format did us no good except for showing 10^5 in a fancy way.
* Mathematical functions : abs() - for absolute value ex: abs(-5) is  5, log() - for natural logarithm (log to the base e?) ex: log(2) will give 0.6931, log(2, base 10) will give 0.30103, exp() for exponential and factorial() for factorial functions. ex: exp(5) = 148.413 and factorial(5) = 120.
* special constants : pi --will give only six digits after decimal by default because, if you go to options() function to see the default options, under digits you can see 7. to change this behaviour, we can give options(digits = 10), then if we print pi again, we can see 9 numbers after the decimal
* There are also many other arithmatic functions . check R Documentation.
* special Numbers : Inf and -Inf (negative infinity), NaN (Not a number), NA (Missing or Not available)
* Inf/Inf will give NaN. is.finite() function will let us know if a expression is infinte or not. Similarly is.nan() function will let us know if a value or expression evaluates to NaN. similarly we have is.na()
* important: NaN is an NA value but NA is not NaN. Example: is.nan(NA) give FALSE but is.na(NaN) gives TRUE
* Logical Operators : >, >=, <, <=, ==, !=, &, |, ! Logical operators can work on character values as well. Example "a" > "b" will give FALSE. However, remember that Character comparisons are LexicoGraphic and can depend on collations and encoding. 
* Vectorised Operations : Vector is a one-dimensional set of values of a similar type (data type). student.marks <- c(10,20,30,40) each of these mark values is a member or an element of the vector. scalar result means single value. mean() function wil work on all elements of vector and return a scalar value. sqrt() squareroot function can take a vector as an input and give vector as output. consider V1+V2+V3 , input is multiple vectors and output is single vector. So, total 3 types of vector operations Vector to Scalar, Vector to Vector, Multiple Vectors to Vector. 
* since we can do vectorised operations in R, we dont need to do Looping like in other programming languages, to do certain operations. 

#R Data Structure - Part 1#
* DataStructures: Atomic Vector, factor, list, Matrix, Dataframe, Array.
* Any data structure has two main components. 1. what kind of data is stored. 2. In what order is it stored. the next two points will define this.
* Atomic Vector, Martix, Array are homogenous data structures (have same type of data). List and Dataframe are heterogenous data structures.
* Atomic Vector is 1D (dimensional), Matrix is 2D, Array is nD. List is 1D and dataframe is 2D.
* Atomic Classes of data : Character ("A"), Numeric (4.36), Integer (3), Logical (TRUE), Complex (2+3i)
* Atomic vectors are commonly known as Vector. In R we use 'L' to explicitly mark any numeric value as integer. So, if you want to create an Integer Vector x, it will be like this x <- c(1L, 5L, 34L)
* For logical classes, we can either use TRUE or T example, x <- c(TRUE, T, F, FALSE) is valid.
* In R, even a scalar value is treated as vector of length 1. so even if you give x <- 1, even though 1 is scalar, it will still be considered as vector with one element.
* integer values can be considered as numeric as well but vice-versa is not true. Example. x <- c(3L, 45L) and is.numeric(x) will give TRUE but x <- c(23, 45) and is.integer(x) will give FALSE. 
*  another way to create a vector is vector() function. Example: if you give vector("integer", length = 4) will give output as [1] 0 0 0 0 (since 0 is the default value for integer in this function). similarly we can create vectors of other classes as well. default for logical is FALSE and for Numeric it is 0 and for complex, it is 0+0i
*  Subsetting : we use [] for subsetting example x <- c(1,2,3) then x[1] will give 1 (in R indexing will start with 1 unlike in other languages where it starts with 0). We can also give logical values while subsetting. Example: x[c(T,F,T)] will give output as 1,3. Even when you give x[x>2] then this is equivalent of x[FALSE,FALSE,TRUE] and you get output as 3 
*  coercion : convert one type to another. This can be implicit (R does it for us if it can) or explict. for doing explicitly we need to use 'as'. example: as.character(1:4) will give c("1","2","3","4"). But be careful for example as.integer(c(1.23,,45,45.3)) will give c(1,45,45) which might not be what we wanted. Also, if you give as.integer(c("Raj", "giri")) will give c(NA, NA). This way of explicit conversion makes no sense we will also get a warning along with this saying NAs are due to coersion
*  Factors: Factors come into picture when you know there are certain columns with Attributes kind of data. Like, gender, Product Type, etc. here instead of doing string comparision with these columns, it makes sense to store these values numerically (Male = 1 and female =2 etc). So, to do that, we can use factor function. If you print the value of a variable created using factor() function, if will show Male and Female with out quotes (hence they are not character type) and will also give levels : Female, male to tell the list of distinct values and thier corresponding numeric Ids (we have to understand the IDs based on order in levels output), example female= 1 and male = 2 here. the IDs are implicitly assigned by R based on alphabetical order of levels (distinct values). Remember that a factor is a one dimensional data structure.
*  We can also implicitly define levels and thier order in factors(). Example : factor(c("A", "B", "AB", "A"), levels = c("AB", "B", "O", "A"). Here, we not only mentioned the order of levels, but also created an extra level called O. Use Factors when needed. They are more efficient than character vectors and more self describing than integer vectors (since integer vector cannot tell a new developer of the code who doesnt know the existing data that 1 = male and 2 = female)
*  List : Heterogenous and 1 dimensional. To create a List, use the list() function
*  When you create a list and print it, you can see the [[]] for index. This is because, the list is heterogenous and each element can have its own dimensions. So, if you give x <- list(c(1,3), c("A"))  and print x, the output will be like [[1]] [1] 1,3 and [[2]] [1] "A" if you have other element as matrix (of 2x2), then it will be [[3]] [1] 4,6 [2] 90,32 . When we subset a list, we get a list only as output (not only for lists, for any data structure, its the same). in this example, if we give y<- list[1], we get a list as output with one element which is c(1,3). You can check this by giving typeof(y). However if you want to retain the actual class of the element even after subsetting a list, you need to give y <- x[[1]]. now class(y) or typeof(y) will give numeric. x$name is other alternative to x[[1]] if you have defined a named list.
*  difference between typeof() and class() - check this. 
*  you can also name the elements in the list and it becomes a named list. ones elements are named, we can use names while subsetting. Example: x ["namehere"] OR x$namehere

#R-Datastructures Part -2#
* last module we saw 1D data structures. Now, 2D
* DataFrame : most popular in R
* use data.frame() function to create a data frame , ensure that all vectors being fed as input should have same length (why? will re-cycling ). after creating a dataframe using data.frame(), if you give typeof(), you will get a list as answer. this is because the data frame is nothing but a list with vectors of equal length. --check what will happend if we give class() instead of typeof(). By default, the data.frame() will consider all character vectors as Frames. to off set this, we need explicitly mention stringAsFactors = FALSE while using the function.
* Subsetting in dataframes is interesting. check this. we can pull data from anyparticular cell, or Row or Column or subset of certain rows and columns etc. 
* Matirces : similar to Data frames in a way that they are two dimensional. but, only thing is they have elements of same class (Homogenous)
* rbind() and cbind() will bind vectors row/column wise (will create a matrix if both vector are of same class? -check)
* matrix() function to create a matrix. important parameters are no. of rows, columns and how to arrange data (by row/column)
* subsetting matrix() is similar to data frames. We can assingn rownames() and colnames() for matix (same with data frames??)
* rowsums() colsums() rowmeans() are some functions that operate at row/column level in matrix. 
* We can also do Mathematical matrix transformations like Inverse and Transpose in R matrices. please refer to R documentation if need be.
* Array <- Rarely used. Homogenous. N Dimensional
* like how SQL TABLE is to SSAS CUBE, MATRIX is to ARRAY. Matrix is 2 dimensional. Imagine an n dimensional matrix (3D for simlicity) and it becomes an ARRAY. Think of an array as Multiple sheets, where in each sheet is a matrix.

#R-Functions#
* R also supports RETURN syntax in functions. but its not mandatory.
* 'Lazy Evaluation' feature is available in R functions. So x <- function(a,b,c=d) {d <- mean(a) and then o <- a+b-c and then o } here, d is the default value of the parameter c but d is being populated only after the function is called. So, at the time of calling the function, even though the value of c is not available, the function will still work because, by the time the parameter c is needed in the function logic, the value of d has already been calculated. This is lazy evaluation which is common feature in many programming languages. 
* if you want the function to return multiple values, we can use the combination of RETURN statement and LIST functions. Example: return(list(total = a, average = b)) will return a named list with total and average values.
* formals() and body() functions give arguments and logic details of any function
* generally we call functino directly like sum(1:4). But there is another way as well using do.call() function. example: do.call(sum, list(a=1, b=2, c=3, d=4)) . here, second argument must be a list while using do.call(). 
* I have not mentioned notes which overlapped with swirl() course functions lesson. So, go check siwrl() course functions lesson to see more functions related notes.
* functions are also first class objects. So we can look into then (print and see the code), assign them to another object etc. 

#R-Flow Control # 
* IF - syntax if (Condition) {lines to be executed when Condition Evaluates to TRUE}
* use paste() for concatination
* IF-ELSE - Syntax if (Condition) {when Condition is true} Else {WHen Condition is false}
* 


