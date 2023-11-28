# Multiclass Classification of Imbalanced Wine Quality Data that Maximize Economic Value for Model Users
Lingling Zhang

## Abstract
This research classifies white wines into multiple quality categories with the objective to maximize the economic value for wineries and merchandisers while using machine learning technologies on extremely imbalanced dataset. Wines with top qualities and wines with poor qualities are extremely rare in the dataset. However, to apply machine learning algorithms, a minimum amount of data samples are required. Therefore, in this research, a minimal regrouping of the categories was conducted (regrouped from 7 quality classes into 5 quality classes) while the original ranking of the wine quality categories was maximizedly preserved. SMOTE oversampling techniques were then used. Multiple machine learning algorithms were experimented and the Extra Tree Classifier model was found to be the best model. It not only has good performance among all the wine quality group classes (ROC 0.86) but also has good performance in rare classes (quality group 8 and 9 has an ROC of 0.93 and quality group 3 and 4 have an ROC of 0.87). Being able to detect and price the top-rating wines could bring great economic value to wineries and merchandisers and being able to prevent poor-quality wines from mixing with other wines is essential for wineries and merchandisers to preserve a good brand image.  Imbalanced data is common in the real world and correctly predicting the rare classes are usually more important for model users. The solution design in this research is recommended as a practical solution for imbalanced data. It can be applied on other data and used in other industries.

## Video
An introduction of the project can be found here.

## Project Design
1.  Exploratory Data Analysis was conducted. The imbalance nature of data was detected. Recategorized wines from 7 quality classes in to 5 quality group classes - wines in quality classes 3 and 4 were grouped into “quality group 4” and wines in quality classes 8 and 9 were grouped into “quality group 8”.
2. Model performance using data with and without regrouping and oversampling was experimented. ROC AUC was used as the evaluation matrix for model selection, with the aim of measuring how well the model is classifying each class. For the best model in each experiment, the model performance metrics (especially ROC and Recall) on each wine quality group were examined and compared.

Altogether four experiments were conducted:
   
- Experiment 1: without regrouping
- Experiment 2: with regrouping but without oversampling using SMOTE
- Experiment 3: with regrouping and oversampling using SMOTE
- Experiment 4: with regrouping and oversampling using SMOTE, use Optuna[4] for model tuning.

## Exploratory Data Analysis
Dataset used in the project is the white wine data available at the UC Irvine Machine Learning Repository [https://archive.ics.uci.edu/dataset/186/wine+quality]. There are 4,898 white wine data examples and 11 physicochemical features of the wine. The Target variable is the quality of the wine, which as evaluated by a minimum of three sensory assessors, which graded the wine in a scale that ranges from 0 (very bad) to 10 (excellent). The final sensory score is given by the median of these evaluations.[3]

### Imbalance of data
It is found that there are 7 quality classes for the white wines. The dataset is not balanced - wines with quality 3 and quality 9 are extremely rare. Wines with quality 4 and quality 8 are also not a lot. See Table 1.

Table 1. The proportion of each category in original data

<img width="189" alt="image" src="https://github.com/littlebeanbean7/wine_quality_classification/assets/19282931/53385ea1-b945-4ba8-9db2-9b43a074247c">

Therefore I regrouped wines in quality classes 3 and 4 into “quality group 4” and wines in quality classes 8 and 9 into “ quality group 8”. After the recategorizing, quality groups “4” and “8” have over 180 samples each, which is worth to try modelling. Wines in quality classes 5, 6, and 7 remain as 3 separate classes (see Table 2). This regrouping solution did not simply change the multi-class classification problem into a binary classification or even regroup rare classes (wine in quality 3, 4, 8, and 9) into one group like [1] did. In contrast, this regrouping strategy preserved the most categories as well as the ranking sequence of the wines.

Table 2. The proportion of each category after regrouping

<img width="224" alt="image" src="https://github.com/littlebeanbean7/wine_quality_classification/assets/19282931/324bd782-1baf-4f78-9dd8-4f1781eb0e44">


### Features

There are 11 physicochemical features of the wines. All of them are numerical. No missing values are indentified. All features are used for modelling as the modelling experiments show that all features contribute to over 5% feature importance, this demostrated all of the features are important for the model to make prediction. Previous study using PCA to do feature selection also proved that dropping feature would make the model performance drop. [2]

Table 3. Statistics of all the columns. The last column "quality" is the Target variable. All other columns are features

<img width="770" alt="image" src="https://github.com/littlebeanbean7/wine_quality_classification/assets/19282931/bdaffad4-811f-4aba-8150-2a284602cc2e">

I have plotted the distribution of each feature per category. Figure 1 shows the distribution of one feature - alcohol per wine qualtiy category as an example. For more plots please reference the notebook.

Figure 1. Alcohol feature's distribution per wine qualtiy category

<img width="832" alt="image" src="https://github.com/littlebeanbean7/wine_quality_classification/assets/19282931/8ae186aa-99b8-4a54-a668-d20c55d93329">

## Experiment setup

Four experiments were conducted to compare whether certain procedure are improve model performance. See table 4 for details.

Table 4. The setup of the four experiments

<img width="472" alt="image" src="https://github.com/littlebeanbean7/wine_quality_classification/assets/19282931/ad2348b1-18db-4c60-b696-e7cfd5b2f8b5">

## Result
This session shows the modeling result of the 4 experiments. For all the experiments, ROC-AUC are used as the matrix for model selection.

### Experiment 1: Without regrouping

In Experiment 1, I did not regroup the rare categories. Experiment 1's model comparision result can be found in Table 5. The Extra Trees Classifer model was found to get the highest ROC-AUC.

Table 5. Model comparision result of Experiment 1

<img width="816" alt="image" src="https://github.com/littlebeanbean7/wine_quality_classification/assets/19282931/abffe66d-a763-4c1e-b40f-bee065bf4590">

Experiment 1 best model's performance by categories can be found in Table 6. It can be found that the model is not good at predicting wines with quality 3 and 4 and wines with quality 8 and 9 categories, althougth the model performance is good for classes that have more data samples.

Table 6. Best model's performance by categories of Experiment 1

<img width="490" alt="image" src="https://github.com/littlebeanbean7/wine_quality_classification/assets/19282931/9057edb7-8afd-48a1-948a-b4b052491a88">


### Experiment 2: With regrouping

In Experiment 2, I regrouped the wine with quality 3 and 4 into one group and wine with 8 and 9 into one group. Experiment 2's model comparision result can be found in Table 7. It can be found that Extra Trees Classifer model gets the highest ROC-AUC again.

Table 7. Model comparision result of Experiment 2

<img width="816" alt="image" src="https://github.com/littlebeanbean7/wine_quality_classification/assets/19282931/2edab552-f0f9-4626-bcc0-4d2563a5a9a8">

### Experiment 3: With regrouping and oversampling with SMOTE

In Experiment 3, besides regroup the rare clases, I also upsampled the rare classes. Experiment 3's model comparision result can be found in Table 8. It can be found that Extra Trees Classifer model still the best ROC-AUC.

Table 8. Model comparision result of Experiment 3

<img width="816" alt="image" src="https://github.com/littlebeanbean7/wine_quality_classification/assets/19282931/4a9ceca3-bbd5-4409-a5d0-cf9f502a8936">

### Experiment 4: With regrouping and oversampling with SMOTE, use Optuna to fine tune the best model from Experiment 3

In Experiment 4, besides regroup the rare clases and oversampling, I used Optuna to fine tune the Extra Tree Classifier model - best model found in Experiment 3. Results showed that the model performance is comparable to Experiment 3, see Table 9.

Table 9 explains the difference treatment among Experiment 2, 3, and 4 by categories, adn the best model's performance in each experiments. From the result we can found that regrouping and oversampling techniques such as SMOTE has boosted the model's performance in the predictioon of rare categories - with with quality 3, 4, 8, and 9 categories, while the overall model performance remains good.

Table 9. The best model's performance in Experiment 2, 3, and 4 by categories

<img width="471" alt="image" src="https://github.com/littlebeanbean7/wine_quality_classification/assets/19282931/72827b47-4b75-4363-9035-e651b2da0909">

#### Model analyses for final model
Due to Experiment 3 and 4 are produce the same result. The boths can be used as the final model. Here we consider Experiment 4 as the final model. Figure 2 to Figure 5 shows that the model is good at identifing rare good and poor wine quality groups. Note that in the figures:

- 0 stand for wine qualty group 3 and 4; 
- 1 stands for wine quality 5;
- 2 stands for wine quality 6;
- 3 stands for wine quality 7;
- 4 stands for wine quality 8 and 9;
  
Figure 6 shows the feature importance of each features, from which we can see that alcohol is the most important feature, accounting for 30% of feature importance. All other features have a feature importance of over 5%, meaning all of them are useful in predicting the wine's quality. Also considering that there are only 11 features all together, it is decided that there is no need to drop any feature.

  
Figure 2. Plot of final model's ROC AUC performance per category

<img width="705" alt="image" src="https://github.com/littlebeanbean7/wine_quality_classification/assets/19282931/671e505a-3765-427e-896f-e6e5a30cf00b">

Figure 3. Plot of final model's confusion matrix per category

<img width="793" alt="image" src="https://github.com/littlebeanbean7/wine_quality_classification/assets/19282931/47155522-69ef-4f7f-b699-1391b2d4412c">

Figure 4. Plot of final model's clasification report per category

<img width="732" alt="image" src="https://github.com/littlebeanbean7/wine_quality_classification/assets/19282931/0af641a5-cdc6-43f9-b8fa-1694e06a8b42">

Figure 5. Plot of final model's probability score for "quality group 8" category (which includes wine with quality 8 and 9) 

<img width="697" alt="image" src="https://github.com/littlebeanbean7/wine_quality_classification/assets/19282931/449d05ee-c879-482d-ac9f-2c855b3ae67e">

Figure 6. Plot of final model's feature importance

<img width="824" alt="image" src="https://github.com/littlebeanbean7/wine_quality_classification/assets/19282931/57c2601f-5bce-4eff-933f-4eec25989d67">

## Conclusion
Imbalanced data is a very common problem in machine learning. It is essential to check the proportion of each category when resolving any classification problem. The choice of model evaluation method is also very important for any machine learning problem and should be carefully decided.
 
Even more importantly, machine learning projects should be designed in a way that are practical for real world use case. In this project, if we simply convert the problem into binary classification problem, or even combine the rare poor quality wines and good quality wines into classes like [1] did, the model’s performances could show to be very good, however the model would not be useful for model users. 

Detecting the rare classes in an imbalanced data are often worth more value for model users. In our case, being able to detect and price top rating wines as well as preventing the poor quality wines to be mix with good or normal quality wines would have the greatest economic values to wineries and merchandiser. 

This project’s solution, from regrouping of categories, oversampling and choice of model evaluation matrix, has taken into account the model user’s biggest interest.

## Reference
[1] Hu, Gongzhu, et al. "Classification of wine quality with imbalanced data." 2016 IEEE International Conference on Industrial Technology (ICIT). IEEE, 2016.

[2] Er, Yeşim, and Ayten Atasoy. "The classification of white wine and red wine according to their physicochemical qualities." International Journal of Intelligent Systems and Applications in Engineering 4.Special Issue-1 (2016): 23-26.

[3] Cortez, Paulo, et al. "Modeling wine preferences by data mining from physicochemical properties." Decision support systems 47.4 (2009): 547-553.

[4] Akiba, Takuya, et al. "Optuna: A next-generation hyperparameter optimization framework." Proceedings of the 25th ACM SIGKDD international conference on knowledge discovery & data mining. 2019.
