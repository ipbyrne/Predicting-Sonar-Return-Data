# Binary-Classification-Solution-to-Predict-Sonar-Return-Data
In This Project I Test a Few Different Machine Learning Algorithms To See Which One Is Best For Classifying Sonar Return Data
### Problem Definition
This project was run on the Sonar Mines vs. Rocks Dataset. The problem is to predict metal or rock objects from sonar return data. Each pattern is a set of 60 numbers in the range 0.0 to 1.0. Each number represents the energy within a particular frequency band, inegrated over a certain period of time. The label associated with each record contains the letter R if the object is a rock and M if it is a mine (metal cylinder). The numbers in the labels are in increasing order of aspect angle, but they do not encode the angle directly.

### Working Through the Problem
I first loaded the data set and peek into the descriptive statistics of the data to get a better understanding of it. Next I compared the algorithms below to see which one works best on the dataset. This was done using 10-fold cross-validation.
- Linear Alogirthms: Logistic Regression (LR) & Linear Discriminant Analysis (LDA).
- Nonlinear Algorthims: Classification and Regression Trees (CART), Support Vector Machines (SVM), Gaussian Naive Bayes (NB) & k-Nearest Neighbors (KNN).

#### Evaluation #1
I first evaluated the algorithms without standarzing the data so see which ones worked the best on the dataset. I compared the performance of each algorithm using a box and whiskers plot.
![Alt text](images/image1.png?raw=true)

This first evaluation showed that the KNN and LR algorithm were performing the best, with the KNN have the least amount of variance. I was surprised to see the SVM model having so much variance. It was possible that the varied distribution of the attributes was having an effect on the accuracy of algorithms such as SVM.

Because of this I re-ran the the test after standardizing the data.
#### Evaltuation #2
After standardizing the data and comparing the algorithms again, I ended up with the following results.
![Alt text](images/image2.png?raw=true)

I can now see that the KNN and SVM algorithms are performing the best so I will further investigate these two.
#### Tuning the KNN Algorithm
The default number of neighbors was 7 and I wanted to try all odd numbers from 1 to 21. Each k value was evaluated using 10-fold cross-validation on the training standardized dataset.
![Alt text](images/image3.png?raw=true)

I was able to see that the optimal configuration is K=1. This is interesting as the algorithm will make predictions using the most similar instance in the training dataset alone.

#### Tuning the SVM Algorithm
I was able to tune 2 parameters in SVM aglorithm. The value of C and the type of kernal. The default for SVM (the SVC class) is to use the Radial Basis Function (RBF) kernel with a C value set to 1.0. Like with KNN, I performed a grid search using 10-fold cross-validation with a standardized copy of the training dataset. I decided to try a number of simpler kernel types and C values with less bias and more bias (less than and more than 1.0 respectively).
![Alt text](images/image4.png?raw=true)

I was able to find that the most accurate configuration was SVM with an RBF kernel and a C value of 1.5. The accuracy 86.7470% is seemingly better than what KNN could achieve.

#### Finalizing the Model
The SVM showed the most promise as a low complexity and stable model for this problem. I then finalized the model by training it on the entire training dataset and made predictions for the hold-out validation dataset to confirm my findings. A part of the findings was that SVM performs better when the dataset is standardized so that all attributes have a mean value of zero and a standard deviation of one. I was able to calculate this from the entire training dataset and apply the same transform to the input attributes from the validation dataset.
![Alt text](images/image5.png?raw=true)

I was able to achieve an accuracy of nearly 86% on the held-out validation dataset. A score that matches closely to my expectations estimated above during the tuning of the SVM algorithm.
