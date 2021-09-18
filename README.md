# Project-2-ETL

### Title: ETL data modelling for vaccination roll-out in the first 6 months in USA, UK, Canada and Italy

## PROJECT PROPOSAL

### Introduction

In our initial session, the group joined together and discussed our subject and how we were to divide out the project between us. After a quick and progressive chat we agreed on;

Subject

Through Kaggle we found a lot of very interesting datasets regarding the Covid Pandemic. We deliberated about what angle to take to best fit this project and looked at several different ideas. We settled on vaccination statistics as our base, looking to assess hwo selected developed nations embraced the concept of the Covid-19 vaccine. We had a particular interest in how fast and early these vaccines were delivered and believed that we could achieve this using the Extract, Transform and Load concept.

We then developed our idea of what we wanted the project to look like and how we could individually contribute. We decided that the best way was for us to look at a dataset each, extract the relevent data, transform our findings and load them into a collective database.

### Delegation of tasks across the group

We chose to divide our datasets geographically. We sourced through Kaggle some comparible datasets regarding daily vaccination figures across four separate countries.

We decided that we would look to tie all of these datasets together based on;

-Date -Daily Vaccination Count -Cumulative Vaccination Count

The work load was shared in the following way:

Extracting data - Sam, Max

Transformation of data - Sam, Max, Jesse, Serdar

Loading data - Serdar, Jesse

Project Proposal - Sam

Project Report - Jesse, Max, Serdar


### Why we chose these datasets

We chose these datasets for several purposes. The UK and Canada have been reported through international media as having some of the most successful vaccination rollout programs on the planet, so we felt that we would likely see the highest functioning trends from these.

We then felt that the USA was also a good dataset to include as it is a country that is commonly accepted as being the leading nation in the world. It is understood that the rollout there has faced some difficult challenges amid lots of other internal and foreign affairs during the pandemic, so we expected to see results that were more of a median.

Finally, Italy was chosen as we felt that the general perception is that, whilst a very affluent country it would likely lag behind the other three, due to differences in healthcare budgets and because of its inclusion in the European Union where their research and resources would be spread across nations other than its own. (Italy was also chosen partly because Sam was on vacation in Italy during this project week, so adding a bit of personal interest and excitement to the work!)

## PROJECT REPORT

Coronavirus is a disease that affects the respiratory system at large; due to its impact on the world, every nation is fighting the pandemic in all available ways that it can. The scope of this project is to access data on how these developed countries, the USA, Canada, Italy and the UK, embraced the concept of the covid-19 vaccine. Particular interest is how fast and early these vaccines were delivered.

This is achieved by applying the ETL data modelling concept:

Extract

Transform

Load

### Data Extraction

As a result of this work, We access four different sets of data from kaggle.com on vaccinations from the USA, Canada, Italy and Canada. (Jesse - USA, Serdar - UK, Max - Canada, Sam - Italy)

https://www.kaggle.com/tenzinmigmar/covid19-vaccine-tracking-in-canada

https://www.kaggle.com/paultimothymooney/usa-covid19-vaccinations

https://www.kaggle.com/rajkumarl/uk-covid-vaccination

https://www.kaggle.com/arthurio/italian-vaccination

A resource folder was created from which the data is uploaded into a Pandas DataFrame: 

ca_vacc_df, us_vacc_df, it_vacc_df, uk_vacc_df

The following dependencies were imported for this project:
pandas, sqlalchemy, functools, matplotlib

### Data Transformation

Prior to loading the data into PostgreSQL, the data transformation has been performed for each dataset. Herebelow is the summary of data transformation that was performed for each specific country:

### UK data transformation

The UK dataset was not very complicated to overcome. There were originally some missing data, as the first 3 rows were in weeks instead of days. So, in order not to drop them (since the first 3 weeks are considered important in understanding the vaccine roll-out success) I modified the original csv file to convert weekly data into daily. Then, loaded data into pandas dataframe and selected only the needed columns and renamed them to be consistent. Finally, I extracted only the first 180 days of the data. 

### USA data transformation

Select and rename the columns that we are interested in and drop all None values from the dataset. Select only the locations that is 'United States' which is the sum of all states. Extract only the first 180 days from the entire dataset.

### Canada data transformation

The data obtained for Canada was fairly simple as most of the data was clear and detailed. For this reason, the first step in cleaning the data was to rename some columns and dropping irrelevant columns and saving into a new DataFrame. It was observed that names for province’s were not given but decided to leave it in the DataFrame as a point of reference. In addition the data revealed that vaccines were distributed to provinces way before actual vaccinations started and so I dropped all zero entries on relevant columns in order to get the starting date for all vaccinations. As a final outlook a dropna function was applied on the total vaccinations column to be sure we have none value entries in the final dataset.

### Italy data transformation

With the Italian dataset, there were a few problems to overcome. Initially the columns provided in the raw data included irrelevent data such as NUTS codes. There were also complications in how the data was structured. There was no column for measuring the cumulative amount of vaccinations and data was divided into genders in defined age ranges by individual regions. This was further divided up by date, so there would be around 8 different pieces of data for each day and for each region. The aim of the project was to simplify these hundreds of numbers daily into one figure that covered all of Italy for each day.

In terms of cleaning this data I ran a groupby based on administration date which made life a lot easier by immediately combining much of the fragmented data. After this I dropped the remaining irrelevant columns, leaving me with the administration date and the number of males and the number of females that were vaccinated on each day. I then created a fourth column to sum the male and femal columns, leaving me with the total number of people vaccinated on each day. After this, with assistance from Serdar I was able to run a further column using a cumsum to create the cumulative counts of total people vaccinated, giving me exactly the data that I required.


### Data Loading

Following data transformation, the data was loaded into PostgreSQL database. To do that, we took the following steps:
Created config file to contain username and password
Created connection with PostgreSQL in jupyter notebook using create_engine function.
Created a database called vaccination in PostgreSQL
Created a table in 'vaccination' database called vaccination.
 We used to_sql function of pandas to move records stored in a dataframe to a PostgreSQL database.
Check if data was loaded successfully by querying from PostgreSQL

### Conclusion

Working on the ETL modelling was a wonderful experience as it brought to light the importance of working in teams. The project took us through the various phases of project development.
The first step involved extracting information from kaggle.com, that is, a csv file. The data was then transformed into a schematic data by way of a cleansing operation where incomplete records were removed from the database. Finally, the schematic data was uploaded into an SQL database.
The data stored in the (SQL) data warehouse could be further investigated by looking at the population figures of each country to assess how well they dealt with the vaccination program. Figure below is an example of the vaccinations carried out over a period of six(6) months.
The line graph in Jupyter Notebook illustrates the vaccination profile in the USA, UK, Italy and Canada. The graph shows a higher number of vaccinations in the USA as compared against the three other countries (UK, Italy and Canada) which could be as a result of population growth. However, it is obvious that there was a cautious handling of the vaccination program, that is, a steady increase in the number of people taking the vaccines by day.
