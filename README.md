# KPMG-Sustainable-Future

**MEMBERS:** Alice Liu, Shoya Dixon, Wang Xiang, Melina Tsai, Rachel Tong, Ana Maria Rodriguez

----

### **CHALLENGE:**
---
Identify and to provide a prescribe placement of electric vehicle charging stations (EVCS) that appealss to the private corporation persona within the Dallas, Texas area. 


### **CONTEXT:**
---
President Biden signed the bipartisan infrastructure bill in November 2021, including a $5 billion investment in self-administered grants for nationwide electric vehicle (EV) charging stations. Specifically for Texas, they plan to dedicate $400 million to implementing charging stations. Moreover, KPMG clients seek advise on how to identify where EVCS should be placed for maximum return on investment.

### **APPROACH:**
---
1. **Research**
  - Brainstorm and research features that would help indicate where EVCS should be placed
  - Utilized Google, Kaggle, US Government website, KPMG provided data websites, OpenStreetMaps, Statistica, City of Dallas GIS Services, etc. 

2. **Data Visualization and Cleaning**
  - Visualize what information the data is trying to tell us
  - Drop/replace missing values
  - Drop irrelevant columns
  - Rename columns
  - Convert rows to zip-code level

3. **Feature Selections**

| Demographics     | Geographic Features                 | Economic Background |
| ---------------- | ----------------------------------- | ------------------- |
| Population       | Business/Residential building ratio | House Value         |
| Gender           | Shops                               | Household Income    |
| Race & Ethnicity | Parking Lots                        | EV registrations    |
|                  | Gas Stations                        |                     |

All the data are in numerical value. 

4. **Data combination**
  - Combined all the data through zip-code level
  
5. **Modeling** 
  - Used: OLS, Lasso, Random Forest, Gradient Boosted Decision Tree (GBDT) model. 
  - Evaluated each model using: RMSE, MSE, K-Fold Validation

RMSE Yielded the best result:

| Model Name    | Description                                                      | RMSE |
| ------------- | ---------------------------------------------------------------- | ---- |
| OLS           | Fits a hyperplane by assigning optimal weights to each feature   | 191  |
| Lasso         | OLS that penalizes features with large weights                   | 117  |
| Random Forest | Fit multiple “overfit” trees in parallel and average the results | 75   |
| GBDT          | Iterative tuning of a tree by correcting errors                  | 79   |

The lower the RMSE value it is the better the evaluation: **RANDOM FOREST** is the winner!

6. **Forecasting Zip Code Charactistics**
Used historical GDP data for Dallas 2002-2020 and ARIMA to help predict the FUTURE GDP data for Dallas 2020-2030. Utilizing these predictions, we obtain the top zip codes that needs EVCS. We sort by largest percentage. 

The top 3 zip codes to place EVCS: 75246, 75210, 75253

### **SUMMARY**
The supply and demand of EVCS can be viewed by examining the current EVCS available (supply) and EV registrations (demand)

The most important features (in descending order):
| Features                   |
| -------------------------- |
| Number of businesses       |
| Asian population           |
| Household income           |
| Parking Lots               |
| House value                |
| Hispanic Population        |
| American indian population |
| Other population           |
| Black population           |
| Population                 |
| Residential business ratio |
| Hawaiian population        |
| Female population          |
| Gas stations               |
| Shops                      |

The top 3 zip codes to place EVCS: **75246, 75210, 75253**

For more in depth insight, refer to the following slide link for the Appendix: https://docs.google.com/presentation/d/1G_5Mfh4qrS0M1IgiVSp9ZvnUrjJShmQMcsFv2btxDrs/edit?usp=sharing

### **FUTURE GOALS**
1. Prediction Improvements
    - Increase accuracy within the simulation model by adding randomization of percentage growth to each feature and using Census data for demographic features
2. Depth
  - Identify specific locations rather than higher-level zip codes
3. Scope
  - Expand analysis outside of Dallas:
    - Confirm analyses about predictors for EV Demand
    - Compare EVCS Supply and Demand in different regions
