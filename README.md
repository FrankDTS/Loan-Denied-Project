# [Loan_Denied_Project](https://github.com/FrankDTS/Loan_Denied_Project/blob/main/Loan_Denied_Project.ipynb)
  1. Built several Neural Network and Machine Learning models (ANN, RandomFordst, and XGboost) to predict whether the bank should deny the loan application
  2. Data processing to transform data and several Feature Engineering methods to fill with columns that have NA values.

# Code and Resoused Used
  * Python 3.8
  * Packages: pandas, numpy, seaborn, matplotlib, sklearn, Xgboost, keras
  * [Xgboost parameter] (https://xgboost.readthedocs.io/en/latest/parameter.html)
  

# Data Preprocessing
  1. drop several columns which already contained in other feature or is not important (Name, LoanNr, State, City, ApprovalFY, DisbursementDate, BalanceGross, SBA_Appv, daysterm, xx)
  2. Normalize or standardize to transform the numeric columns (NoEmp, CreateJob, RetainedJob, DisbursementGross, GrAppv)
  3. Feature engineering with some columns (Zip, ApprovalDate, Term, FranchiseCode, RevLineCr, LowDoc)
     1. Zip: only take second and third number since the first numbers is State information, which is all same. The second and third number means smaller region.
     2. ApprovalDate: it is 5 numbrer format. So first change it to Y-m-d format, then take year and month information
     3. Term: group 60, 84, 120, 240, 300 days together since it has a significantly larger amount of people apply at these durations, and also their MIS_Status situation is the same. I also Separate 36 days as a single category since it also has significantly more people apply at that duration compare to other days but it has different MIS_Status with the group above.
     
     ![](/images/Days.png)
     
     4. FranchiseCode: Seperate FranchiseCode = 1 and 2 as two category since there are much more people in these two group compare to others. group other FranchiseCode as one group
     
     ![](/images/FranchiseCode.png)
     
     5. RevLineCr: it have some wrong value in the data set (0, T), so treat them as Null value
     6. LowDoc: it have some wrong value in the data set (0, S, A), so treat them as Null value

  4. one hot encoding for categorical paramete
  5. Built Xgboost model to predict BankState, LowDoc, and RevLineCr Null value
     * The reason for this predict order is because BankState and LowDoc have much lower null value (3, 8) compare to RevLineCr (786)



# Fit and Predict models
  1. ANN
  2. RandomForest model
  3. Xgboost model
