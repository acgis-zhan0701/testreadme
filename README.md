==Title==

Elevation for Each Ecological Zone

==Description==

User uses the selected R tools and packages to extract elevation information at four different level of ecological zones.
Four ecological zones are: ecozone, ecoprovince, ecoregion, ecodistrict.

==Requirement==

Make sure you have R Studio installed on your computer, you can download R Studio from https://www.rstudio.com/products/rstudio/download/.

==R packages==

This project requires four open source packages, as shown below:

1. raster:            
2. sf:                
3. foreign:           
4. exactextractr:     

 - Raster::raster tool is used to create a raster layer file from an existing file.
 - sf:: st_read tool is used to read shapefile.
 - foreign::wrtie.dbf tool is used to write a dataframe to a .dbf file.
 - exactextractr::extract tool is used to extract value from raster layer. 

==Input Data==

1. "Canada_DEM250m_LCC.tif". This subset of global 250m digital elevation model(DEM) data is produced by McMilian (2016).
2. "DEM_250M_C.tif". This is the modified version of the "Canada_DEM250m_LCC.tif". Negative elevation are converted to zero by using raster calculator.
3. GIS datasets for the different ecological zones. GIS dataset is produced by CanSIS, https://sis.agr.gc.ca/cansis/nsdb/ecostrat/gis_data.html
	- "Ecozone_shp.zip"
	- "Ecoprovince_shp.zip"
	- "Ecoregion_shp.zip"
	- "Ecodistrict_shp.zip"

==Output File==

Output files will be named as follows:

"XX_elevation"
(ex: "zn_elevation.dbf")

Four output database files are listed as follows:
	- "zn_elevation.dbf" for Ecozone
	- "pr_elevation.dbf" for Ecoprovince
	- "rg_elevation.dbf" for Ecoregion
	- "dt_elevation.dbf" for Ecodistrict
==Note==

Exactextractr::extract tool does not support Points vertor data when extracting values from raster layer. 
If you want to extract information from raster layers as points, raster::extract and terra:extract are both support points data.

Speed comparsion for raster::extract, terra:extract and exactextractr:extract. Source:https://tmieno2.github.io/R-as-GIS-for-Economists/extract-speed.html
raster::extract is the slowest.
If you have a small size raster layer (province wide), terra::extract would be the fastest.
If you have a large size raster layer (whole country), exactextractr::extract is the best choice. 
