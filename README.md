# AMR_forecasting
Code to accompany "Predicting future hospital antimicrobial resistance prevalence using machine learning"
https://doi.org/10.1101/2023.11.30.23299234

# Dataset
A subset of the antibiotic resistance dataset is available through UKHSA’s online data service, Fingertips: https://fingertips.phe.org.uk/profile/amr-local-indicators/data#page/9/gid/1938132908/pat/158/par/ID_trust/ati/118/are/NQ115/yrr/1/cid/4/tbm/1 . 

Information on the use of antibiotics in secondary care was obtained from IQVIA (formerly QuintilesIMS, formed from the merger of IMS Health and Quintiles). All IQVIA data used retains IQVIA Solutions UK Limited and its affiliates Copyright. All rights reserved. Use of IQVIA data for sales, marketing or any other commercial purposes is not permitted without IQVIA Solutions UK Limited's approval, expressed by IQVIA’s Terms of Use.

https://digital.nhs.uk/services/organisation-data-service/export-data-files/csv-downloads/other-nhs-organisations etr contains a list of all TrustCodes and TrustNames. 

https://digital.nhs.uk/data-and-information/publications/ci-hub/summary-hospital-level-mortality-indicator-shmi 
Provider spells methodology contains "lookups for provider codes that have changed as a result of trust mergers or demergers. Using this data all activity can be mapped to current organisations and reported against the most recent trust code."

Denominators were downloaded from:
https://www.england.nhs.uk/statistics/statistical-work-areas/bed-availability-and-occupancy/bed-data-overnight/
https://www.england.nhs.uk/statistics/statistical-work-areas/bed-availability-and-occupancy/bed-data-day-only/

Total day and overnight bed occupancy data was chosen as the denominator, and merged with the antibiotic usage data by TrustCode and quarter-year. Total DDDs per trust per antibiotic per month were divided by the average daily number of occupied day and overnight beds. These were further divided by the number of days in the respective month and multiplied by 100 in order to obtain the average daily antibiotic usage rate per month (e.g. the antibiotic usage of 40 DDDs amoxicillin per 100 bed-days means 40% of inpatients receive one DDD of amoxicillin every day, an estimate of the therapeutic intensity).

# Toy dataset
The datasets in the analysis cannot be shared, therefore, we construct toy datasets with a similar structure, so that the interested reader can easily arrange their own datasets in this format and run the analysis. However, note that both the resistance prevalence and the usage rates provided in our toy examples are simply independent random samples froma U(0,100) distribution. 

# Models 
Models contain a jupyter notebook with code ran on the toy dataset for feature engineering, model fitting, predictions, as well as feature importance calculations. In order to save the outputs, please uncomment pd.DataFrame commands. 

# System requirements 
The analysis was run on macOS, using packages that from what I am aware should be compatible with all other operating systems. 

python 3.10.10 (main, Mar 21 2023, 13:41:39) [Clang 14.0.6 ]
pandas 1.5.3
numpy 1.23.5
scikit-learn 1.2.2
xgboost 1.7.4
shap 0.41.0
graphviz 2.50.0

# Installation guide
I recommend installing anaconda, creating a virtual environment, installing python, jupyter notebook, and all above required packages. This should only take a few minutes. 

# Demo
The jupyter notebook already reads in the toy datasets from this github repository. If you would like to save the outputs, please uncomment pd.DataFrame commands. These will then save .csv files with predictions for train and test dataset for all pathogen-antibiotic combinations and all model settings (different feature engineering, different parameters). These will be reflected in the .csv file names. One .csv file per pathogen-antibiotic combination will be saved with the feature importances. The runtime will depend on the size of your dataset and for example for the hyperparameter tuning on the number of combinations, however, one model runs very quickly, and the demo itself should finish running on the toy dataset in only a few minutes. 






