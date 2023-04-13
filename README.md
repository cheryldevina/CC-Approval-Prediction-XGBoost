# CC-Approval-Prediction-XGBoost
A data mining project to extract, clean, and analyze data to try and predict if a CC applicant should be approved with an XGBoost model.

## Dataset

Dataset consists of 2 tables connected by an ID.
There are a total of 18 columns for _application_record.csv_ and 3 columns for _credit_record.csv_

## Objective
- To clean data, remove unused columns, and keep columns of importance.
- To label applicants as either *accepted* or *rejected* depending on status of CC payments per month in _credit_record.csv_.
- Create a machine learning model to predict whether an applicant should be accepted or rejected. 

## Steps
1. Correlated each status to a 'REP'

STATUS
* 0: 1-29 days past due
* 1: 30-59 days past due
* 2: 60-89 days past due
* 3: 90-119 days past due
* 4: 120-149 days past due
* 5: >150 days past due
* C: Paid off that month
* X: No loan that month

If status is C, X, 0, 1 REP is set to *1*
If status is 2, 3, 4, 5, REP is set to *-1*

2. Sum the REP for all months for each account
3. If by the end REP value is positive, label applicant as accepted.
4. If by the end REP value is negative, label applicant as rejected. 
5. Plotted heatmap to determine columns that may be dropped.
6. Oversampled 'rejected' data to balance the data.
