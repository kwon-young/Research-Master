# Descriptive and exploratory statistics


## Representing and viewing data

* where does the data come from
  * is the data representative
  * how to collect data
    * sample representative data
    * database design

## Describing 1D data

* From a single variable X observed on n samples, we want to
  * describe the variable
  * summarize the information
* data are usually organized in tables
* for continuous data, group into classes !

* categorical data
* discrete data

Empirical distributions : histograms

* used to display the empirical distribution
* for smooth histogram
  * use of a sliding window

Empirical distributions : stem and leaf plots

Empirical distributions : pareto diagrams

* highlight the most important factors

Scattors plots for numerical variables

Numerical summaries of the data

* central characteristics
  * mean, median, mode
* deviation around the central point
  * extrema, standard deviation, quantiles
* overall shape
  * skewness

Yule's condition

a good statistical summary should :

* be defined objectively
* be dependent on all the observations
* have a concrete and clear meaning
* be simple to compute
* be insensitive to sampling fluctuations

Central characteristics

* empirical mean but sensitive to outliers
* alpha-truncated mean : empirical mean after discarding the extremum values
* median : value of the middle sample after sorting
* mode : local extrema of the histogram

dispersion and shape of a variable

* dispersion
  * minimum, maximum, range
  * variance and standard deviation
  * quantiles
    * bound of the intervals dividing the data in equal parts
    * interquartile range IQR = Q3 - Q1
* Shape

Box and whisker plots

* compact representation of the mean and dispersion
  * 1st and 3rd quartiles
  * higher values <= Q3 + 1.5(Q3-Q1)
  * smaller value >= Q1 - 1.5(Q3-Q1)
  * outliers

## Measuring the relation between variables

Correlation

* Pearson's linear correlation coefficient
  * doesn't say if there is a linear correlation

## Exploring multidimensional data

Projection vs Clustering

* change the data and reduce dimensions
  * Principle component analysis
  * Linear discriminant analysis
* clustering : find group of data

General idea of *factor analysis*

PCA the easy way

* find the best projections
* keep distances unchanged
* maximize the variance
* maximize inertia
* least square error


