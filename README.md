# project_2_ETL
<h1 align=center> Austin, Texas Dockless Vehicle Study </h1> <br>

![Dockless Scooter](http://s79f01z693v3ecoes3yyjsg1.wpengine.netdna-cdn.com/wp-content/uploads/2018/03/sf.Bird_.0307.jpg) <br>

### Project Members:
#### Petros Paterakis, Michael Alrafati, Omar Abusheikh

<hr><h3 align=center> What is the correlation between dockless vehicle usage & weather in Austin? </h3><hr>

### Overview: 

* **Extraction** (from 2 data sources): <br>
	The [City of Austin](https://data.austintexas.gov/Transportation-and-Mobility/Dockless-Vehicle-Trips/7d8e-dm7r "City of Austin Dataset") maintains a dataset for dockless vehicle usage in the city, and this was imported in csv format into a python jupyter notebook file for further analysis.  
	Weather data was collected from [LSU's Souther Regional Climate Center (SRCC)](http://hrly.lsu.edu/ "Weather API") using the API which they have available; the API reponse was returned in JSON format & was also imported into a seperate jupyter notebook file.  
	*In this report, the two sets will be referred to as the 'Dockless Dataset', and the 'Weather Dataset'*. 
* **Transformation**: <br>
	All steps in the transformation process were performed within python jupyter notebook files.  
	The 'Dockless Dataset' is relatively recent, and only included data starting on April 2018, through the present day.  This data was downloaded as a csv, and was converted into a pandas dataframe.  
	API queries on the 'Weather Dataset' were restricted to match the dates in the 'Dockless Dataset'.  Futhermore, we elected to use the API to query the following fields, to allow for the most effective analysis: temperature, dew point, relative humidity, percipitation (hourly), wind speed , pressure at sea level. API calls were returned in JSON format.  
	Both datasets included data which was rather clean, so minimal transformation was required.  Each dataset was first converted into a python pandas dataframe.  The raw date & time fields were different among the two datasets, so they were rounded to the hour and converted from a time string into a datetime format. Finally, the dataframes were transposed to convert the list of dictionaries to a dictionary of lists, to prepare them for the final loading step.   
  <br>
* **Loading**: <br>
	The datasets were loaded into two distinct collections wihtin a Mongo database (NoSQL) via pymongo.  This data will be maintained locally, so that further analysis can be conducted on it in the future.  
<hr><br>

### Other Information: <br>

* **Further Potential Analysis**:
	- Determine regular usage patterns as a foundation, to be able to compare/contrast abnormal behaviour,
	- Compare current trends in data with traffic information (new dataset required), to determine correlation,
		- Google maps or a similar API can be used,
	- Analyze scooter usage during different weather conditions,
	- Compare usage to income data to determine correlation (new dataset required).
* **Challenges**:
	- The SRCC API did not have good documentation, and some trial and error was required to understand how to perform the desired queries, 
	- The time fields were retrieved as date strings, but needed to be converted into datetime so that they could be read properly by pandas,  
	- Converting the data from a pandas dataframe into dictionary format was challening.
