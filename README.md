# Brazil_ETL

We will attempt to find a correlation between government expenditures and forest fires.<br>  
<br>
Here we are extracting monthly emissions data for the area of the Amazon Rainforest.<br>
<br>
We will be looking at a five year span from 2014 to 2018. The goal is to try and see<br>
if there is an increase in the amount of forest fires in the region and if the demand
for soybean and corn is directly linked to it.

Data files
We will be using soybean and corn data gathered from Kaggle.com and carbon emissions data gathered from
the Global Fire Emissions Database (GFED). Data from GFED are all stored in HDF5 files and
requires some drilling down to get to the tables we need -- the monthly carbon emissions table.
