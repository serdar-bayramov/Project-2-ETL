# Project-2-ETL
INTRODUCTION
Coronavirus is a disease that affects the respiratory system at large; due to its impact on the world, every nation is fighting the pandemic in all available ways that it can. The scope of this project is to access data on how these developed countries, the USA, Canada, Italy and the UK, embraced the concept of the covid-19 vaccine. Particular interest is how fast and early these vaccines were delivered.
This is achieved by applying the ETL data modelling concept:
Extract
Transform
Load
Data Extraction
As a result of this work, we access four different sets of data from kaggle.com on vaccinations from the USA, Canada, Italy and Canada.
https://www.kaggle.com/tenzinmigmar/covid19-vaccine-tracking-in-canada
https://www.kaggle.com/paultimothymooney/usa-covid19-vaccinations
https://www.kaggle.com/rajkumarl/uk-covid-vaccination
https://www.kaggle.com/arthurio/italian-vaccination
A resource folder was created from which the data is uploaded into a Pandas DataFrame 
Canada_df
Usa_df
Italy_df
uk_df
The following dependencies were imported:
Pandas
PostgreSQL
Data Transformation
Maxwell
The data obtained for Canada was fairly simple as most of the data was clear and detailed. For this reason, the first step in cleaning the data
Was to rename some columns and dropping irrelevant columns and saving into a new DataFrame. It was observed that names for province’s were not given but decided to leave it in the DataFrame as a point of reference. In addition the data revealed that vaccines were distributed to provinces way before actual vaccinations started and so I dropped all zero entries on relevant columns in order to get the starting date for all vaccinations. As a final outlook a dropna function was applied on the total vaccinations column to be sure we have none value entries in the final dataset. 

Maxwell Ansah  11:49 AM
Conclusion
Working on the ETL modelling was a wonderful experience as it brought to light the importance of working in teams. The project took us through the various phases of project development.
The first step involved extracting information from kaggle.com, that is, a csv file. The data was then transformed into a schematic data by way of a cleansing operation where incomplete records were removed from the database. Finally, the schematic data was uploaded into an SQL database.
The data stored in the (SQL) data warehouse could be further investigated by looking at the population figures of each country to assess how well they dealt with the vaccination program. Figure below is an example of the vaccinations carried out over a period of six(6) months.
The line graph illustrates the vaccination profile in the USA, UK, Italy and Canada. The graph shows a higher number of vaccinations in the USA as compared against the three other countries (UK, Italy and Canada) which could be as a result of population growth. However, it is obvious that there was a cautious handling of the vaccination program, that is, a steady increase by the day.
