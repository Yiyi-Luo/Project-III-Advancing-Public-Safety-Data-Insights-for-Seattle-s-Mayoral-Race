### **Advancing Public Safety: Data Insights for Seattle's Mayoral Race**

![seattle-washington-cityscape-13-aged-pixel](https://github.com/Yiyi-Luo/Advancing-Public-Safety-Data-Insights-for-Seattle-s-Mayoral-Race/assets/149438809/bc30d8c6-7058-4a9d-a3ae-85c05ddb9ddd)


## **Overview and Business Understanding**

Welcome to Civic Insights Consulting, a pioneering firm specialized in empowering political campaigns with data-driven strategies.This year, we're thrilled to collaborate with a progressive mayoral candidate in Seattle. Leveraging our state-of-the-art data analytics platform and deep understanding of local issues, we're committed to sculpting a campaign that resonates with the heart of Seattle. Building upon our firm's commitment to enhancing political campaigns through data-driven insights, Civic Insights Consulting is proud to embark on an innovative project that aligns perfectly with the needs of our mayoral candidate in Seattle. This initiative involves developing a sophisticated classifier to predict arrest outcomes following Terry Stops, utilizing variables such as weapon presence, call times, and other critical factors.

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

<img width="752" alt="Screenshot 2024-01-02 at 9 11 36 PM" src="https://github.com/Yiyi-Luo/Advancing-Public-Safety-Data-Insights-for-Seattle-s-Mayoral-Race/assets/149438809/d0d8129d-622e-4b4c-88a3-534f9bc0086d">


## **Evaluation**

**1. Cross-Validation Technique:** Utilized cross-validation to assess the robustness of the predictive model, ensuring generalizability across different data samples;

**2. Accuracy Assessment:** Employed the score() function, also known as the accuracy score, as a primary metric to measure the overall correctness of the model's predictions;

**3. Detailed Performance Metrics:** Analyzed the confusion matrix to visualize true positives, true negatives, false positives, and false negatives, providing insight into the type of errors made by the model

## **Our Best Model: Random Forest**

**Overall accuracy** of **77%** on the test dataset

**Cross-validation scores** ranged from **86.1%** to **90.4%**, with a mean score of **88.3%**

**Recall rates** of **83%** and **61%** for different outcomes, demonstrating the model's ability to correctly identify true instances

**F1-scores** of **84%** and **60%**, balancing precision and recall, reflecting the model's robustness in prediction accuracy

<img width="854" alt="Screenshot 2024-01-02 at 4 07 19 PM" src="https://github.com/Yiyi-Luo/Advancing-Public-Safety-Data-Insights-for-Seattle-s-Mayoral-Race/assets/149438809/dbc57dd9-8e09-471c-8bfe-613080223996">



## **Limitations**

**Imbalanced Data**: The class imbalance in our dataset (18701 instances of class '0' vs. 7416 of class '1') is significant and can inherently bias models towards the majority class ('0'). Such imbalances are typical in law enforcement and public safety datasets due to the nature of the events being recorded. 

**Complexity of Predictive Factors**: The factors that contribute to whether an arrest is made after a Terry Stop are multifaceted and may not be entirely captured by the dataset. Variables like the type of call, officer characteristics, subject demographics, and perceived threat level are complex and have nuanced interactions. 

**Inherent Limitations**: The ceiling for model performance might be inherently limited by the complexity and quality of the data. Real-world data, especially in sensitive areas like law enforcement, often contains noise, biases, and unobserved factors that can impact predictive accuracy. 

**Class "1" Challenges:** Achieving high accuracy for the minority class ('1') is often more challenging due to fewer instances from which the model can learn. The characteristics of instances leading to an arrest might be more varied or less distinctly patterned than those that do not, making it harder for models to accurately predict. 

**Performance vs. Cost:** Sometimes, the pursuit of higher accuracy, especially in more challenging classes, can lead to diminishing returns. Consider the cost-benefit ratio of further improvements. Early improvements to our model (like basic preprocessing, feature engineering, or trying different algorithms) might have led to significant increases in accuracy. However, after a certain point, we found that even substantial efforts in tuning, trying complex models, or advanced preprocessing techniques only lead to very marginal improvements in accuracy.

## **Conclusion**

**1. Arrest Rates Over the Years:** There has been a fluctuation in arrest rates over the years, with a notable peak in 2018 and a sharp decline in recent years, particularly in 2021. This decline could be due to various external factors such as changes in policing policy, societal changes, or other external events affecting law enforcement practices.

![Arrest Rates by Year](https://github.com/Yiyi-Luo/Advancing-Public-Safety-Data-Insights-for-Seattle-s-Mayoral-Race/assets/149438809/f08500ee-32b6-4ba9-b88f-4554fe624e0a)


**2. Crime Trends Over the Years for Top 8 Crime Types:** The multi-year trend across various crime types suggests that certain categories of crime have seen fluctuations over the given period. The spike in "Person With Weapon" incidents, for example, might reflect an actual increase in such incidents or a heightened law enforcement focus on these types of calls. Similarly, "Drug Related Incidents" peak at certain intervals, which could correlate with enforcement campaigns or changes in societal drug use patterns.

![Crime Trends Over the Years for Top 8 Crime Type](https://github.com/Yiyi-Luo/Advancing-Public-Safety-Data-Insights-for-Seattle-s-Mayoral-Race/assets/149438809/7478e66c-633c-469a-b9d9-de74314e7df1)

**3. Subject Race:** Black: The PDP for Subject_Race_Black indicates that when the subject is black, there is a higher likelihood of an arrest being predicted by the model. White: Conversely, the PDP for Subject_Race_White shows a decrease in the likelihood of an arrest, suggesting that the model predicts a lower likelihood of arrest for white subjects.

![Subject Race Black-Partial Dependence Plot](https://github.com/Yiyi-Luo/Advancing-Public-Safety-Data-Insights-for-Seattle-s-Mayoral-Race/assets/149438809/1b6457cd-c90f-4c52-92c7-6f533ead544b)
![Subject Race White-Partial Dependence Plot](https://github.com/Yiyi-Luo/Advancing-Public-Safety-Data-Insights-for-Seattle-s-Mayoral-Race/assets/149438809/d75c8e4f-4b4b-4d58-a768-c667ee02c761)


**4. Officer Gender:** The sharp drop in partial dependence at the value "1" on the x-axis suggests that when the officer is female, the model predicts a lower likelihood of an arrest compared to when the officer is male (value "0" on the x-axis). This means that, according to the model's understanding, the gender of the officer is an influential factor, with female officers being less likely to result in an arrest through a Terry Stop, based on the model's predictions.
![Officer Gender-Partial Dependence Plot](https://github.com/Yiyi-Luo/Advancing-Public-Safety-Data-Insights-for-Seattle-s-Mayoral-Race/assets/149438809/46d56ff8-c7b4-4108-b928-cfb613bdf3b0)


**5: Officer Age:** The PDP suggests that the likelihood of arrest decreases as the officer's age increases. This might imply that younger officers are associated with a higher likelihood of making an arrest.
![Officer Age-Partial Dependence Plot](https://github.com/Yiyi-Luo/Advancing-Public-Safety-Data-Insights-for-Seattle-s-Mayoral-Race/assets/149438809/fbc5f28f-52a7-4119-a14c-833dba67ba7b)


## **Recommendations:** 

**1. Focused Training and Resources:**
Develop targeted training programs for officers to address the trends observed in "Person With Weapon" and "Drug Related Incidents." 

**2. Bias and Fairness Audit:**
Conduct a thorough audit of arrest practices to investigate any potential biases indicated by the higher likelihood of arrest for black subjects and the lower likelihood for white subjects. 

**3. Mentorship and Experience Sharing:**
Pair younger officers with more experienced ones to address the higher likelihood of arrests among younger officers.

**4. Diversity and Inclusion Programs:**
Strengthen diversity and inclusion programs within the police force. Ensure that such programs address the disparities in arrest likelihood as indicated by the model’s predictions regarding officer gender. 





