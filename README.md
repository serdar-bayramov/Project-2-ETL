# Project-2-ETL

Vaccination progress in USA, UK, Canada and Italy

In this project, we will be comparing the vaccination progress of USA, UK, Canada and Italy.

PROJECT PROPOSAL

Introduction

In Tuesdays initial session, the group joined together and discussed our subject and how we were to divide out the project between us. After a quick and progressive chat we agreed on;

Subject

Through Kaggle we found a lot of very interesting datasets regarding the Covid Pandemic. We deliberated about what angle to take to best fit this project and looked at several different ideas. We settled on vaccination statistics as our base, looking to assess hwo selected developed nations embraced the concept of the Covid-19 vaccine. We had a particular interest in how fast and early these vaccines were delivered and believed that we could achieve this using the Extract, Transform and Load concept.

We then developed our idea of what we wanted the project to look like and how we could individually contribute. We decided that the best way was for us to look at a dataset each, extract the relevent data, transform our findings and load them into a collective database.

Delegation of tasks across the group

We chose to divide our datasets geographically. We sourced through Kaggle some comparible datasets regarding daily vaccination figures across four separate countries;

-USA - Jesse's dataset - https://www.kaggle.com/paultimothymooney/usa-covid19-vaccinations
-UK - Serdar's dataset - https://www.kaggle.com/rajkumarl/uk-covid-vaccination
-Canada - Maxwell's dataset - https://www.kaggle.com/tenzinmigmar/covid19-vaccine-tracking-in-canada
-Italy - Sam's dataset - https://www.kaggle.com/arthurio/italian-vaccination

A resource folder was created from which the data is uploaded into a Pandas DataFrame 
Canada_df
Usa_df
Italy_df
uk_df
The following dependencies were imported:
Pandas
PostgreSQL

We decided that we would look to tie all of these datasets together based on;

-Date
-Daily Vaccination Count
-Cumulative Vaccination Count

Why we chose these datasets

We chose these datasets for several purposes. The UK and Canada have been reported through international media as having some of the most successful vaccination rollout programs on the planet, so we felt that we would likely see the highest functioning trends from these. 

We then felt that the USA was also a good dataset to include as it is a country that is commonly accepted as being the leading nation in the world. It is understood that the rollout there has faced some difficult challenges amid lots of other internal and foreign affairs during the pandemic, so we expected to see results that were more of a median. 

Finally, Italy was chosen as we felt that the general perception is that, whilst a very affluent country it would likely lag behind the other three, due to differences in healthcare budgets and because of its inclusion in the European Union where their research and resources would be spread across nations other than its own. (Italy was also chosen partly because Sam was on vacation in Italy during this project week, so adding a bit of personal interest and excitement to the work!)

Merge

Our plan then was to then merge the cleansed datasets and then load them through SQL as a database.

PROJECT REPORT

Sam - With the Italian dataset, there were a few problems to overcome. Initially the columns provided in the raw data included irrelevent data such as NUTS codes. There were also complications in how the data was structured. There was no column for measuring the cumulative amount of vaccinations and data was divided into genders in defined age ranges by individual regions. This was further divided up by date, so there would be around 8 different pieces of data for each day and for each region. The aim of the project was to simplify these hundreds of numbers daily into one figure that covered all of Italy for each day.

In terms of cleaning this data I ran a groupby based on administration date which made life a lot easier by immediately combining much of the fragmented data. After this I dropped the remaining irrelevant columns, leaving me with the administration date and the number of males and the number of females that were vaccinated on each day. I then created a fourth column to sum the male and femal columns, leaving me with the total number of people vaccinated on each day. After this, with assistance from Serdar I was able to run a further column using a cumsum to create the cumulative counts of total people vaccinated, giving me exactly the data that I required.

