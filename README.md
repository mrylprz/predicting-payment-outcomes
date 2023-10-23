![cover](https://github.com/mrylprz/predicting-payment-outcomes/blob/main/cover.png)
# Invoice Payment Outcome Prediction

## Introduction

This project focuses on predicting invoice payment outcomes using supervised machine learning. Inefficient accounts receivable (AR) management can lead to financial and efficiency problems. This project aims to optimize AR management through AI, specifically by determining the most suitable supervised ML technique for this application.

## Problem Statement
AR management teams often struggle with invoice management and payment collection. Relying on manual methods and past experience for client reminders can lead to financial losses and operational inefficiencies. This could necessitate increased resources and result in missed collections, excessive debt, worsened customer relations, and harm to the company's reputation. This project focuses on implementing supervised machine learning techniques for predicting payment outcomes, enabling data-driven and proactive account management to enhance efficiency to address these issues.

## Objectives

- Build a prediction model using supervised ML for invoice payment outcomes.
- Determine the best ML technique for this application.
- Optimize AR management, improve customer relations, and maximize profit.

## Repository Structure
This repository is organized as follows:
*	Data: Contains the dataset used in this analysis.
*	Graphs
* Tables: Summary of model characteristics, and results
* Orange File (.ows file) 
*	References: List of Studies and Articles used as references
  
## Benefits of AI and ML

AI and ML bring automation and analytics to AR management. They streamline processes, automate tasks, and provide insights for proactive management. Predictive analytics aids in early intervention for delayed payments.

## Methodology

This is a supervised multiclass classification problem, predicting invoice payment outcomes based on historical data. The dataset is divided into four age buckets: **(0) on time**, **(1) 1-14 days**, **(2) 15-30 days**, and **(3) more than 30 days**. A sample dataset is utilized for analysis.
The following ML Techniques were utilised and compared based on different accuracy metrics: **Random Forest (RF)**, **Neural Network (NN)**, **AdaBoost (AB)**, **Gradient Boosting (GB)**, and **Naïve Bayes (NB)**.

## The Dataset

The dataset, [sample AR dataset](https://www.kaggle.com/datasets/hhenry/finance-factoring-ibm-late-payment-histories), is sourced from Kaggle, consisting of 2466 invoices for 100 distinct customers. Data preparation includes cleaning, transformation, and attribute generation.

## Data Preparation

Tool Used: Microsoft Excel
* Data cleaning to check for null and duplicate values, invalid entries and formatting issues; irrelevant columns were dropped.
* Data Transformation and Generation of Attributes:
  * Invoice - Level
    * **Gap between current and previous invoice due date**: difference between due dates of two succeeding invoices
    * **Age Buckets**: based on the minimum and maximum values of the invoice ages 
  * Client - Level
    *	**Average Paid Amount, Average Paid Amount (Late), Average Days to Settle and Average Days Late**: The average of all datapoints’ raw attributes are computed and mapped to each datapoint
    * **Ratio of the Total Amount of Paid Invoices belonging to an Age Bucket by the Total Amount of Paid Invoices** and **Ratio of the Number of Paid Invoices belonging to an Age Bucket by the Total Number of Paid Invoices**: These ratios are computed per client given the number of invoices they have that fall under specific age buckets

##### Distribution of Training Data
<p align="center">
   <img src="https://github.com/mrylprz/predicting-payment-outcomes/blob/main/Graphs/Figure%201%20-%20Distribution%20of%20Training%20Data.png" width="800">
</p>

## List of Features
<p align="center">
   <img src="https://github.com/mrylprz/predicting-payment-outcomes/blob/main/Tables/List%20of%20Features.png" width="800">
</p>

Target Variable: **Age Bucket**

## Model Evaluation
Five (5) different ML techniques are used in this report. Each model is assessed on accuracy (using metrics) and usability (using confusion matrices). The metrics for comparison of accuracy of the different models are listed in the table below:

*Summary of Accuracy Metrics*
<p align="center">
   <img src="https://github.com/mrylprz/predicting-payment-outcomes/blob/main/Tables/Summary%20of%20Accuracy%20Metrics.png" width="500">
</p>

The following supervised ML techniques were tested in predicting payment outcomes:

* **Random Forest (RF)**
  
  RF combines the output of several decision trees (independent to one another) to obtain more accurate results (compared to decision trees). It is known for its ease of use, not easily overfitting, and flexibility in handling classification and regression problems (IBM 2022c). 
Trees: 30

* **Neural Network (NN)**
  
  NNs leverage labelled datasets to train algorithms for classification problems. NNs mimic how brains learn, using artificial neurons or nodes grouped in layers that signal and connect to one another (IBM 2022b). They rely on training data (supervised) and become more accurate over time.
Neurons, layers: 100 neurons, 1 layer

  **NOTE** Researcher found negligible improvement upon increasing neurons to 200 or increasing layers to 2 (with 100 neurons per layer)

* **AdaBoost (AB)**
  
  AB is an ensemble method deploying trees in series. However, in AB, trees (called stumps) are constructed dependent on the previous tree’s mistake. It is a boosting method combining weak classifiers in series to build a stronger classifier (GeeksforGeeks 2022). The disadvantage of this method is it is easily overfitted.
Estimators: 50	Learning rate: 1

	
* **Gradient Boosting (GB)**
  
  GB is another iterative supervised ML technique combining weak learners into a one strong classifier. Like AdaBoost, each learner corrects the previous learner’s error. However, it uses the residual errors of predecessor as labels to train each predictor (GeeksforGeeks 2020).
Number of estimators: 100
Learning rate: 0.1

* **Naïve Bayes (NB)**

  NB is a simple, yet powerful classification algorithm based on the Bayes Theorem which assumes predictors are independent of one another. The NB classifier assumes a feature present in a class is not related to other features. The algorithm is applicable to binary and multi-class classification problems (IBM, 2022a).

The table below summarises the characteristics of the supervised ML techniques utilised in this report which are of value to the business (Data School 2015). 

*Comparison of Models*
<p align="center">
   <img src="https://github.com/mrylprz/predicting-payment-outcomes/blob/main/Tables/Comparison%20of%20Models.png" width="800">
</p>

**Tool Used: Orange**

[Orange](https://orangedatamining.com/) is used to implement the models for multiclass classification. It utilises visual programming (widgets) for building data analysis workflows. Figure below shows the workflow for analysing the AR dataset using the different ML techniques. 

*Data Analysis workflow in Orange*

<p align="center">
   <img src="https://github.com/mrylprz/predicting-payment-outcomes/blob/main/Graphs/Data%20Analysis%20Workflow%20in%20Orange.png" width="1000">
</p>

## Summary of Results

*Accuracy Metrics Results (Overall)*
<p align="center">
   <img src="https://github.com/mrylprz/predicting-payment-outcomes/blob/main/Tables/Accuracy%20Metrics%20(Overall).png" width="1000">
</p>

*Accuracy Metrics Results (per Possible Outcome)*
<p align="center">
   <img src="https://github.com/mrylprz/predicting-payment-outcomes/blob/main/Tables/Accuracy%20Metrics%20(Per%20Possible%20Outcome).png" width="1000">
</p>

To ensure that the models are applicable for practical use, it is important the model can precisely classify outcomes and meet the objectives of building the model, helping the AR team on predicting whether an invoice will be paid on time or if not, how late it will likely be paid. Table 5 summarises the resulting confusion matrices.

*Confusion Matrices*
<p align="center">
   <img src="https://github.com/mrylprz/predicting-payment-outcomes/blob/main/Tables/Confusion%20Matrices.png" width="1000">
</p>

Overall, the best model considering accuracy and usability is the Gradient Boosting technique. It is a good classifier especially for categorising invoices whether they will be paid on-time or not. Although it does not precisely predict age buckets of 2 and 3, it still categorises them as late invoices (age bucket 1) which can be utilised in prescribing the appropriate (proactive) actions in AR management. 

# Conclusion

The proposed methodology is the first step in achieving full automation in AR, the lifeblood of companies. By leveraging the capabilities of predictive analytics, predicting payment outcomes especially delay in payments, puts companies on top of their processes. By identifying which clients and invoices to prioritise, the proposed method can help the company save valuable time and resources, and generate more value. Out of the models tested, GB gives 80% accuracy and precision on predicting payment outcomes. Therefore, it is a good starting point for deployment in actual scenarios to gain insights on future trends.

# Recommendations

The method used in this report is a simple yet effective way to utilise ML in the business scenario. Listed below are recommendations to improve the proposed method or other areas of ML to explore: 

* Use of balanced data to improve accuracy of predicting outcomes 2 and 3
* Use of sophisticated tools like Python or R to fine-tune parameters of the GB algorithm
* After starting with simpler models, the next step is to transition into more complex models like XGBoost (eXtreme GB)
* Combining different machine learning models (cascading) to achieve more accurate results aiming for full automation

