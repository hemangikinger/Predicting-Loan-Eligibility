# Predicting-Loan-Eligibility

The problem

In this notebook we look at the data we got via this Kaggle dataset.

This company called "Housing Finance company" wants to automate the loan eligibility process based on the customer information and identify the factors/customer segments who are eligible for taking the loan.
We will explore the dataset given, check the various features we have and we will make an algorithm that can predict whether or not the loan would be approved in order to automate the process


Import the important libraries / packages

These packages are needed to load and use the dataset

![image-1](https://github.com/hemangikinger/Predicting-Loan-Eligibility/blob/master/image-1.JPG)

![image-2](https://github.com/hemangikinger/Predicting-Loan-Eligibility/blob/master/image-2.JPG)

It seems that we have a lot of text / category information (these are of the Dtype 'object') and a few numerical columns (Dtypes 'int64' and 'float64').
The last column 'Loan_status' is the column we would like to predict.

![image-3](https://github.com/hemangikinger/Predicting-Loan-Eligibility/blob/master/image-3.JPG)

![image-4](https://github.com/hemangikinger/Predicting-Loan-Eligibility/blob/master/image-4.JPG)


Loan Status in this Dataset

approved or rejected

As Loan Status is the column we want to predict, let's explore this column in the training dataset.

![image-5](https://github.com/hemangikinger/Predicting-Loan-Eligibility/blob/master/image-5.JPG)

![image-6](https://github.com/hemangikinger/Predicting-Loan-Eligibility/blob/master/image-6.JPG)

It looks like this is not well balanced in this set. But as this is the only data we have, I will leave this as is for now.

Handling missing values

Let's continue with handling the missing values in this dataset. Let's see where and how many missing values there are in this dataset.

![image-7](https://github.com/hemangikinger/Predicting-Loan-Eligibility/blob/master/image-7.JPG)

Looks like a good feature to use, as there is clearly a difference in the size of the columns for the yes and the no, so let's look deeper!

![image-8](https://github.com/hemangikinger/Predicting-Loan-Eligibility/blob/master/image-8.JPG)

Seems that if you have a credit history, it is more likely to get the loan approved.

Options in handling these missing values:

    Drop all the rows with missing values
    Handle the missing values with 0 (so no history) as there is nothing clear.
    Or we use the most frequent number, which is 1 for the credit history.

In this case, I tend to go for the most frequent number, as this is 86% of the dataset, so most likely to be true.

![image-9](https://github.com/hemangikinger/Predicting-Loan-Eligibility/blob/master/image-9.JPG)

As this seems to have no effect on the outcome, I will fill these with the most frequent one (so No)

![image-10](https://github.com/hemangikinger/Predicting-Loan-Eligibility/blob/master/image-10.JPG)

![image-11](https://github.com/hemangikinger/Predicting-Loan-Eligibility/blob/master/image-11.JPG)


Take a closer look at some of the features

let's look at the outliers!

![image-12](https://github.com/hemangikinger/Predicting-Loan-Eligibility/blob/master/image-12.JPG)

![image-13](https://github.com/hemangikinger/Predicting-Loan-Eligibility/blob/master/image-13.JPG)

![image-14](https://github.com/hemangikinger/Predicting-Loan-Eligibility/blob/master/image-14.JPG)

![image-15](https://github.com/hemangikinger/Predicting-Loan-Eligibility/blob/master/image-15.JPG)


Make all columns numeric

We need to make all column input numeric to use them further on. This is what I will do now.

![image-16](https://github.com/hemangikinger/Predicting-Loan-Eligibility/blob/master/image-16.JPG)

![image-17](https://github.com/hemangikinger/Predicting-Loan-Eligibility/blob/master/image-17.JPG)

Right so now all columns are numeric

![image-18](https://github.com/hemangikinger/Predicting-Loan-Eligibility/blob/master/image-18.JPG)

![image-19](https://github.com/hemangikinger/Predicting-Loan-Eligibility/blob/master/image-19.JPG)

![image-20](https://github.com/hemangikinger/Predicting-Loan-Eligibility/blob/master/image-20.JPG)

Seems that the three feature selection models differ in what feature is the most important. For the first test I will keep:

    Credit history (high in all three tests and the highest in the correlation)
    Co Applicant Income (high in two tests, negative in the correlation, but this is explainable, as no income for the spous means more risk)
    Property Area (high in two tests)
    Married (mentioned in two tests)

After a test, these 4 gave better results than using all features.
Machine learning Model

As this is a binary problem (so yes or no in the status), I choose for binary models:

    Decision Tree
    K-nearest Neighbors

But we can cross check it with a logistic regression model here.

For the record, I left out Random Forrest, as this is a random decision tree model, so not the same each time you run the model

![image-21](https://github.com/hemangikinger/Predicting-Loan-Eligibility/blob/master/image-21.JPG)


Split the dataset in train and test

Before we are going to use the models choosen, we will first split the dataset in a train and test set. This because we want to test the performance of the model on the training set and to be able to check it's accuracy.

![image-22](https://github.com/hemangikinger/Predicting-Loan-Eligibility/blob/master/image-22.JPG)

Try and check the models

![image-23](https://github.com/hemangikinger/Predicting-Loan-Eligibility/blob/master/image-23.JPG)

K-Nearest Neighbors

![image-24](https://github.com/hemangikinger/Predicting-Loan-Eligibility/blob/master/image-24.JPG)

Decision Tree

![image-25](https://github.com/hemangikinger/Predicting-Loan-Eligibility/blob/master/image-25.JPG)

Logistic regression

![image-26](https://github.com/hemangikinger/Predicting-Loan-Eligibility/blob/master/image-26.JPG)


Conclusion:

We would need more data to make the models perform better.

For now, The decision tree has the highest accuracy and precision scores with the 4 most important features. Therefore this would be the model to use for the prediction on the status

