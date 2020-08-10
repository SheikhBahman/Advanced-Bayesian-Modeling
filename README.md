# Advanced-Bayesian-Modeling
Course project of my CS 598: Advanced Bayesian Modeling

This is my individual course project for Advanced Bayesian Modeling. For this project The data file EUCOVIDdeaths.csv contains data from the European Center for
Disease Prevention and Control (ECDC) on daily deaths related to COVID-19 in the 27 European Union (EU) member states for the second half of March 2020.1 Each row represents an
EU country, and the columns are as follows:

* Country name of the country (member state)
* PopulationM 2018 population of the country, in millions
* Mar16 {Mar31 number of COVID-19 deaths recorded in the country for that date

I have used JAGS and R software to analyze the data as briefly explained here. For the complete report please see the PDF file.

# Author
* Bahman Sheikh

# Programming Language
* R programming
* JAGS
* Markov chain


# Introduction

The Coronaviruses under the microscope have a crown-like appearance that is why this family of viruses are called corona which is a Latin word means crown. Coronavirus family are common in human and many different animals, including camels, cattle, cats, and bats. In human Coronavirus spreads mainly from person to person, mostly through breathing droplets produced when an infected person talks directly to another person or when he/she coughs or sneezes. Generally Coronavirus is spreading more efficiently than influenza, but less efficient than measles. Coronavirus family which is known as CoV is not new. CoVs have been discovered since the 1960’s [1]. For example Zoonotic coronaviruses have discovered and caused human outbreaks, such as the Severe Acute Respiratory Syndrome (SARS) in 2003 and the Middle East Respiratory Syndrome (MERS) since 2012. So far, about 7 coronaviruses have been discovered: Beta coronavirus HCoV-OC43, HCoV-HKU1, Alpha coronavirus HCoV-229E, Alpha coronavirus HCoV-NL63, SARS-CoV, SARS-CoV2 and MERS-CoV [1, 2]. The novel coronavirus known as COVID-19 was emerged to cases in Wuhan, China on 31 December 2019 is a novel type of SARS-CoV2 and genetically groups within Beta coronavirus subgenus Sarbecovirus [3]. One of the main characteristics of COVID-19 is its high reproduction number (R0) defined as mean number of infections produced by a case of an infection in a completely vulnerable population. On 12 January 2020, Chinese government announced the sequence of a novel coronavirus as type of SARS-CoV-2 isolated from some clustered cases. In European countries on 24 January 2020 first case was confirmed in France, 27 January in Germany, and 31 January in Spain, Italy and United Kingdom. As of 21 February 2020 about 47 confirmed cases of COVID-19 in 9 European countries reported: 21 were linked to two clusters in Germany and France, 14 were infected in China. Median case age was 42 years; 25 were male. As at 5 March, in European countries there were 4,250 confirmed cases. As of 17 March, all Europe countries reported confirmed cases of COVID-19, where Montenegro was the last country to report at least one case. As of 18 March, more than 250 million people were in lockdown in Europe [6, 7]. Review of 12 statistical and clinical modeling in Europe shows that the reproductive number for COVID-19 (R0) is at about 3.28, with a median of 2.79. For instance R0 in Italy estimates between 2 and 3. And form 11 European countries R0 estimated to be around of 3.87 on average. However when social distancing or other restriction are in place the population cannot be considered completely vulnerable therefore the effective reproductive number (Re) is defined. In European Union the Re in Germany is one of the lowest and remains around one or below since the 22 March (95% CI ≈ 3.0 - 4.7) An obvious decrease in Re happened following the social distancing and restriction rules are placed in several European countries. As of 8 May, in Europe Spain with 221,447 confirmed cases is the highest and Liechtenstein with 83 confirmed cases is the lowest infected countries. As of 19 March, Public Health England, no longer classified COVID-19 as a “High consequence infectious disease”. Also, on May 6 German chancellor Angela Merkel announced that the goal of slowing down the virus has been achieved and that the first phase of the pandemic is over in Germany [1, 2, 4, 5, 8].

# Data

The dataset contains daily deaths related to COVID-19 in the 27 European Union countries from March 16 to March 31 (16 days). In the dataset “Country” column shows the name of the country, “PopulationM” column is the population of country in million people and columns named 16-Mar to 31-Mar show the number of deaths related to COVID-19 by day in each country. Some initial investigation of the data are provided in Figure 1. As it can be seen in figure1 (a) total number of death in the EU increases linearly in the time period of 18 to 28 of March and between 28 and 31 of March the total cases of death in EU per day was almost a plateau. However, average number of death per countries in EU increases linearly in our time period (see Figure 1(b)). Figure 2 shows number of deaths versus day and number of deaths per million inhabitants versus day. According to figure 2:
•	Which country has the most deaths over this period?
Italy had the most death per day which was on 28 of March with 971 cases. During this time period Italy also had the most total number of death among the 27 EU countries.
•	Which country has the highest death rate per capita over this period?
Spain had the most death per capita which was 17.93 death per million inhabitants of the country.
•	Which countries have no deaths over this period?
Latvia, Malta and Slovakia didn’t have death cases in this time period.

![GitHub Logo](/IMG/1.png)
![GitHub Logo](/IMG/2.png)

# First model
#	The model is a log-linear regression model (Poisson model). Response variable, deaths [i, j]), is number of COVID-19 deaths recorded in country i (i = 1...27) on day j (j = 1…16).
#	Hyperparameters are mu.intercept, sigma.intercept, and slope.
Parameters are lambda and intercept.
#	JAGS model in the file named firstmodel.bug

Number of chains =  4
Length of adaptation = 10,000
Length of burn-in = 50,000
Number of iterations used per chain = 200,000
Thinning = 100


# Second model

JAGS model in firstmodel.bug, create an extended JAGS model that allows each country to have a separate slope

Number of chains =  4

Length of adaptation = 10,000

Length of burn-in = 50,000

Number of iterations used per chain = 300,000

Thinning = 100

# Conclusions
In this project data from of daily deaths related to COVID-19 in the 27 European Union (EU) member states for the second half of March 2020 investigated. First the data briefly investigated and then two Bayesian model was used to further explore the data and try to fit a Bayesian model. From the data I found the following:
Total number of death in the EU increases linearly in this time period.
Italy had the most death per day.
Spain had the most death per capita.
Latvia, Malta and Slovakia didn’t have death cases in this time period.

Two Bayesian model fitted using JAGS in R. Both model are a log-linear regression model (Poisson model). For the first model similar slope for different countries is assumed. For the second model, however, slope for different countries assumed to be independent and identically distributed.
It is found that the second model is better than the first model.
Main summary of the models are as follows:

First model:
Number of chains =  4
Length of adaptation = 10,000
Length of burn-in = 50,000
Number of iterations used per chain = 200,000
Thinning = 100
DIC: 3715
Effective number of parameters = 27

Second model:
Number of chains =  4
Length of adaptation = 10,000
Length of burn-in = 50,000
Number of iterations used per chain = 300,000
Thinning = 100
DIC: 2590
Effective number of parameters = 42



