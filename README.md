# Binary-Classification-Solution-to-Predict-Sonar-Return-Data
In This Project I Test a Few Different Machine Learning Algorithms To See Which One Is Best For Classifying Sonar Return Data
### Problem Definition
This project was run on the Sonar Mines vs. Rocks Dataset. The problem is to predict metal or rock objects from sonar return data. Each pattern is a set of 60 numbers in the range 0.0 to 1.0. Each number represents the energy within a particular frequency band, inegrated over a certain period of time. The label associated with each record contains the letter R if the object is a rock and M if it is a mine (metal cylinder). The numbers in the labels are in increasing order of aspect angle, but they do not encode the angle directly.

### Working Through the Problem
I first loaded the data set and peek into the descriptive statistics of the data to get a better understanding of it. Next I compared the algorithms below to see which one works best on the dataset. This was done using 10-fold cross-validation.
- Linear Alogirthms: Logistic Regression (LR) & Linear Discriminant Analysis (LDA).
- Nonlinear Algorthims: Classification and Regression Trees (CART), Support Vector Machines (SVM), Gaussian Naive Bayes (NB) & k-Nearest Neighbors (KNN).

#### Evaluation #1
I first evaluated the algorithms without standarzing the data so see which ones worked the best on the dataset.

dd
