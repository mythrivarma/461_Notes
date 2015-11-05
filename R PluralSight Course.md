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
* 


