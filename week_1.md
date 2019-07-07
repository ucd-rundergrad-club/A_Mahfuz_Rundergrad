---
title: "week 1"
output: 
  html_document: 
    keep_md: yes
---



## Swirl Tutoriol Notes


##### 1. Basic Building Blocks

  * can be used as a interactive calculator ; ex. 6 + 3
  * variable <- value
  * vector 
    * small collection of numbers
    * simplest type of data structure in R
    * length of vector is # of #s in the vector ; single # is vector of length 1
    * c() function to create vectors
    * numeric vectors can be used in arithmetic expressions ; ex. if z = 1, 2, 3, then z * 2 <- in this case, all #s in vector z were multiplied by 2 (remember 2 is vector of lenth one)
    * if 2 vector r same length, then R can perform the specified arithmetic operation element by element 
    * if vectors r diff lengths, then R recycles shorter vector till same length as longer one 
  * use `?` command for ?s on a function 
  * sqaure root use sqrt() function
  * absolute value use abs() function
  * up arrow takes u to previous commands 
  * first 2 letters of variable to quickly c what u assigned to it


##### 3. Sequence of Numbers 

  * use `:` operator to create squence of #s (uses increments of 1)
  * if have ?s abt operator, type ? and operator name in tick marks/wuotes ; ex. ?`:`
  * seq() function gives more control over sequence
  * to change increment, do seq(#, #, by = increment here) 
  * to get a specific length, do seq(#, #, length = length here)
  * length() function gives length of variable
  * seq_along () function gives a new vector that is same length as another vector (whatever sequence/variable was put in the parenthesis)
  * rep () function allows you to repeat by (#/vector/varialbe, times/each = # of times you want to repeat)


##### 4. Vectors

  * 2 kinds of vectors: atomic (one data type) and lists (multiple-data type)
  * atomic vectors include:
    * logical
      * include true, false, NA
      * logical operators include <, >, <=, >=, == (exact equality), and != (inequality)
      * if 2 logical expressions, A and B, ask if one is true using A | B or ask if both are true using A & B
      * !A is negation of A and is true when A is false and vice versa
    * character
      * double quotes are used to distinguish character objects 
      * to add words to a charcter vector use c (variable for vector / vector, "words you want to add")
      * use paste (variable for vector / vector, collapse = " ") to join elements of vector into one continous character string (character vector of length 1)
      * use paste (variable for vector/ vector #1, variable for vector/ vector #2, sep = " ") to join elements of multiple character vectors 
      * **THE SPACE BETWEEN THE DOUBLE QUOTES SIGNIFIES WHAT YOU WANT BETWEEN THE JOINED ELEMENTS**
    * integer 
    * complex 


##### 5. Missing Values

  * NA signifies missing values and not avialable 
  * if NA is present, answer is usually NA
  * to select random elements from data, use sample(vector, # of random elements wanted)
  * is.na() function tells whether each element of a vector is NA
  * TRUE is recognized as 1 and FALSE is recognized as 0
  * to find # of NA in data, use sum(data/variable). the answer is the # of NA
  * NaN means not a number
  * Inf stands for infinity 


##### 6. Subsetting Vectors

  * to select particular element (subset) of vector -> name of vector["index vector"]
  * there are 4 kinds of index vectors: 
    * logical vectors:
      * identical() tells whether 2 vectors are the same
      * `!` gives negation of logical expression
      * to get all values that are not NA use !is.na(x) (read as `is not NA`) as index vector
      * write variable > 0 as index vector to get all positive integers of vector
    * vectors of positive integers:
     * if you want * term of a vector use c(*) function as index vector
    * vectors of negative integers: 
      * if you want all elements except * term of a vector, use c(-*) as index vector
      * tip: type - in front of vector ; ex. -c(*)
    * vectors of character strings: 
      * to assign numbers to names use c(# = "name", etc.)
      * names(variable for vector) will give you names that were assigned to numbers in the vector 
      * assign numbers to names by writing vector w/ numbers then setting it to names by doing names(vector / variable for vector) <- c("name", "name", etc.)
      * to get * element of vector, use "word" or c("word", "word") that corresponds to * term/s as index vector
  * R is one-based indexing so first element of vector is considered element 1


##### 7. Matrices and Data Frames 

  * both represent rectagular data (tabular data, ie. rows and columns)
  * matrices contain sungle class of data
  * data frames have many diff classes of data
  * to get or set the 'dim' of an objecy, use dim() function 
  * attributes() allows you to see 'dim'
  * first # of dim is # of rows, second is # of columns
  * class() allows u to c what the object is 
  *   * easier way to make matrix is using matrix(data which is either c function or `:`, nrow = , ncol = , byrow = (FALSE means the #s will go up to down, TRUE means the #s will go left to right), dimnames = NULL if no name, )
  * cbind(vector column you want to add or variable that represents it, matrix / variable) to combine columns and matrices together **ONLY USE THIS WHEN THE COLUMN AND MATRIX YOU WANT TO COMBINE ARE THE SAME TYPE OF DATA ; EX. CHARACTER STRINGS**
  * data.frame() function allows you to store character vectors and matrix of numbers side by side
  *colnames(matrix/variable for matrix) <- vector created for colnames or variable that represents it


##### 8. Logic

  * 2 logical values in R (boolean values) which are TRUE and FALSE
  * `!=` tests if two values are not equal 
  * ! always negates/means opposite ; ex. !TRUE = FALSE, !FALSE = TRUE
  * the `&` and `&&` operator evalutes whether both operands in an expression are true. if **both** are true than the statement is true, otherwise it is false 
  * `&` evalutes across entire vector on both sides
  * `&&` only evalutes first member of a vector 
  * `|` and `||` operator evalutes whether one or the other operands are true. as long as one operand is true than the entire statement is true, but if both are false, than the statement is false. 
  *`|` evalutes across the entire vector 
  `||` evalutes the first member of the vector 


##### 12. Looking at Data

  * ls() lists the variables in your workspace
  * data frame is default class for data read into R using functions like read.csv() and read.table()
  * nrow() tells u how many rows and ncol() tells u how many columns
  * to see how much memory is occupied by dataset, use object.size()
  * names () will give u cahracter vector of column names 
  * head() allows you preview top of dataset
    * by default will only show you first six rows of data w/ the column name
    * to see more data, do head(data set, # of rows)
  * tail() wllows you to preview end of dataset
  * summary () shows how each variable is distributed and how much of dataset is missing 
  * use table(variable for/dataset$name of column) to see how many times each value occurs in the data >> use if in the summary() function there was an other category >> basically this function is how you go more in depth of the previous function 
  * str() provides structure of something and is a general function that shows most of the info abt dataset
