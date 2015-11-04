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
* 












