---
title: 'Lab 2: Sampling Distributions & Confidence Intervals'
description: "In this lab, we investigate the ways in which the statistics from a random sample of data can serve as point estimates for population parameters. We’re interested in formulating a sampling distribution of our estimate in order to learn about the properties of the estimate, such as its distribution.\n\nAfter practicing with sampling distribution, we will see how to build confidence intervals using the standard error and sample statistics of the mean and standard deviation."
---

## Explore data: load data and identify numeric variables

```yaml
type: NormalExercise
key: 07a1ff1894
xp: 100
```

We consider real estate data from the city of Ames, Iowa. Our focus for this lab will be all residential home sales in Ames between 2006 and 2010. This collection represents our population of interest. In this lab we would like to learn about these home sales by taking smaller samples from the full population. 

First, we'll load the data using the `load()` function, specifying the url where the data are stored.

After loading the data, let's look at the variables using the `summary()` function.  You see many variables in the dataset.  For this lab, we’ll just work with two of the variables: the above ground living area of the house in square feet (Gr.Liv.Area) and the sale price (SalePrice).

`@instructions`
Load the data with the `load()` function using the url "http://www.openintro.org/stat/data/ames.RData".  This creates an R dataframe object called ames.

Explore the different variable types in `ames` using the `summary()` function.  Which variables appear to be continuous and which discrete?

`@hint`


`@pre_exercise_code`
```{r}

```

`@sample_code`
```{r}
load("http://www.openintro.org/stat/data/ames.RData")

# Check out which variables are included
names(ames)

# Look at summary statistics for the variables in the dataset
summary(___)



```

`@solution`
```{r}
# Load the ames dataset into memory
load("http://www.openintro.org/stat/data/ames.RData")

# Check out which variables are included
names(ames)

# Look at summary statistics for the variables in the dataset
summary(ames)



```

`@sct`
```{r}

```

---

## Inference: Simulate sampling distribution

```yaml
type: NormalExercise
key: 568c9f0399
xp: 100
```

In this lab we have access to the entire population, but this is rarely the case in real life. Gathering information on an entire population is often extremely costly or impossible. Because of this, we often take a sample of the population and use that to understand the properties of the population.

We can create random samples from the population all houses in Ames using the `sample()` function.  

In this exercise, we will draw several samples of the living area of 50 houses in Ames and compare their estimated mean area.

`@instructions`
The ames dataset is already loaded.  Using the `sample()` function, draw three samples from the full population of houses' living areas in Ames.  

Examine the mean living area estimate from each sample.  How variable are these estimates of the mean?

`@hint`


`@pre_exercise_code`
```{r}
load(url("http://www.openintro.org/stat/data/ames.RData"))
```

`@sample_code`
```{r}
# The ames data set is already loaded.

# Draw one sample
sample1 <- sample(ames$Gr.Liv.Area, 50)
# Print the mean living area in that sample
mean(sample1)

# Draw another sample
sample2 <- sample(ames$Gr.Liv.Area, 50)
# Print the mean living area in that sample
mean(sample2)

# Draw a third sample
sample3 <- sample(___, __)
# Print the mean living area in that sample
mean(___)

```

`@solution`
```{r}
# The ames data set is already loaded.

# Draw one sample
sample1 <- sample(ames$Gr.Liv.Area, 50)
# Print the mean living area in that sample
mean(sample1)

# Draw another sample
sample2 <- sample(ames$Gr.Liv.Area, 50)
# Print the mean living area in that sample
mean(sample2, 50)

# Draw a third sample
sample3 <- sample(ames$Gr.Liv.Area, 50)
# Print the mean living area in that sample
mean(sample3, 50)


```

`@sct`
```{r}

```

---

## Explore data: Calculate mean and standard deviation

```yaml
type: NormalExercise
key: c58d27ef76
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

---

## Inference: Calculate standard error

```yaml
type: NormalExercise
key: d319ba296c
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

---

## Inference: Interpret standard error

```yaml
type: PureMultipleChoiceExercise
key: 722b051211
xp: 50
```



`@hint`


`@possible_answers`


`@feedback`


---

## Inference: Calculate confidence intervals

```yaml
type: NormalExercise
key: 8f67b77e3f
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

---

## Inference: Interpret confidence interval

```yaml
type: PureMultipleChoiceExercise
key: 08b306a6eb
xp: 50
```



`@hint`


`@possible_answers`


`@feedback`
