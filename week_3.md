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
## ── Attaching packages ─────────────────────────────────────────────────────────────────────── tidyverse 1.2.1 ──
```

```
## ✔ ggplot2 3.2.0     ✔ purrr   0.3.2
## ✔ tibble  2.1.3     ✔ dplyr   0.8.1
## ✔ tidyr   0.8.3     ✔ stringr 1.4.0
## ✔ readr   1.3.1     ✔ forcats 0.4.0
```

```
## ── Conflicts ────────────────────────────────────────────────────────────────────────── tidyverse_conflicts() ──
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

 - types of variables:
  - int stands for integers
  - dbl stands for doubles, or real number
  - chr stands for character vectors, or string
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
   - starts_with("abc"): matches names that begin with “abc”
   - ends_with("xyz"): matches names that end with “xyz”
   - contains("ijk"): matches names that contain “ijk”
   - matches("(.)\\1"): selects variables that match a regular expression. This one matches any variables that contain repeated characters. You’ll learn more about regular expressions in strings
   - num_range("x", 1:3): matches x1, x2 and x3
   - use rename() to rename variables
   - use everything() in select() to move variables to front of dataset

  - Create new variables with functions of existing variables (mutate())
   - to keep only new variables, use transmute() 
   - %/% (integer division), discards the remainder
   - %% (remainder)
  
  - Collapse many values down to a single summary (summarise())
   - na.rm = TRUE to get rid of NA values before computation 
   - use group_by() with summarise to make it more useful 
   - %>% (the pipe) is v useful so you don't have to name intermediate data frames (ggplot2 doesn't have pipe tho) 
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

**1.7 Find all flights that departed between midnight and 6am (inclusive).**
 

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


```r
arrange(flights, desc(is.na(dep_time)), dep_time)
```

```
## # A tibble: 336,776 x 19
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
## # … with 336,766 more rows, and 12 more variables: sched_arr_time <int>,
## #   arr_delay <dbl>, carrier <chr>, flight <int>, tailnum <chr>,
## #   origin <chr>, dest <chr>, air_time <dbl>, distance <dbl>, hour <dbl>,
## #   minute <dbl>, time_hour <dttm>
```

Use is.na to determine whether the variable is NA or not. If it is missing, then it will be listed first because the statement is TRUE and TRUE > FALSE. 

2. Sort flights to find the most delayed flights. Find the flights that left earliest.

most delayed flights:

```r
arrange(flights, desc(dep_delay))
```

```
## # A tibble: 336,776 x 19
##     year month   day dep_time sched_dep_time dep_delay arr_time
##    <int> <int> <int>    <int>          <int>     <dbl>    <int>
##  1  2013     1     9      641            900      1301     1242
##  2  2013     6    15     1432           1935      1137     1607
##  3  2013     1    10     1121           1635      1126     1239
##  4  2013     9    20     1139           1845      1014     1457
##  5  2013     7    22      845           1600      1005     1044
##  6  2013     4    10     1100           1900       960     1342
##  7  2013     3    17     2321            810       911      135
##  8  2013     6    27      959           1900       899     1236
##  9  2013     7    22     2257            759       898      121
## 10  2013    12     5      756           1700       896     1058
## # … with 336,766 more rows, and 12 more variables: sched_arr_time <int>,
## #   arr_delay <dbl>, carrier <chr>, flight <int>, tailnum <chr>,
## #   origin <chr>, dest <chr>, air_time <dbl>, distance <dbl>, hour <dbl>,
## #   minute <dbl>, time_hour <dttm>
```

earliest flights:

```r
arrange(flights, dep_delay)
```

```
## # A tibble: 336,776 x 19
##     year month   day dep_time sched_dep_time dep_delay arr_time
##    <int> <int> <int>    <int>          <int>     <dbl>    <int>
##  1  2013    12     7     2040           2123       -43       40
##  2  2013     2     3     2022           2055       -33     2240
##  3  2013    11    10     1408           1440       -32     1549
##  4  2013     1    11     1900           1930       -30     2233
##  5  2013     1    29     1703           1730       -27     1947
##  6  2013     8     9      729            755       -26     1002
##  7  2013    10    23     1907           1932       -25     2143
##  8  2013     3    30     2030           2055       -25     2213
##  9  2013     3     2     1431           1455       -24     1601
## 10  2013     5     5      934            958       -24     1225
## # … with 336,766 more rows, and 12 more variables: sched_arr_time <int>,
## #   arr_delay <dbl>, carrier <chr>, flight <int>, tailnum <chr>,
## #   origin <chr>, dest <chr>, air_time <dbl>, distance <dbl>, hour <dbl>,
## #   minute <dbl>, time_hour <dttm>
```

**3. Sort flights to find the fastest flights.**


```r
fastest_flights <- mutate(flights, mph = distance / air_time * 60)
fastest_flights <- select(fastest_flights, mph, distance, air_time,flight, origin, dest, year, month, day)
arrange(fastest_flights, desc(mph))
```

```
## # A tibble: 336,776 x 9
##      mph distance air_time flight origin dest   year month   day
##    <dbl>    <dbl>    <dbl>  <int> <chr>  <chr> <int> <int> <int>
##  1  703.      762       65   1499 LGA    ATL    2013     5    25
##  2  650.     1008       93   4667 EWR    MSP    2013     7     2
##  3  648       594       55   4292 EWR    GSP    2013     5    13
##  4  641.      748       70   3805 EWR    BNA    2013     3    23
##  5  591.     1035      105   1902 LGA    PBI    2013     1    12
##  6  564      1598      170    315 JFK    SJU    2013    11    17
##  7  557.     1598      172    707 JFK    SJU    2013     2    21
##  8  556.     1623      175    936 JFK    STT    2013    11    17
##  9  554.     1598      173    347 JFK    SJU    2013    11    16
## 10  554.     1598      173   1503 JFK    SJU    2013    11    16
## # … with 336,766 more rows
```

4. Which flights travelled the longest? Which travelled the shortest?

longest flight:

```r
arrange(flights, desc(distance))
```

```
## # A tibble: 336,776 x 19
##     year month   day dep_time sched_dep_time dep_delay arr_time
##    <int> <int> <int>    <int>          <int>     <dbl>    <int>
##  1  2013     1     1      857            900        -3     1516
##  2  2013     1     2      909            900         9     1525
##  3  2013     1     3      914            900        14     1504
##  4  2013     1     4      900            900         0     1516
##  5  2013     1     5      858            900        -2     1519
##  6  2013     1     6     1019            900        79     1558
##  7  2013     1     7     1042            900       102     1620
##  8  2013     1     8      901            900         1     1504
##  9  2013     1     9      641            900      1301     1242
## 10  2013     1    10      859            900        -1     1449
## # … with 336,766 more rows, and 12 more variables: sched_arr_time <int>,
## #   arr_delay <dbl>, carrier <chr>, flight <int>, tailnum <chr>,
## #   origin <chr>, dest <chr>, air_time <dbl>, distance <dbl>, hour <dbl>,
## #   minute <dbl>, time_hour <dttm>
```

shortest flight:

```r
arrange(flights, distance)
```

```
## # A tibble: 336,776 x 19
##     year month   day dep_time sched_dep_time dep_delay arr_time
##    <int> <int> <int>    <int>          <int>     <dbl>    <int>
##  1  2013     7    27       NA            106        NA       NA
##  2  2013     1     3     2127           2129        -2     2222
##  3  2013     1     4     1240           1200        40     1333
##  4  2013     1     4     1829           1615       134     1937
##  5  2013     1     4     2128           2129        -1     2218
##  6  2013     1     5     1155           1200        -5     1241
##  7  2013     1     6     2125           2129        -4     2224
##  8  2013     1     7     2124           2129        -5     2212
##  9  2013     1     8     2127           2130        -3     2304
## 10  2013     1     9     2126           2129        -3     2217
## # … with 336,766 more rows, and 12 more variables: sched_arr_time <int>,
## #   arr_delay <dbl>, carrier <chr>, flight <int>, tailnum <chr>,
## #   origin <chr>, dest <chr>, air_time <dbl>, distance <dbl>, hour <dbl>,
## #   minute <dbl>, time_hour <dttm>
```

#### 5.4.1 Exercises

1. Brainstorm as many ways as possible to select dep_time, dep_delay, arr_time, and arr_delay from flights.


```r
select(flights, dep_time, dep_delay, arr_time, arr_delay)
```

```
## # A tibble: 336,776 x 4
##    dep_time dep_delay arr_time arr_delay
##       <int>     <dbl>    <int>     <dbl>
##  1      517         2      830        11
##  2      533         4      850        20
##  3      542         2      923        33
##  4      544        -1     1004       -18
##  5      554        -6      812       -25
##  6      554        -4      740        12
##  7      555        -5      913        19
##  8      557        -3      709       -14
##  9      557        -3      838        -8
## 10      558        -2      753         8
## # … with 336,766 more rows
```


```r
select(flights, "dep_time", "dep_delay", "arr_time", "arr_delay")
```

```
## # A tibble: 336,776 x 4
##    dep_time dep_delay arr_time arr_delay
##       <int>     <dbl>    <int>     <dbl>
##  1      517         2      830        11
##  2      533         4      850        20
##  3      542         2      923        33
##  4      544        -1     1004       -18
##  5      554        -6      812       -25
##  6      554        -4      740        12
##  7      555        -5      913        19
##  8      557        -3      709       -14
##  9      557        -3      838        -8
## 10      558        -2      753         8
## # … with 336,766 more rows
```


```r
select(flights, starts_with("dep_"), starts_with("arr_"))
```

```
## # A tibble: 336,776 x 4
##    dep_time dep_delay arr_time arr_delay
##       <int>     <dbl>    <int>     <dbl>
##  1      517         2      830        11
##  2      533         4      850        20
##  3      542         2      923        33
##  4      544        -1     1004       -18
##  5      554        -6      812       -25
##  6      554        -4      740        12
##  7      555        -5      913        19
##  8      557        -3      709       -14
##  9      557        -3      838        -8
## 10      558        -2      753         8
## # … with 336,766 more rows
```

2. What happens if you include the name of a variable multiple times in a select() call?


```r
select(flights, dep_time, dep_time, arr_time)
```

```
## # A tibble: 336,776 x 2
##    dep_time arr_time
##       <int>    <int>
##  1      517      830
##  2      533      850
##  3      542      923
##  4      544     1004
##  5      554      812
##  6      554      740
##  7      555      913
##  8      557      709
##  9      557      838
## 10      558      753
## # … with 336,766 more rows
```

There is no error or any toruble printing the function. 

3. What does the one_of() function do? Why might it be helpful in conjunction with this vector?


```r
vars <- c("year", "month", "day", "dep_delay", "arr_delay")
```

The one_of function matches varaible names in a character vector. It would be helpful becuase instead of writing out seperate arguments for each character variable, you could write out the variable name like this:


```r
select(flights, one_of(vars))
```

```
## # A tibble: 336,776 x 5
##     year month   day dep_delay arr_delay
##    <int> <int> <int>     <dbl>     <dbl>
##  1  2013     1     1         2        11
##  2  2013     1     1         4        20
##  3  2013     1     1         2        33
##  4  2013     1     1        -1       -18
##  5  2013     1     1        -6       -25
##  6  2013     1     1        -4        12
##  7  2013     1     1        -5        19
##  8  2013     1     1        -3       -14
##  9  2013     1     1        -3        -8
## 10  2013     1     1        -2         8
## # … with 336,766 more rows
```

4. Does the result of running the following code surprise you? How do the select helpers deal with case by default? How can you change that default?


```r
select(flights, contains("TIME"))
```

```
## # A tibble: 336,776 x 6
##    dep_time sched_dep_time arr_time sched_arr_time air_time
##       <int>          <int>    <int>          <int>    <dbl>
##  1      517            515      830            819      227
##  2      533            529      850            830      227
##  3      542            540      923            850      160
##  4      544            545     1004           1022      183
##  5      554            600      812            837      116
##  6      554            558      740            728      150
##  7      555            600      913            854      158
##  8      557            600      709            723       53
##  9      557            600      838            846      140
## 10      558            600      753            745      138
## # … with 336,766 more rows, and 1 more variable: time_hour <dttm>
```

It is surprising that contains() ignores case as R doesn't ignore case. To deal with this default, you can change it by using ignore.case = FALSE in you contains() function. 

#### 5.5.2 Exercises

1. Currently dep_time and sched_dep_time are convenient to look at, but hard to compute with because they’re not really continuous numbers. Convert them to a more convenient representation of number of minutes since midnight.


```r
flights_time <- mutate(flights, dep_time_mins = (dep_time %/% 100 * 60 + dep_time %% 100) %% 1440, sched_dep_time_mins = (sched_dep_time %/% 100 * 60 + sched_dep_time %% 100) %% 1440)
select(flights_time, dep_time, sched_dep_time, dep_time_mins, sched_dep_time)
```

```
## # A tibble: 336,776 x 3
##    dep_time sched_dep_time dep_time_mins
##       <int>          <int>         <dbl>
##  1      517            515           317
##  2      533            529           333
##  3      542            540           342
##  4      544            545           344
##  5      554            600           354
##  6      554            558           354
##  7      555            600           355
##  8      557            600           357
##  9      557            600           357
## 10      558            600           358
## # … with 336,766 more rows
```

**DON'T UNDERSTAND THE MATH, READ 5.1.1.!**

2. Compare air_time with arr_time - dep_time. What do you expect to see? What do you see? What do you need to do to fix it? 

I expect that air_time = arr_time - dep_time. 


```r
flights_airtime <- mutate(flights, dep_time = (dep_time %/% 100 * 60 + dep_time %% 100) %% 1440, arr_time = (arr_time %/% 100 * 60 + arr_time %% 100) %% 1440, air_time_diff = air_time - arr_time + dep_time)
filter(flights_airtime, air_time_diff != 0) 
```

```
## # A tibble: 327,150 x 20
##     year month   day dep_time sched_dep_time dep_delay arr_time
##    <int> <int> <int>    <dbl>          <int>     <dbl>    <dbl>
##  1  2013     1     1      317            515         2      510
##  2  2013     1     1      333            529         4      530
##  3  2013     1     1      342            540         2      563
##  4  2013     1     1      344            545        -1      604
##  5  2013     1     1      354            600        -6      492
##  6  2013     1     1      354            558        -4      460
##  7  2013     1     1      355            600        -5      553
##  8  2013     1     1      357            600        -3      429
##  9  2013     1     1      357            600        -3      518
## 10  2013     1     1      358            600        -2      473
## # … with 327,140 more rows, and 13 more variables: sched_arr_time <int>,
## #   arr_delay <dbl>, carrier <chr>, flight <int>, tailnum <chr>,
## #   origin <chr>, dest <chr>, air_time <dbl>, distance <dbl>, hour <dbl>,
## #   minute <dbl>, time_hour <dttm>, air_time_diff <dbl>
```

There should be no flights where air_time_diff doesn't equal 0, but there are. This means that there are flights where time zones were changed or the dep_time was greater than arr_time. I don't know how to fix it. 

3. Compare dep_time, sched_dep_time, and dep_delay. How would you expect those three numbers to be related?

I expect dep_delay = dep_time - sched_dep_time, but like the previous question there will be discrepencies due to the dep_time and sched_dep_time being on different days. 

4. Find the 10 most delayed flights using a ranking function. How do you want to handle ties? Carefully read the documentation for min_rank(). 


```r
flights_delayed <- mutate(flights, dep_delay_min_rank = min_rank(desc(dep_delay)))
flights_delayed <- (filter(flights_delayed, !(dep_delay_min_rank >10)))
flights_delayed <- arrange(flights_delayed, dep_delay, dep_delay_min_rank)
select(flights_delayed, dep_delay, dep_delay_min_rank)
```

```
## # A tibble: 10 x 2
##    dep_delay dep_delay_min_rank
##        <dbl>              <int>
##  1       896                 10
##  2       898                  9
##  3       899                  8
##  4       911                  7
##  5       960                  6
##  6      1005                  5
##  7      1014                  4
##  8      1126                  3
##  9      1137                  2
## 10      1301                  1
```

To handle ties, you can use dense_rank(). 

5. What does 1:3 + 1:10 return? Why?


```r
1:3 + 1:10 
```

```
## Warning in 1:3 + 1:10: longer object length is not a multiple of shorter
## object length
```

```
##  [1]  2  4  6  5  7  9  8 10 12 11
```

When adding two vectors, the code recylces the shorter one to match the length of the longer one. 

#### 5.6.7 Exercises 

5. Which carrier has the worst delays? Challenge: can you disentangle the effects of bad airports vs. bad carriers? Why/why not? (Hint: think about flights %>% group_by(carrier, dest) %>% summarise(n()))


```r
flights %>%
group_by(carrier) %>%
summarise(arr_delay = mean(arr_delay, na.rm = TRUE)) %>%
arrange(desc(arr_delay))
```

```
## # A tibble: 16 x 2
##    carrier arr_delay
##    <chr>       <dbl>
##  1 F9         21.9  
##  2 FL         20.1  
##  3 EV         15.8  
##  4 YV         15.6  
##  5 OO         11.9  
##  6 MQ         10.8  
##  7 WN          9.65 
##  8 B6          9.46 
##  9 9E          7.38 
## 10 UA          3.56 
## 11 US          2.13 
## 12 VX          1.76 
## 13 DL          1.64 
## 14 AA          0.364
## 15 HA         -6.92 
## 16 AS         -9.93
```

```r
filter(airlines, carrier == "F9")
```

```
## # A tibble: 1 x 2
##   carrier name                  
##   <chr>   <chr>                 
## 1 F9      Frontier Airlines Inc.
```

Frontier Airline Inc. has the worst delays. 
