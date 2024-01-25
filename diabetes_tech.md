---
layout: default
---

## Sample of Technical Report: Gaussian Naive Bayes for Diabetes Prediction ###

__Introduction__
As reported by the World Health Organization (WHO), diabetes has become a global epidemic, with approximately 422 million adults living with the condition in 2014. It is predicted to be the seventh leading cause of death by 2030 (1). The dataset was sourced from the National Institute of Diabetes and Digestive and Kidney Diseases (2). It contained 768 observations from females at least 21 years old of Pima Indian heritage. Predictor variables included pregnancies, glucose, blood pressure, skin thickness, insulin, BMI, diabetes pedigree function, and age. The target variable was outcome. The exploratory analysis also includes a comparison between the Pima Indian population and the US population. 

__Exploratory Analysis__

In evaluating standard deviations (fig.1) and feature distributions (fig.2), insulin shows the greatest number of outliers, and a similar spread to glucose. Blood pressure, skin thickness and BMI have narrow spreads. This is to be anticipated as these values fall within a range biologically. Diabetes pedigree function has a very narrow spread since this measure maximizes at 2.42. Normalization may be necessary since this feature is smaller than other features within the dataset.

![image](https://github.com/cagoodri2/cagoodri2.github.io/assets/156851134/01cac2a1-ecad-4658-906e-476563b20819)

Figure 1. .describe() table of features

![image](https://github.com/cagoodri2/cagoodri2.github.io/assets/156851134/ed1ac969-838e-4c99-bf2a-0f5ba4de0f2c)

Figure 2. Seaborn Boxplot of Feature Distribution

_Correlation_  

The cross-correlation heatmap revealed relationships between features and the target variable, and within them (fig.3). Glucose was most highly correlated with the target variable outcome (0.49). This was followed by BMI (0.31), age (0.24), and pregnancies (0.22). Diabetes pedigree function and blood pressure showed the lowest correlations with outcome (0.17 & 0.116 respectively). Within the features, pregnancies were highly correlated with age (0.54), glucose was correlated with insulin (0.4), and blood pressure was correlated with age (0.33) and BMI (0.28). Finally, skin thickness was correlated with BMI (0.54) and insulin (0.24).   

![image](https://github.com/cagoodri2/cagoodri2.github.io/assets/156851134/3687ecec-e59b-4ada-b381-17e30237630d)

Figure 3. Seaborn Correlation Heatmap

The scatterplot of glucose and BMI shows potential groupings (Figure 4), with most negative diabetes outcome clustered to the lower left corner (reduced Glucose and BMI). The scatterplot suggests that lower BMI/lower glucose resulted in a negative diabetes outcome. High BMI and higher glucose generally resulted in a positive diabetes outcome.   

![image](https://github.com/cagoodri2/cagoodri2.github.io/assets/156851134/da485b5a-ac73-4db7-972e-01c23b0574fa)

Figure 4: Scatterplot of Glucose & BMI colored by outcome 
 
The scatterplot of insulin and age shows potential clusters again in the lower left-hand corner of the scatter - where age and insulin are lowest (figure 5). There are not clear linear divisions between the potential groupings. NA values within the dataset had to be replaced with the mean as the dataset was too small to remove the NA instances. However, in some distributions the effects of this become apparent with the strong linear stack of instances at the mean.   

![image](https://github.com/cagoodri2/cagoodri2.github.io/assets/156851134/f5175b1e-c5a0-4be6-8ef0-6b13e473bb71)

Figure 5: Scatterplot of Insulin & Age

![image](https://github.com/cagoodri2/cagoodri2.github.io/assets/156851134/28cc199a-4615-451d-a046-3961613fb59a)

Figure 6: Scatterplot of Skin Thickness and Diabetes Pedigree Function colored by outcome  

The scatterplot of skin thickness and diabetes pedigree function also has the most negative diabetes outcome clustered to the lower left corner (reduced skin thickness and diabetes pedigree function)(Figure 6, above). Again, there are not clear linear divisions between the potential groupings. Machine learning techniques were applied to make clear the distinctions within the measurements indicating a positive diabetes outcome for classification. 

_Pima Indian Population vs. National Population_

National values for many of the features contained in the Pima Indians diabetes dataset were difficult to find. The Behavioral Risk Factor Surveillance System (BRFSS), an annual telephone survey conducted by the CDC (Centers for Disease Control) evaluating healthy patterns nationally, did contain information related to BMI and diabetes diagnosis for 253,680 instances. Extensive preprocessing will not be performed on the dataset, as the intention is to compare the Pima Indian population with the national population for context. 

![image](https://github.com/cagoodri2/cagoodri2.github.io/assets/156851134/3c5f8c26-276c-4114-a1f6-b1cd32b1a9f5)

Figure 7. Seaborn Boxplot National Population vs. Pima Indian Population BMI 

The BMI within the national dataset has a lower mean with many more outliers compared with the Pima Indian dataset (fig. 7). The spread of the BMIs for the Pima Indian dataset appears wider and higher than the national. In comparing the percentage of diabetes diagnosis, the Pima Indian population had a 5% higher diabetes occurrence in comparison with the national proportion.

__Gaussian Naive Bayes__

Gaussian Naïve Bayes was next applied as features within the dataset are continuous. While Naïve Bayes offers limited tuning, variable smoothing was tuned with a np.logspace(0, -9, num=100) using GridSearchCV. A 10-fold cross validation was selected since the dataset is small. The initial model used the training and testing splits without additional changes. GridSearchCV selected a smoothing of approximately 1.23e-05. The initial model resulted in a training set accuracy of 0.76, a testing accuracy of 0.71 and a weighted average F1 score on the testing set of 0.70. The model did not appear to be overfitting. The classification report (below) shows the model performed with higher precision (0.80) and recall (0.85) on the non-diabetic classification (0) for the training set. On the testing set, precision decreased for the non-diabetic classification (0.77) and recall remained close to the training set (0.84).

To improve the model, the normalized training and testing data was attempted next. GridSearchCV and 10-fold cross validation was still applied. GridSearchCV selected a smoothing of approximately 0.12. The variable smoothing parameter increased notably. The normalized data resulted in the same accuracy on the training and testing sets as the base data (0.76, 0.71 respectively). The F1 was also identical at 0.71. Normalizing the data did not improve the model performance. Finally, highly correlated features were removed for model improvement. The following variables were removed due to their higher correlation: pregnancies (correlated with age at 0.54), insulin (correlated with glucose at 0.40), skin thickness (correlated with BMI at 0.54), and blood pressure (correlated with age at 0.33). Each of these variables had additional correlations at lower levels to the remaining variables. The contributions of each variable to the outcome variable were also considered prior to removal.   

Reducing the dataset did result in performance improvements. GridSearchCV and 10-fold cross validation was still applied. GridSearchCV selected a smoothing of approximately 3.51e-06. The accuracy for the training set was 0.78, the accuracy for the testing set was 0.75. A difference of 0.3 indicates the model is not overfitting. The weighted average F1 score of the reduced correlation model was 0.75, which is an improvement of 0.2. The precision and recall on both the positive and negative diabetes classification improved versus previous models.

This was the more parsimonious model since the features had been reduced. Parsimony, F1 and accuracy considered - this is the best of the Gaussian Naive Bayes models. The model was then fit on the full reduced dataset.  

__Conclusions & Future Work__

The Gaussian Naïve Bayes model with the reduced dataset had an accuracy of 0.75 on the testing set. The weighted average F1 score was 0.75 on the testing set. Precision on classification of non-diabetics was 0.80 and recall for non-diabetics was 0.86 (testing set). For positive diabetic classification, the precision was 0.62 and the recall was 0.52 on the testing set – lower than desirable. The Gaussian NB with the reduced dataset was computationally easy and eager but did not have a high recall/precision with the positive diabetic outcome. Future work should explore alternative models to improve predictions. 

1) World Health Organization. (2016). Global report on diabetes. Retrieved from https://www.who.int/publications/i/item/9789241565257  
   
2) National Dataset accessed via Kaggle.com: 	https://www.kaggle.com/datasets/alexteboul/diabetes-health-indicators-dataset  
Pima Indian Dataset accessed via Kaggle.com:  https://www.kaggle.com/datasets/uciml/pima-indians-diabetes-database  

[Sample Python Code](./diabetes_python.html)

[Executive Summary](./ml_diabetes.html)

[All Projects](./)
