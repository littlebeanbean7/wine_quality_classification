# wine_quality_classification
## I. Abstract

## II. Video

## III. EDA
### Imbalance of data
#### Without regrouping

<img width="189" alt="image" src="https://github.com/littlebeanbean7/wine_quality_classification/assets/19282931/53385ea1-b945-4ba8-9db2-9b43a074247c">

#### With regrouping

<img width="224" alt="image" src="https://github.com/littlebeanbean7/wine_quality_classification/assets/19282931/324bd782-1baf-4f78-9dd8-4f1781eb0e44">


### Features

Below show the distribution of one feature per category as an example. For more plots please reference the notebook.

<img width="832" alt="image" src="https://github.com/littlebeanbean7/wine_quality_classification/assets/19282931/8ae186aa-99b8-4a54-a668-d20c55d93329">


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

