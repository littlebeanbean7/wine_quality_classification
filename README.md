# wine_quality_classification
## I. Abstract
This research classifies wine’s quality with the objective to maximize the economic value for wine
ry and merchandisers using machine learning technologies. An extremely imbalanced dataset containing the white wine’s quality was used. Wines with extremely good and poor qualities are extremely rare in the dataset. To predict the quality of wine using machine learning algorithms, a minimum amount of data samples are required. In this research,  a minimal grouping was conducted without the original ranking of the wine quality are maximizedly preserved. Then SMOTE oversampling techniques was used to treat the imbalance of the data. Multiple machine learning algorithms were experimented and Random forest with hyper parameters fine tuned by Optuna was found to be the best model which not only have good performance among all the wine quality classes (ROC 0.855) but also the rare classes (quality 3 and 4 have a ROC of 0.86, and quality 8 and 9 have a ROC of 0.92). As in real world, imbalance data are very common whereas the rare classes are usually more important and carries more commercial value. The solution proposed by this research, which preserved the importance of rare classes and utilized machine learning technologies, an be applied on other data and used in other industries.

## II. Video

## III. EDA
### Imbalance of data
#### Without regrouping

<img width="189" alt="image" src="https://github.com/littlebeanbean7/wine_quality_classification/assets/19282931/53385ea1-b945-4ba8-9db2-9b43a074247c">

#### With regrouping

<img width="224" alt="image" src="https://github.com/littlebeanbean7/wine_quality_classification/assets/19282931/324bd782-1baf-4f78-9dd8-4f1781eb0e44">


### Features

There are 11 features. All of them are numerical. No missing values are indentified. All features are used for modelling as the modelling experiments show that all features contribute to over 5% feature importance, this demostrated all of the features are important for the model to make prediction. Previous study using PCA to do feature selection also proved that dropping feature would make the model performance drop. [2]

Below shows the statistics of all the columns. The last column "quality" is the Target variable. All other columns are features.
<img width="770" alt="image" src="https://github.com/littlebeanbean7/wine_quality_classification/assets/19282931/bdaffad4-811f-4aba-8150-2a284602cc2e">

Below show the distribution of one feature per category as an example. For more plots please reference the notebook.

<img width="832" alt="image" src="https://github.com/littlebeanbean7/wine_quality_classification/assets/19282931/8ae186aa-99b8-4a54-a668-d20c55d93329">

## Experiment setup
Four experiments were set up to resolve this problem:

<img width="472" alt="image" src="https://github.com/littlebeanbean7/wine_quality_classification/assets/19282931/ad2348b1-18db-4c60-b696-e7cfd5b2f8b5">

## Result
This session shows the modeling result of Random Forest Model in 4 experiments. Experiment 4's model was chosen as the final model

### Without regrouping

Experiment 1 model comparision result can be found below. It can be found that Extra Trees Classifer model gets the best ROC-AUC.

<img width="816" alt="image" src="https://github.com/littlebeanbean7/wine_quality_classification/assets/19282931/abffe66d-a763-4c1e-b40f-bee065bf4590">

Experiment 1 best model's performance by categories can be found below. It can be found that the model was not good at predicting the quality 3, 4 and quality 8, 9 categories, althougth the overall model performance is good.

<img width="490" alt="image" src="https://github.com/littlebeanbean7/wine_quality_classification/assets/19282931/9057edb7-8afd-48a1-948a-b4b052491a88">


### With regrouping
Experiment 2 model comparision result can be found below. It can be found that Extra Trees Classifer model get the best ROC-AUC again.

<img width="816" alt="image" src="https://github.com/littlebeanbean7/wine_quality_classification/assets/19282931/2edab552-f0f9-4626-bcc0-4d2563a5a9a8">

Experiment 3 model comparision result can be found below. It can be found that Extra Trees Classifer model still the best ROC-AUC.

<img width="816" alt="image" src="https://github.com/littlebeanbean7/wine_quality_classification/assets/19282931/4a9ceca3-bbd5-4409-a5d0-cf9f502a8936">

Below table shows the best model's performance in Experiment 2, 3, 4 by categories. The table explains the difference among the experiments and from the table we can found that regrouping and oversampling techniques such as SMOTE has boosted the model's performance when predicting the quality 3, 4 and quality 8, 9 categories, while the overall model performance remains good.

<img width="471" alt="image" src="https://github.com/littlebeanbean7/wine_quality_classification/assets/19282931/72827b47-4b75-4363-9035-e651b2da0909">

Plot of final model's ROC AUC performance per category

<img width="705" alt="image" src="https://github.com/littlebeanbean7/wine_quality_classification/assets/19282931/671e505a-3765-427e-896f-e6e5a30cf00b">

Plot of final model's confusion matrix per category

<img width="793" alt="image" src="https://github.com/littlebeanbean7/wine_quality_classification/assets/19282931/47155522-69ef-4f7f-b699-1391b2d4412c">

Plot of final model's clasiffication report per category

<img width="732" alt="image" src="https://github.com/littlebeanbean7/wine_quality_classification/assets/19282931/0af641a5-cdc6-43f9-b8fa-1694e06a8b42">

Plot of final model's probability score for "group 8" category (which includes wine with quality 8 and 9) 

<img width="697" alt="image" src="https://github.com/littlebeanbean7/wine_quality_classification/assets/19282931/449d05ee-c879-482d-ac9f-2c855b3ae67e">

Plot of final model's feature importance

<img width="824" alt="image" src="https://github.com/littlebeanbean7/wine_quality_classification/assets/19282931/57c2601f-5bce-4eff-933f-4eec25989d67">

## Reference
[1] Hu, Gongzhu, et al. "Classification of wine quality with imbalanced data." 2016 IEEE International Conference on Industrial Technology (ICIT). IEEE, 2016.


[2] Er, Yeşim, and Ayten Atasoy. "The classification of white wine and red wine according to their physicochemical qualities." International Journal of Intelligent Systems and Applications in Engineering 4.Special Issue-1 (2016): 23-26.

[3] Cortez, Paulo, et al. "Modeling wine preferences by data mining from physicochemical properties." Decision support systems 47.4 (2009): 547-553.

[4] Akiba, Takuya, et al. "Optuna: A next-generation hyperparameter optimization framework." Proceedings of the 25th ACM SIGKDD international conference on knowledge discovery & data mining. 2019.
