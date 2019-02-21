---
title: 'Lab 3: Hypothesis tests and linear regression'
description: ""
---

## Explore: Load data and compare variables

```yaml
type: NormalExercise
key: 13462cb399
xp: 100
```

This chapter is intended to give a quick tour of hypothesis testing - both for means and for regression coefficients.

We will start by simply loading some data and exploring the variables included.

In 2004, the state of North Carolina released a large data set containing information on births recorded in this state. This data set is useful to researchers studying the relation between habits and practices of expectant mothers and the birth of their children.  For our exercises, we will work with a random sample of observations from this data set.

`@instructions`
Load the dataset from the url specified, using provided code.  This will create a dataframe object (our sample) called `nc` that you can explore.

Look at summary statistics for all the variables in the dataset using the `summary()` function. How many variables are included in this dataset?

Use the `by()` function to calculate the mean of `weight`, split by `habit` (mother's smoking habit).  The `by()` function lets us use one function on different subsets of our data set.

`@hint`
Put the name of the dataframe (nc) in the summary command!

`@pre_exercise_code`
```{r}

```

`@sample_code`
```{r}
# Load data
load(url("http://www.openintro.org/stat/data/nc.RData"))

# Use summary() to explore variables
summary(___)

# Use by() to calculate the mean birth weight, by mom's smoking habit
by(nc$weight, nc$habit, mean)
```

`@solution`
```{r}
# Load data
load(url("http://www.openintro.org/stat/data/nc.RData"))

# Use summary() to explore variables
summary(nc)

# Use by() to calculate the mean birth weight, by mom's smoking habit
by(nc$weight, nc$habit, mean)
```

`@sct`
```{r}
ex() %>% check_code("summary(nc)", fixed = TRUE)
success_msg("Good start! Now, to figure out whether that's a statistically significant difference between those means!")
```
