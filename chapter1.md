---
title: 'Lab 1: Orientation to DataCamp'
description: "This is an orientation to labs for STAT/CSSS/SOC 221.    The purpose of these 'labs' is to provide a brief introduction to doing statistics in the kind of computing framework in which most data scientists work today.\n\nThe labs will be completed in the R programming language, using DataCamp's online learning interface.  They feature step-by-step exercises designed to demonstrate the power of computing for data analysis, while giving you the opportunity to practice applying concepts of statistical inference with real data.\n\nThis short 'chapter' will provide an orientation to the data camp learning environment, and demonstrate loading a data set into R and generating basic summary statistics and plots from that data set."
free_preview: true
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
success_msg("Great! Now let's get started")
```

---

## Examining Data

```yaml
type: NormalExercise
key: bd32a0e106
xp: 100
```

For this exercise, we will use data from The Behavioral Risk Factor Surveillance System (BRFSS).  This is an annual telephone survey of 350,000 people in the U.S. that is designed to identify emerging health trends. For example, respondents are asked about their diet and weekly physical activity, their HIV/AIDS status, tobacco use, and their level of healthcare coverage.  We will focus on a random sample of 20,000 people from the BRFSS survey conducted in 2000. This dataset is already loaded into memory and is called `cdc`.

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
load(url("https://assets.datacamp.com/production/repositories/4625/datasets/59016f8f9e27761faf10c9932a85dbbf339e162b/cdc.RData"))
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
ex() %>% check_output_expr("names(cdc)")
ex() %>% check_output_expr("nrow(cdc)")
ex() %>% check_output_expr("head(cdc)")
success_msg("Well done!")
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
load(url("https://assets.datacamp.com/production/repositories/4625/datasets/59016f8f9e27761faf10c9932a85dbbf339e162b/cdc.RData"))
```

`@sct`
```{r}
msg1 <- "Not quite, give it another shot."
msg2 <- "Nope, try again!"
msg3 <- "Good choice"
msg4 <- "Not that one, variables are columns, not rows!"

ex() %>% check_mc(3, feedback_msgs = c(msg1, msg2, msg3, msg4))

success_msg("Nice job!  Note you could also use the command ncol() to count the number of columns.")
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
load(url("https://assets.datacamp.com/production/repositories/4625/datasets/59016f8f9e27761faf10c9932a85dbbf339e162b/cdc.RData"))
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
ex() %>% check_code("mean(cdc$weight)", fixed = TRUE)
ex() %>% check_code("mean(cdc$wtdesire)", fixed = TRUE)
ex() %>% check_code("sd(cdc$weight)", fixed = TRUE)
ex() %>% check_code("sd(cdc$wtdesire)", fixed = TRUE)
success_msg("Great!  Now you know how to explore basic measures of center and spread.")
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
load(url("https://assets.datacamp.com/production/repositories/4625/datasets/59016f8f9e27761faf10c9932a85dbbf339e162b/cdc.RData"))
```

`@sct`
```{r}
msg1 <- "Nice one!"
msg2 <- "Nope, try again!"
msg3 <- "Not quite, give it another shot."
ex() %>% check_mc(1, feedback_msgs = c(msg1, msg2, msg3))
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
load(url("https://assets.datacamp.com/production/repositories/4625/datasets/59016f8f9e27761faf10c9932a85dbbf339e162b/cdc.RData"))
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
table(cdc$genhlth, cdc$gender)
```

`@sct`
```{r}
ex() %>% check_code("table(cdc$genhlth)", fixed = TRUE) 
ex() %>% check_code(c("table(cdc$genhlth, cdc$gender)",
                     "table(cdc$gender, cdc$genhlth)"), fixed = TRUE,
                   missing_msg = "It looks like you haven't included a table command including both `cdc$genhlth` and `cdc$gender`.") 
success_msg("Well done!")
```

---

## Exploring data with graphs

```yaml
type: NormalExercise
key: c75ec5f8ee
xp: 100
```

Finally, let's explore how to make a plot of variables in our data.

First, we'll make a boxplot of of the ages of our surey respondents.

Next, we'll make a scatterplot of people's height and weight, using the `plot()` command.  By default `plot` creates dot or scatter plots.

`@instructions`
Enter `cdc$age` as the input to the `boxplot` command and examine the plot that is generated.

Enter `cdc$height` and `cdc$weight` as the 'x' and 'y' inputs to the `plot` command to draw a scatterplot of these two variables.

`@hint`
Fill in the appropriate variables as defined in the instructions inside the parentheses of each function.  Make sure to included the `cdc$` before the column name.

`@pre_exercise_code`
```{r}
load(url("https://assets.datacamp.com/production/repositories/4625/datasets/59016f8f9e27761faf10c9932a85dbbf339e162b/cdc.RData"))
```

`@sample_code`
```{r}
# Make a boxplot of respondent's ages
boxplot(cdc$___)

# Make a scatterplot of with height as the explanatory variable and weight as the response variable.
plot(x = cdc$height, y = ___)
```

`@solution`
```{r}
# Make a boxplot of respondent's ages
boxplot(cdc$age)

# Make a scatterplot of with height as the explanatory variable and weight as the response variable.
plot(x = cdc$height, y = cdc$weight)
```

`@sct`
```{r}
ex() %>% check_function("boxplot") %>% check_arg(., "x") %>% check_equal()
ex() %>% check_function("plot") %>% {
  check_arg(., "x") %>% check_equal()
  check_arg(., "y") %>% check_equal()
}
success_msg("Nice job! It is easy to make many different kinds of plots in R quickly with other similar commands.")
```

---

## R skills: Saving values as objects

```yaml
type: NormalExercise
key: 062d688720
xp: 100
```

Often when doing an analysis you want to save certain variables or calculated values so that you can use them again.

In R, we can save values by "assigning" them to a name, that we can then refer to later (like how we typed `cdc` when we wanted to access the cdc dataset).  

To assign a value to a name, we use to "assignment operator": `<-`.  The name we want to save goes on the left side, the function output, value, or variable that we want to save with that name goes on the right.

In this exercise you will practice saving summary statistics and individual variables and then using them in later code.

`@instructions`
Calculate the mean actual weight and desired weight of the CDC survey respondents.  Remember the variable names are `weight` and `wtdesire`.

Save the two means to two 'objects' (what we call items that we've saved in our R console) called `mean_actual_weight` and `mean_desired_weight`.

Print each of the means using the `print()` function

Calculate the difference between the two means.

`@hint`
In the `mean()` function you should specify the `wtdesire` variable in the `cdc` dataframe. Use the `$` to indicate the variable in the dataframe.  To print the value saved to a name, just put the name inside the parentheses of `print()`.

`@pre_exercise_code`
```{r}
load(url("https://assets.datacamp.com/production/repositories/4625/datasets/59016f8f9e27761faf10c9932a85dbbf339e162b/cdc.RData"))
```

`@sample_code`
```{r}
# The cdc dataframe is loaded in R.

# Calculate and save the mean actual weight
mean_actual_weight <- mean(cdc$weight)

# Calculate and save the mean desired weight
mean_desired_weight <- mean(___)

# Print the mean actual weight
print(mean_actual_weight)
# Print the mean desired weight
print(___)

# Calculate the difference between the mean actual and desired weight
mean_actual_weight - mean_desired_weight
```

`@solution`
```{r}
# The cdc dataframe is loaded in R.

# Calculate and save the mean actual weight
mean_actual_weight <- mean(cdc$weight)

# Calculate and save the mean desired weight
mean_desired_weight <- mean(cdc$wtdesire)

# Print each mean value
print(mean_actual_weight)
print(mean_desired_weight)

# Calculate the difference between the mean actual and desired weight
mean_actual_weight - mean_desired_weight
```

`@sct`
```{r}
ex() %>% check_object("mean_actual_weight") %>% check_equal()
ex() %>% check_object("mean_desired_weight") %>% check_equal()
ex() %>% check_output_expr("mean_actual_weight")
ex() %>% check_output_expr("mean_desired_weight")
ex() %>% check_output_expr("mean_actual_weight - mean_desired_weight")
success_msg("Great! Now you know about how to assign a value to named object so you can use it again!")
```

---

## R skills: Doing math in the console

```yaml
type: NormalExercise
key: 2ab94a4669
xp: 100
```

You can do many different simple and complex mathematical operations in R.

In the last exercise, you saw an example of this, when you calculated the difference between the mean actual and desired weights.  It will be useful in future lab exercises to do calculations with saved objects.  

In this exercise, we will step through the mathematical operations to calculate the z-score of the weight of an individual who weighs 120 lbs.

`@instructions`
Calculate the mean and standard deviation of the actual weight, using the `mean()` and `sd()` functions and save them to objects named `mean_weight` and `sd_weight`.

Calculate the z-score for a weight of 120 and save it to an object called `zscore120`.

Print the z-score.

`@hint`
Make sure to use the `cdc$weight` variable in the `mean()` and `sd()` functions.  

Remember that to calculate the z-score you have to divide by the standard deviation, which you should have saved as an object called `sd_weight`.

`@pre_exercise_code`
```{r}
load(url("https://assets.datacamp.com/production/repositories/4625/datasets/59016f8f9e27761faf10c9932a85dbbf339e162b/cdc.RData"))
```

`@sample_code`
```{r}
# The cdc dataset is already loaded into R

# Save the mean and standard deviations of actual weight as objects
mean_weight <- mean(___)
sd_weight <- ___(cdc$weight)

# Calculate the z-score of 120 and save it as an object
zscore120 <- (120 - mean_weight)/sd_weight

# Print the z-score in the console
print(___)
```

`@solution`
```{r}
# The cdc datasetis already loaded into R

# Save the mean and standard deviations of actual weight as objects
mean_weight <- mean(cdc$weight)
sd_weight <- sd(cdc$weight)

# Calculate the z-score of 120 and save it as an object
zscore120 <- (120 - mean_weight)/sd_weight

# View the z-score in the console
zscore120
```

`@sct`
```{r}
ex() %>% check_object("mean_weight") %>% check_equal()
ex() %>% check_object("sd_weight") %>% check_equal()
ex() %>% check_object("zscore120") %>%check_equal()
ex() %>% check_output_expr("zscore120")
success_msg("Well done! Now you have some basic familiarity with R data operations that you can use to practice other statistical tasks.")
```
