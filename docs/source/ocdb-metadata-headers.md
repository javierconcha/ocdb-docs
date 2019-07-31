# Metadata Headers

Below, the list of required and optional headers is shown, with description and examples.
Note that some optional headers are recommended: they are used to perform measurements quality check. Measurements for which these metadata are not provided, cannot be flagged as best quality.

## Required Headers

The following headers are required to be pass validation check

* __investigators__ Full name of the contributor(s) of the data file. Principal investigator is listed first. Format: Name_Surname. A list of investigators already present in ocdb is available [here](ocdb-PI-affiliation-experiment-cruise.md/#investigators).

* __affiliations__ All investigator affiliations list. Format: Full_affiliation_name. Please do not exceed 25 characters. A list of existing affiliations already in ocdb is available [here](ocdb-PI-affiliation-experiment-cruise.md/#affiliations). 

* __contact__ An email address for one of the investigator(s) or a point of contact for the data file. 

* __experiment__ Full name long-term research project or funding program. It should be the same used in submission path. Please do not exceed 25 characters. A list of existing experiments already in ocdb is available [here](ocdb-PI-affiliation-experiment-cruise.md/#experiments). 

* __cruise__ The name of the specific cruise (or subset of the experiment) to which measurements are releted to. Please do not exceed 25 characters. A list of existing cruises already in ocdb is available [here](ocdb-PI-affiliation-experiment-cruise.md/#cruises).

* __documents__ Comma separated list of documents provided during the submission process, releted to the measurements included in the file.

* **data_type**
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

* **calibration_files** Comma separated list of files containing coefficients and techniques used to calibrate the instruments used in data collection, also attached to submission.

* **water_depth** Water depth at the measuring point (in meters). If not known, set it to _NA_.

* __missing__ Value (only one!) used as a numeric placeholder for any missing data in the data file. This value a non-zero number, e.g. -9999. If your file includes below_detection_limit and above_detection_limit  values are also provided (obsolete), please set them to different values then missing.

* __delimiter__ Indicates how the columns of data are delimited. Accepted delimiters include tab, space, and comma. Only a single (1) delimiter per file.

* __fields__ Comma-separated list of the field names for each column of data included in the data file, one for each column. Empty columns are not admitted.

* __units__ Comma-separated of the units for each column of data included in the data file. Every value in /fields must have a corresponding value listed here.


## Optional Headers
The following headers are optional. Some of them, if not provided, are automatically added by the system, after validation

* **start_date** The earliest date measurements in the file were collected (format: 'YYYYMMDD'). Added during submission processing if not provided.
 
* **end_date** The latest date measurements in the file were collected (format: 'YYYYMMDD'). Added during submission processing if not provided.

* **start_time** The earliest time measurements were collected on 'start_date' (format: 'HH:MM:SS [GMT]'), in Greenwich Mean Time (GMT). Added during submission processing if not provided.

* **end_time**
The latest time measurements were collected on 'end_date' (format: 'HH:MM:SS [GMT]'), in GMT. Added during submission processing if not provided.

* **north_latitude** Maximum latidude measurements in the file were collected (in decimal degrees, with a '[DEG]' trailer). Use negative values for latitudes south of the equator. Added during submission processing if not provided.
 
* **south_latitude** Minimum latidude measurements in the file were collected (in decimal degrees, with a '[DEG]' trailer). Use negative values for latitudes south of the equator. Added during submission processing if not provided.

* **east_longitude** Maximum longitude measurements in the file were collected (in decimal degrees, with a '[DEG]' trailer). Use negative values for longitude west of the Prime Meridian. Added during submission processing if not provided.

* **west_longitude** Minimum longitude measurements in the file were collected (in decimal degrees, with a '[DEG]' trailer). Use negative values for longitude west of the Prime Meridian. Added during submission processing if not provided.

* **station** The name of the station where measurements in the file were collected.

* **data_file_name** The name of the data file submitted. Added during submission processing if not provided. 

* **data_status** The condition, or status, of the data file. The value _preliminary_ is used when the data are new and the investigator intends to analyze the data further. The value _update_ indicates the data are being resubmitted and informs users that an additional resubmission will occur in the future. The value final is used when the investigator has no intention of revisiting the data set. Recommended

* **identifier_product_doi** The DOI (Digital Object Identifier; see http://www.doi.org/) associated with the experiment or the Dataset, if availabe

* **wavelength_option** Set to hyperspectral or multispectral, Required for products that have an associated wavelength.

* **instrument_model** Comma seprataed list of the model of the instruments whose measurements are being reported. Replace any spaces in the names with underscores. Recommended.

* **instrument_manufacturer** Comma seprataed list of the instrument manufacturers of the measurements that are being reported (e.g., Biospherical_Instruments_Inc.) Replace any spaces in the name with underscores. Recommended.

* **calibration_date** The most recent relevant calibration date for the primary instrument (format: 'YYYYMMDD'). Recommended.

* **cloud_percent** Percent cloud cover for the entire sky: 0 indicates no clouds and 100 indicates completely overcast. Could be also provided as a data field. Recommended.

* **secchi_depth** The secchi depth at the station where the data were collected (in meters). Could be also provided as a data field. Recommended.

* **wave_height** The wave height at the station where the data were collected (in meters). Could be also provided as a data field. Recommended.   

* **wind_speed** The wind speed at the station where the data were collected (in meters per second). Could be also provided as a data field. Recommended.   


## Headers added by OCDB staff
The following fields (marked as obsolete in the vaildation rules) are added and managed by OCDB staff.
* **received** Date when the file has been submitted into the Database by investigators
* **processed** Date when the file has been processed and published into the Database


## Example 
```bash
     /begin_header
     /investigators=Astrid_Bracher
     /identifier_product_doi=10.1594/PANGAEA.898929
     /affiliations=Alfred-Wegener-Institute_Helmholtz_Centre_for_Polar_and_Marine_Research
     /contact=Astrid.Bracher@awi.de
     /experiment=SO
     /cruise=SO234
     /data_file_name=Bracher_2019_SO234_db.txt
     /documents=see_comments
     /calibration_files=see_comments
     /data_type=cast
     /data_status=final
     /start_date=20140710
     /end_date=20140710
     /start_time=12:21:00 [GMT]
     /end_time=02:00:00 [GMT]
     /north_latitude=-20.1266 [DEG]
     /south_latitude=-29.695 [DEG]
     /east_longitude=58.82304 [DEG]
     /west_longitude=39.67942 [DEG]
     /water_depth=NA
     /wavelength_option=NA
     /instrument_model=NA
     /instrument_manufacturer=NA
     /calibration_date=NA
     /cloud_percent=NA
     /secchi_depth=NA
     /wave_height=NA
     /wind_speed=NA
     !
     ! COMMENTS
     !
     ! Citation:
     !  Bracher, Astrid; Cheah, Wee; Wiegmann, Sonja (2019): Phytoplankton pigment concentrations in the tropical Indian Ocean in July and August 2014 during RV Sonne cruises SO234 and SO235. Alfred Wegener Institute, Helmholtz Centre for Polar and Marine Research, Bremerhaven, PANGAEA, https://doi.org/10.1594/PANGAEA.898929. 
     !  Supplement to: Booge, Dennis; Schlundt, Michael; Bracher, Astrid; Endres, Sonja; Zäncker, Birthe; Marandino, Christa A (2018): Marine isoprene production and consumption in the mixed layer of the surface ocean - a field study over two oceanic regions. Biogeosciences, 15(2), 649-667, https://doi.org/10.5194/bg-15-649-2018
     !
     ! Data converted from PANGAEA.
     ! For docs and cal_files, see: https://doi.org/10.1594/PANGAEA.898929
     !
     /missing=-9999.
     /delimiter=comma
     /fields=station,sample,gear,date,time,lat,lon,depth,allo,asta,but-fuco,tot_chl_a,chl_b,chl_c3,chlide_a,diadino,diato,dino,dv_chl_a,dv_chl_b,fuco,hex-fuco,lut,neo,perid,phide_a,phytin_a,phytin_b,pyrophide_a,pyrophytin_a,viola,zea
     /units=none,none,none,yyyymmdd,hh:mm:ss,degrees,degrees,m,mg/m^3,mg/m^3,mg/m^3,mg/m^3,mg/m^3,mg/m^3,mg/m^3,mg/m^3,mg/m^3,mg/m^3,mg/m^3,mg/m^3,mg/m^3,mg/m^3,mg/m^3,mg/m^3,mg/m^3,mg/m^3,mg/m^3,mg/m^3,mg/m^3,mg/m^3,mg/m^3,mg/m^3
     /end_header
```