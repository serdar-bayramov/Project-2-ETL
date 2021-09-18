# Project-2-ETL

Vaccination progress in USA, UK, Canada and Italy

In this project, we will be comparing the vaccination progress of USA, UK, Canada and Italy.

PROJECT PROPOSAL

Introduction

In Tuesdays initial session, the group joined together and discussed our subject and how we were to divide out the project between us. After a quick and progressive chat we agreed on;

Subject

Through Kaggle we found a lot of very interesting datasets regarding the Covid Pandemic. We deliberated about what angle to take to best fit this project and looked at several different ideas. We settled on vaccination statistics as our base.

We then developed our idea of what we wanted the project to look like and how we could individually contribute. We decided that the best way was for us to look at a dataset each that we could clean and trim to fit together in one collective dataset.

Delegation of tasks across the group

We chose to divide our datasets geographically. We sourced through Kaggle some comparible datasets regarding daily vaccination figures across four separate countries;

-USA - Jesse's dataset
-UK - Serdar's dataset
-Canada - Maxwell's dataset
-Italy - Sam's dataset

We decided that we would look to tie all of these datasets together based on;

-Date
-Daily Vaccination Count
-Cumulative Vaccination Count

The plan then was to then combine the cleansed datasets and load them through SQL as a database.

PROJECT REPORT

Sam - With the Italian dataset, there were a few problems to overcome. Initially the columns provided in the raw data included irrelevent data such as NUTS codes. There were also complications in how the data was structured. There was no column for measuring the cumulative amount of vaccinations and data was divided into genders in defined age ranges by individual regions. This was further divided up by date, so there would be around 8 different pieces of data for each day and for each region. The aim of the project was to simplify these hundreds of numbers daily into one figure that covered all of Italy for each day.

In terms of cleaning this data I ran a groupby based on administration date which made life a lot easier by immediately combining much of the fragmented data. After this I dropped the remaining irrelevant columns, leaving me with the administration date and the number of males and the number of females that were vaccinated on each day. I then created a fourth column to sum the male and femal columns, leaving me with the total number of people vaccinated on each day. After this, with assistance from Serdar I was able to run a further column using a cumsum to create the cumulative counts of total people vaccinated, giving me exactly the data that I required.

