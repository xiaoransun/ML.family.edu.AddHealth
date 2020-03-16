# ML.family.edu.AddHealth
Documentation of programming scripts for the cross-study synthesis on adolescents' family experiences as predictors of young adult educational attainment with machine learning, based on Add Health data. <br>
Paper in press at Journal of Child and Family Studies. <br>
<br>
The purpose of this GitHub repository is:
* To share the codes for data pre-processing, machine learning models training and testing, and visualization for the paper, thereby other researchers can replicate this study.
* To provide pedagogical explanations, step by step, for how we conducted the analyses for this paper. Researchers should be able to use our codes to conduct machine learning research with their own substantive research interests and research questions.
* To facilitate post-publication communication. If you have any questions regarding our paper, analysis or codes, feel free to post in the 'Issues' section of this repository and we will try our best to answer your questions.

### Step 0: Getting prepared for data processing.
This paper uses public dataset (Wave I and Wave IV) of National Longitudinal Study of Adolescent Health (Add Health). To conduct analyses with the data, please first download the data following their instructions at: https://www.cpc.unc.edu/projects/addhealth/documentation/publicdata
<br>
We followed the instructions to download data from [ICPSR](https://www.icpsr.umich.edu/icpsrweb/ICPSR/studies/21600?archive=ICPSR&q=21600).
<br>
<br>
The particular datasets used in this study are listed below. You can find the 'Download' option under the 'Data & Documentation' tab at the ICPSR data repository.
* DS1 Wave I: In-Home Questionnaire, Public Use Sample
  * We used both the R and SPSS versions of the data because the SPSS version has more information regarding the missing data pattern.
* DS22 Wave IV: In-Home Questionnaire, Public Use Sample
  * We used the R version for this data.
* DS31 Wave IV: Public Use Weights
  * We used the R version for this data.

For a detailed description of this sample, please refer to the **Participants** section in the manuscript.
<br>

### Step 1: Pre-processing the data.
This step includes:
* Selecting and creating the 55 identified family variables from the raw data
* Missing data imputation, with
  * mean imputation for the legitimate skips
  * multiple imputation for the remaining missingness, with the R `mice` package.
* Selecting and creating the college enrollment and college completion variables.
* Preliminary analysis for descriptives (weighted).

See `01_DataPreProcessing.rmd` for detailed instructions, codes and annotations. <br>

Descriptions of this procedure can also be found in the **Measures** and **Data preparation** sections in the manuscript.
<br>

### Step 2: Tuning, training and testing machine learning models predicting educational attainment.
This step is to answer the question, "Do family experiences in adolescence predict college enrollment and graduation in young adulthood?", which includes:
* Tuning, training, and testing regularized logistic regression and random forests models in predicting college enrollment and college graduation with the 53 family experience variables, using stratified nested cross-validation (5-fold; see visualization below)
* Calculating AUC and Accuray for each algorithm predicting each outcome

Codes for this step include (one Jupyter markdown for each outcome variable and each algorithm):
* `02-1_collen_LR.ipynb` college enrollment, regularized logistic regression
* `02-2_collen_RF.ipynb` college enrollment, random forests
* `02-3_collcom_LR.ipynb` college completion (i.e., graduation), regularized logistic regression
* `02-4_collcom_RF.ipynb` college completion (i.e., graduation), random forests

This step corresponds to the **Method--Data Analysis--Question 1** and **Results--Do Family Experiences in Adolescence Predict Educational Attainment in Young Adulthood?** sections in the manuscript.
<br>

<img src="https://github.com/xiaoransun/ML.family.edu.AddHealth/blob/master/visualization/nested%205-fold%20cross-validation.jpg" alt="nested cross-validation" width="800">

### Step 3: Selecting the best predictors-- feature importance and recursive feature elimination
This step is to answer the question, "Which family experience factors are key predictors of young adult educational attainment?", which includes:
* Compute feature importance of all the 53 predictors in the trained logistic regression and random forests mdoels predicting college enrollment and graduation, respectively.
* Conduct recursive feature elimination (RFE) to identify the set of predictors that remained in models with prediction accuracy equivalent to the original model that included all predictors. 

Codes for this step include:
* `03-1_FeatureImportance_collen.ipynb` feature importance and RFE for predicting college enrollment
* `03-2_FeatureImportance_collcom.ipynb` feature importance and RFE for predicting college graduation
* `03-3_FeatureImportancePlotting.rmd` Plot feature importance using ggplot2 in R (Figures S1 & S2 in the manuscript supplemental material)

This step corresponds to the **Method--Data Analysis--Question 2** and **Results--Which Family Experiences Are Key Predictors of Educational Attainment?** sections in the manuscript.
<br>

### Step 4: Visualizing nonlinear and interactive effects--Partial Dependence Plots
This step is to answer the question, "What complex patterns, including nonlinearities and interactions involving this set of family factors, merit further examination?" <br>
Here, following the random forests training-testing, 2D and 3D partial dependence plots (PDPs) are made to visualize nonlinear and/or interactive effects between features/predictors. <br>
Codes for this step include:
* `04-1_PDP_collen.ipynb` PDPs for random forests model predicting college enrollment
* `04-2_PDP_collcom.ipynb` PDPs for random forests model predicting college graduation

In particular, within this interactive notebook, you can plug in the selected features and obtain the PDP to your interest!

This step corresponds to the **Method--Data Analysis--Question 3** and **Results--What Complex Patterns of Predictors Merit Further Examination?** sections in the manuscript.





