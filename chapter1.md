---
title: 'Lab 1: Orientation to DataCamp'
description: "This is an orientation to labs for STAT/CSSS/SOC 221.    The purpose of these 'labs' is to provide a brief introduction to doing statistics in the kind of computing framework in which most data scientists work today.\n\nThe labs will be completed in the R programming language, using DataCamp's online learning interface.  They feature step-by-step exercises designed to demonstrate the power of computing for data analysis, while giving you the opportunity to practice applying concepts of statistical inference with real data.\n\nThis short 'chapter' will provide an orientation to the data camp learning environment, and demonstrate loading a data set into R and generating basic summary statistics and plots from that data set."
---

## Welcome to DataCamp

```yaml
type: NormalExercise
key: 2bafef99a3
lang: r
xp: 100
skills: 1
```

Welcome to the DataCamp interface! 

Looking at your screen, you should see four different sections on this page in your browser: 
- Upper left: The context panel, which you are reading right now, provides guidance and necessary context for each of the exercises.
- Lower left: The instructions panel provides the instructions to complete the current exercise. This panel may also provide hints in case you need help to complete the exercise.
- Upper right: The editor panel shows the script that you should use or modify to complete the exercise.  Click the refresh button to reset the code, 'Run Code' to run the code in the editor, or 'Run Solution' when you are ready to submit your answer and move on.
- Lower right: The R console panel prints the output of your code.

`@instructions`
Click 'Submit Answer' and see how the console shows you the executed R code.

`@hint`
Just click the 'Submit Answer' button!

`@pre_exercise_code`
```{r}

```

`@sample_code`
```{r}
# This is the editor and the part below the white line is called the console.

# The hashtag is used to add comments

# An addition
5 + 5

# A substraction
5 - 5

# A division
(5 + 5) / 2

# A plot
plot(cars, type = "o", col = "blue")
```

`@solution`
```{r}
# This is the editor and the part below the white line is called the console.

# The hashtag is used to add comments

# An addition
5 + 5

# A substraction
5 - 5

# A division
(5 + 5) / 2

# A plot
plot(cars, type = "o", col = "blue")
```

`@sct`
```{r}

```

---

## Examining Data

```yaml
type: NormalExercise
key: bd32a0e106
xp: 100
```

For this exercise, we will use data from The Behavioral Risk Factor Surveillance System (BRFSS).  This is an annual telephone survey of 350,000 people in the United States that is designed to identify emerging health trends. For example, respondents are asked about their diet and weekly physical activity, their HIV/AIDS status, possible tobacco use, and even their level of healthcare coverage.  We will focus on a random sample of 20,000 people from the BRFSS survey conducted in 2000. This dataset is already loaded into memory and is called `cdc`.

The data set `cdc` that shows up in your workspace is a *data matrix*, with each
row representing a *case* and each column representing a *variable*.  R calls 
this data format a *data frame*, which is a term that will be used throughout 
the labs.



	

`@instructions`
View the names of the variables by entering the command `names(cdc)`.

View the number of observations (number of rows) by entering the commands `nrow(cdc)`.

View the first few rows of the data set with the command `head(cdc)`.

`@hint`
Replace the underscores in `nrow(___)` and `head(___)` with the letters `cdc` to create the code `head(cdc)`.

`@pre_exercise_code`
```{r}
source("http://www.openintro.org/stat/data/cdc.R")
```

`@sample_code`
```{r}
# Print the names of the variables
names(cdc)

# Print the number of observations (rows)
nrow(___)

# Print the top few rows
head(___)

```

`@solution`
```{r}
# Print the names of the variables
names(cdc)

# Print the number of observations (rows)
nrow(cdc)

# Print the top few rows
head(cdc)

```

`@sct`
```{r}

```

---

## Checkpoint: identifying variables

```yaml
type: MultipleChoiceExercise
key: 646bdbbb14
xp: 50
```

How many variables are in the `cdc` data set?  The 	`cdc` data set is loaded in the R console to the right, so you can check again to remind yourself using the `names(cdc)` command.

`@possible_answers`
- 3 variables
- 5 variables
- [9 variables]
- 20000 variables

`@hint`
Enter `names(cdc)` in the console and count the number of variables.

`@pre_exercise_code`
```{r}
View("http://www.openintro.org/stat/data/cdc.R")
```

`@sct`
```{r}

```

---

## Exploring data: numerical summaries

```yaml
type: NormalExercise
key: 8287eb6106
xp: 100
```

It is simple in R to get a five number summary (min, max, median, IQR) and mean for all numeric variables in your data set (including binary variables coded as 0 or 1).

The `summary()` function prints summary information for all variables in your data set.

Alternatively, you can use the functions `mean()`, `sd()`, and `median()` to calculate the mean, standard deviation, and median of individual variables. 

We use the `$` to name the variable we want from the data set. For example, `mean(cdc$height)` will calculate the mean of the `height` variable in the `cdc` data set.


`@instructions`
Print the summary statistics for all variables in the cdc dataset, which is loaded and available in the console already with the `summary` function.

Calculate the mean actual weight (`cdc$weight`) and desired weight (`cdc$wtdesire`).

Calculate the standard deviation of actual weight and desired weight.

`@hint`
Replace the underscores before parenthesis with the name of the statistical function you want to calculate.  

Replace the underscores after the $ with the name of the variable.

`@pre_exercise_code`
```{r}
source("http://www.openintro.org/stat/data/cdc.R")
```

`@sample_code`
```{r}
# Print summary statistics for all variables
summary(cdc)

# Calculate mean of actual weight
mean(cdc$weight)
# Calculate mean of desired weight
___(cdc$wtdesire)

# Calculate standard deviation of actual weight
sd(cdc$___)
# Calc4ulate standard deviation of desired weight
sd(cdc$___)
```

`@solution`
```{r}
# Print summary statistics for all variables
summary(cdc)

# Calculate mean of actual weight
mean(cdc$weight)
# Calculate mean of desired weight
mean(cdc$wtdesire)

# Calculate standard deviation of actual weight
sd(cdc$weight)
# Calc4ulate standard deviation of desired weight
sd(cdc$weight)
```

`@sct`
```{r}

```

---

## Checkpoint: summary statistics

```yaml
type: MultipleChoiceExercise
key: 625b9abab3
xp: 50
```

Which variable has greater variability, actual weight (`cdc$weight`) or desired weight (`cdc$wtdesire`)?  

The dataset `cdc` is loaded in the console. You can use the `sd()` or `summary()` commands you just practiced to remind yourself which variable has greater spread.

`@possible_answers`
- [Actual weight has more variability.]
- Desired weight has more variability.
- Actual and desired weight have the same variability.

`@hint`
Enter `sd(cdc$weight)` and `sd(cdc$wtdesire)` to calculate the standard deviations of each variable.

`@pre_exercise_code`
```{r}
source("http://www.openintro.org/stat/data/cdc.R")
```

`@sct`
```{r}

```

---

## Exploring data: contingency tables

```yaml
type: NormalExercise
key: 5782a02399
xp: 100
```

We can easily make a _frequency table_ for categorical variables in R, using the `table()` command.  For example, to create a frequency table of the male and female respondents in this survey we would enter `table(cdc$gender)`.

If we want to make a _contingency table_, comparing two categorical variables, we include two variables in the `table()` function, separated by a comma.  For example, `table(cdc$gender, cdc$exerany)` would create a contingency table of gender and whether respondents exercise (the variable exerany).

`@instructions`
Report how many respondents reported each of five levels of health, by creating a table of the `genhlth` variable.

Next, create a contingency table of general health and gender by including both variables in the `table()` function.

`@hint`
Replace the underscores with the variable name "genhlth" and the command "table".

`@pre_exercise_code`
```{r}
source("http://www.openintro.org/stat/data/cdc.R")
```

`@sample_code`
```{r}
# Print a table of the genhlth variable
table(cdc$___)

# Print a contingency table of genhlth and gender
___(cdc$genhlth, cdc$gender)
```

`@solution`
```{r}
# Print a table of the genhlth variable
table(cdc$genhlth)

# Print a contingency table of genhlth and gender
table(cdc$genhlth)
```

`@sct`
```{r}

```

---

## Exploring data with graphs

```yaml
type: NormalExercise
key: c75ec5f8ee
xp: 100
```



`@instructions`


`@hint`


`@pre_exercise_code`
```{r}

```

`@sample_code`
```{r}

```

`@solution`
```{r}

```

`@sct`
```{r}

```
