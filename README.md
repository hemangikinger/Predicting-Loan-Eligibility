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
