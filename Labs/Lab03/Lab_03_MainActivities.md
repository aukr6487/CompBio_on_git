# Lab 03: Introduction to R

### Goals for this week:  

Get acquainted with the basic, universal features of R and RStudio that you will need to know for just about anything you do in R.

### Preparation:  
1.	If you have not done so already, and if you are new to R, please take the time now to watch this short video about R: [https://youtu.be/TG77MVHfC8E](https://youtu.be/TG77MVHfC8E)
2.	If you are brand new to R, I strongly recommend that you try the first tutorial of `swirl`.  To do so:  
Go to [https://swirlstats.com/students.html](https://swirlstats.com/students.html) and do steps 3 and 4.  (You have already done the first two steps as part of this class by (previously) installing R and RStudio!  Woohoo!).  Proceed from the prompts in RStudio that follow when you give the `swirl()` command, and do the first module it offers, `1: R Programming: The basics of programming in R`.

### Instructions for this lab:  

Please read and do all of the exercises below, in sequence.  Read the instructions carefully to save yourself time.  Have fun, ask questions, and talk to people around you about what you are doing!  Use Google searches like "how to ______ in R" if you are stuck.  Challenge yourself to become self-sufficient!  A detailed list of activities for this lab appears below.  The numbered items are the "action items", i.e., things you need to do for this lab.

### Cheat Sheat of R Commands:

Note: do NOT type the "`>`" that you see at the beginning of each line below.  That symbol simply represents the command prompt in R and in RStudio's "console".

```
	> help("commandname") 		# get help within RStudio on a command
	
	> myVec <- c(1,2,3)			# make a vector with the elements 1 2 3
	
	> myMat <- cbind(vec1, vec2, vec3) 	# make a matrix that is a concatenation of vectors
	
	> myDf <- as.data.frame(myMatrix)		# make a data frame out of a matrix
	
	> myDf <- data.frame(vec1, vec2, vec3) 	# make a data frame that is a concatenation of vectors
	
	> str(dataObject) 		# get information about the structure of a data object of any type
	
	> dim(dataObject)		# see the dimensions of a data object
	
	> length(vec)			# see the number of elements in a vector
	
	> typeof(dataObject)	# see what class of object a given variable is
	
	> vec1 == vec2			# test if elements of two objects are equal
	
	> all(vec1 == vec2)		# test if ALL elements of two objects are equal
```	
	

#### PART I.  BASIC OPERATIONS

(1) Open RStudio  
(2)	Open a new R script.  **Please do all work for this lab in that script so that you can save your work**.  **Please save your script as "YOURLASTNAME_Lab3.R"** (without the quotes) in a "Lab03" directory inside your CompBioHWandLabs directory (hint: you'll need to push it to GitHub when you are done).    
Note that this should be a plain R Script (*NOT* an R markdown document and *NOT* an "R Project").  In RStudio, this can be done from the "file" menu or from the button with the plain plus sign on it.
*Hint*: Use the console to test lines of code, but make sure the finished product appears in the script.

Now, we’re going to do a bunch of basic programming activities.  To make it more interesting, we’re going to tell a story.  Suppose you are a huge Star Wars fan, and you are having a movie-watching party at your home to watch Episodes IV-VI back-to-back-to-back.  As a well-practiced host/hostess, you want to make sure you have enough food and drink for everyone. You start the night with 5 bags of chips (Flaming Hot Cheetos, to be precise). Suppose you have 8 guests coming (not including yourself).

(3) Make two variables, one that stores the number of bags of chips you start with, and one that stores the number of guests you have coming. Give your variables intelligent names that makes it easy to know what they represent.  

Adding comments to code/scripts is a critical piece of good programming.  so, we’re going to start adding comments right away.  In programming, a "comment" is a phrase for the human reader of the code; comments are not evaluated by the program itself.  In R, comments are designated with the pound sign or hashtag ("`#`").  Anything on a line that follows a hashtag will not be interpreted by the program; it is just for the benefit of any human reading the code and trying to understand what it is meant to do.

(4) Add a line of comments just above the lines you just wrote for step 3.  The comment should explain the lines that come immediately after it.  Note:  please begin that comment with the text "lab step #3:"

Note about good practice:  In addition to comments, keeping your code readable is very important.  One of simplest things you can do to keep your code readable is to always put spaces between variables and operators.  Here are two examples.  The first way in each example is much better practice than the second:  
		GOOD: `x <- 5`; BAD: `x<-5`  
		GOOD: `y <- x + (2 * z)`; BAD: `y<-x+2*z`  
So, PLEASE get into the habit of always puting spaces between operators and variables.  Note that grouping operations with parentheses also greatly increases clarity of your intentions!

(5) Suppose you expect that each of your guests will eat an average of 0.4 bags of chips. Store this quantity in a new variable.  

(6) Add a comment just above your work for step 5 to explain it.  Please begin that comment with the text "lab step #5:".  

(7) You should now have a total of three variables defined.  Use these three variables to calculate the expected amount of leftover chips.  In addition to the 8 guests, assume that you will also consume 0.4 bags of chips yourself.  Again, precede this step by a comment.

#### PART II.  SOME PRACTICE WITH OBJECTS THAT HOLD DATA, AND SOME PRACTICE USING SOME BUILT-IN FUNCTIONS WITH THOSE OBJECTS
After watching the trilogy (and all the other movies), you and some of your friends decide to compare rankings of all nine movies (episodes I – IX).  The following table gives the rankings for you and some of your friends:


| Episode | Self | Penny | Lenny | Stewie |
| --------- | :----: | :----: | :----: | :----: |
|	I	|	7 |	5    |	    6   |	1   |
|	II	|	9 |	9    |	   5    |	9   |
|	III	|	8 |	8    |	   4    |	5   |  
|	IV	|	1 |	3    |	   9    |	6   |
|	V	|	2 |	1    |	   8    |	8   |  
|	VI	|	3 |	2    |	   7    |	7   |  
|	VII	|	4 |	4    |	   3    |	2   |
|       VIII  |       6 |   7    |     2    |     3   |
|       IX    |      5  |   6    |     1    |     4   |


(8) Make 4 vectors, one for each person, containing his/her/their rankings in the order given here.  In other words, the first element of each vector should be the rank given to Episode I, the second element the ranking for Episode II  and so on. (Hint: use the "`c()`" function.).  Yes, this involves some slightly repetitive and tedious typing.  That’s all part of the learning and reinforcing.  Add an appropriate comment.

##### Accessing elements of vectors.  

Once you have data in a vector, it is often essential to be able to access, manipulate, and change specific elements (i.e., specific entries or numbers).  Across programming languages, this is done by "indexing" by position with integer numbers.  In R, indexing is done with square braces ("`[ ]`") and numbers inside them. For example, suppose we have a vector named "x" that has 8 elements:  
`x[3] # access third element of x`

(9) Using indexing (with a single set of square braces "`[ ]`"), access Penny’s ranking for Episode IV, and store it in a new variable called "`PennyIV`".  Make another variable for Lenny’s rank of Episode IV. Add an appropriate comment.  


(10) Concatenate all 4 sets of rankings into a single data object.  (Hint:  use "`cbind()`").  This new object should have 9 rows and 4 columns. Add an appropriate comment.  


(11) Use the "`str()`" function to inspect the structure of `PennyIV`, `Penny`, and the result of step #10.  In words (using a "comment" after the code), verbally describe the differences between these three data objects in terms of the results you get from `str()`.  


(12) Now make a "data frame" using the 4 vectors of rankings.  The data frame should have the names of the people as the names of its columns.  Given what we already have in memory (from the steps above), there are two ways to do this, one using "`data.frame()`" and one using "`as.data.frame()`".  Try BOTH ways in your code just for the sake of learning.  


(13) Verbally (using a comment after step #12) describe the similarities and differences between (a) the object created in step #10 using `cbind()` and (b) one of the objects created as a data frame in step #12.   To do this you will probably find it helpful to use `dim()`, `str()`, `==`, and `typeof()` and verbally describe the results of what you get from each.

R can make vectors of characters or "strings" of characters too.  To tell R that something is a character or string, just put quotes around it.   

 
 (14) Make a vector of the Episode names as Roman numerals (i.e., "I", "II", and so on). (hint: use `c()`).  Add an appropriate comment.  Note that since these are made with text (not actual numbers), you will have to put quotes around each element when creating the vector.


(15) Up to now, the results from steps #10 and #12 had names of the columns, but did not have names of the rows.  Using the result of step 14 and the `row.names()` function, name the rows of the objects created in steps 10 and 12.  Inspect the variables in your console window just to make sure this worked as intended.  
HINT: If you aren't sure how to use `row.names()` and the vector from part #14 to do, this, try `help("row.names")` in your RStudio console.

##### Accessing elements of matrices and data frames.  

There are multiple ways to access specific elements or ranges of elements of that are stored in two-dimensional matrices or data frames in R.  Let’s start with the method that is the most universal across programming languages, and the one we used above in step #9: indexing by position with integer numbers inside square braces. For a two-dimensional object (e.g., our 9 x 4 matrix), we specify data we want by specifying two pieces of information: one to specify the row(s) we want, and one to specify the column(s).  The row specification is always first, and the column specification always second, with the two separated by a comma.  For example, suppose we have a matrix named "`x`" that has 8 rows and 4 columns.  In R, we can do things like the following to specify or access elements in `x`.

```
	x[2,3] # element in second row, third column
	x[2,] # ALL of the second row
	x[,3] # ALL of the third column 
```

Let’s start with accessing one whole row or column  

(16) Access the third row of the matrix produced from step #10.  (Note: By "access", I mean write a line of code in your script that, when evaluated, causes the specified data to simply be printed out in RStudio's console.)

(17) Access the fourth column from a data frame produced from step #12  


Now, let’s do a specific element using any of the objects that work.

(18) Access your ranking for Episode V.  

(19) Access Penny’s ranking for Episode II.  


Now, let’s do a range of rows:  


(20) Access everyone’s rankings for episodes IV – VI.  


(21) Access everyone’s rankings for episodes II, V, and VII.  

Now let’s do specific rows and columns all at once:  

(22) Access rankings for just Penny and Stewie for just episodes IV and VI.

Now, let’s use indexing to assign new values to entries in a matrix or data frame.   


(23) In one of the objects created in step 10 or 12, switch Lenny’s rankings for Episodes II and V.  There are several ways to do this, but make sure you get your index numbers right, and make sure you don’t delete one of the numbers you need!  Hints: Usually, this type of "swap" requires three lines of code and the use of one new variable.  

Accessing elements, rows, and columns by number (indexing) is indeed the most universal way to work with specific entries in a matrix, but R does offer additional capabilities as well, which are sometimes very convenient.  Some of these apply to both matrices and data frames, and some apply only to data frames.   Let’s look first at using row and column names instead of numbers.  This can be done with matrices and with data frames.  For example, to get Penny’s rating of episode III, I could write `allRankings[3, 2]` ("3" for the row number for Episode III, "2" for the column number for Penny), but I could also write
`allRankings["III", "Penny"]`.  The latter is less universal (you can’t do this in all programming languages), but does remove some guesswork for this kind of operation.  


(24) Try the example I just gave (`allRankings["III", "Penny"]`) with the matrix from step 10 and with one of the data frames from step 12 just to show yourself that it works.  

(25) Use this method (names rather than indexes) to undo the switch made in step 23  

Finally, a method that works only on data frames involves the "`$`" operator to access the columns of the data frame.  Recall from outputs above using `str()` that R refers to each column of a data frame as a "variable".  E.g., for a data frame from step 12, `str()` will tell you that it is a "`'data.frame': 9 obs. of  4 variables:`".   In this case, each person’s rankings are considered to be a "variable" in the data frame.  If "rankings" is a data frame, we can access all of one person’s rankings, e.g., Lenny’s, by typing: `rankings$Lenny`.  We could then access specific elements of Lenny’s rankings just as we did in step #9 above, that is, with a single number inside a set of square braces, e.g., Lenny’s ranking of Episode II could be accessed by typing: `rankings$Lenny[2]`.  


(26) Use this last method to re-do the switch from step 23.

(27) **Please save your script as "YOURLASTNAME_Lab3.R"** in a "Lab03" directory inside your homework and labs directory.  add, commit, and push to turn it in

