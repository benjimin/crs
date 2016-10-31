crs
===

Intended to facilitate a standard python interface for geospatial coordinate 
reference systems.

Surrounding geospatial python ecosystem
---------------------------------------

### Geopandas

For wrangling data tables that have geometry columns (i.e. shapefiles).

Has "to_crs" method for transforming entire table column.

`crs` attribute expected in fiona dict form. 
Alternatively accepts epsg key-word argument.


### Fiona

For vector file IO (i.e. shapefiles).

crs attribute in dict form (proj4 string broken into components).
Also wkt available.
(Also can reassemble proj4 string?)

### Rasterio



### Datacube (AGDCv2)

CRS class.


### Arc? (and QGIS?)

### proj.4

### GDAL/OGR bindings? OSR.SpatialReference?