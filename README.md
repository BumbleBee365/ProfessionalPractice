# Impact of Increasing AI Useage on Employment Opportunities for the Younger Generation

# Executive Summary

An article based on data from the USA discussed the impact of increasing use of AI on employment opportunities for the younger generation, specifically  ‘Corporate workers are fighting for a shrinking pool of jobs as mass lay-offs and a hiring slowdown stoke fears of a “white-collar recession”, amid mounting pressure from tariffs, slowing economic growth and artificial intelligence’ (Armstrong, 2025)
The project aim is to determine if AI usage has significantly impacted employment in the UK. Data has been sourced from the Office of National Statistics website and cleansed allowing Exploratory Data Analysis (EDA) to identify trends for investigation. 
The EDA found employment is generally rising with notable declines largely due to COVID and long-term recessions impacts. Importantly the ‘Professional Science and Technical Industry’ continues to rise.
There is no evidence to support a rise in unemployment is solely related to the younger generation. There is evidence employment in older age categories continues to increase slightly.
There is not enough evidence to confirm if AI is a key driver impacting employment opportunities, as the key professions identified included mining and agricultural. The analysis does provide some valuable insights employment has risen in the older generation which could be a result of an ‘ageing population’ because of declining birth rates and a tendency for people to work longer (Pretz, 2019)
Spending Review 2025 has also committed to ‘Growing the artificial intelligence (AI) sector and ramping up AI adoption across the UK’ (Treasury, 2025) which aims to ‘provide jobs for the future and improve people's everyday lives’ (Technology, 2025) as opposed to removing opportunities.
AI is in very early stages and the results do not currently suggest AI is a key factor at this stage.
 
## Data Infrastructure & Tools

Public datasets have been sourced from the Office of National Statistics in excel format.

•	A05 SA: Employment, unemployment and economic inactivity by age group (seasonally adjusted)  (Team, 2025)
Output from the Labour Force Survey providing detail on the number of people employed across age groups. It does not provide any intelligence of professions; a second dataset is required to provide context into which professions are fluctuating.

Labour Force Survey is not mandatory meaning there are limitations in the data is sampled; in additional ‘Response rates fell particularly quickly during the Covid-19 pandemic,’ (Francis-Devine, 2023). It was identified in a report by the House of Commons that ‘Falling response rates to the Labour Force Survey mean that labour market data published by the Office for National Statistics (ONS) has become less reliable’ (Francis-Devine, 2023)

•	JOBS02: Workforce jobs by industry  (Team, 2025)

Dataset covers employment by industry. There are limitations in the way professions are grouped at a high level and not broken down into specific roles. This data is not created from one single source and is a result of a number or surveys including the Labour Force Survey.

There are discrepancies in the number of people employed between the datasets due to how they are created and the adjustments made within.

Tools used for analysis are Excel and PowerBI. These are readily available tools which are very easy to use.  Whilst excel can perform the required level of data analysis, PowerBI has been selected for analysis due to its ability to handle large datasets and publish dashboards. As explained in an article from Data Camp, “Power BI does not have the same restrictions as excel in terms of data size and is able to handle millions of rows of data” (Bothma, 2025). Python would also be suitable option over excel as this is ‘more customisable’ and able to handle ‘big data’ (Munira, 2024).
 
##Data Engineering

The ETL process, figure 1, begins by extracting datasets from ONS website and importing the data into PowerBI to be reviewed and cleansed in accordance with the six core data quality dimensions as defined by DAMA; Completeness, Uniqueness, Timeliness, Validity, Accuracy and Consistency (DAMA UK, 2020)

Figure 1 ETL Process

Datasets have been reviewed for duplicates and nulls values to ensure these do not skew the analysis and any unnecessary columns removed. Initial analysis shows the data appears consistent and does not show any bias in terms of ages groups or professions. 

There are no privacy issues with this data, these are publicly available datasets and do not include any personal information or pose any security issues.

Dataset 1

Age categories are not filled across all fields; to address this the data has been grouped into separate tables for each age group and headings for “Employment” and “Unemployment” promoted.

Custom column has been added to determine the age group. This method has been repeated across 6 age categories and the data appended into one dataset.
This dataset includes a rolling total based on 3-month blocks which may skew analysis. For this project an annual summary will meet the requirements. The year has been separated and a filter applied to only include data collected in March to May of each year.
 
Figure 2 Dataset 1 Transformation

Dataset 2

The second dataset has headers promoted. This is a monthly dataset and has been filtered to only include data reported in March of each year as this is a sufficient level of detail for this analysis and corresponds with the approach taken for dataset 1.

Blank columns have been removed. Some date errors were identified which were corrected using a find and replace.
Professions have been unpivoted to be used as a legend on a bar chart. A year column is required to analyse the data.  The Month-Year column has been split using a custom field to populate the year. 

Figure 3 Dataset 2 Transformation

##Visualizations 

PowerBI has been used for the EDA, specific visualisations chosen are discussed in the EDA section of this report. Visuals used in EDA have been included in the dashboard, Figure 4 and Figure 5. The dashboard provides the user with the functionality to use slicers to interrogate the data and identify trends.
 
Figure 4  Employment by Age
 
Figure 5 Jobs by Industry

##Analysis

###Exploratory Data Analysis

Line charts in figure 6 demonstrate employment and unemployment rates across each age group to identify any peaks/troughs in the data. Initial findings suggest employment rates remained steady across age groups however unemployment rates have started to rise.
 
Figure 6 Employment vs Unemployment
 
Waterfall chart, figure 7, demonstrates which professions are changing to determine if there is correlation to professions most likely to be using AI techniques. Professional Scientific & Technical has risen each year from 2021 suggesting AI has not negatively impacted this area.
 
Figure 7 Profession Changes by Industry

The bar chart in Figure 8 has been created using a custom column in PowerBI to calculate the delta between 2025 vs 2021 demonstrating a significant reduction in employment during recent years is largely due to the agricultural and the mining industry rather than data science related industries.
 
Figure 8 Profession Change by Industry Since 2021
 
Figure 9 demonstrates the ramp up in employment in the Professional Scientific & Technical industry
 
Figure 9 Profession Scientific & Technical

The line chart, Figure 10, shows Information and Communication Industry has seen a subtle decline from 2023-2024:
 
Figure 10 Information & Communication
 
###Metrics

High-level employment data can be used to predict future growth in employment using Linear Trend Time Series Analysis. It is hypothesised the number of employment opportunities will continue grow in line with the trend seen in figure 11, the null hypothesis being it will not continue to grow.
 
Figure 11 Jobs by Year with Trendline

Data has been divided into a train and test dataset; allowing predictions to be tested to determine if the model will be successful. 
Regression analysis has been completed in excel, providing the intercept and variable to allow a forecast to be made and essentially provide a line of best fit. Figure 12 shows the results of the analysis. The R square and adjusted R square are close indicating there are no outliers or overfitting.  The low P value indicates the null hypothesis can be rejected. 
 
Figure 12  Statistical Analysis

Metrics calculated to test predictions are Mean Average Percentage Error (MAPE) and Root Mean Square Error (RMSE). RMSE indicates the forecast can be out by 396 people which is acceptable in proportion to the scale of the population. The MAPE calculates the percentage difference between the actuals and predicted is 1.07% which indicates predications are highly accurate.

Figure 13 shows how the forecast aligns with actuals. 
 
Figure 13 Results of Analysis

##Recommendations

This analysis would benefit from a single source data set bringing together employment by age group and profession based using the same creation parameters. This will enable more detailed analysis to be conducted and insights into which industries are seeing a decrease in the younger generation to indicate whether AI is a potential factor. It would be advantageous to investigate other factors which could influence employment for the younger generation such as population, economic, social etc. 




<!-- this is a comment --> 

![Histogram](images/histogram-example-2%20(1).png) 

(Test.md)
