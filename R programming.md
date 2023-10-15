---
banner_icon: 🤓
---


- [[#Function|Function]]
- [[#Argument|Argument]]
- [[#variable/onjects|variable/onjects]]
- [[#Comment -|Comment -]]
- [[#Vectors|Vectors]]
	- [[#Vectors#Atomic vectors|Atomic vectors]]
	- [[#Vectors#Creating lists|Creating lists]]
- [[#Pipes|Pipes]]
- [[#data structures in R|data structures in R]]
- [[#Dates and times in R|Dates and times in R]]
- [[#Data structres and file systems in R|Data structres and file systems in R]]
	- [[#Data structres and file systems in R#Data frames|Data frames]]
	- [[#Data structres and file systems in R#creating File|creating File]]
	- [[#Data structres and file systems in R#Copy file|Copy file]]
	- [[#Data structres and file systems in R#Delete File|Delete File]]
	- [[#Data structres and file systems in R#Matrices|Matrices]]
- [[#Logical Operators and conditional satatements|Logical Operators and conditional satatements]]
	- [[#Logical Operators and conditional satatements#Conditions|Conditions]]
- [[#Refrences|Refrences]]
- [[#Definitions|Definitions]]

## Function

-  functions are a body of reusable code used to perform specific tasks in R. 

	- Functions begin with function names like print or paste, and are usually followed by one or more arguments in parentheses.
## Argument 
the argument is information that a function needs to run.
## variable/onjects 
- A represents a vaule in R that can be storeed for later use during programming 
- varibale names is case sensitive 
- ![[Pasted image 20230523062212.png]]
```r
first_variable <- "This is my variable"
second_variable <- "12.5"
```

## Comment - # 
## Vectors 
- A vector is a group of the **same type stored ina sequence 
- we can make vector using combined function : its just using "c"
	```R 
	c(x,y,z,....)
```
- Assignment of vector : eg, so now automtically we use vec_1 we use these values instead of typing each time.
	```R
	> vec_1 <- c(12, 56.8, 111.2)
> vec_1
[1]  12.0  56.8 111.2
```
- There are two types of vectors 
### Atomic vectors
There are six primary types of atomic vectors:
![[Pasted image 20230523151259.png]]
- **Creating vectors**
	-  create a vector is by using the **c()** function (called the “combine” function).
	- The c() function in R combines multiple values into a vector.
	- ***INTEGER VECTOR*** : To create a vector of integers using the c() function, you must place the letter "L" directly after each number.
	```R 
	c(1L, 5L, 15L)
```
	- ***Character vector*** : You can also create a vector containing characters or logicals.
	```R 
	c("Sara", "Lisa", "Anna") # Character vetcor
	c(TRUE, FASLE, TRUE)  # LOGICAL VECTOR
```
- ***Code To find type of vector and lenght of vector
```R
# For type
typeof(c(1L , 3L))

#> [1] "integer" # output

# For lenght 

x <- c(33.3, 343, 2224.33)

lenght(x)

#> [1] 3
```
-  **Naming vectors**
	- By **names()** function.
 ```R
 #Step1 
 x <- c(1, 3, 5)
 
 #step2 : You can use the names() function to assign a different name to each element of the vector.
 names(x) <- c("a", "b", "c")
 
 # Step 3 : Now, when you run the code, R shows that the first element of the vector is named a, the second b, and the third c.
#> a b c 

#> 1 3 5
```
### Creating lists
- Lists are diffrent from atomic vector as this contain any data types.
- You can create a list with the **list()** function, the list() function is just list
```R 
# Example
list("a", 1L, 1.5, TRUE)
```
- ***lists can contain other lists*** : list(list(list(1 , 3, 5)))
- **structure of lists**
	- By using str() we can find out diffrent types data elements present in a give list. 
	```R 
	# By using str() in  front of list 
	str(list("a", 1L, 1.5, TRUE))
	# we get op as 
	#> List of 4

#>  $ : chr "a"

#>  $ : int 1

#>  $ : num 1.5

#>  $ : logi TRUE
> str(list("a", 1L, 1.5, TRUE))
List of 4
 $ : chr "a"
 $ : int 1
 $ : num 1.5
 $ : logi TRUE
> z <- list(list(list(1 , 3, 5)))
> str(z) # Now run str of z
List of 1
 $ :List of 1
  ..$ :List of 3
  .. ..$ : num 1
  .. ..$ : num 3
  .. ..$ : num 5
```
- ***Naming List 
```R 

list('Chicago' = 1, 'New York' = 2, 'Los Angeles' = 3)
```

## Pipes 
- Pipe is tool in R to express a **sequence of mulliple operations, REPRESENTED by "%>%"
- It is used to use output of one function to another function. 
- Instaed of nested function which is function within function we can use pipe 
- where in pipe if mention it and write the code or function below %>% will be considered for the above function 
- this make it easy to organzise and read the code. 
```R 
data("ToothGrowth")
View(ToothGrowth)
# Install filter function 
install.packages("dplyr")
library(dplyr)
# Now will filter by dose and arrage or sort by teeth lenght 

filtered_tg <- filter(ToothGrowth,dose==0.5)
View(filtered_tg)

arrange(filtered_tg,len)

# Using same filter with nested function we get same result as prevous 2 steps

arrange(filtered_tg, len)

# Using same filter with pipe function 

filtered_pipe <- ToothGrowth %>%
  filter(dose==0.5) %>%
  arrange(len)

```
## data structures in R
- a **data structure** is a format for organizing and storing data.
- The most common data structures in the R programming language include: 
	-   Vectors
	    
	-   Data frames
	    
	-   Matrices
	    
	-   Arrays
## Dates and times in R
- we use lubredate package 
```R 
# Install 
> library(tidyverse)
> library(lubridate) 
> today()
[1] "2023-05-23"
> now()
[1] "2023-05-23 10:27:23 UTC"

### **Converting from strings**
> dmy("14th May, 1999")
[1] "1999-05-14"

> ymd(20210120)
[1] "2021-01-20"


```
## Data structres and file systems in R
### Data frames 
- Is collection of columns and rows
- it is easy summarize the data and organize and read easily
- elements in the same column should be of the same type.
```R
> data.frame(x = c( 1, 2, 3) , y = c(1.2, 3, 23))
  x    y
1 1  1.2
2 2  3.0
3 3 23.0
```
### creating File 
```R 
dir.create ("destination_folder")
EX : 
file.create (“new_text_file.txt”)
```
### Copy file 
```R 
file.copy (“new_text_file.txt” , “destination_folder”)
```
### Delete File 
```R 
unlink (“some_.file.csv”)
```
### Matrices
- Are in 2D have both row an colume 
- both vector and matix can contain same data type
- Matrix has 2 parametrs 1. Vector and 2. No. of rows or coulmes
```R 
> matrix(c(3:8), nrow = 2)
     [,1] [,2] [,3]
[1,]    3    5    7
[2,]    4    6    8
> matrix(c(3:8), ncol = 2)
     [,1] [,2]
[1,]    3    6
[2,]    4    7
[3,]    5    8
```
## Logical Operators and conditional satatements
![[IH3jvjscStK94747HNrSCg_9681cba255d44707b891ea5e0eb0e2f1_Logical-operators-and-conditional-statements.pdf]]

### Conditions 
Let’s discuss how to create conditional statements in R using three related statements: 

-   **if()** 
    
-   **else()**
    
-   **else if()**
    

-  **if statement**

	The **if** statement sets a condition, and if the condition evaluates to TRUE, the R code associated with the if statement is executed.
	
	In R, you place the code for the condition inside the parentheses of the if statement. The code that has to be executed if the condition is TRUE follows in curly braces (expr). Note that in this case, the second curly brace is placed on its own line of code and identifies the end of the code that you want to execute. 
	
	if (condition) {
	
	 expr
	
	}
	
	For example, let’s create a variable _x_ equal to 4.
	
	x <- 4
	
	Next, let’s create a conditional statement: if _x_ is greater than 0, then R will print out the string “x is a positive number". 
	
	if (x > 0) {
	
	  print("x is a positive number")
	
	}
	
	Since x = 4, the condition is true (4 > 0). Therefore, when you run the code, R prints out the string “x is a positive number".
	
	[1] "x is a positive number"
	
	But if you change x to a negative number, like -4, then the condition will be FALSE (-4 > 0). If you run the code, R will not execute the print statement. Instead, a blank line will appear as the result.

-  **else statement**

	The **else** statement is used in combination with an if statement. This is how the code is structured in R: 
	
	if (condition) {
	
	  expr1
	
	} else {
	
	 expr2
	
	}
	
	The code associated with the else statement gets executed whenever the condition of the if statement is _not_ TRUE. In other words, if the condition is TRUE, then R will execute the code in the if statement (_expr1_); if the condition is _not_ TRUE, then R will execute the code in the else statement (_expr2_). 
	
	Let’s try an example. First, create a variable _x_ equal to 7.  
	
	x <- 7
	
	Next, let’s set up the following conditions: 
	
	-   If x is greater than 0, R will print “x is a positive number”.
	    
	-   If x is less than or equal to 0, R will print “x is either a negative number or zero”.
	    
	
	In our code, the first condition (x > 0) will be part of the if statement. The second condition of x less than or equal to 0 is implied in the else statement. If x > 0, then R will print “x is a positive number”. Otherwise, R will print “x is either a negative number or zero”. 
	
	x <- 7
	
	if (x > 0) {
	
	 print ("x is a positive number")
	
	} else {
	
	 print ("x is either a negative number or zero")
	
	}
	
	Since 7 is greater than 0, the condition of the if statement is true. So, when you run the code, R prints out “x is a positive number”.
	
	[1] "x is a positive number"
	
	But if you make x equal to -7, the condition of the if statement is _not_ true (-7 is not greater than 0). Therefore, R will execute the code in the else statement. When you run the code, R prints out “x is either a negative number or zero”. 
	
	x <- -7
	
	if (x > 0) {
	
	 print("x is a positive number")
	
	} else {
	
	 print ("x is either a negative number or zero")
	
	}
	
	[1] "x is either a negative number or zero"

- **else if statement**

	In some cases, you might want to customize your conditional statement even further by adding the **else if** statement. The else if statement comes in between the if statement and the else statement. This is the code structure: 
	
	if (condition1) {
	
	 expr1
	
	} else if (condition2) {
	
	 expr2
	
	} else {
	
	 expr3
	
	}
	
	If the if condition (_condition1_) is met, then R executes the code in the first expression (_expr1_). If the if condition is not met, and the else if condition (_condition2_) is met, then R executes the code in the second expression (_expr2_). If neither of the two conditions are met, R executes the code in the third expression (_expr3_). 
	
	In our previous example, using only the if and else statements, R can only print “x is either a negative number or zero” if x equals 0 or x is less than zero. Imagine you want R to print the string “x is zero” if x equals 0. You need to add another condition using the else if statement.
	
	Let’s try an example. First, create a variable _x_ equal to negative 1 (“-1”).  
	
	x <- -1
	
	Now, you want to set up the following conditions:
	
	-   If x is less than 0, print “x is a negative number”
	    
	-   If x equals 0, print “x is zero”
	    
	-   Otherwise, print “x is a positive number”
	    
	
	In the code, the first condition will be part of the if statement, the second condition will be part of the else if statement, and the third condition will be part of the else statement. If x < 0, then R will print “x is a negative number”. If x = 0, then R will print “x is zero”. Otherwise, R will print “x is a positive number”. 
	
	x <- -1
	
	if (x < 0) {
	
	 print("x is a negative number")
	
	} else if (x == 0) {
	
	 print("x is zero")
	
	} else {
	
	 print("x is a positive number")
	
	}
	
	Since -1 is less than 0,  the condition for the if statement evaluates to TRUE, and R prints “x is a negative number”. 
	
	[1] "x is a negative number"
	
	If you make x equal to 0, R will first check the if condition (x < 0), and determine that it is FALSE. Then, R will evaluate the else if condition. This condition, x==0, is TRUE. So, in this case, R prints “x is zero”. 
	
	If you make x equal to 1, both the if condition and the else if condition evaluate to FALSE. So, R will execute the else statement and print “x is a positive number”.
	
	As soon as R discovers a condition that evaluates to TRUE, R executes the corresponding code and ignores the rest.
# Week 3
## Data Frame 
- is a collection of columes and rows they summarize data and easy to read 
- colume should be name based on variable they represent 
- ***Tiblles : as_tibble(diamonds)
	- easy to print 
	- he tibble only returns the first **10 rows** in a neatly organized table. That makes it easier to view and print.
- **Tidy data standards 
	- ![[Pasted image 20230527061050.png]]
- ***head()
	- Is used to get 1st 6 data of a dataset 



## Data imports Packages and functions 
- data()
	- Can import data from avaible data sets by 
	- This includes the list of preloaded datasets from the _datasets_ package.

- **The readr package**
	The goal of readr is to provide a fast and friendly way to read rectangular data. readr supports several read_ functions. Each function refers to a specific file format.
	
	-   read_csv(): comma-separated values (.csv) files
	    
	-   read_tsv(): tab-separated values files
	    
	-   read_delim(): general delimited files
	    
	-   read_fwf(): fixed-width files
	    
	-   read_table(): tabular files where columns are separated by white-space
	    
	-   read_log(): web log files
- To read from a file 
```R 
> readr_csv(readr_example("chickens.csv"))
```
-  readxl package : To import spreadsheet data into R
	- library(readxl)
	-  **Reading a .csv file with readxl**

	Like the readr package, readxl comes with some sample files from built-in datasets that you can use for practice. You can run the code readxl_example() to see the list.  
	
	You can use the **read_excel()** function to read a spreadsheet file just like you used read_csv() function to read a  .csv file. The code for reading the example file “type-me.xlsx” includes the path to the file in the parentheses of the function.  
	
	read_excel(readxl_example("type-me.xlsx"))
	
	You can use the [excel_sheets()](https://readxl.tidyverse.org/reference/excel_sheets.html "This link takes you to Tidyverse's readxl documentation that describes the excel_sheets function.") function to list the names of the individual sheets. 
	
	 excel_sheets(readxl_example("type-me.xlsx"))
	
	[1] "logical_coercion" "numeric_coercion" "date_coercion" "text_coercion"
	
	You can also specify a sheet by name or number.  Just type “sheet =” followed by the name or number of the sheet. For example, you can use the sheet named “numeric_coercion” from the list above. 
	
	read_excel(readxl_example("type-me.xlsx"), sheet = "numeric_coercion")
	
	When you run the function, R returns a tibble of the sheet.

## Cleaning up with the basics
```R
# Cleaning data 

install.packages("here")
library("here")
#Used to skim 
install.packages("skimr")
library("skimr")

# jaintor package functions for cleaning data 
install.packages("janitor")
library("janitor")

# with this also install diplyr 

install.packages("dplyr")
library("dplyr")


# Will do this with palmer penguins 

install.packages("palmerpenguins")
library("palmerpenguins")

```
- The skim_without_charts() and glimpse() functions both return a summary of the data frame, including the number of columns and rows.
- 
## Operators 
### Arthermitic 
![[Pasted image 20230605104404.png]]
### Relation
![[Pasted image 20230605104441.png]]
### logical operator
![[Pasted image 20230605104509.png]]
### **Assignment operators**
![[Pasted image 20230605104852.png]]
## Clean Data 
1. sort data by arranage func. 
2. save the data 
3. 


---- 
## Refrences 
What should you use to assign a value to a variable in R?

1 point

***An operator***

An argument

A comment

A vector

- An analyst is checking the value of the variable _x_ using a logical operator, so they run the following code: x > 35 & x < 65 Which values of _x_ would return TRUE when the analyst runs the code? Select all that apply.

1 point

35

50

60

70

> x <- c(35, 50, 60, 70)
> x > 35 & x < 65
[1] FALSE  TRUE  TRUE FALSE

----
 ## Definitions 
- Concept

Function

Definition

A body of reusable code for performing specific tasks in R

- Argument

Definition

Information needed by a function in R in order to run

- Variable

Definition

A representation of a value in R that can be stored for later use
- Pipe

Definition

A tool in R for expressing a sequence of multiple operations, represented with _%>%_

- The assignment operator (<-) assigns the variable sales_1 to the value of 100 * sales_2. The multiplication operator (*) multiplies 100 by sales_2.
 
