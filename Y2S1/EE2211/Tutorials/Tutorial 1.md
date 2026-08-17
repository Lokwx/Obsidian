Question 1: What is the difference between ML (Machine Learning) and AI (Artificial Intelligence)?

Machine Learning a subset of artificial intelligence
Artificial Intelligence is any technique which enables computers to mimic human behavior
Machine learning is AI techniques that give computers the ability to learn without explicitly programmed to do so

Example of AI but not ML: Deductive Reasoning 
→ Uses explicit rules and logic. For example “All humans are mortal. Socrates is human. Therefore, Socrates is mortal”


1)
>Chatgpt is both AI and ML applications (deep learning models)
>SLAM is the middle ground between AI and ML

In between ML and DL → Classical Machine Learning (Regression)

### Deductive reasoning

In deductive reasoning, the computer doesn’t learn the reasoning rules from data. Humans give it facts and logical rules and it derives conclusions from them

---

Question 2: Which of the following is the most reasonable definition of machine learning? 
(a) Machine learning is the field of allowing robots to act intelligently. 
(b) Machine learning is the science of programming computers. 
(c) Machine learning only learn from unlabeled data. 
(d) Machine learning is the field of study that gives computers the ability to learn without being explicitly programmed.

Answer: (d)
Machine learning (Supervised Learning) is the field of study that gives computers the ability to learn without being explicitly programmed.

2 → D

Machine learning is the field of allowing robots to act intelligently. → Algorithms
Machine learning is the science of programming computers. → Programming Methodology
"Machine learning only learn from unlabeled data → Can be both

---

Question 3: A computer program is said to learn from experience E with respect to some task T and some performance measure P, if its performance on T, as measured by P, improves with experience E. Suppose we feed a learning algorithm a lot of historical weather data, and have it learn to predict weather. In this setting what is T? 
(a) The historical weather data. 
(b) The probability of it correctly predicting a future data’s weather. 
(c) The weather prediction task. 
(d) None of these.

TPE → Task, Performance, Experience

Suppose we feed a learning algorithm a lot of historical weather data, and have it learn to predict weather. In this setting what is T? 

Task → The weather prediction task
Performance → The probability of it correctly predicting a future data’s weather/==Accuracy Rate/Accurate Score (Rate of success)==
Experience (Datasets/Training Data) → The historical weather data

Answer: (c)

---
Question 4: Suppose you are working on weather prediction and use a learning algorithm to predict tomorrow’s temperature (in degrees Centigrade/Fahrenheit). (i) Would you treat this as a classification or a regression problem? 
(a) Regression. 
(b) Classification. 
(c) Clustering. 
(d) None of these. 

- **Regression** → Predict **continuous values**
  - Question: **"How much?"**
  - E.g. house price, temperature, salary

- **Classification** → Predict **predefined classes/categories**
  - Question: **"Which class?"**
  - E.g. fish species, ball colour, spam/not spam

- **Clustering** → Group **similar unlabeled data**
  - Question: **"Which group?"**
  - E.g. COVID zones, customer groups

> [!important] Classification vs Clustering
> - **Classification** → Classes are already known/labelled
> - **Clustering** → No labels; algorithm discovers the groups

I would use a regression problem because the weather data is a continuous value and it is hard to sort them into different categories 

(ii) What kind of data should you gather?

I would gather the date vs temperature graph



Supervised (Labels → Ground Truth)
If the labels is continuous, then it is a regression task
> For example, temperature can range from a range of values

If the labels is categorical, then it is  a classification task
> Finite labels (cloudy/sunny day)

## Supervised Task
- Labels are fixed (Ground truth)
- Suggest some features (for example changes in pressure, weather condition etc.)

---
Question 5: You want to develop learning algorithms to address each of the following two problems. 
P1: You’d like the software to examine your email accounts, and decide whether each email is a spam or not. 
P2: You have a large quantity of green tea (e.g., 1000kg) with a record of previous sales. You want to predict how much of it will sell over the next 6 months. Should you treat these as classification or as regression problems? 
(a) Treat both P1, P2 → regression problems. 
(b) Treat both P1, P2 → classification problems. 
(c) Treat P1 → regression problem, P2 → classification problem. 
(d) Treat P1 → classification problem, P2 → regression problem.

P1 → Labelled data (classification)
P2 → Regression problem 
Past sales → regression model → predicted future sales

> [!note] 
> The 1000 kg mainly tells you the maximum stock available

- Plot **historical sales against time**
  - **x-axis** → Time (months)
  - **y-axis** → Amount sold (kg)
- Use the historical sales trend to **predict the expected sales for the next 6 months**
- Since the predicted output is a **continuous quantity (kg)** → **Regression**

> [!important]
> We don't plot against the "6-month expected sales" because that is what we are trying to **predict**.




---
Question 6: Suppose you are working on stock market prediction. Typically tens of millions of shares of a company’s stock are traded each day. You would like to predict the number of shares that will be traded tomorrow. 
(i) Would you treat this as a classification or a regression problem? 
(a) Regression. 
(b) Classification. 
(c) Clustering. 
(d) None of these. 

Ans: regression → multiple data points (continuous data)

PCA (Principle Component Analysis) → Feature extraction/Feature Selection

> [!important]
> GIGO (Garbage In Garbage Out)
> We are not able to select all the features, so we need to select/extract relevant features


- We are predicting the **number of shares traded tomorrow**
- The output is a **numerical quantity**
  - E.g. 10,000,000 shares
  - 12,500,000 shares
  - 15,000,000 shares
- Therefore → **Regression**

> [!important]
> Even though the number of shares is technically **discrete** (you can't trade 0.5 of a share in this framing), it is treated as **regression** because we're predicting a numerical quantity over a very large range.

**Quick rule:**  
Predict **how many / how much** → usually **Regression**

(ii) If the data you have collected involved millions of attributes, what would you do?
I would plot them into a graph and use it to estimate the next days company stock

---
Question 7: Some of the problems below are best addressed using a supervised learning algorithm, and the others with an unsupervised learning algorithm. Which of the following would you apply supervised learning to? (Select all that apply) Assume some appropriate dataset is available for your algorithm to learn from. 
(a) Determine whether there are vocals (i.e., a human voice singing) in each audio clip extracted from a piece of music, or it is a clip of only musical instruments and no vocals. 
(b) Given data on how 1000 medical patients respond to an experimental drug (such as effectiveness of the treatment, side effects, etc.), discover whether there are different categories or “types” of patients in terms of how they respond to the drug, and if so what these categories are. 
→ Clustering algorithm
(c) Given a large dataset of medical records of patients suffering from heart disease, try to learn whether there might be different clusters of such patients for which we might tailor separate treatments. 
→ Clustering
(d) Given a set of data which contains the diet and the occurrence of diabetes from a population over a 10-year period. Predict the odds of a person developing diabetes over the next 10 years.
→ Supervised (There are labels for the health conditions etc)

Supervised learning → Labelling/Regression/Classification
Unsupervised learning → Clustering (Finding underlying patterns in data)

(a) labelling of vocals is possible through the sound frequencies of human voices or wtv

> [!note]
> - Train using audio clips that are **already labelled** as vocals/no vocals
> - Model learns features of the audio → predicts the class

> [!note]
> It's not supervised simply because we can analyse human voice frequencies.
> It's supervised because we have **known labels** that the model can learn from. 

(b) unsupervised learning
(c) clusters → unsupervised learning
(d) Supervised learning (regression)

## Question 7 — Supervised vs Unsupervised Learning

### (a) Vocals vs No Vocals → Supervised ✅

- **Classification problem**
- Classes:
  - Vocals
  - No vocals
- Train using audio clips that are **already labelled** as vocals/no vocals
- Model learns features of the audio → predicts the class

> [!note]
> It's not supervised simply because we can analyse human voice frequencies.
> It's supervised because we have **known labels** that the model can learn from.

### (b) Discover types of patients → Unsupervised ❌

- Categories are **not given beforehand**
- Algorithm must **discover groups/patterns**
- → **Clustering**


### (c) Discover clusters of heart patients → Unsupervised ❌

- Explicitly asks to find **different clusters**
- Groups are not predefined
- → **Clustering**

### (d) Predict odds of developing diabetes → Supervised ✅

- Historical data contains:
  - Diet/features → **Input**
  - Diabetes occurrence → **Known outcome/label**
- Use these known outcomes to train a model
- → **Supervised Learning**

> [!important]
> **Answers to select: (a) and (d)**

---

Suppose you are working on a machine learning algorithm to predict if a patient is COVID-19 infected according to the patient’s particulars such as age and health conditions, symptomatic data, such as fever, dry cough, tiredness, aches and pains, sore throat, diarrhoea, conjunctivitis, and headache etc. What are the Task, Performance, and Experience involved according to the definition of machine learning?

Task: patient classification into “infected” or “uninfected”
Performance: Accurately detect if the patient is infected with COVID-19
Experience: labelled health conditions data and symptomatic data

---
Question 9: We use labelled data for supervised learning, where the labels are used as the desired target of prediction for classifiers. Which of the next data are the useful labelled data? 
(a) To build an image object classifier to discriminate between apple and orange, we have many fruit images labelled with the country of origin. 
(Not useful)
(b) To build a system to predict the number of COVID cases for tomorrow given the past daily record, we have a collection of daily data for a period of 12 months. 
(Useful)
→ Past data can help to predict the future because it helps due to community immunity
(c) To build a classifier to automatically evaluate student essays, we have collected a set of student essays that have not been graded by teachers" 

(a) is not because we are trying to discriminate between apple and orange, but labelled images with country of origin doesn’t help
(b) It is a useful labelled data because for regression methods, the daily data over a period is useful to predict the number of COVID cases
(c) Ungraded scripts does not help with the task, which is to automatically evaluate student essays

Answer: (b)

---
Question 10: Determine whether each of the following is “inductive” or “deductive” reasoning? 
(a) The first coin I pulled from the bag is a penny. The second and the third coins from the bag are also pennies. Therefore, all the coins in the bag are pennies. (inductive reasoning)
(b) All men are mortal. Harold is a man. Therefore, Harold is mortal.

### Deductive reasoning
Given a fact, you can deduce something from it
Singapore is in Asia
Nus is in Singapore
NUS is in Asia

### Deductive reasoning
- All the data to obtain the correct conclusion is available
- We are able to reach logical conclusions deterministically

### Inductive Reasoning
- Probable reasoning
- Not all information is available to reach the conclusion 

Ans: (b) is a deductive reasoning

---

Question 11: Find a problem of your interest and formulate it as a machine learning problem. List out the input features and output response and provide your choice regarding the types of learning (such as supervised or unsupervised learning,

Task: Predict the species of insects
Performance: Accuracy of detecting the correct species
Experience: Labelled image data

Supervised learning because we are providing labelled image data for it to generate a function that

### 1. Regression

- Predicts a **continuous numerical value**
- Model learns a function/trend from labelled training data
- E.g. predict house price, temperature, future sales

> [!example]  
> **Input:** House size  
> **Output:** Predicted price = $500,000

Think: **"How much?"**

---

### 2. Classification

- Predicts a **class / category**
- Model learns a **decision boundary** that separates classes
- E.g. fish species, spam/not spam, cat/dog images

> [!example]  
> **Image labelling:**  
> Image → Model → **Cat / Dog**
> 
> This is **Classification**, not regression.

### Decision Boundary

For example, with two fish species:

Species A  • • •   |   × × ×  Species B

         • • •     |    × ×

                   ↑

            Decision Boundary

The boundary separates the different classes.

> [!important]  
> **Regression** → learn a function to estimate a **value**  
> **Classification** → learn a decision boundary to determine a **class**


Note: the classification boundary isn't always literally a **straight line**. It could be curved or very complex, especially for images.