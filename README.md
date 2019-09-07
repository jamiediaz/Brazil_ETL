# Brazil_ETL

We will attempt to find a correlation between government expenditures and forest fires.  

Here we are extracting monthly emissions data for the area of the Amazon Rainforest.

![](images/amazon.jpg)

We will be looking at a five year span from 2014 to 2018. The goal is to try and see
if there is an increase in the amount of forest fires in the region and if the demand
for soybean and corn is directly linked to it.

### Data files
We will be using soybean and corn data gathered from Kaggle.com and carbon emissions data gathered from
the Global Fire Emissions Database (GFED). Data from GFED are all stored in HDF5 files and
requires some drilling down to get to the tables we need -- the monthly carbon emissions table.

### HDF5 files

HDF is completely portable file format with no limit on the number or size of data objects in the collection.  In this case, we are dealing with datasets that are 720 rows x 1440 columns for each month of the year and for each section of the GFED.

![](images/hdf5_sample.png)

Each cell on the table corresponds to the latitude and longitude coordinates.  Each cell data contains a measurement for that coordinate on the map.  i.e. a percentage of how much area burned for that particular coordinate.  

### H5PY Library

We imported the H5PY library which allowed us to use python to parse through the database.  

![](images/h5py.png)

To parse through it, it's as simple as the following command each layer. You will need to copy it to a variable and use .File() to keep going into the database. 

![](images/command.png)

### Dataset 
The table we need resides in C under each month of the year.
We will extract this data and put it to a dataframe.
We then filter the data frame from column 444 to 519 and from row 352 to 399.
The table corresponds to the lat, long coordinates for the rectangular area that
is roughly the area of the Amazon Rainforest.

Coordinates
NW: 1.819447, -68.950113
NE: 1.819447, -50.397135
SE: -9.666005, -50.397135
SW: -9.666005, -68.950113

### HDF to Pandas

After finding and extracting the data, we copied each table to a Pandas dataframe and sent them to PostGres. 

We did this for every month for every year.  

![](images/parse.png)
