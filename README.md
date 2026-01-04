# ProfessionalPractice


# Executive Summary


In an article based on data from the USA it was discussed that the increasing use of AI may have impacted employment opportunities particularly for the younger generation, specifically  ‘Corporate workers are fighting for a shrinking pool of jobs as mass lay-offs and a hiring slowdown stoke fears of a “white-collar recession”, amid mounting pressure from tariffs, slowing economic growth and artificial intelligence’ (Armstrong, 2025)
The key objective of this data science project is to determine if there has been any significant impact in employment in the UK across any age category which may be linked to the impact of increasing usage of AI.
Data has been sourced from the Office of National Statistics website and cleansed allowing exploratory data analysis to completed. PowerBI was used to identify trends in the data worth further investigation. 
The Exploratory Data Analysis (EDA) found the number of people in employment is on the rise with some notable decreases largely due to COVID and recessions. Importantly the ‘Professional Science and Technical Industry’ continues to rise at a similar rate to the overall employment rise.
There is no evidence in the analysis to support a rise in unemployment is solely related to the younger generation. There is evidence that employment in older age categories continues to increase slightly.
In summary the work identified there is not enough evidence to confirm if AI is a key driver impacting employment opportunities, as the key professions identified included mining and agricultural. However, the analysis did provide some valuable insights. There is evidence employment has risen in the older generation suggesting people are working longer resulting in an ‘ageing population’ because of declining birth rates and a tendency for people to work longer (Pretz, 2019)
Future development work could consider additional factors impacting employment opportunities for example rise in retirement age, improved health, population and therefore analyse the longer-term impact to the younger generation. In addition, the government Spending Review 2025 has committed to ‘Growing the artificial intelligence (AI) sector and ramping up AI adoption across the UK through the AI Opportunities Action Plan. (Treasury, 2025) which aims to ‘provide jobs for the future and improve people's everyday lives’ (Technology, 2025) as opposed to removing opportunities.


# Data Infrastructure & Tools

Two public datasets have been sourced from the Office of National Statistics.
•	Dataset 1:  A05 SA: Employment, unemployment and economic inactivity by age group (seasonally adjusted) – Released Oct 2025 (Team, 2025)
This dataset is an output from the Labour Force Survey and provides detail on the number of people employed across several age groups however it does not provide any intelligence as to which professions have been impacted. Therefore, a second dataset will also be analysed to provide more context into which professions are growing or reducing across the UK.
It was identified in a report by the House of Commons that ‘Falling response rates to the Labour Force Survey mean that labour market data published by the Office for National Statistics (ONS) has become less reliable’ (Francis-Devine, 2023)
It is important to note the Labour Force Survey is not a mandatory survey and therefore there are limitations in the data provided in that it is a sample only; in additional ‘Response rates fell particularly quickly during the Covid-19 pandemic,’ (Francis-Devine, 2023)
•	Dataset 2: JOBS02: Workforce jobs by industry - Released dec 2025 (Team, 2025)
This dataset looks specifically at employment by industry and will be used to understand if there are any trends in technology areas.
There are limitations in the way professions are grouped in that they are high level groupings and not broken down into specific roles. The data is not created from one single source and is a result of a number or surveys including the Labour Force Survey however there are discrepancies shown in the number of people employed between the 2 datasets due to how they have been created and the adjustments made within.
The tools used in the analysis are primarily Excel and PowerBI. These are readily available tools in the business which are very easy to use.  The data has been extracted from the ONS website and is in an Excel format. Whilst excel is capable of performing the required level of data analysis, PowerBI has been selected for this analysis due to its ability to handle large datasets and publish dashboards for sharing. As explained in an article from Data Camp, “Power BI does not have the same restrictions as excel in terms of data size and is able to handle millions of rows of data” (Bothma, 2025). In contrast Python would be another suitable option over excel as this is ‘more customisable’ and able to handle ‘big data’ (Munira, 2024) however PowerBI is more than capable of performing this analysis.

# Data Engineering
The ETL process shown in figure 1 begins by extracting both datasets from ONS website into an excel format and importing the required excel sheets into PowerBI to be reviewed and cleansed in accordance with the six core data quality dimensions as defined by DAMA; Completeness, Uniqueness, Timeliness, Validity, Accuracy and Consistency (DAMA UK, 2020)

** insert screenshots ***

Both datasets have been reviewed for duplicates and nulls values to ensure these do not skew any of the analysis. Upon analysis the data outputs appear to be consistent and do not show any bias in terms of ages groups selected or professions selected.
There are no privacy issues with this data, these are publicly available datasets and do not include any personal information or pose any security issues.
Dataset 1
In dataset 1, only columns with “Employment” and “Unemployment” figures are required, therefore any unnecessary data have been removed.
The age groupings are not filled across all fields; to address this the data has been grouped into separate tables for each age group. Any unnecessary rows have been removed and headings for “Employment” and “Unemployment” promoted.
A custom column has been added to determine the age group.
This method has been completed across 6 age categories. The data has then been appended into one dataset which has only the required columns and the appropriate age groups identified,
This dataset uses a rolling total based on 3-month blocks which will skew any analysis as 3 rows will include data for the same month. For this analysis, an annual summary will meet the requirements therefore the year has been separated from the date so this can be used for charts. A filter has then been applied to only included data in the March to May summary.

** insert screenshots ***
Dataset 2
The second dataset has headers promoted. As this is a monthly dataset this has been filtered to only include data reported in March of each year of this is a sufficient level of detail for this analysis and correspond with the approach taken for dataset 1.
Blank columns have been removed. Some date errors were identified which were corrected using a find and replace.
Professions have been unpivoted so this data can be plotted onto a bar chart. A year column is required to analyse the data.  This has been added be splitting the Month-Year column and using a custom field to populate the year fully. Any unnecessary columns have been removed.

** insert screenshots ***

# Visualizations 
The datasets have been loaded into PowerBI to perform the exploratory data analysis and visualise the results. PowerBI has been chosen due to its ease of use and is widely available in the business and ease of use. The business is set up to be able to publish and share dashboards with stakeholders. 
**** dashboard *****


# Analysis
## Exploratory Data Analysis
Line charts have been used to analyse employment and unemployment rates across each age group to identify any peaks/troughs in the data. Initial findings suggested employment rates has remained steady across most age groups however unemployment rates have risen across 16-17 year olds and 18-24 years

** insert screenshots ***


A waterfall chart has been used to understand which professions are having the most change to determine if there is any correlation to professions most likely to be using more AI techniques.

** insert screenshots ***
 
Professional scientific & technical activities have risen each year from 2015 suggesting increasing AI has not negatively impacted this area.
The chart below also demonstrates a significant reduction in employment is due to the mining industry rather than data science related industries.

** insert screenshots ***

 The chart below demonstrates the ramp up in recent years in employment in the Professional scientific & technical activities industry

 ** insert screenshots ***

Information and communication industry has seen a suitable decline from 2023-2024:

 ** insert screenshots ***

## Metrics
The high-level employment data has been used to predict future growth in employment. It is hypothesised that the number of employment opportunities will continue grow in line with the steady trend seen in figure  xxxxxx
The data has been divided into a train and test dataset; this will allow predictions to be tested and determine if the model will be successful. A moving average has been added to smooth the data and remove any seasonality.
Linear regression analysis has been completed in excel using the regression analysis option in the analysis tool pack. This provides the intercept and variable to allow a forecast to be made and essentially provide a line of best fit.
Figure xxx shows the results of this analysis. 
The metrics calculated to test the predictions are Mean Average Percentage Error (MAPE) and Root Mean Square Error (RMSE) explain why…..
The MAPE has been calculated as 1.07% which indicates predications will be off by only 1.07% which is highly accurate.
The RMSE indicates the forecast can be out by 396 people which is acceptable in the proportion to the scale of the population.

 ** insert screenshots ***

Figure xxx shows the output of the model and how closely the test dataset aligns with the actual results.

 ** insert screenshots ***

It should be noted there are some limitations to this analysis specifically it does not consider any external influencing factors such as economic impacted or population. While this is a small dataset it provides confidence additional data could be used to forecast growth at a more detailed level i.e. industry or age.

# Recommendations
This analysis would benefit from a single source data set which brings together employment by age group and profession based on the same creation parameters. This will enable much more detailed analysis to be conducted. Additional insights into which industries are seeing a decrease in the younger generation would give an indication If AI is a strong factor. It would also be advantageous to investigate other factors which could influence employment for the younger generation	such as population, economic, social etc. AI still in very early stages and the results do not currently suggest AI is a key factor as this stage.



 


<!-- this is a comment --> 

![Histogram](images/histogram-example-2%20(1).png) 

(Test.md)
