### **Advancing Public Safety: Data Insights for Seattle's Mayoral Race**
**Yiyi Luo**

![seattle-washington-cityscape-13-aged-pixel](https://github.com/Yiyi-Luo/Advancing-Public-Safety-Data-Insights-for-Seattle-s-Mayoral-Race/assets/149438809/bc30d8c6-7058-4a9d-a3ae-85c05ddb9ddd)


## **Overview and Business Understanding**

Welcome to Civic Insights Consulting, a pioneering firm specialized in empowering political campaigns with data-driven strategies. This year, we're thrilled to collaborate with a progressive mayoral candidate in Seattle. Our new venture is designed to create a sophisticated classifier aimed at predicting arrest outcomes for Terry Stops. By analyzing critical variables, we aim to uncover underlying patterns that could reshape our client's approach to public safety and justice. Our analysis will provide a clear picture of the current state of law enforcement interactions in Seattle, offering invaluable insights into areas needing reform.


## **Data Understanding and Preparation**

1. **Data Selection and Cleaning**: Carefully chosen key features for analysis, including 'Year', 'Month', 'Time of Day', 'Initial and Final Call Types', 'Officer and Subject Demographics', 'Weapon Type', and 'Stop Resolution'; Executed thorough data cleaning and organization to ensure accuracy and relevance

2. **Feature Engineering and Preprocessing**: Applied OneHotEncoding and OrdinalCoding to transform categorical data for analytical compatibility; Utilized 'dropna' technique to maintain data integrity and reliability

3. **Addressing Data Imbalance**: Recognized and addressed the imbalance in the 'Stop Resolution' target variable; Employed oversampling, class weights, and SMOTE strategies to achieve a more balanced dataset for unbiased insights

4. **Preparation for Predictive Modeling**: Transformed and structured data to feed into our sophisticated classifier; Ensured data preparation aligns with our objective of delivering actionable and equitable public safety solutions

## **Modeling**

Modeling in machine learning involves experimenting with a variety of algorithms to identify the one that performs best for a given dataset. In this project, we explored a comprehensive range of models, each with its unique strengths and applications. 

Starting with a **Baseline Classifier**, which serves as a simple comparison point; 

We progressed through **Logistic Regression**, known for its effectiveness in binary classification problems;

**Decision Trees** and **Random Forests** were employed for their ability to handle non-linear data, with Random Forest providing the added advantage of reducing overfitting by averaging multiple trees;

**Gradient Boosting Machines (GBM)** and **AdaBoost**, both boosting methods, incrementally improve weak learners, making them robust for complex datasets;

**Support Vector Machine (SVM) with different kernels (rbf, linear, polynomial)** offers versatility in dealing with varied data structures;

**The k-Nearest Neighbors (k-NN)** algorithm was also used, for its simplicity and effectiveness in classification tasks;

**Ensemble Methods**, which combine predictions from multiple models, served to enhance the overall predictive power;

To fine-tune these models, we utilized **GridsearchCV** and **RandomizedSearchCV** for hyperparameter optimization, ensuring the best configuration for each model. Additionally, the use of **feature importances** helped in understanding which features most significantly impact model predictions. Finally, **Partial Dependence Plots** were employed as an interpretability tool, providing insights into the relationship between features and the target variable. This comprehensive approach not only enhances the predictive accuracy but also ensures a thorough understanding of the models' behavior and their decision-making process.

<img width="651" alt="Cross Validation Scores" src="https://github.com/Yiyi-Luo/Advancing-Public-Safety-Data-Insights-for-Seattle-s-Mayoral-Race/assets/149438809/5637ce46-23c3-45dc-b41c-8e8e736e3e3a">

## **Our Best Model: Random Forest**

**Overall accuracy** of **77%** on the test dataset

**Cross-validation scores** ranged from **86.1%** to **90.4%**, with a mean score of **88.3%**

**Recall rates** of **83%** and **61%** for different outcomes, demonstrating the model's ability to correctly identify true instances

**F1-scores** of **84%** and **60%**, balancing precision and recall, reflecting the model's robustness in prediction accuracy

<img width="854" alt="Screenshot 2024-01-02 at 4 07 19 PM" src="https://github.com/Yiyi-Luo/Advancing-Public-Safety-Data-Insights-for-Seattle-s-Mayoral-Race/assets/149438809/dbc57dd9-8e09-471c-8bfe-613080223996">

The Random Forest model shows an improvement over the baseline, with an accuracy of approximately 76.7% on the test set. The precision, recall, and f1-score for class 1 (the minority class) have improved significantly compared to the dummy classifier, which is a positive sign. However, the high training accuracy (99.7%) compared to the test accuracy indicates that the model may be overfitting to the training data. This overfitting is also hinted at by the cross-validation scores, which, while good (mean score around 88.3%), are still noticeably lower than the training score.

**True Positives (TP)** is critical because it represents the cases where the model correctly predicts an arrest. Given that arrests are the minority class and likely the primary focus of your analysis, maximizing TP is crucial.

**False Negatives (FN)** is equally important because it represents the cases where the model failed to predict an arrest when there actually was one. A high FN means missing out on correctly identifying potential arrest situations, which is a significant error.

Our primary interest is in **accurately predicting arrests (class "1")**, thus we will focus more on the metrics specific to this class, such as the **recall and precision for class "1"**. It's particularly important in imbalanced datasets to see how well the model is identifying the minority class.

**Precision (Positive Predictive Value)** means the proportion of stops that were predicted as arrests and were actually arrests. High precision means that when the model predicts an arrest, it's likely to be correct.

**Recall (Sensitivity)** is extremely important in imbalanced datasets. It measures the proportion of actual arrests that were correctly identified by the model. High recall means the model is good at catching most of the actual arrests.

**F1-Score**: Since it's the harmonic mean of precision and recall, it's a useful single metric to look at when we need a balance between precision and recall. It's particularly useful when the dataset is imbalanced.

## **Top 15 Important Features in Random Forest Model**
<img width="999" alt="Top 15 Important Features in Random Forest Model" src="https://github.com/Yiyi-Luo/Advancing-Public-Safety-Data-Insights-for-Seattle-s-Mayoral-Race/assets/149438809/f29f705a-c8dd-4a0a-be4c-1ad26966c993">


## **Limitations**

**Imbalanced Data**: The class imbalance in our dataset (18701 instances of class '0' vs. 7416 of class '1') is significant and can inherently bias models towards the majority class ('0'). Such imbalances are typical in law enforcement and public safety datasets due to the nature of the events being recorded. 

**Complexity of Predictive Factors**: The factors that contribute to whether an arrest is made after a Terry Stop are multifaceted and may not be entirely captured by the dataset. Variables like the type of call, officer characteristics, subject demographics, and perceived threat level are complex and have nuanced interactions. 

**Performance vs. Cost:** Sometimes, the pursuit of higher accuracy, especially in more challenging classes, can lead to diminishing returns. Consider the cost-benefit ratio of further improvements. Early improvements to our model (like basic preprocessing, feature engineering, or trying different algorithms) might have led to significant increases in accuracy. However, after a certain point, we found that even substantial efforts in tuning, trying complex models, or advanced preprocessing techniques only lead to very marginal improvements in accuracy.

## **Conclusion**

**1. Arrest Rates Over the Years:** There has been a fluctuation in arrest rates over the years, with a notable peak in 2018 and a sharp decline in recent years, particularly in 2021. This decline could be due to various external factors such as changes in policing policy, societal changes, or other external events affecting law enforcement practices.

![Arrest Rates by Year](https://github.com/Yiyi-Luo/Advancing-Public-Safety-Data-Insights-for-Seattle-s-Mayoral-Race/assets/149438809/f08500ee-32b6-4ba9-b88f-4554fe624e0a)


**2. Crime Trends Over the Years for Top 8 Crime Types:** By 2023, the most frequent incident type has shifted to "Suspicious Circum/Person/Vehicle", indicating an increase in reports of suspicious activities or individuals. It's worth noting that while "Prowler/Trespass/Burglary" incidents have decreased since their peak, they still represent a significant portion of the crime incidents.

![Crime Trends Over the Years for Top 8 Crime Type](https://github.com/Yiyi-Luo/Advancing-Public-Safety-Data-Insights-for-Seattle-s-Mayoral-Race/assets/149438809/7478e66c-633c-469a-b9d9-de74314e7df1)

**3. Subject Race:** Black: The PDP for Subject_Race_Black indicates that when the subject is black, there is a higher likelihood of an arrest being predicted by the model. White: Conversely, the PDP for Subject_Race_White shows a decrease in the likelihood of an arrest, suggesting that the model predicts a lower likelihood of arrest for white subjects.

<img width="1010" alt="Screenshot 2024-01-04 at 12 02 44 PM" src="https://github.com/Yiyi-Luo/Advancing-Public-Safety-Data-Insights-for-Seattle-s-Mayoral-Race/assets/149438809/dc915541-261a-4f9e-aea3-2f459c0e4bf1">

**4. Officer Gender:** The sharp drop in partial dependence at the value "1" on the x-axis suggests that when the officer is female, the model predicts a lower likelihood of an arrest compared to when the officer is male (value "0" on the x-axis). This means that, according to the model's understanding, the gender of the officer is an influential factor, with female officers being less likely to result in an arrest through a Terry Stop, based on the model's predictions.

<img width="888" alt="Screenshot 2024-01-04 at 12 02 32 PM" src="https://github.com/Yiyi-Luo/Advancing-Public-Safety-Data-Insights-for-Seattle-s-Mayoral-Race/assets/149438809/37edff08-6671-49e0-8f08-82eb03f22879">

**5: Officer Age:** The PDP suggests that the likelihood of arrest decreases as the officer's age increases. This might imply that younger officers are associated with a higher likelihood of making an arrest.
![Officer Age-Partial Dependence Plot](https://github.com/Yiyi-Luo/Advancing-Public-Safety-Data-Insights-for-Seattle-s-Mayoral-Race/assets/149438809/fbc5f28f-52a7-4119-a14c-833dba67ba7b)


## **Recommendations:** 

**1. Advocate for the implementation of wide-reaching public education campaigns** under the mayoral leadership. These campaigns will focus on educating Seattle's citizens about recognizing and appropriately reporting suspicious behavior. 

**2. Bias and Fairness Audit:**
Conduct a thorough audit of arrest practices to investigate any potential biases indicated by the higher likelihood of arrest for black subjects and the lower likelihood for white subjects. This step resonates with our candidate's dedication to ensuring fairness and transparency in policing, thereby reinforcing public trust in law enforcement agencies.

**3. Mentorship and Experience Sharing:**
Pair younger officers with more experienced ones to address the higher likelihood of arrests among younger officers. This approach supports our candidate's vision for a more balanced and experienced police force, contributing to more measured and equitable law enforcement practices in Seattle.

## **Next Steps**

1. Partner with independent auditors and experts in law enforcement practices to ensure an unbiased and thorough examination;

2. Conducting workshops and interactive sessions that specifically focus on reducing disparities in arrest likelihood, as well as ensuring representation and inclusivity in the force





