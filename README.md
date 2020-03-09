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
See `01_DataPreProcessing.rmd` for detailed instructions, codes and annotations. <br>
<br>
This step includes:
* Selecting and creating the 55 identified family variables from the raw data
* Missing data imputation, with
  * mean imputation for the legitimate skips
  * multiple imputation for the remaining missingness, with the R `mice` package.
* Selecting and creating the college enrollment and college completion variables.
* Preliminary analysis for descriptives (weighted).

Descriptions of this procedure can also be found in the **Measures** and **Data preparation** sections in the manuscript.
<br>






