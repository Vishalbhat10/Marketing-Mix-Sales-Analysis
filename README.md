# Mix_Marketing_Sales_Analysis
Simple marketing mix model with Python

# Summary 
 
The goal of the project is to solve the marketing attribution problem.It aims to predict how much each marketing channel is 
contributed to the sales of the business.The problem becomes complex when the market channels are offline channels like TV,radio.
Teh project also gives idea about the relationship between the various media channels and the relationship with the sales.
 
# About the data
 
There is an input file advertising.csv (located at the data folder) which comprises of 200 records and 4 columns.
The data is split in the ratio of 80:20 into train and test files.

* Sales: It is the dependent and target variable.
* TV: It is a continous variable and denotes amount spent in the TV for sales.
* Radio: It is a continous variable and denotes amount spent in the radio for sales.
* Newspaper: It is a continous variable and denotes amount spent in the newspapers for sales.

# Exploratory data analysis

All the variables are continous variables including the target variable. The target variable is almost distributed normally and ranges 
from 1.6 to 27 sales.

![alt text](https://github.com/eggom/PersoProject___Mix_Marketing_Sales_Analysis/blob/master/media/SalesDist.png)

No null values has been found and no outliers were seen.The data is cleaned by removing unnecessary columns.

# Relation between depedent and independent variables

![alt text](https://github.com/eggom/PersoProject___Mix_Marketing_Sales_Analysis/blob/master/media/PairsPlot.png)

From the plots , a strong correlation is observed between the TV and sales.ie) when the TV spending cost increases sales also increases.
Simiarly average trend occurs between radio and sales but points are scattered comapring sales and newspaper.

# Correlation analysis

We can see that there’s a strong correlation between TV and sales (0.82), a moderate correlation between radio and sales (0.61), 
and a weak correlation between newspaper and sales (0.22). 
It’s still too early to conclude anything but this is good to keep into consideration moving forward.

![alt text](https://github.com/eggom/PersoProject___Mix_Marketing_Sales_Analysis/blob/master/media/CorrMatrix.png)

# Feature selction

Feature selection is one of the  important steps before building the model.
Here we used random forest variable importance function to calculate the significance of the features.
TV feature has more significance than radio which is more significant than newspaper.

TV> Radio > Newspaper

![alt text](https://github.com/eggom/PersoProject___Mix_Marketing_Sales_Analysis/blob/master/media/FeatImp.png)


# Model Development

Since the target variable is continous variable , we used multiple linear regression model to predict the sales.
Below is the summary of the built model.

![alt text](https://github.com/eggom/PersoProject___Mix_Marketing_Sales_Analysis/blob/master/media/OLSSummary.png)

We have attained a R sqaure value close 0.88 which indicates the model is performing better and not overfitted model.
We also have F- stat value of 410 which is greater than 1 ie) the model performs better .
This higher F stat value is because of the small dataset.

The linear regression equatio  can be written as 

sales= 2.72 + 0.046 * TV + 0.187 * radio + 0.036 * newspaper

When we see the p values , newspaper feature is not significant. If we remove the feature , the R square values decreases
but the model's predicitve power will increase.


# Evaluating model

![alt text](https://github.com/eggom/PersoProject___Mix_Marketing_Sales_Analysis/blob/master/media/Predictions.png)

Using test data set , we predict the sales value using the trained model.
Now we compare the predicted values and actual values and the plot indicates there is mot much deviation and the residuals
are in range of less errors.

# Conclusion

By R square value it indicates , 90% probability  the target value can be predicted using the features of TV, radio and Newspapers.
* We can also add the seasonality data of the company to increase the predicitng power of the model.
* We are also not sure of the imapct of the marketing is immediate.
* Not every sale is attributed to marketing. If a company spent absolutely nothing on marketing and still made sales, 
this would be called its base sales.Thus, to take it a step further, you could try to model advertising spend on 
incremental sales as opposed to total sales.
