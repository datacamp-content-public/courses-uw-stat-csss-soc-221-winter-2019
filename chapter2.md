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
load(url("http://www.openintro.org/stat/data/ames.RData"))

# Check out which variables are included
names(ames)

# Look at summary statistics for the variables in the dataset
summary(___)



```

`@solution`
```{r}
# Load the ames dataset into memory
load(url("http://www.openintro.org/stat/data/ames.RData"))

# Check out which variables are included
names(ames)

# Look at summary statistics for the variables in the dataset
summary(ames)



```

`@sct`
```{r}
ex() %>% check_code("summary(ames)", fixed = TRUE)
success_msg("Exploring new datasets is one of the most fun parts of analysis.  What did you notice when you looked at all the variables in the Ames housing data?")
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

## Inference: Simulate sampling distribution 2

```yaml
type: NormalExercise
key: ec43918fba
xp: 100
```

Not surprisingly, every time we take another random sample, we get a different sample mean.  In this lab, because we have access to the population, we can build up the sampling distribution for the sample mean by repeating the above steps many times. Here we will generate 5000 samples and compute the sample mean of each.

We will use a programming method called a "loop" to draw 5000 samples and calculate their means. You do not need to modify the code in the loop, but you may want to take a look and see if you can tell what it is doing.

Once we have generated our 5000 samples and saved their means (to an object called `sample_means50`) we will generate a histogram to visualize the sampling distribution of the mean living area.

`@instructions`
Run the loop code to generate the R object `sample_means50` that contains all the sample means.

Generate the histogram of the means of the 5000 samples of 50 houses each.

`@hint`


`@pre_exercise_code`
```{r}
load(url("http://www.openintro.org/stat/data/ames.RData"))
```

`@sample_code`
```{r}
# The ames dataset is already loaded

# Run loop to fill in the set of 5000 sample means
sample_means50 <- rep(NA, 5000)
for(i in 1:5000){
   samp <- sample(ames$Gr.Liv.Area, 50)
   sample_means50[i] <- mean(samp)
   }

# Plot histogram
hist(sample_means50)
```

`@solution`
```{r}
# The ames dataset is already loaded

# Run loop to fill in the set of 5000 sample means
sample_means50 <- rep(NA, 5000)
for(i in 1:5000){
   samp <- sample(ames$Gr.Liv.Area, 50)
   sample_means50[i] <- mean(samp)
   }

# Plot histogram
hist(sample_means50)
```

`@sct`
```{r}

```

---

## Inference: Simulate larger-N sampling distribution

```yaml
type: NormalExercise
key: faddd2cde4
xp: 100
```

The law of large numbers means that as our sample size increases, the mean living area should be a more reliable estimate of the population mean, and the standard error of the sample distribution will decrease.

In this exercise, we will demonstrate this by repeating our sampling loop from the last exercise,this time drawing 5000 samples of 100 houses rather than samples of 50 houses.  

We will then generate histograms of the two sampling distributions to see how they compare

`@instructions`
The ames dataset and the sample_means50 object are both already loaded.

Run the code to loop over 5000 samples of 100 houses each, which will be saved in the `sample_means500` object. 

Generate two histograms, one for each sampling distribution (`sample_means50` and `sample_means500`, using the `hist()` function.  Before plotting the histograms run the two lines of code that set options for how the histograms are displayed

`@hint`
Have you made sure to put the name of the `sample_means100` object inside the second histogram command?

`@pre_exercise_code`
```{r}
load(url("http://www.openintro.org/stat/data/ames.RData"))
sample_means50 <- rep(NA, 5000)
for(i in 1:5000){
   samp <- sample(ames$Gr.Liv.Area, 50)
   sample_means50[i] <- mean(samp)
   }

```

`@sample_code`
```{r}
# Loop over 5000 samples of 100 houses
sample_means500 <- rep(NA, 5000)
for(i in 1:5000){
   samp <- sample(ames$Gr.Liv.Area, 500)
   sample_means500[i] <- mean(samp)
   }

# code to let us put two plots on top of each other
par(mfrow = c(2, 1))
# code to make the x-axis of the plots consistent so we can compare
xlimits <- range(sample_means50)

hist(sample_means50, xlim = xlimits)
hist(___, xlim = xlimits)
```

`@solution`
```{r}
# Loop over 5000 samples of 100 houses
sample_means500 <- rep(NA, 5000)
for(i in 1:5000){
   samp <- sample(ames$Gr.Liv.Area, 500)
   sample_means500[i] <- mean(samp)
   }

# code to let us put two plots on top of each other
par(mfrow = c(2, 1))
# code to make the x-axis of the plots consistent so we can compare
xlimits <- range(sample_means50)

hist(sample_means50)
hist(sample_means500)
```

`@sct`
```{r}

```

---

## Checkpoint: Understanding sampling distributions

```yaml
type: PureMultipleChoiceExercise
key: 8dcbcf00a9
xp: 50
```

In the previous exercise you generated two sampling distributions.  Which of the following were NOT features of the distributions you plotted?

`@hint`


`@possible_answers`
- The smaller sample size had a wider spread than the larger sample size.
- [The center of the two distributions was approximately the same.]
- The larger sample size had more variability in its sampling distribution

`@feedback`
- Try again!
- Great job!
- Try again!

---

## Explore data: Calculate mean and standard deviation

```yaml
type: NormalExercise
key: c58d27ef76
xp: 100
```

In practice, we do not have access to data for the full population, and can only draw one sample from the population.

In this case, we can't draw the full sampling distribution.  Instead, we use confidence intervals calculated from the standard error of our estimate of the mean.  In this and the following exercise, will walk through calculating the standard error and confidence intervals.

To start, we will draw a sample from our population of houses, and calculate the _mean_ and _standard deviation_ of the living area of the houses in the sample.

`@instructions`
The ames dataframe is already loaded.  As we did in previou exercise, draw a sample (with a sample size of 60) from the living areas of the whole population of houses.

Next, calculate the mean and standard deviation of the living area sample and save these statistics to sensibly named objects.

`@hint`


`@pre_exercise_code`
```{r}
load(url("http://www.openintro.org/stat/data/ames.RData"))
```

`@sample_code`
```{r}
# The ames dataframe is already loaded 

# Draw a sample of living areas for 60 houses from the population
area_sample <- sample(ames$Gr.Liv.Area, 60)

# Calculate and save the mean living area in the sample
mean_area <- mean(area_sample)

# Calculate and save the standard deviation of the sample of living areas
sd_area <- sd(area_sample)
```

`@solution`
```{r}
# The ames dataframe is aready loaded.

# Draw a sample of living areas for 60 houses from the population
area_sample <- sample(ames$Gr.Liv.Area, 60)

# Calculate and save the mean living area in the sample
mean_area <- mean(area_sample)

# Calculate and save the standard deviation of the sample of living areas
sd_area <- sd(area_sample)
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

In the last exercise, you drew a random sample of 60 houses and calculated the mean and standard deviation of the living area _in your sample_.

For this exercise, the `ames` dataframe and a sample mean (`mean_area`) and standard deviation (`sd_area`) area already loaded.  Note that this sample mean and standard deviation may be different than what you calculated in the last exercise as they are calculated for a new sample for this exercise.

In this exercise, we will use the sample mean and standard deviation to calculate the 95% confidence interval around the sample estimate of the mean.  

We will also check whether our sample is one of the 95% of samples that we expect to contain the population parameter.

`@instructions`
Calculate the standard error of the estimate, using the equation for standand error: the standard deviation divided by the square root of the sample size.  The R function `sqrt()` calculates square roots!

Calculate the lower and upper limits of the 95% confidence interval.  Remember, the 95% confidence interval is defined by 1.96 standard errors above and below the estimated mean.  

Finally, calculate the population mean to check whether it falls within your confidence interval.

`@hint`


`@pre_exercise_code`
```{r}
load(url("http://www.openintro.org/stat/data/ames.RData"))
# Draw a sample of living areas for 60 houses from the population
area_sample <- sample(ames$Gr.Liv.Area, 60)

# Calculate and save the mean living area in the sample
mean_area <- mean(area_sample)

# Calculate and save the standard deviation of the sample of living areas
sd_area <- sd(area_sample)
```

`@sample_code`
```{r}
# ames dataframe, mean_area, and sd_area are already loaded.

# Calculate standard error and save as object 'se', using a sample size of 60
se <- sd_area/sqrt(60)

# Calculate and save the upper and lower C.I.
lower <- mean_area - 1.96 * se
upper <- ___ _ 1.96 * ___

# Print the confidence interval:
print(lower)
print(upper)

# Calculate and print the population mean
mean(ames$Gr.Liv.Area)
```

`@solution`
```{r}
# ames dataframe, mean_area, and sd_area are already loaded.

# Calculate standard error and save as object 'se', using a sample size of 60
se <- sd_area/sqrt(60)

# Calculate and save the upper and lower C.I.
lower <- mean_area - 1.96 * se
upper <- mean_area + 1.96 * se

# Print the confidence interval:
print(lower)
print(upper)

# Calculate and print the population mean
mean(ames$Gr.Liv.Area)
```

`@sct`
```{r}

```

---

## Checkpoint: Interpret confidence interval

```yaml
type: PureMultipleChoiceExercise
key: 08b306a6eb
xp: 50
```

What is the best interpretation of the 95% confidence you calculated?

`@hint`


`@possible_answers`
- There is a 95% probability that the true population value is within the confidence interval range
- [In 19 out of 20 samples, this range would include the true population value]
- It is impossible for the true population parameter to be outside the range of the confidence interval

`@feedback`
- Try again!
- Great job!
- Try again!

---

## Inference: Calculate confidence intervals

```yaml
type: NormalExercise
key: 8f67b77e3f
xp: 100
```

As a last exercise to explore sampling distributions and confidence intervals, we will confirm that confidence intervals _do not always contain the population parameter_.

We will do this by running code that loops over 50 samples of the living area (like we did for sampling distributions earlier).  Again, you do not need to modify this code, but you may want to look at it and figure out what it is doing.

Once we have drawn our 50 samples, we will calculate the confidence interval around the mean for each sample and plot them.

`@instructions`
Run the loop code to draw 50 samples of 60 houses and save the 50 sample means and standard deviations.

Calculate the upper and lower bounds of the confidence intervals for each sample, saving the collected upper and lower bounds in objects called `upper_bounds` and `lower_bounds`.

Run the `plot_ci()` function to generate a plot of all the confidence intervals, a line showing the population mean, and highlighting of intervals that do not contain the population mean.

`@hint`


`@pre_exercise_code`
```{r}
load(url("http://www.openintro.org/stat/data/ames.RData"))
```

`@sample_code`
```{r}
# Loop function to calculate the sample means and sds for 50 samples of 60 houses each:
samp_mean <- rep(NA, 50)
samp_sd <- rep(NA, 50)
for(i in 1:50){
  samp <- sample(ames$Gr.Liv.Area, 60) # obtain a sample of size n = 60 from the population
  samp_mean[i] <- mean(samp)    # save sample mean in ith element of samp_mean
  samp_sd[i] <- sd(samp)        # save sample sd in ith element of samp_sd
}

# Construct 95% confidence intervals
lower_vector <- samp_mean - 1.96 * samp_sd / sqrt(60) 
upper_vector <- ___

plot_ci(lower_vector, upper_vector, mean(ames$Gr.Liv.Area))
```

`@solution`
```{r}

# Loop function to calculate the sample means and sds for 50 samples of 60 houses each:
samp_mean <- rep(NA, 50)
samp_sd <- rep(NA, 50)
for(i in 1:50){
  samp <- sample(ames$Gr.Liv.Area, 60) # obtain a sample of size n = 60 from the population
  samp_mean[i] <- mean(samp)    # save sample mean in ith element of samp_mean
  samp_sd[i] <- sd(samp)        # save sample sd in ith element of samp_sd
}

# Construct 95% confidence intervals
lower_vector <- samp_mean - 1.96 * samp_sd / sqrt(60) 
upper_vector <- samp_mean + 1.96 * samp_sd / sqrt(60) 

#plot_ci(lower_vector, upper_vector, mean(ames$Gr.Liv.Area))

```

`@sct`
```{r}

```
