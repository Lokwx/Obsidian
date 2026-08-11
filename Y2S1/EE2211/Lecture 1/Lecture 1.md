## Definition of machine learning
### Task
### Experience
### Performance Measure

==if its performance at tasks in T, as measured by P, improves with experience E.==

## Supervised Learning
$$
	\text{Data + Output} \to \text{ML System} \to \text{Function F (Learned)}
$$

![](Lec_1.pdf#page=8&rect=10,153,634,352&color=yellow|Lec_1,%20p.8)

Many data and output pairs, each of it is associated with a label.

Once I have derived the function f, when i feed in an image of a cat, the ML function should output the label “cat”
>If the function is able to do this, we have a perfect dog and cat classifier

---
## Artificial Intellgence
 - Any technique which enables computers to mimic human behavior

## Machine Learning 
- Subset of AI (Learning)

## Deep Learning
- Machine learning using neural networks
- Generative AI (GenAI) 
- Grammaly (Neural Network for grammar checker)

---
### When do we need machine learning?
1) Lack of human expertise/human intervention (mars rover)
2) Involves huge amount of data 

### When do we not need machine learning
1) When there is nothing to be learned (e.g calculation of payroll → follow equation only)

---
## Application of machine learning
1) Image recognition 
	e.g USPS letter differentiator
	![](Lec_1.pdf#page=12&rect=10,53,717,385|Lec_1,%20p.12)

Task (T): Digit Recognition
Performance Measure (P): Classification Accuracy
Experience (E): Labelled Images

**If it sees similar images, it is able to generalize the data and output the correct labels**

## Supervision
Is also known as labels

---
## Applications of machine learning
### Email Filtering
To design a filter to filter emails into inbox and spam

Training (T): Email Categorization
Performance (P): Classification Accuracy
Experience (E): Email Data
> Sometimes the email data might be labelled. For e.g. when you open the email and you realise that an important email has been placed in the spam folder
> When I move the important email from spam into my inbox, this is implicitly providing some supervision/labels to the system

### Alpha Go

Task (T): Playing Go Game
Performance (P): Chances of winning 
Experience (E): Records of past games 
> Winning against other players == Training


### COVID-19 
My goal is to identify COVID-19 clusters. I want to identify these groups because no one knows how COVID-19 is spread.

![](Lec_1.pdf#page=15&rect=271,39,717,345|Lec_1,%20p.15)

I want to identify these groups such that within each cluster, I have a prediction of what the COVID-19 patient rates/high risk of counties with COVID-19

**I want to identify the largest clusters**

Task (T): Identifying COVID-19 Clusters
Performance (P): Smaller Internal Distances
> I want to find smaller local clusters such that all the clusters are tightly grouped together

Large external distance
> Only in this case, I can identify smaller and tight clusters

Experience (E): Records of COVID-19 Patients

---
## Supervised Learning
Continuous Data
- Regression (Using a regression line to predict a real-valued y given x)

Categorical Data
- Classification (Using a function f(x) to predict categorical y given x)
> The goal of classification is to find a function 

![](Lec_1.pdf#page=20&rect=8,29,696,298|Lec_1,%20p.20)

> Everything to the left of the green line will be treated as a salmon and everything to the right of the red line will be treated as a sea bass

The function separates the two classes. 
- If I measure a new fish, after i measure its lightness and width and it lies within the zone of the sea bass, it can be considered as a sea bass

## Categorical and Continuous Data
- Type of fish (discrete levels) vs ice levels (continuous levels)

---
## Unsupervised Learning
## Clustering

Given
$$
	x_{1}x_{2}x_{3}

$$
I only know that these data points are close to each other, so they form a clusters. 
*Unsupervised Learning is finding underlying patters in data*
- Finding clusters is one part of unsupervised learning

![](Lec_1.pdf#page=22&rect=5,39,712,359|Lec_1,%20p.22)

==No Label / Supervision is given==

---
## Reinforcement Learning
- Based on the rule, I know which action to take

### Asking the computer to play games

![Pasted image 20260811152722](Pasted%20image%2020260811152722.png)

==*Everytime you encouter a machine learning task that involves a sequence of actions/states it is reinforcement learning*==

- At each time, you have to decide whether to move left or move right

State: Ball Location/Paddle Location/Bricks
Actions: Moving the paddle left or moving the paddle right
Rewards:
1) When the ball hits a brick and clears all brick (Positive Reward)
2) When the paddle misses the ball (Negative Reward)
3) Cases in between (Zero reward)

---
![](Lec_1.pdf#page=26&rect=325,255,656,466|Lec_1,%20p.26)

>Identify clusters → Unsupervised 

![](Lec_1.pdf#page=26&rect=75,47,303,251|Lec_1,%20p.26)

There is provide some supervision (marking as spam)

![](Lec_1.pdf#page=26&rect=327,44,652,257|Lec_1,%20p.26)

A sequence of actions

---

![](Lec_1.pdf#page=27&rect=11,178,523,462|Lec_1,%20p.27)

![](Lec_1.pdf#page=27&rect=529,182,713,462|Lec_1,%20p.27)

>We are trying to match the samples with the new sample that we got → and assign a label to it

---

### ? How do i define most similar
$$
	\text{Feature Extraction (Attributes of Sample)} \to \text{Sample Classification}
$$
Machine Learning Pipeline

1) Extract features
	e.g lightness/colour/size/shape

2) Sample Classification
> Use the features to classify the new sample


![[Lec_1.pdf#page=28&rect=12,186,512,457|Lec_1, p.28]]
- Assigning features for each sample

![[Lec_1.pdf#page=29&rect=87,87,635,436|Lec_1, p.29]]

Summary of all the features extracted for each sample


![[Lec_1.pdf#page=31&rect=14,70,724,415|Lec_1, p.31]]

Recode the features and assign a ==similarity value/index== to it, then out of all the attributes, we will take the highest similarity among them and classify it as that sample
	*Assuming that we cannot take no for an answer*

## **Nearest Neighbour Classifier**
1) Find the nearest neighbour among the samples with the highest similarity index
2) Assign the label to the nearest neighbour within the sample

---

## Inductive vs Deductive Reasoning
*Inference* → Make predictions

## Main types of inference
1) Inductive Inference
2) Deductive Inference

### Inductive Inference
- We do not have sufficient information to get the perfect result (Probability and Statistics)

### Deductive Reasoning
- We have all the information to reach the correct conclusion (Rule Based Reasoning)






