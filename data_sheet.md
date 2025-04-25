# Datasheet: National Gas Transmission (subset of daily data for system price prediction)


## Motivation

**For what purpose was the dataset created?**

The dataset was created to improve the operation of the UK's natural gas market by reducing market uncertainty, ensuring equal access to information, and increasing information transparency. The goal is to increase efficiency in the capacity and energy markets, while providing fair and timely access to operational and market information. Further details are at https://www.nationalgas.com/our-businesses/operational-data/our-data

**Who created the dataset (e.g., which team, research group) and on behalf of which entity (e.g., company, institution, organization)? Who funded the creation of the dataset?**?

It was created by National Gas Transmission, which is funded by market participants in the form of gas transmission fees, in the course of its normal business.

 
## Composition

**What do the instances that comprise the dataset represent (e.g., documents, photos, people, countries)?**

The instances in this subset of Nation Gas Transmission data each represent one measurement from one day's operation of the gas National Transmission System

**How many instances of each type are there?**

This subset contains 1815 instances: one for each day from 1st May 2020 and 19th April 2025 inclusive

**Is there any missing data?**

Many of the instances of "Composite Weather Variable - Actual" are missing, mainly for 2020-2021 when Covid restrictions were in force. A small number of instances of other data items are also missing, most likely because a final measurement was unavailable operationally.

**Does the dataset contain data that might be considered confidential (e.g., data that is protected by legal privilege or by    doctor–patient confidentiality, data that includes the content of individuals’ non-public communications)?**

No

## Collection process

**How was the data acquired?**

Actuals data (making up most of the features): observed using industrial metering of the transmission system

Forecasts: https://www.nationalgrid.com/sites/default/files/documents/8589937808-Gas%20Demand%20Forecasting%20Methodology.pdf

Prices: System Average Price is the average price of gas traded via the On the Day Commodity Mechanism, operated by ICE Endex. System Marginal Price (Buy) is the greater of SAP + 0.0533 p/kWh or the Price in p/kWh which is equal to the highest market offer price in relation to a market balancing action taken for that day. System Marginal Price (Sell) is the lesser of SAP - the default System Marginal Price in p/kWh or the Price in p/kWh which is equal to the lowest market offer price in relation to a market balancing action taken for that day


**If the data is a sample of a larger subset, what was the sampling strategy?**

This is subset of features of the full National Gas dataset, and a 5 year snapshot covering 1st May 2020 to 16th April 2025

**Over what time frame was the data collected?**

Actuals and price data are collected and published within a few hours of the end of the gas day if not sooner.

Weather and demand forecasts are published either annually at the start of October, or hourly depending on the forecast horizon.

## Preprocessing/cleaning/labelling

**Was any preprocessing/cleaning/labeling of the data done (e.g., discretization or bucketing, tokenization, part-of-speech tagging, SIFT feature extraction, removal of instances, processing of missing values)? If so, please provide a description. If not, you may skip the remaining questions in this section.**

Composite Weather Variables and demand forecasts are calculated according to the methodology at https://www.nationalgrid.com/sites/default/files/documents/8589937808-Gas%20Demand%20Forecasting%20Methodology.pdf

**Was the “raw” data saved in addition to the preprocessed/cleaned/labeled data (e.g., to support unanticipated future uses)?**

Some of the raw data used as inputs to the demand forecast are also available at https://data.nationalgas.com/
 
## Uses

**What other tasks could the dataset be used for?**

The subset could be used for any high-level investigation concerned with natural gas balancing or demand forecasting on the UK gas transmission network

**Is there anything about the composition of the dataset or the way it was collected and preprocessed/cleaned/labeled that might impact future uses? For example, is there anything that a dataset consumer might need to know to avoid uses that could result in unfair treatment of individuals or groups (e.g., stereotyping, quality of service issues) or other risks or harms (e.g., legal risks, financial harms)? If so, please provide a description. Is there anything a dataset consumer could do to mitigate these risks or harms?**

No - this is high-level industrial data


**Are there tasks for which the dataset should not be used? If so, please provide a description.**

Not in particular

## Distribution

**How has the dataset already been distributed?**

Yes - the full dataset is publicly available at https://data.nationalgas.com/

**Is it subject to any copyright or other intellectual property (IP) license, and/or under applicable terms of use (ToU)?**

Terms of Use: https://www.nationalgas.com/our-policies/terms-and-conditions

## Maintenance

**Who maintains the dataset?**

The full dataset is supported, hosted and maintained by National Gas Transmission.	The full dataset is updated continuously with new data. Corrections are made as appropriate, including in response to users' requests. Updates are not communicated to users, with the exception of users inquiring about corrections. Contact form at https://data.nationalgas.com/request-data or +44 1926 656474

