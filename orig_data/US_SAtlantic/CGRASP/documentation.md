# C-Grasp Dataset Documentation

This document details the USGS Coast Grain Size Portal ([C-Grasp](https://zenodo.org/record/5874231#.YeePiVuIbRY)), the data sources it is comprised of, and  any alterations/decisions made in the compilation processes.

### About the dataset:

The overall preliminary dataset is composed from 6 secondary databases and gathered primary sources, totaling over 210 primary sources for grainsize measurements. The samples from these sources have been ranked and selected by their relevancy in leiu of the objectives of this project which is to find spatially and temporally explicit surficial sediment grainsize data on the Eastern Continental United States. This data is gathered as a part of the [National Oceaographic Partnership Programm (NOPP) Hurricane Coastal Impacts (NHCI) project](https://nopphurricane.sofarocean.com/). Four versions of this dataset can be found on [C-Grasp](https://zenodo.org/record/5874231#.YeePiVuIbRY):


  * Entire Coastal Dataset: This is all data that is found to be within 10km of the  [Natural Earth physical 1:10m coastline polyline](https://www.naturalearthdata.com/downloads/10m-physical-vectors/):
    * *463,165 Total Samples*   
    * *12,913 Dated Samples*
    * *213 Primary Sources*  

<p align="center">
  <img src=https://github.com/C-GRASP/AnalysisNotebooks/blob/main/documentation/images/overallsed_data_pic_forgit.png width="450" />
</p>


  
  * Estimated Onshore Dataset: This is all the data from "Entire Coastal Dataset" that lies within the [Natural Earth 1:10m United States Polygon](https://www.naturalearthdata.com/downloads/10m-physical-vectors/):
    * *70,305 Total Samples*
    * *6,005 Dated Samples*
    * *133 Primary Sources*   
  
<p align="center">
  <img src=https://github.com/C-GRASP/AnalysisNotebooks/blob/main/documentation/images/estimated_data_pic_forgit.png width="450" />
</p>

  
  
  * Verified Onshore Dataset: This is all data that was able to be verified onshore from either sampling method, note, or location type data (ie Sample_type_code==1, see below):
    * *5,356 Total Samples*
    * *5,272 Dated Samples*
    * *61 Primary Sources*

<p align="center">
  <img src=https://github.com/C-GRASP/AnalysisNotebooks/blob/main/documentation/images/verified_data_pic_forgit.png width="450" />
</p>



### In order to access this data via spatiotemporal queries, see our [sample_query tool](https://github.com/C-GRASP/AnalysisNotebooks/tree/main/sample_query)

---

## Dataset Fields:

The dataset fields were compiled and/or generated by the C-Grasp team based on potential use value. Below is a description of each dataset field.

#### Sample_ID:

This unique ID is any unique ID provided from the source dataset. 


#### Sample_Type_Code:

This sample ranking, ranked by field is as follows: 
   * (1): A surficial sediment sample that is explicitly stated as coming from  on-shore, intertidal ,or supertidal either from the source project's documentation of location type or gathering method 
   * (2): An offshore surficial sediment sample gathered by a grab device
   * (3): A non-surficial sample (e.g. core) 
   * (N/A or Blank): not stated or known

#### Project:

Databases for this dataset are composed of different data sources. In this case, this field is populated by the specific project the relevant sample was gathered in

#### dataset:

The dataset that the sample was gathered from. For more specifics on each dataset, see below.

#### Date:

Date that the sample was gathered (not analyzed) standardized to yyyy-mm-dd format.

#### Location_Type:

If populated by "Beach?Y" the sample was specified to be gathered onshore through metadata or note information. If other, this field was populated by in the original dataset nomenclature of where on the beach a sample was gathered (e.g. berm, dune, intertidal, etc.)

#### Latitude & Longitude

The coordinates of a sample projected to EPSG:4326. Cases in which coordinates had to be reprojected can be found in the source data break-down below


#### Contact:

The most relevant contact information that was able to be found for each sample, ranging in specificity from providing source agency to gatherer of the sample.

#### num_orig_dists:

This is the amount of cumulative distribution values (e.g. d10,d50,d90) that were provided with the sample. Other ones provided were extrapolated by the C-Grasp team.


#### Measured_Distributions

These are the distributions that were provided (accounted for in num_orig_distributions). All other provided cumulative distribution values were extrapolated by the C-Grasp team.


#### Grainsize

This field is populated when a sample grainsize was provided with a measurement, but with no further data specifying measurement. This most frequently occured with the US Seabed dataset in which the metadata says that grainsize is a measurement of "median or mean". Grainsize is in mm units.

#### Mean

Mean calculated using the Folk and Ward (1957) graphical moments method (Also see Blott & Pye, 2001). In mm units.

#### Median

This is provided when a sample's median grainsize was provided but differed from the interpolated d50 value.

#### Wentworth

Sediment grainsize classification from Wentworth, 1922.

 
#### Kurtosis

Kurtosis calculated using the Folk and Ward (1957) graphical moments method (Also see Blott & Pye, 2001). In mm units.


#### Kurotis_Class

Kurtosis classification from Folk and Ward (1957) (Also see Blott & Pye, 2001).


#### Skewness

Skewness calculated using the Folk and Ward (1957) graphical moments method (Also see Blott & Pye, 2001). In mm units.


#### Skewness_Class

Skewness classification from Folk and Ward (1957) (Also see Blott & Pye, 2001).


#### Std
Sample standard deviation calculated using the Folk and Ward (1957) graphical moments method.

#### Sorting
Sorting classificationusing the Folk and Ward (1957) graphical moments method (Also see Blott & Pye, 2001). 

#### d[5-95]

These fields are populated by their relevant cumulative distribution percentile value. The method in which this is done can be found in the AnalysisNotebooks interpolation notebook tools, further expanded upon for each dataset in the source data breakdown below. These values are in mm units.

#### Notes:

These notes consist of all other data provided in this source datasets that did not seem immediately useful for the purposes of this dataset, but may be helpful for other endeavors. This data consists of information such as sampling methods, sediment petrography, or whether shells/biological material were present within the sample. For more information, see the data breakdown below.


---

# Source Data Documentation:

Listed below are the sources that we compiled for the overall dataset with notes on  the original provided descriptions, the given conditions of the dataset, where to access them, any alterations and decisions that were made by the C-Grasp Team, and any other relevant notes. If the dataset's name is different than the notation in the "dataset" field, it is denoted in the titles below as such: Name (dataset == 'name_abbreviation')

## Databases/Secondary Sources:


These data were collected from databases composed of samples from compiled, relevant projects. These projects, when extractable, are specified listed under the "Project" field for each sample. 

### Dataset: Louisiana Barrier Island Comphrehensive Monitoring Program ("dataset"== "bicms")(https://www.usgs.gov/special-topics/gulf-of-mexico/science/barrier-island-comprehensive-monitoring-program-bicm)

Total Samples: 3392

From Website: The goal of the State of Louisiana Barrier Island Comprehensive Monitoring (BICM) program is to provide long-term data on the barrier islands of Louisiana that could be used to plan, design, evaluate, and maintain current and future barrier-island restoration projects. The U.S. Geological Survey (USGS) has partnered with the Louisiana Coastal Protection Restoration Authority [CPRA] to help achieve these goals. The BICM program used both historical and newly acquired data to assess and monitor changes in the aerial and subaqueous extent of islands, habitat types, sediment texture and geotechnical properties, environmental processes, and vegetation composition. BICM datasets included aerial still and video photography (multiple time series) for shoreline positions, habitat mapping, and land loss; light detection and ranging (lidar) surveys for topographic elevations; single-beam and swath bathymetry; and sediment grab samples. Products produced using BICM data and analyses included (but were not limited to) storm-impact assessments, rate of shoreline and bathymetric change, shoreline-erosion and accretion maps, high-resolution elevation maps, coastal-shoreline and barrier-island habitat-classification maps, and coastal surficial-sediment characterization maps.

Kindinger, J.L., Buster, N.A., Flocks, J.G., Bernier, J.C., and Kulp, M.A., 2013, Louisiana Barrier Island Comprehensive Monitoring (BICM) Program Summary Report: Data and Analyses 2006 through 2010: U.S. Geological Survey Open-File Report 2013–1083, 86 p.

#### The data used for C-GRASP is merged from BICM data from 2008 and 2015 databases. Used from this source data are location & date data, sampling coordinates, 3 cumulative distributions provided for samples (d10, d50, d90), and sample statistics in micrometers (Mean, Skewness, Kurtosis). Samples were collected on projects from dates ranging from 1955-2014. Details/Alterations:
 * Date was converted from yyyymmdd to yyyy-mm-dd.  Measurements were converted to mm units. Coordinates were reprojected from Northings & Eastings (epsg:26915) to decimal degrees (epsg=4326).
 * Cumulative distribution values were interpolated from the source data distributions via the methods in the Interpolation Notebook.
 * The "Notes" field is composed of the source files' Lithology, sediment color,equipment, sample_type, geoloc, depth, depth and comments fields (among other relevant fields identified in the sample notes).
 * The "Sample_ID" column comes from the source data "SAMPLE_ID" field.


### Dataset: Bureau of Ocean Energy Management Marine Minerals Information System ("dataset"== "BOEM")(https://mmis.doi.gov/BOEMMMIS/):

Total Samples: 9458

From Website: "OCS sand and gravel resources are vital sources of material for the construction of coastal protection and restoration projects, including efforts to protect coastal communities, national defense facilities, and federal and state infrastructure. In recent years, there has been a growing demand for OCS sediment for planned projects, as well as for emergency needs to restore areas damaged by natural disasters. On a national scale, little is known about the character, quantity, and location of sand resources on the OCS and the habitat it provides for biological communities.

Proponents of planned infrastructure projects are requesting higher volumes of OCS sediment, driven by diminishing resources in state waters and a high frequency of recent storms along the Atlantic and Gulf of Mexico coasts. Further, given the significant number of other ocean users (e.g., energy infrastructure, fiber optic telecommunication cables, electrical transmission lines, and fisheries), BOEM strives to reduce or eliminate the potential for multiple use conflicts or environmental impacts that could result from marine minerals projects. This can make it challenging to identify new potential areas from which to borrow or dredge sediment.

As the system continues to grow and mature, BOEM plans to add more features and data sets.

Key MMIS features include:

 * More than30 years of BOEM-funded geological and geophysical research data
 * Data from more than40 partners in federal, state and local government, academia and other entities
 * A viewer with more than 20 available data layers
 * Sediment data offshore 18 coastal states
 * GIS-mapping capabilities
 * Tools to download data into geodatabases, shapefiles, or .csv files
 * Statistics on sand volume, number of projects, number of states, and use trends
Links to environmental studies and assessments, data from state cooperative agreements"




#### The data used for C-GRASP is from the MMIS portal comprising of data merged from 7 spatial queries in order to aquire the entire sediment dataset and avoid the download cap. To replicate these steps, one must merge both downloaded "sample_table.csv" and "grab_samples.csv" files on the basis of ID in order to add coordinate data to sample measurements. Used from this source data are location & date data, sampling coordinates, and sample statistics in Phi units (Mean, Skewness, Median, Kurtosis). Samples were collected on projects from dates ranging from 1986-2016 Details/Alterations:

 * Measurements were converted to mm units. Source coordinates provided are in the EPSG 4326 datum. The "Notes" field is composed of the source files' Analysis date, lithology, sediment description, sediment color,equipment, sample_type, geoloc, depth, depth and comments fields (among other relevant fields identified in the sample notes such as OilPresent).
 * The "Sample_ID" column comes from the source data "SampleID" and "GrabID" fields, merged.
 * The "Sample_Type" field comes from the source data "Sampler" field


### Dataset: USGS East Coast Sediment Texture Database (https://woodshole.er.usgs.gov/project-pages/sediment/index.html)

Total Samples: 2846

<u>From Website </u> : The U.S. Geological Survey East-Coast Sediment Texture Database contains information on the collection, location, description, and texture of samples taken by marine sampling programs at the Woods Hole Coastal and Marine Science Center. Most of the samples are from the Atlantic Continental Margin of the United States, a small number of samples have been collected from a variety of other locations such as Lake Baikal, Russia, the Hawaiian Islands region, Puerto Rico, and Lake Michigan. At present, the database contains about 28,000 samples, including texture data for approximately 3,800 samples taken or analyzed by the Atlantic Continental Margin Program, a joint U.S. Geological Survey/Woods Hole Oceanographic Institution project conducted from 1962 to 1970 (Emery and Schlee, 1963; Hathaway; 1971). Texture data for approximately 24,000 samples analyzed by the Sediment Laboratory of the Coastal and Marine Geology Program of the U.S. Geological Survey, Woods Hole MA after 1980 make up the rest of the database. Although most records contain complete grain size analyses, some are simple bottom descriptions from rocky and bouldery locations where samples were not taken. Most of the samples were collected with some type of grab sampler; a few were obtained by coring. The information contained in this database is important because grain size is the most fundamental property of sediments. Geologists use information on sediment grain size to study trends in surface processes related to the dynamic conditions of transportation and deposition, ecologists use it when studying benthic habitats, engineers use it to study permeability and stability under load, geochemists use it to study kinetic reactions and the affinities of fine-grained particles and contaminants, and hydrologists use it when studying the movement of subsurface fluids (Syvitski, 1991). The basic structure of the database is a matrix where records are rows representing individual samples and the columns contain information on sample identification, navigation, classifications, analyzed parameters, and comments in 58 fields. The database, which can be accessed through the Data Catalog, is provided in three formats: comma delimited ASCII text (.csv), Microsoft Excel 2010 (.xls), and Esri shapefile (.shp).


McMullen, K.Y., Paskevich, V.F., and Poppe, L.J., 2014, GIS data catalog (ver. 3.0, November 2014), in Poppe, L.J., McMullen, K.Y., Williams, S.J., and Paskevich, V.F., eds., USGS east-coast sediment analysis: Procedures, database, and GIS data, U.S. Geological Survey Open-File Report 2005-1001, available online at http://pubs.usgs.gov/of/2005/1001/.

U.S. Geological Survey East-Coast Sediment Texture Database, online at URL:
http://woodshole.er.usgs.gov/project-pages/sediment/

 

#### The data used for C-GRASP provided in this source data are location & date data, sampling coordinates, seive measurements in Phi, and sample statistics in Phi (Mean, Skewness, Kurtosis). Samples were collected on projects from dates ranging from 1955-2014.  Details/Alterations:
 * These measurements were converted to mm units.
 *  date was standardized from year, month, and date fields to yyyy-mm-dd. 
 *  Cumulative distribution values were calculated via the methods in the Interpolation Notebook. The "Notes" field is composed of the source files' Lithology, Area (i.e. location), and comments fields. 

 *  The "Sample_ID" column comes from the source data "DB_ID" field.



### Dataset: Regional Offshore Sand Source Inventory (dataset=='rossi') (http://rossi.urs-tally.com/)

Total Samples: 2084

 From Website: This inventory of sand sources provides information for coastal engineers and geologists, project managers and the public to assess and identify potential offshore sand resources that are suitable for beach nourishment projects. ROSSI, an online information management system, can be searched through an online query builder, as well as with ArcIMS Geographic Information System mapping tools. The project has incorporated geological and geotechnical data for the Florida offshore continental shelf. The primary area of interest is within 10 miles of the shoreline. Data and information from farther offshore that assists in understanding or predicting potential sand resources within the area of primary interest is also included in the database.
 
Our purpose is to enable users to make the most informed decision possible when it comes to management of our Florida beaches and coastlines. Data that is both current and easily accessible are the key ingredients that facilitate the management process. Two basic types of data will be used in this effort. Spatial data will be used because the environment is geographic in nature. Tabular data will be used to store information about events which take place at locations stored as spatial data and referred to as spatial features.

The database stores information about sand samples. Information associated with sand samples includes, but is not limited to, granulometric data, bathymetry, seismic and sidescan sonar images, core photos, core logs, core descriptions, Munsell Color, metadata (information about the original data), and associated project information.

 

#### The data used for C-GRASP from the [ROSSI spatial query portal](http://rossi.urs-tally.com/Map). Used from this source data are location & date data, sampling coordinates, seive measurements in units phi, and sample statistics in Phi units (Mean, Skewness, Median, Kurtosis).  Samples were collected on projects from dates ranging from 1955-2014. Details/Alterations:
 * Cumulative distribution values were calculated via the methods in the Interpolation Notebook. Measurements were converted to mm units.
 *  Source data coordinates provided are in the EPSG 4326 datum.
 *  Date comes from the source data "SAMPLE_DATE" field standardized from m/d/y to yyyy-mm-dd
 *  The "Notes" field is composed of the source files' various shape, lithology, wentworth weight %, and lab comments a fields (among other relevant fields identified in the sample notes such as OilPresent).
 * The "Sample_ID" column comes from the source data "SampleID" and "GrabID" fields, merged.
 *  The "Sample_Type" field comes from the source data "COLLECTION_METHOD" field
 *  Location_Type comes from the source data 'BEACH_DATA" field



### Dataset: usSEABED ("dataset"== "US_SeaBed")(https://www.usgs.gov/programs/cmhrp/science/usseabed)

Total Samples: 443525

 From Website: "Information about seafloor characteristics from the beach to the deep sea improves the understanding of interactions between land and sea, effects of river discharge and sea level changes, distributions of benthic flora and fauna, location and type of resources, potential consequences of human activities on the oceans, and other critical issues. Large- and small-scale maps of the seabed, as well as reliable data over broad geographical areas, allow for integrated insights into these issues and more.

 To assist in addressing these issues, the USGS and the University of Colorado have created usSEABED.  The usSEABED datasets currently hold georeferenced point data for more than 300,000 data sites in U.S. waters from the beach to the deep sea, rivers, lakes, and estuaries. In usSEABED, existing data from the USGS and other research groups are processed and extended to maximize their density and usability creating unified, comprehensive, relationally linked datasets for mapping and analysis.  Source data include surficial and subbottom data from physical sampling equipment (grabs and cores) and virtual sampling such as descriptions from seafloor photographs and videos.

 In addition to quantified lab-derived data, the datasets of usSEABED also include estimated numeric values for those typical seabed characteristics—noted above—based on the extensive accumulation of word-based data in U.S. waters. These data are rich in information, but were previously difficult to quantify, map, plot, or use in comparative analyses or models.

 These descriptive data—from short sentences, small essays, or single phrases—are treated as a mathematical equation that is considered as a whole. Filters based on fuzzy set theory assign relative weight to each word in the description, and estimate the values of textural and other parameters. In addition, the textural implications of non-textural terms—such as 'broken shells' or Halimeda—are included in the calculation of grain-size parameters.

 The resulting numeric data, now useable in a GIS or model, should be considered "fuzzy"; that is, they give an approximation—not a rigorous measurement—of the assessed values."


#### The data used for C-GRASP  is merged from the MMIS portal from 7 spatial queries in order to aquire the entire sediment dataset and avoid the download cap. Used from this source data are location & date data, sampling coordinates, and sample statistics in Phi units (Mean, Skewness, Median, Kurtosis). Samples were collected on projects from dates ranging from 1856-2007. Details/Alterations:
 * Measurements were converted to mm units. Coordinates provided are in the EPSG 4326 datum. 
 * The "Notes" field is composed of the source files' Analysis date, lithology, sediment description, sediment color,equipment, sample_type, geoloc, depth, depth and comments fields (among other relevant fields identified in the sample notes such as OilPresent).  
 * The "Sample_ID" column comes from the source data "SampleID" and "GrabID" fields, merged.
 * The "Sample_Type" field comes from the source data "Sampler" field




## Primary Sources:

These data were collected from projects and publications that include grainsize measurements. Some of these projects include use of sample data from other publications or projects, the name of which can be found in the "Project" field for each sample. 

### Dataset:Clark (dataset == 'C_Alexander')

Total Samples: 98

This data was collected and provided by Dr. Clark Alexander, UGA Skidaway Institute of Oceanography using "Combined sieve (<4 phi) and Sedigraph (>4 phi) analysis technique" from onshore, beach samples from sampling campaigns on Jekyll Island, Sea Island, and St.Simons Island, GA in August, 2016.

##### The data used for C-GRASP provided in the source data are location & date data, sampling coordinates, and sample statistics in Phi (Mean, Sorting, Skewness, Kurtosis). Details/Analysis:
 * These measurements were converted to mm units and date was standardized from dd-MM-YY to yyyy-mm-dd.
 *  The Sample_ID type comes from column comes from the dataset's "Station" field.
 *   Sample_Type_Code for all files is assigned to 1


### Dataset: Massachusetts Beach Grain Size and Slope Data (dataset=='UMass') https://scholarworks.umass.edu/data/115/:

Total Samples: 989

From Website: This data repository contains grain size and beach face slope data from approximately 100 paired summer and winter transects collected along 18 separate beaches in southern New England. The study is focused to beaches of Massachusetts, which represents a particularly unique section of the Northeastern US coast in that it: 1) lies at the interface between New England’s paraglacial lowlands and Mid-Atlantic Coastal Plain, 2) spans both micro- and meso- tidal regimes, 3) encompasses a wide range of seasonally varying wave conditions, and 4) contains a diverse array of geomorphic and grain size characteristics. Between 2 and 10 intertidal transects were conducted for each of the sites depending on the length of the beach and accessibility. Transect positions were chosen at representative locations along the beach and equally spaced when possible. At each transect at least three separate samples were collected at near 1) high-tide, 2) mid-tide and 3) low-tide. When possible, additional samples were collected along berm crest, storm berms and dune. To assess seasonal variations in grain size distribution and slope, all transects along beaches were sampled and surveyed twice, once at the end of the summer and then revisited again at the end of the winter season. Surface sediments from the top 15-30 cm were collected from sites primarily composed of sand and pebbles (i.e. < 64 mm), and brought back to the University of Massachusetts in Amherst, MA for analysis. Exclusively sand samples were collected in 1-liter (1-quart) bags, predominantly sand samples were collected in 4-liter (1-gallon) bags and mixed sand and pebble samples in 19 -liter (5 gallon) buckets. Areas comprised primarily of cobbles and boulder (> 64 mm) were measured in the field using a gravelometer and standard pebble count technique. Sediment samples were washed and dried thoroughly to remove salt and debris (sticks, seaweed, etc.). Each sample was weighed and sub-divided into fractions greater and less than 4 mm. Distributions for grains greater than 4 mm were obtained via standard sieving techniques. Grain size distributions for sample fractions < 4 mm were measured on a CAMSIZER digital particle size analyzer capable of measuring particles between 30 μm and 4 mm. The elevation of each sampling location as well as inter-tidal beach slope for each transect was obtained using a using a Real Time Kinematic (RTK) GPS survey system or a total station survey system tied to local benchmarks.


Woodruff, J.D., Venti, N., Mabee, S., DiTroia, A., Beach, D., Massachusetts Beach Grain Size and Slope Data (2020)

##### The data used for C-GRASP provided in the source data are location & date data, sampling coordinates, and seive measurements in mm. Details/Analysis:
 * Latitude and Longitude values are from the source data coordinates, epsg:4326
 * Cumulative distribution percentile values are calculated from the seive measurements using methods from the Interpolation notebook.
 * Mean, standard deviation, skewness, kurtosis, and sorting were calculated using graphical moments (see above)
  * Sample_Type_Code for all files is assigned to 1
 * The "Location" field is from the source data's 'Beach' and field.
 * Date is stardardized from m/d/y to yyyy-mm-dd from the source data "CreationDate"
 * The "Notes" field comes from the source data "season", "beach face", and "transect" fields


### Dataset:McFall (dataset=='mcfall_via_weigl')

Total Samples: 35

This data was collected and provided by Dr. Brian C McFall, US Army Corps of Engineers, Coastal & Hydraulics Laboratory, and is composed of sediment sample measurements that he compiled from publications for his 2019 publication relating grainsize and slope measurements (see reference below).

##### The data used for C-GRASP provided in the source data are location & date data, sampling coordinates, and sample statistics in mm (Mean). Details/Analysis:
 * Sample_Type_Code is set to 1 for all data
 * The Sample_ID type comes from column comes from the dataset's "Label" field.

McFall, B. C. (2019). The relationship between beach grain size and intertidal beach face slope. Journal of Coastal Research, 35(5), 1080-1086.

### Dataset: SandSnap  https://navigation.usace.army.mil/SEM/SandSnapViewer':

Total Samples: 273

From Website: SandSnap is a collaborative project to engage citizen scientists, build a database of beach sand grain size, and educate the next generation about coastal processes. To understand how and why coastlines change, we must know the grain size of the sand on the beach. This information helps us model sand movement caused by the tides and waves, and allows us to predict how the coast will change.

Researchers and resource managers collect and analyze data to help understand how our coastlines have evolved and how they are likely to change in the future. Data on waves, topography, tides, and sand size are all needed to understand these complex systems.

Grain size is particularly difficult to collect because a scientist must visit each location to collect a sample. After the sample is collected, it must be physically processed in the lab to determine the sediment characteristics. This work is time consuming. Additionally, this process needs to be repeated because the sediment on the beach is constantly changing.

SandSnap allows anyone with a cell phone to take an image of the sand with a US coin and measure the sand’s grain size using a deep learning neural network (Buscombe 2020; McFall et al. 2020). The image and grain size information is readily available to the user and public in the Data Viewer. 

##### The data used for C-GRASP provided in the source data are location & date data, and cumulative distribution percentile values (d[10,16,25,50,65,75,84,90]) in mm. Samples were collected from images taken from 2018-2022 Details/Analysis:

 * Latitude and Longitude values were extracted from the source json file using geopandas, crs was set to epsg:4326
 * Other distributions (d[5,30,75]) are calculated from the source distributions provided using methods in the Interpolation notebook
 * Mean, standard deviation, skewness, kurtosis, and sorting were calculated using graphical moments (see above)
 * The Sample_ID type comes from column comes from the dataset's "user_sample_id" field.
 * Sample_Type_Code for all files is assigned to 1
 * The "Location" field is from the source data's 'location_town' and 'location_state' fields, merged
 * Date is stardardized from ms to yyyy-mm-dd from the source data "CreationDate"
 * The "Notes" field comes from the source data "notes" and "coin" fields




### Dataset: Susan Bell (dataset=='SusanBell_UniversitySouthernFlorida')  https://www.ncei.noaa.gov/access/metadata/landing-page/bin/iso?id=gov.noaa.nodc:0083190:

Total Samples: 464

From Website: Sampling for macroinfauna from swash zones of beaches along the SE Gulf of Mexico and SE coast of Florida was conducted from May 2010- July 2011. At each site, sampling was conducted using sediment cores (10cm diameter, 20cm deep) and all sampling was conducted within 2 hrs of low tide. Cores were collected within an approximately 100m linear distance parallel to the shoreline at each site. Some sites were intensively sampled across 3 subareas of the swash zone: high (near maximum wave run-up), mid, and low (near maximum wave back-wash) swash. Core contents were washed through a 1mm mesh and contents retained on the sieve were returned to the laboratory and frozen at 4°C. In the laboratory, samples were sorted and all macroinfauna removed. The dominant macroinfauna Donax variabilis (coquina) and Emerita talpoida (mole crab), making up over 99% of all organisms, were enumerated. Mean number (SD) per core and subarea within the swash zone are reported.

Additionally, three 60 ml cores were collected for sediment analyses from within the swash zones of all beaches, on or near each sampling date. Sediment samples were returned to the laboratory, dried for 24 h at 60°C, and median grain size determined. 

 	
Bell, Susan S.; University of South Florida - St. Petersburg (USF) (2012). Macroinfauna and sediment data from swash zones of sandy beaches along the SE Gulf of Mexico and SE Florida coast, 2010-2011, in response to the Deepwater Horizon Oil Spill (NCEI Accession 0083190). [indicate subset used]. NOAA National Centers for Environmental Information. Dataset. https://www.ncei.noaa.gov/archive/accession/0083190. 

##### The data used for C-GRASP provided in the source data are location & date data, sampling coordinates, and sample statistics in mm (Mean, Median, Skewness, Kurtosis). Details/Analysis:
 * Latitude and Longitude values were split from a combined Lat,Lon column in the source data
 * The Sample_ID type comes from column comes from the dataset's "Site/date ID" field.
 * Sample_Type_Code for all files is assigned to 1
 * The "Notes" field for this data come from the source data "Taxa" field and project metadata




