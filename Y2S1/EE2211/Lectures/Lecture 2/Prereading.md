1) Types of data
2) Data wrangling and cleaning
3) Data integrity and visualization

## Ways of viewing data
- Nominal data
- Ordinal data
- Interval data
- Ratio data

## Based on numerical / Categorical

## Other Aspects
- Available or missing data

***

## Types of data / Scales of measurement
## NOIR
## N: Nominal Data
- Categorical data with no relative ordering
- Lowest level of measurement (No Manual Order)

## O: Ordinal Data
- Categorical data with ordering

## I: Interval Data
- Categorical data with ordering and at fixed intervals

## R: Ratio Data
- Categorical data with ordering, fixed intervals and true zero

## Mean, Median, Mode
Mean: Average
Median: Middle Number
Mode: Most frequent Number

---

Nominal Data
- Lowest level of measurement 
- Discrete categories
- **No** natural order
- Estimating a mean, median, or standard deviation would be meaningless

Possible Measure: Mode/Frequency Distribution

For example: Gender/Occupation
***
Ordinal Data
- Ordered categories
- Relative ranking
- Unknown “distance” between categories: order matters but not the difference between values

Possible Measure: Mode, Frequency distribution + median 
### Why median? 
Because median requires an order

For e.g., eye colour = (blue, brown, green)
There is no meaningful order such as:
> Blue < Brown < Green

To find the median, we need to sort them and find the middle number. But in this case, there isnt any ordering so we are unable to find the middle number

Types of ordinal data:
- Evaluate the difficulty of an exam (Very easy (1), Easy (2), About Right(3), Difficult (4), Very Difficult (5))
- There is some sort of ordering in between ordinal data. However the distance between each data is “unknown"

***

Interval Data
- Ordered Categories
- Well-defined “unit” measurement:
	- Distance between points on the scale are measurable and well defined
	- Equal intervals → It means that the same numerical difference represents the same amount of change anywhere on the scale
		- **Equal Numerical gaps have equal meaning**

> [!example]
> For temperature, 20.3 - 20.1 = 0.2 and 30.3 - 30.1 = 0.2 and both represent exactly the same temperature increase of 0.2 
> 
> This can also be applied to date of birth for example, where a person born in 2010 vs a person born in 2000 is **10 years difference**. Similarly, a person born in 2020 vs a person born in 2010 is also a **10 years difference**. 
> 
> This shows that distance between points are measurable and well defined and at equal intervals they have the same meaning


- For interval data, the zero point is arbitrary (Meaning that it does not represent the complete absence of the quantity)
	- For example (temperature in Celsius) 
		- 0 deg does not mean “no temperature”

- Ratio is meaningless

> [!example]
> You might calculate 
>
> $$
>	\frac{20\text{deg}}{10\text{deg}} = 2
> $$
>
> However, converting those into another unit like Fahrenheit where 
>
> $$
>	\frac{68\text{deg}}{50\text{deg}} = 1.36 
> $$ 
>
> This shows that the ratio is not describing anything real about the temperatures

If changing the measurement scale changes the ratio, the ratio isn’t meaningful.

However, for mass e.g. 10kg vs 20kg and 10000g and 20000g. We can see that the ratio shows a meaningful difference

Possible measures: mode, frequency distribution + median + mean, standard deviation, addition/subtraction
***
Ratio Data
- Most precise and highest level of measurement
- Ordered
- Equal Intervals

Natural Zeros:
If the variable equals zero, it means that there is **None** of that variable
Not arbitrary (unlike interval)
Possible measures: mode, frequency distribution + median + mean, standard deviation, addition/subtraction + multiplication and division (ratio)

e.g weights, time
***

## Summary of the difference measurement methods

## Levels of precision
Ratio → Interval → Ordinal → Nominal


## Ordered?
Yes: Ratio / Interval / Ordinal
No: Nominal

### Is there an equal interval between each measurement?
Yes: Ratio / Interval 
No: Ordinal

### Is there an arbitrary 0 value in the measurements?
Yes: Ratio
No: Interval

### Possible measurements
1) Nominal → Mode + Frequency distribution
2) Ordinal → Mode + Frequency distribution | Mean + standard deviation
	> Frequency distribution vs standard deviation?
	> Frequency distribution: How often the point appears in the dataset
	> Standard deviation: How much the values spread away from the mean

### Examples
Nominal: Fish species/Male Female/Occupation etc
Ordinal: Likert scale (On a scale rate the driver)
Interval: Temperature (0 is arbitrary)
Ratio: Weight (0 is not arbitrary)
***
![Pasted image 20260817195220](Pasted%20image%2020260817195220.png)


![Pasted image 20260817195606](Pasted%20image%2020260817195606.png)

Favorite Restaurant 
1) Mcdonald’s, Burger King, Subway, KFC (Nominal)

Weight of luggage measured in KG (Ratio, 0 is not arbitrary)
SAT Scores: note that, SAT ranges is [400, 1600] (Interval because there is not a true zero)
Size of packet eggs in supermarkets (Small, Medium, Large, Extra Large) → Ordinal
Military Rank → Ordinal
Number of people in a household → Ratio
Credit Score → Interval because there is not a true zero and the differences between the intervals are meaningful
***
Ways of viewing Data

## Numerical or Categorical
## Categorical
### 1) Nominal → Unordered categories
### 2) Ordinal → Ordered categories
## Numerical (Quantative)
### 1) Discrete → Whole numerical values (outcome of tossing any value within a range)
### 2) Continuous → Can take any value within a range (temperature in a day)

## Numerical (Quantative)
### 1) Interval → Arbitrary 0 
### 2) Ratio → Non Arbitrary 0

***
Missing Data
- Data that is missing and you do not know the mechanism

*Mechanism* → How or why something happens (in this case, you do not know why certain data points are missing)

For ==Missing Data==, use a common code for all missing values (for example “NA”) rather than leave any entries blank
***
Data wrangling and cleaning

## Data Wrangling
The process of transforming and mapping data from one “raw” data form into another
Make it more appropriate and valuable for a variety of downstream purposes such as analytics


transforms data → more readable/useful
***
## Formatting Data

## Binary Encoding (e.g. one hot encoding)
Binary coding to convert categories into binary form
→ one hot encoding (unify several entities/features into one vector)

For example given the colour of a pixel can be red/yellow/green

$$
\mathbf{x} = [x_{1},x_{2},x_{3}]
$$

where x1 = red, x2 = yellow and x3 = green

$$
\mathbf{\mathrm{Re}d} = [1,0,0] 
$$

$$
	\mathbf{Yellow} = [0,1,0]
$$

$$
	\mathbf{Green} = [0,0,1]
$$

This is very common in classification tasks whereby we need to encode a category into a binary form.

## Normalization
### Linear Scaling
- Scale each variable to [0,1]

### z-score standardization
- Each independent dimension of data is normally distributed whereby 
  The mean = 0
  The standard deviation = 1
  
- It converts the data from actual values into z-scores, which lets you compare data points from different distributions directly, regardless of their original units or scales
***
## Data cleaning 

### 1. Removing the examples with missing features from the dataset
### 2. Using a learning algorithm that can deal with missing feature values
e.g Forest Tree
- is a machine learning algorithm (a subset of AI which gives computers the ability to learn without being explicitly told to do so) 
- Creates many decision trees
- Makes its own prediction
- Combine their predictions 
  Classification → Majority Vote
  Regression → Average

Random Forest reduces overfitting and usually generalizes better than one decision tree.

### 3. Using a data imputation technique

Replace the missing value of a feature by an average value of this feature in the dataset

OR

Highlight the missing value

Set it to -1 (which is a value outside the predicted normal range), enforce the learning algo to learn what is the best method to do when the value has a different value from the expected values
***

## Data integrity
maintenance and assurance of data accuracy and consistency
- A critical aspect to the design, implementation and usage of any system that stores, processes and retrieves data.

Example:
In a dataset, numeric columns/cells should not accept alphabetic data 
A binary entry should only allow binary inputs

### Data Visualization

Distribution: Bar Graph 
Box Plots

Visualization allows us to show the difference between datasets with similar summary statistics

***
Colour → Nominal
Size → ordinal
Shape → Nominal

- **Color → Nominal**: categories with no meaningful ranking, e.g. red, blue, green.
- **Size → Ordinal**: there is a meaningful order, e.g. Small < Medium < Large, but the **difference** between Small → Medium isn't necessarily the same as Medium → Large.
- **Shape → Nominal**: categories such as circle, square, triangle have no meaningful ranking.

Label → Yes/No (Nominal) no relative ranking





