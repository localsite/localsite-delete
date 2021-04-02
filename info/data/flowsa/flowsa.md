# State and County Industry Lists - Data Prep  

The following documents how to generate a CSV file containing BLS data pulled from the [EPA's Flowsa API](https://github.com/USEPA/flowsa). You may also opt to pull from static json files generated for the [USEEIO widgets](../../../../io/charts/).  

The following verified that holes resided in Automotive Manufacturing at the county level.  To resolve, a [Google Sheet](https://docs.google.com/spreadsheets/d/1OX8TsLby-Ddn8WHa7yLKNpEERYN_RlScMrC0sbnT1Zs/edit#gid=0) provides [auto manufacturing employment levels](../../../info/#show=vehicles) exported from state DOL data.  And/or PUMA data may allow for comparison.

## BLS Data Preparation 

The steps below have been applied in our [Google CoLab for exploring NAICS](https://colab.research.google.com/drive/1HLK4HIUMLlgTR524QoCKvfaNl-La48XU?usp=sharing) which can be used to output 6-digit naics by state to a [CSV file](https://drive.google.com/drive/u/0/folders/1EoWDvNoaKO8xLclX4fr5exw83jJkkJIy) called naics-6digit-ga.csv on Google Drive. We've manually output [3 years](https://github.com/modelearth/community-data/tree/master/us/state/GA/naics) using the CoLab script.  The original Python also resides in our [FLOWSA fork](https://github.com/modelearth/flowsa/tree/master/colabs).

[Compare to FactFnder](https://data.census.gov/cedsci/table?g=0400000US13&n=336111&tid=CBP2018.CB1800CBP&hidePreview=true)  

U.S. Bureau of Labor Statistics (BLS) industry data  
BLS data is pulled using the [FLOWSA Python script](https://github.com/USEPA/flowsa/blob/master/flowsa/BLS_QCEW.py)
maintained by Catherine Birney.
<!--Check if 2017 has been added to master crosswalk  -->

**Flowsa Wiki**  
[Install & Run](https://github.com/USEPA/flowsa/wiki)  
How Flowsa data is prepared - Creating a FlowByActivity Dataset

If you change BLS_QCEW.py, do so in our [FLOWSA fork](https://github.com/modelearth/flowsa).

Check for 6-digit 336111 automobile industry NAICS when outputting using FLOWSA.  
Note that only 4-digit NAICS resides in "By-Industry" in [BLS downloadable files](https://www.bls.gov/cew/downloadable-data-files.htm).  


Output to [state data files](https://github.com/modelearth/community-data/tree/master/us/state)    

Output 5 columns with names: fips, naics, employees, wages and firms (establishment count)

- fips - Location (fips for county)  
- naics - ActivityProducedBy (6-digit naics)  
- employees - Employment FlowAmount (Number of Employees)  
- wages - Money (Annual Wages)
- firms - Other (Number of Extablishments)  