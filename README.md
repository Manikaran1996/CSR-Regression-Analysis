# CSR-Regression-Analysis  
The code for crawling of CSR data from the official website is uploaded in [this](https://github.com/Manikaran1996/Crawling) repository.  
For using any of the files, you just need to change the folder path to the path name where you will store all the files.  
This repository contains python notebooks used for data collection, data-preparation and analysis of CSR spending in INDIA.  
All the files required for analysis are uploaded on [this](https://drive.google.com/file/d/1Dk7KRR-6cwOjSrntt9AMO8njCwWHnOfY/view?usp=sharing) folder  
For performing the analysis, first crawl the latest csr data from www.csr.gov.in website, next run the data preparation script which requires a number of data files - MPLAD Ministers data, Ministry x Sector matrix, Lok Sabha elections 2014 data, Aspirant districts data downloaded from niti aayog website, the RS and Lok Sabha ministers along with their ministry details. All these files are uploaded on the link shared above. Finally, run the analysis script.  
We performed following regression analysis -  
1. **Linear Regression Analysis** - Our aim was to establish a relationship between the CSR amount spent in all the Lok Sabha constituencies of the country in Fy 2014-15. The following variables were used for analysis-  
	1. **(type of constituency is GEN) x (not_backward)** The constituency is unreserved and not backward.  
	1. **(type of constituency is SC) x (not_backward)**  The constituency is reserved for SC candidate and not backward.  
	1. **(type of constituency is ST) x (not_backward)**  The constituency is reserved for ST candidate and not backward.  
	1. **(type of constituency is GEN) x (backward)** The constituency is unreserved and is backward.  
	1. **(type of constituency is SC) x (backward)** The constituency is reserved for SC candidate and is backward.  
	1. **(type of constituency is ST) x (backward)** The constituency is reserved for ST candidate and is backward
	1. **Vote margin (%) between ruling MP & runners up** We are interested to know if the vote margin by which the current MP has won has any significance on the CSR expenditure that constituency has attracted.  
	1. **if there is state alignment** It can be said that if the MP belongs to the alliance which is in power in state then it would be easier for him/her to do development work in his/her constituency, so in order to find it out, we have this feature if there is state alignment.  
	1. **if there is center alignment** Here we analysed if the MP belongs to the alliance ruling in center. It is possible that in order to fetch some advantage from central government a company expends CSR in the constituency of MPs belonging to the ruling alliance.   
	1. **if MP is a minister** The ministers have the executive authority and play key role in policy-making. A policy related to business can effect it in numerous way- positive or negative,  therefore in order to benefit the business a company may lure a minister by expending more CSR amount in his/her constituency
	1. **if a district in constituency is selected by Rajya Sabha MP who is minister as MPLAD District** It has been found that a number of key ministries are possessed by the RajyaSabha MP, to study the effect of these RajyaSabha MPs, we found the district chosen by them for expending their MPLAD fund. A company may be interested in expending CSR amount in these districts for getting any benefit in return.  
	1. **is there any overlap between MPs Ministry and company's sector**  In the last two features we are analysing the effect on CSR expenditure in a constituency if MP is a minister, here we are going one step further as a company might be able to get more benefit from a minister if the business sector of the company can be influenced by the MPs study.  
	
	
	The prepared dataset contains the amount spent in every Lok Sabha constituency. Notebook **DataPreparationForLinearRegAnalysis1** is used for preparing the dataset for this analysis. We created 6 linear regression models using different combinations of features. The **LinearRegressionAnalysisModels** contain the code for training all the 6 regression models.
	
1. **Logistic Regression Analysis** - Logistic regression analysis was performed in order to find out the factors that makes a company expend it's CSR fund in any district. The dependent variable is 1 if the company has spent amount in the district, 0 otherwise.The data set contained 25,85,296 data points out of which only 8165 belonged to the positive class, so the majority class data was randomly under sampled to create a balanced data set. We have  18,165 data points were available in the models fit. The independent features used were akin to the features used in linear regression analysis.  
Notebook **DataPreparationForLogisticRegAnalysis2** is used for preparing the dataset for this analysis. The **LogisticRegressionAnalysisModels** contain the code for training all the 6 regression models
