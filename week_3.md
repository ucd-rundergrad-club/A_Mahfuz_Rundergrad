---
title: "week_3"
output: 
  html_document: 
    keep_md: yes
---



### Chapter 4

#### Notes

 - surround entire ssignment with () to make an assignment and print to screen
 
 - enviroment shows all assignments made

#### 4.4 Practice

1. Why does this code not work?
 
my_variable <- 10
my_varıable

This code doesn't work becuase in the second line, the character i in my_varıable doesn't match the character i in the first line. 

2. Tweak each of the following R commands so that they run correctly:
 

```r
library(tidyverse)
```

```
## ── Attaching packages ──────────────────────────────────────────────────── tidyverse 1.2.1 ──
```

```
## ✔ ggplot2 3.2.0     ✔ purrr   0.3.2
## ✔ tibble  2.1.3     ✔ dplyr   0.8.1
## ✔ tidyr   0.8.3     ✔ stringr 1.4.0
## ✔ readr   1.3.1     ✔ forcats 0.4.0
```

```
## ── Conflicts ─────────────────────────────────────────────────────── tidyverse_conflicts() ──
## ✖ dplyr::filter() masks stats::filter()
## ✖ dplyr::lag()    masks stats::lag()
```

```r
ggplot(data = mpg) + 
  geom_point(mapping = aes(x = displ, y = hwy))
```

![](week_3_files/figure-html/unnamed-chunk-1-1.png)<!-- -->

```r
filter(mpg, cyl == 8)
```

```
## # A tibble: 70 x 11
##    manufacturer model displ  year   cyl trans drv     cty   hwy fl    class
##    <chr>        <chr> <dbl> <int> <int> <chr> <chr> <int> <int> <chr> <chr>
##  1 audi         a6 q…   4.2  2008     8 auto… 4        16    23 p     mids…
##  2 chevrolet    c150…   5.3  2008     8 auto… r        14    20 r     suv  
##  3 chevrolet    c150…   5.3  2008     8 auto… r        11    15 e     suv  
##  4 chevrolet    c150…   5.3  2008     8 auto… r        14    20 r     suv  
##  5 chevrolet    c150…   5.7  1999     8 auto… r        13    17 r     suv  
##  6 chevrolet    c150…   6    2008     8 auto… r        12    17 r     suv  
##  7 chevrolet    corv…   5.7  1999     8 manu… r        16    26 p     2sea…
##  8 chevrolet    corv…   5.7  1999     8 auto… r        15    23 p     2sea…
##  9 chevrolet    corv…   6.2  2008     8 manu… r        16    26 p     2sea…
## 10 chevrolet    corv…   6.2  2008     8 auto… r        15    25 p     2sea…
## # … with 60 more rows
```

```r
filter(diamonds, carat > 3)
```

```
## # A tibble: 32 x 10
##    carat cut     color clarity depth table price     x     y     z
##    <dbl> <ord>   <ord> <ord>   <dbl> <dbl> <int> <dbl> <dbl> <dbl>
##  1  3.01 Premium I     I1       62.7    58  8040  9.1   8.97  5.67
##  2  3.11 Fair    J     I1       65.9    57  9823  9.15  9.02  5.98
##  3  3.01 Premium F     I1       62.2    56  9925  9.24  9.13  5.73
##  4  3.05 Premium E     I1       60.9    58 10453  9.26  9.25  5.66
##  5  3.02 Fair    I     I1       65.2    56 10577  9.11  9.02  5.91
##  6  3.01 Fair    H     I1       56.1    62 10761  9.54  9.38  5.31
##  7  3.65 Fair    H     I1       67.1    53 11668  9.53  9.48  6.38
##  8  3.24 Premium H     I1       62.1    58 12300  9.44  9.4   5.85
##  9  3.22 Ideal   I     I1       62.6    55 12545  9.49  9.42  5.92
## 10  3.5  Ideal   H     I1       62.8    57 12587  9.65  9.59  6.03
## # … with 22 more rows
```

3. Press Alt + Shift + K. What happens? How can you get to the same place using the menus?

It takes you to a menu with keyboard shortcuts. Keyboard shortcuts can also be found under tools in the menu. 

### Chapter 5

#### Notes 

 - types of variables
 
  - int stands for integers
  
  - dbl stands for doubles, or real numbers

  - chr stands for character vectors, or strings

  - dttm stands for date-times (a date + a time)
  
  - lgl stands for logical, vectors that contain only TRUE or FALSE

  - fctr stands for factors, which R uses to represent categorical variables with fixed possible values

  - date stands for dates.
 
 - dplyr functions:

  - Pick observations by their values (filter())
  
   - x %in% y will select every row where x is one of the values in y; ex. nov_dec <- filter(flights, month %in% c(11, 12))
   
   - !(x & y) is the same as !x | !y, and !(x | y) is the same as !x & !y
   
   - only includes observations that are TRUE; explicitly ask for values that are NA or FALSE
  
  - Reorder the rows (arrange())
  
   - changes order of rows from smallest value to largest
   
   - use desc() to re-order by a column in descending order
   
   - if you list multiple columns, the proceeding column will be used as a tie breaker
   
   - NA is always at the end
   
  - Pick variables by their names (select())
  
   - 
  
  - Create new variables with functions of existing variables (mutate())
  
  - Collapse many values down to a single summary (summarise())
  
  - group_by() changes the scope of function from entire dataset to group 
  
 - how verbs work:
 
  1. first argument is dataset
  
  2. subsequent arguments are variables and what to do with them 
  
#### 5.2.4 Exercises

 1.1. Find all flights that had an arrival delay of two or more hours.
 

```r
library(nycflights13)
filter(flights, arr_delay >= 120)
```

```
## # A tibble: 10,200 x 19
##     year month   day dep_time sched_dep_time dep_delay arr_time
##    <int> <int> <int>    <int>          <int>     <dbl>    <int>
##  1  2013     1     1      811            630       101     1047
##  2  2013     1     1      848           1835       853     1001
##  3  2013     1     1      957            733       144     1056
##  4  2013     1     1     1114            900       134     1447
##  5  2013     1     1     1505           1310       115     1638
##  6  2013     1     1     1525           1340       105     1831
##  7  2013     1     1     1549           1445        64     1912
##  8  2013     1     1     1558           1359       119     1718
##  9  2013     1     1     1732           1630        62     2028
## 10  2013     1     1     1803           1620       103     2008
## # … with 10,190 more rows, and 12 more variables: sched_arr_time <int>,
## #   arr_delay <dbl>, carrier <chr>, flight <int>, tailnum <chr>,
## #   origin <chr>, dest <chr>, air_time <dbl>, distance <dbl>, hour <dbl>,
## #   minute <dbl>, time_hour <dttm>
```
 
 1.4. Find all flights that departed in summer (July, August, and September).
 

```r
filter(flights, month <= 9, month >= 7)
```

```
## # A tibble: 86,326 x 19
##     year month   day dep_time sched_dep_time dep_delay arr_time
##    <int> <int> <int>    <int>          <int>     <dbl>    <int>
##  1  2013     7     1        1           2029       212      236
##  2  2013     7     1        2           2359         3      344
##  3  2013     7     1       29           2245       104      151
##  4  2013     7     1       43           2130       193      322
##  5  2013     7     1       44           2150       174      300
##  6  2013     7     1       46           2051       235      304
##  7  2013     7     1       48           2001       287      308
##  8  2013     7     1       58           2155       183      335
##  9  2013     7     1      100           2146       194      327
## 10  2013     7     1      100           2245       135      337
## # … with 86,316 more rows, and 12 more variables: sched_arr_time <int>,
## #   arr_delay <dbl>, carrier <chr>, flight <int>, tailnum <chr>,
## #   origin <chr>, dest <chr>, air_time <dbl>, distance <dbl>, hour <dbl>,
## #   minute <dbl>, time_hour <dttm>
```
 
 1.5. Find all flights that arrived more than two hours late, but didn’t leave late. 
 

```r
 filter(flights, arr_delay >= 120, dep_delay <= 0)
```

```
## # A tibble: 29 x 19
##     year month   day dep_time sched_dep_time dep_delay arr_time
##    <int> <int> <int>    <int>          <int>     <dbl>    <int>
##  1  2013     1    27     1419           1420        -1     1754
##  2  2013    10     7     1350           1350         0     1736
##  3  2013    10     7     1357           1359        -2     1858
##  4  2013    10    16      657            700        -3     1258
##  5  2013    11     1      658            700        -2     1329
##  6  2013     3    18     1844           1847        -3       39
##  7  2013     4    17     1635           1640        -5     2049
##  8  2013     4    18      558            600        -2     1149
##  9  2013     4    18      655            700        -5     1213
## 10  2013     5    22     1827           1830        -3     2217
## # … with 19 more rows, and 12 more variables: sched_arr_time <int>,
## #   arr_delay <dbl>, carrier <chr>, flight <int>, tailnum <chr>,
## #   origin <chr>, dest <chr>, air_time <dbl>, distance <dbl>, hour <dbl>,
## #   minute <dbl>, time_hour <dttm>
```

 **1.7** Find all flights that departed between midnight and 6am (inclusive).
 

```r
filter(flights, dep_time == 2400 | dep_time <= 600)
```

```
## # A tibble: 9,373 x 19
##     year month   day dep_time sched_dep_time dep_delay arr_time
##    <int> <int> <int>    <int>          <int>     <dbl>    <int>
##  1  2013     1     1      517            515         2      830
##  2  2013     1     1      533            529         4      850
##  3  2013     1     1      542            540         2      923
##  4  2013     1     1      544            545        -1     1004
##  5  2013     1     1      554            600        -6      812
##  6  2013     1     1      554            558        -4      740
##  7  2013     1     1      555            600        -5      913
##  8  2013     1     1      557            600        -3      709
##  9  2013     1     1      557            600        -3      838
## 10  2013     1     1      558            600        -2      753
## # … with 9,363 more rows, and 12 more variables: sched_arr_time <int>,
## #   arr_delay <dbl>, carrier <chr>, flight <int>, tailnum <chr>,
## #   origin <chr>, dest <chr>, air_time <dbl>, distance <dbl>, hour <dbl>,
## #   minute <dbl>, time_hour <dttm>
```
 
 2. Another useful dplyr filtering helper is between(). What does it do? Can you use it to simplify the code needed to answer the previous challenges?
 
between() is a shortcut for x >= left & x <= right. You can simplify the statement _departed in the summer_.


```r
filter(flights, between(month, 7, 9))
```

```
## # A tibble: 86,326 x 19
##     year month   day dep_time sched_dep_time dep_delay arr_time
##    <int> <int> <int>    <int>          <int>     <dbl>    <int>
##  1  2013     7     1        1           2029       212      236
##  2  2013     7     1        2           2359         3      344
##  3  2013     7     1       29           2245       104      151
##  4  2013     7     1       43           2130       193      322
##  5  2013     7     1       44           2150       174      300
##  6  2013     7     1       46           2051       235      304
##  7  2013     7     1       48           2001       287      308
##  8  2013     7     1       58           2155       183      335
##  9  2013     7     1      100           2146       194      327
## 10  2013     7     1      100           2245       135      337
## # … with 86,316 more rows, and 12 more variables: sched_arr_time <int>,
## #   arr_delay <dbl>, carrier <chr>, flight <int>, tailnum <chr>,
## #   origin <chr>, dest <chr>, air_time <dbl>, distance <dbl>, hour <dbl>,
## #   minute <dbl>, time_hour <dttm>
```

 3. How many flights have a missing dep_time? What other variables are missing? What might these rows represent?
 

```r
filter(flights, is.na(dep_time))
```

```
## # A tibble: 8,255 x 19
##     year month   day dep_time sched_dep_time dep_delay arr_time
##    <int> <int> <int>    <int>          <int>     <dbl>    <int>
##  1  2013     1     1       NA           1630        NA       NA
##  2  2013     1     1       NA           1935        NA       NA
##  3  2013     1     1       NA           1500        NA       NA
##  4  2013     1     1       NA            600        NA       NA
##  5  2013     1     2       NA           1540        NA       NA
##  6  2013     1     2       NA           1620        NA       NA
##  7  2013     1     2       NA           1355        NA       NA
##  8  2013     1     2       NA           1420        NA       NA
##  9  2013     1     2       NA           1321        NA       NA
## 10  2013     1     2       NA           1545        NA       NA
## # … with 8,245 more rows, and 12 more variables: sched_arr_time <int>,
## #   arr_delay <dbl>, carrier <chr>, flight <int>, tailnum <chr>,
## #   origin <chr>, dest <chr>, air_time <dbl>, distance <dbl>, hour <dbl>,
## #   minute <dbl>, time_hour <dttm>
```

Other variables that are missing are arr_time for these rows. This means that these flights probably got cancelled. 

#### 5.3.1 Exercises 

1. How could you use arrange() to sort all missing values to the start? (Hint: use is.na()).

```{}
arrange(flights, desc(is.na(dep_time)), dep_time)
```

Use is.na to determine whether the variable is NA or not. If it is missing, then it will be listed first because the statement is TRUE and TRUE > FALSE. 

2. Sort flights to find the most delayed flights. Find the flights that left earliest.

most delayed flights:
```{}
arrange(flights, desc(dep_delay))
```

earliest flights:
```{}
arrange(flights, dep_delay)
```

**3. Sort flights to find the fastest flights.**

```{}
fastest_flights <- mutate(flights, mph = distance / air_time * 60)
fastest_flights <- select(fastest_flights, mph, distance, air_time,flight, origin, dest, year, month, day)
head(arrange(fastest_flights, desc(mph)))
```

4. Which flights travelled the longest? Which travelled the shortest?

longest flight:
```{}
arrange(flights, desc(distance))
```

shortest flight:
```{}
arrange(flights, distance)
```

