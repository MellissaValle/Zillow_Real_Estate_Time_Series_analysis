# Zillow Real Estate Data Time Series Analysis 
![house image](https://photos.zillowstatic.com/fp/04c06dbff7b83e156bd68e7dd1a0171f-cc_ft_960.jpg)


## Repo Structure

Main Analysis Notebook - Record of our Data Science process

Facebook Prophet Notebook - Additional EDA and modeling process using Facebook Prophet

Images - Relevant visualizaitons


## Project Overview

Our goal with this project is to use predictive time series modelling on Zillow home sale price data to determine which 5 metro areas in New York State are the most optimal for short term real estate investment. The metric we decided to use for this project is ROI, as we feel that using ROI (over things like net profit) better incorporates risk as a factor. While of course profitability is essential to the company utilizing this data, ROI serves as a guide towards the best investment opportunities, and specific dollar amount profit targets can be met by adjusting the amount of money initially invested. Our data comes from Zillow, courtesy of their public research data page, which we link to below. The raw dataset has information on over 900 metro areas across the US.

This project culminates in a recommendation of which 5 New York State metro areas are the most prime for investing in now, and selling a year from now. 

## Data Science Process

### 1. Exploratory Data Analysis

During EDA, we noticed that the dataset as provided by Zillow comes in "wide format" and for our time series models to run, we had to convert it to "long format". Luckily a function to do this was provided to us along with the dataset. We graphed the distribution of the values for just NY State, and found NYC to be an obvious outlier. We also plotted a time series for all of New York State to get an idea of the overall trend. 

![](Images/NY%20State%20Home%20Prices.png)

### 2. Data Preparation

Because our business problem is focused solely on New York, and the raw dataset contained metro areas from across the US, we filtered our dataframe down to the 26 metro areas within NY State. We also knew from our EDA that like the rest of the country, NY State housing prices were hit hard in 2008, and continued to decline for several years afterwards. We decided to shorten our dataset to only include data from 2012 to the present to avoid the crash of 2008 negatively affecting our models. 

In this step we also reformatted our dataframe from wide format, to long format for use in our ARIMA models, and performed a train test split. 

### 3. Modeling

Because each of the 26 cities required their own model, which had to be gridsearched, fit, and used to generate predictions, we wrote custom functions to streamline the process. These functions ran auto_arima, a gridsearching function, fit an ARIMA model with the optimal parameters, and made predictions using the fit models. 

We also wrote separate prediction functions for model validation, and for visualizing the predictions. 

### 4. Model Results

Our models trained on data from 2012 - 2019 and tested on data from 2019 - 2021 far outperformed an EDA based approach on the same time periods, telling us that modeling was well worth the effort. The EDA based technique for selecting which 5 cities to invest in gave us an ROI of 17.7%, where the model based approach resulted in an ROI of 29.5%, a massive increase. Our models were also only 13% off from the true final values for the test time period. 

## Conclusions

The five New York State metro areas recommended by our models when they were trained on the entire 2012-2019 dataset are in order of descending predicted ROI:

1. Utica
2. Binghamton
3. Jamestown
4. Syracuse
5. Albany

Possible next steps:
1. Our top 5 predicted ROIs for the next year are suspiciously high, and could be the result of our models overfitting. While we believe that our models do a good job of indicating which metro areas are good choices for investment due to how they compared to an EDA based method, a good next step would be to delve deeper into why these predicted ROI figures are so high. 

2. Another possible iteration on this project would be to move to a SARIMAX time series model, which can intake additional regression variables, and add metrics like population change, as well as economic and job rate data.

# Resources

Our Slide Deck on these Findings - https://www.canva.com/design/DAEv_ki9q1c/D8YewyvIj_3w_KyLjRQHTw/view?utm_content=DAEv_ki9q1c&utm_campaign=designshare&utm_medium=link2&utm_source=sharebutton

Zillow Research Data - https://www.zillow.com/research/data/




