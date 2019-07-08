# Metadata Headers

Below, the list of required, optional or obsolete metadata headers is shown, with description and examples.

## Required Headers

The following headers are required to be pass validation check

### investigators
Full name of the contributor(s) of the data file. Principal investigator is listed first. Format: Name_Surname.
A list of investigators already present in ocdb is avaialble [here](ocdb-PI-affiliation-experiment-cruise.md/#investigators)
 
### affiliations
All investigator affiliations list. Format: Full_affiliation_name. Please do not exceed 25 characters.
A list of existing affiliations already in ocdb is avaialble [here](ocdb-PI-affiliation-experiment-cruise.md/#affiliations). 

### contact
An email address for one of the investigator(s) or a point of contact for the data file. 
 
### experiment
Full name long-term research project or funding program. It should be the same used in submission path. Please do not exceed 25 characters.
A list of existing experiments already in ocdb is avaialble [here](ocdb-PI-affiliation-experiment-cruise.md/#experiments). 
 
### cruise
The name of the specific cruise (or subset of the experiment) to which measurements are releted to. Please do not exceed 25 characters.
A list of existing cruises already in ocdb is avaialble [here](ocdb-PI-affiliation-experiment-cruise.md/#cruises). 

### documents
Comma separated list of documents provided during the submission process, releted to the measurements included in the file.

### data_type
Method used for the measurements. Accepted values include:
- cast (for vertical profiles)
- flow_thru (for continuous measurements as, e.g., underway flow through systems)
- above_water (for above water surface radiometry measurements)
- sunphoto (for sunphotometric measurements)
- mooring (for moored and buoy measurements)
- drifter (for drifter and drogue measurements)
- scan (for discrete hyperspectral measurements)
- lidar (for lidar/active remote-sensing measurements)
- pigment (for any laboratory measured pigment data (e.g. fluorometry, spectrophotometry, HPLC))
- bottle (for other types of measurements from water samples collected at discrete depths (e.g. nutrients))
- diver (for measurements made by a diver)
- auv (for measurements made by an Autonomous Underwater Vehicle)
- airborne (for measurements made via aircraft)
 
### calibration_files
Comma separated list of files containing coefficients and techniques used to calibrate the instruments used in data collection, also attached to submission.

### water_depth
Water depth at the measuring point (in meters). If not known, set it to _NA_.

### missing
Value (omly one!) used as a numeric placeholder for any missing data in the data file. This value a non-zero number, e.g. -9999. 
If your file includes below_detection_limit and above_detection_limit values are also provided, please set them to different values then missing.

### delimiter
Indicates how the columns of data are delimited. Accepted delimiters include tab, space, and comma. Only a single (1) delimiter per file.
 
### fields
Comma-separated list of the field names for each column of data included in the data file, one for each column. Empty columns are not admitted.
 
### units
Comma-separated of the units for each column of data included in the data file. Every value in /fields must have a corresponding value listed here.


## Optional Headers
The following headers are optional. Some of them, if not provided, are automatically added by the system, after validation

### start_date
The earliest date measurements in the file were collected (format: 'YYYYMMDD'). Added during submission processing if not provided.
 
### end_date
The latest date measurements in the file were collected (format: 'YYYYMMDD'). Added during submission processing if not provided.

### start_time
The earliest time measurements were collected on 'start_date' (format: 'HH:MM:SS [GMT]'), in Greenwich Mean Time (GMT). Added during submission processing if not provided.

### end_time
The latest time measurements were collected on 'end_date' (format: 'HH:MM:SS [GMT]'), in GMT. Added during submission processing if not provided.

### north_latitude
Maximum latidude measurements in the file were collected (in decimal degrees, with a '[DEG]' trailer). Use negative values for latitudes south of the equator. Added during submission processing if not provided.
 
### south_latitude
Minimum latidude measurements in the file were collected (in decimal degrees, with a '[DEG]' trailer). Use negative values for latitudes south of the equator. Added during submission processing if not provided.

### east_longitude
Maximum longitude measurements in the file were collected (in decimal degrees, with a '[DEG]' trailer). Use negative values for longitude west of the Prime Meridian. Added during submission processing if not provided.

### west_longitude

Minimum longitude measurements in the file were collected (in decimal degrees, with a '[DEG]' trailer). Use negative values for longitude west of the Prime Meridian. Added during submission processing if not provided.

### station
The name of the station where measurements in the file were collected.

### data_file_name
The name of the data file submitted. Added during submission processing if not provided. 