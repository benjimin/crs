crs
===

Intended to facilitate a standard python interface for geospatial coordinate 
reference systems.

Probably also want a geoshape and georaster object (latter generalisable to xarray), 
and wrappers of basic operations (file io, rasterise, vectorise, transform, intersect/union, etc).

Note, crs support has been deprecated from GeoJSON specification.
(Formely, this was a place that preferred *urn:ogc:def:crs:authority:version:name*
identifiers, e.g. over EPSG identifiers.) It remains part of the Simple Features
specification (which includes WKT strings and SRID lookup tables; CRS is apparently
absent from WKB however).

Surrounding geospatial python ecosystem
---------------------------------------

Geopandas
    For wrangling data tables that have geometry columns (i.e. shapefiles).

    Has "to_crs" method for transforming entire table column.

    `crs` attribute expected in fiona dict form. 
    Alternatively accepts epsg key-word argument.


Fiona
    For vector file IO (i.e. shapefiles).

    crs attribute in dict form (proj4 string broken into components).
    Also wkt available.
    (Also can reassemble proj4 string?)

Rasterio
    For geospatial raster file IO.
    
    Can reproject (taking a pair of crs, plus respective affine transforms).
    Can also transform point coordinates between crs.
    
    crs in proj4 dict form. Also has a CRS wrapper class (e.g. providing limited methods
    for string or epsg code conversion, but not including equality tests).
    
Shapely
    For vector geometry operations in a Cartesian plane. 
    
    Support primarily for affine transformations; explicitly naive to coordinate systems.

Datacube (AGDCv2)
    CRS class.


Arc/QGIS
    ?

PyProj
    For transformations on the globe (wrapper of proj.4). 
    
    Proj.4 represents crs using strings, and is itself a de-facto standard. 
    In practice the proj4 library is the ultimate arbiter of whether
    two crs are identical (however multiple strings describe the same crs).
    

GDAL/OGR bindings? 
    crs corresponds to osr.SpatialReference instance
    (able to be exported as Wkt).
    
    These can be used to build osr.CoordinateTransformation objects, 
    which are accepted for the .Transform method of ogr Geometry objects.
    Also, gdal has facility for warping rasters (i.e. reprojection).
    
    
    
    
    
