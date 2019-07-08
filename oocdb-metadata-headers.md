# Metadata Headers

Below, the list of required, optional or obsolete metadata headers is shown, with description and examples.

## Required Headers

The following headers are requird to be pass validation check

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
- scan for discrete hyperspectral measurements
    lidar for lidar and other active remote-sensing measurements (e.g. MPL)
    pigment for laboratory measured pigment data (e.g. fluorometry, spectrophotometry, HPLC)
    bottle for other types of measurements from water samples collected at discrete depths (e.g. nutrients)
    diver for measurements made by a diver
    auv for measurements made by an autonomous underwater vehicle (auv)
    airborne for measurements made via an aircraft

 
calibration_files

required
Refers to supplementary files containing coefficients and techniques used to calibrate the instruments used in data collection.
start_date

required

The earliest date data in the file were collected (in YYYYMMDD).


For example, a start date of March 14, 2001 would be written as /start_date=20010314

 
end_date

required

The latest date data in the file were collected (in YYYYMMDD).


For example, an end date of March 14, 2001 would be written as /end_date=20010314

 
start_time

required

The earliest time of day measurements were collected during the start_date in the file (in HH:MM:SS). Times are in Greenwich Mean Time. This header requires a [GMT] trailer.


For example: /start_time=12:30:00[GMT]

 
end_time

required

The latest time of day data data were collected during the end_date in the file (in HH:MM:SS). Times are in Greenwich Mean Time. This header requires a [GMT] trailer.


For example: /end_time=13:30:00[GMT]

 
north_latitude

required

The farthest north data in the file were collected (in decimal degrees). This header requires a [DEG] trailer. Latitudes south of the equator are negative.


For example: /north_latitude=42.750[DEG]

 
south_latitude

required

The farthest south data in the file were collected (in decimal degrees). This header requires a [DEG] trailer. Latitudes south of the equator are negative.


For example: /south_latitude=36.500[DEG]

 
east_longitude

required

The farthest east data in the file were collected (in decimal degrees). This header requires a [DEG] trailer. Longitudes west of the Prime Meridian are negative.


For example: /east_longitude=-68.500[DEG]

 
west_longitude

required

The farthest west data in the file were collected (in decimal degrees). This header requires a [DEG] trailer. Longitudes west of the Prime Meridian are negative.


For example: /west_longitude=-85.750[DEG]

 
water_depth

required

The water (bottom) depth at the station where the data were collected (in meters).

 
missing

required

Refers to the NULL value used as a numeric placeholder for any missing data in the data file. Note that each row of data must contain the same number of columns as defined in the /fields and /units headers. Only one (1) missing value is allowed per file. This value MUST be non-zero. A common choice is -9999 or some other large negative number large enough to never be confused with valid measurements. If your file includes below_detection_limit or above_detection_limit values, use different NULL values for each.

/missing=-9999

 
delimiter

required

Indicates how the columns of data are delimited. Accepted delimiters include tab, space, and comma. Only a single (1) delimiter is permitted per data file.

 
fields

required

A list of the field names for each column of data included in the data file. Each entry describes the data in a single (1) column, and every column must have an entry.

 
units

required

A list of the units for each column of data included in the data file. Every value in /fields must have an appropriate value listed here.



### station
(optional, if station appears in /fields= list)

The name of the station or deployment where data in the file were obtained.


data_file_name

required

The current name of the data file.
