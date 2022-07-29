MEDICARE FRAUD DETECTION
 
BUSINESS PROBLEM:
Health care expenditures constitute a significant portion of governmental budgets.  In 2020, National health expenditure grew 9.7 percent to $4.1 trillion, reaching $12,530 per person, and accounted for 19.7 percent of Gross Domestic Product (GDP). However, health care fraud costs the nation $68 billion to $283 billion annually, contributing 3 to 10 percent of the nation's health care spending. Health care fraud involves peers of providers, physicians, beneficiaries acting together to make fraud claims. In particular, some medical providers commit fraud, including double billing, phantom billing, unbundling, upcoding etc. Hence, our goal is to build a prediction model to aid in medical fraud assessment.

RESEARCH QUESTION:
Detect frauds by medical providers and classify common types of frauds.
Predict the potentially fraudulent providers based on claim information they performed and prescription drugs they administered.
Figure out predictors with highest importance in predicting fraudulent providers.


BUSINESS IMPACT:

[It is useful if you can provide an estimated impact of your target/moonshot analysis. If things go exactly as planned, how much does your company benefit? If things go much better than planned, how much does your company benefit?]

The Medicare system is estimated to spend $2.5 trillion dollars in 2009. Fraud doesn’t lurk too far behind. The latest estimates from the Center for Medicaid and Medicare Services (CMS) indicate that the government’s exposure to fraud and abuse within this program is over $100 billion annually. Our team’s fraud analysts, using a variety of data resources to ferret out fraud, would benefit the security of Medicare and Medicaid systems by predicting which claims have a high probability of being fraudulent. This would benefit the taxpayers of this country and potentially help the government save 100 billion dollars of losses on fraud and abuse annually in the Medicaid and Medicare system. Since Medicare is funded through a payroll tax on both the employer and employee, as more funds are needed, taxes are raised. Thus, everyone employed could benefit from our analysis. If your organization has a company-rated healthcare plan, fraud affects your claims history which will directly affect your rating and corresponding premium amounts. For self-insured plans, fraudulent claims directly steal from you. Our analysis would prevent these fraudulent crimes from happening and save taxpayers hundreds of millions of dollars per year.


DATA SOURCING:
Type I: Data from the Medicare & Medicaid Services
The following Data are grouped/aggregated by Provider NPI:
Part D
Medicare Part D Prescribers - by Provider
Data Description: The Medicare Part D Prescribers by Provider dataset contains information on prescription drugs prescribed by individual physicians and other health care providers and paid for under the Medicare Part D Prescription Drug Program. The dataset identifies providers by their National Provider Identifier (NPI) and summarizes for each prescriber the total number of prescriptions that were dispensed, which include original prescriptions and any refills, and the total drug cost.
Data Source: Medicare & Medicaid Services
Year: 2019
Number of rows: 1,240,595
Link:https://data.cms.gov/provider-summary-by-type-of-service/medicare-part-d-prescribers/medicare-part-d-prescribers-by-provider/data
Data Dictionary: https://data.cms.gov/resources/medicare-part-d-prescribers-by-provider-data-dictionary
Medicare Part D Prescribers - by Provider and Drug
This data set is a more detailed data set for Part D. On top of the dataset  "Medicare Part D Prescribers - by Provider", this dataset also contains the drug brand name (if applicable) and drug generic name.
		Data Source: Medicare & Medicaid Services
		Year: 2019
		Number of rows: 25,401,870
Link:https://data.cms.gov/provider-summary-by-type-of-service/medicare-part-d-prescribers/medicare-part-d-prescribers-by-provider-and-drug
Part A
Medicare Inpatient Hospitals - by Provider and Service
Data Description: Information on hospital discharges from Original Medicare (fee-for-service) Part A (Hospital Insurance) beneficiaries by Inpatient Prospective Payment System (IPPS) hospitals; aggregated by provider and service.
		Data Source: Medicare & Medicaid Services
		Year: 2019
Number of rows: 188,806	Link:https://data.cms.gov/provider-summary-by-type-of-service/medicare-inpatient-hospitals/medicare-inpatient-hospitals-by-provider-and-service
Part B
Medicare Outpatient Hospitals - by Provider and Service
Data Description: Information on services provided to Original Medicare (fee-for-service) Part B (Medical Insurance) beneficiaries by Outpatient Prospective Payment System (OPPS) hospitals; aggregated by provider and service.
Data Source: Medicare & Medicaid Services
Year: 2019
Number of rows: 115,507
Link: https://data.cms.gov/provider-summary-by-type-of-service/medicare-outpatient-hospitals/medicare-outpatient-hospitals-by-provider-and-service
DMEPOS
For DMEPOS, the following data sets contain similar information but grouped differently.
Medicare Physician & Other Practitioners - by Provider and Service
The dataset provides information on use, payments, and submitted charges organized by National Provider Identifier (NPI), Healthcare Common Procedure Coding System (HCPCS) code, and place of service.
Number of rows: 10,140,228
Link:https://data.cms.gov/provider-summary-by-type-of-service/medicare-physician-other-practitioners/medicare-physician-other-practitioners-by-provider-and-service
Remark: This data sets have separate entries for claims under the same NPI provider
Medicare Durable Medical Equipment, Devices & Supplies - by Referring Provider
The dataset contains information on usage, payments, submitted charges and beneficiary demographic and health characteristics organized by National Provider Identifier (NPI).
Number of rows: 389,310
Link:https://data.cms.gov/provider-summary-by-type-of-service/medicare-durable-medical-equipment-devices-supplies/medicare-durable-medical-equipment-devices-supplies-by-referring-provider/data
Type II: Data from the LEIE
This data contains excluded data from 1977.
Related columns: NPT, EXCLTYPE
Remark: This data does not has the reinstatement data
Link: https://oig.hhs.gov/exclusions/exclusions_list.asp
The information of monthly exclusions and reinstatement can be found here.
Link: https://oig.hhs.gov/exclusions/supplements.asp
For the column of EXCLTYPE, read the description of each type in below.
Link: https://www.ssa.gov/OP_Home/ssact/title11/1128.htm
Type III: Supplementary dataset (Optional)
Rate my doctor dataset.
Link: https://www.ratemds.com
A synthesis dataset from CMS for research use:
https://www.cms.gov/research-statistics-data-and-systems/downloadable-public-use-files/synpufs
A synthesis dataset from CMS that contains claims start-end date:
https://www.cms.gov/Research-Statistics-Data-and-Systems/Downloadable-Public-Use-Files/SynPUFs
Remark: the real data does not contain start-end date.
Existing program for fraud detection: https://www.cms.gov/About-CMS/Components/CPI

METHODS:
Models
Baseline Machine learning models: given the processed dataset contains features and fraud labeling of a medical provider, classic classification models in supervised learning can be explored in this project
Logistic regression
Random forest
Neural network if resources permit
Clustering: In addition, if we eliminate the labeling from external data, we can consider the problem as unsupervised, and therefore apply clustering models to it. 
K-means: the most simple and commonly used clustering model, but may require to define number of clusters in advance
Other more advanced clustering algorithms: models that do not require defining k in the first place are also available, such as Mean-shift, GMM (Gaussian mixture model), DBSCAN and so on. 
Notes
In terms of this particular question, pre-setting the number of clusters might be difficult, as while non-fraud behaviors follow a similar distribution, fraud behaviors could have large variations and are hard to identify as the same cluster. Therefore, algorithms that do not need to define the number of clusters might be a better option here.
Although we do not use the external source of labeling in training the model for clustering, the dataset of true labels is still a useful resource when evaluating the performance of our clustering models. For example, we can compare the distribution of true labels with that of clusters to see if they coincide. 
Feature selection/importance: it will be interesting to look at which features of a medical provider will have a larger impact on its fraud behavior. This step can help us better interpret the model and lower the dimension of features.

Libraries: we are going to use Python as the main language of data analysis. Packages that are used include pandas, scikit and matplotlib. On the other hand, Tableau might be used for generating the interactive dashboard. 
