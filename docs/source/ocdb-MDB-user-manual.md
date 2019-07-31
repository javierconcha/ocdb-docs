# Matchup Database files
Matchups Database (MDB) netCDF files, including matchups for AERONET-OC, MOBY and OCDB-subitted _in-situ_ data, are provided as well through FTP, directly accesible from the Database webpage.

For AERONET and MOBY they are organised by months and updated on a monthly basis.

For _in-situ_ data submitted to OCDB, they are organised by products and updated on a monthly basis as well.

A short description of the content as well as the format follows.

## MDBs content
Each MDB file contains: 

- All OLCI level-2 Full Resolution products, **25x25 pixels** centered on site/measurement point

- **Fully normalized** OLCI Remote Sensing Reflectance (Rrs) values up to 709 nm  

- BRDF factors provided to retrieve original directional reflectance of OLCI products

- Any _in-situ_ measurement available for each point/site within **24 hours** OLCI overpass

- In case of AERONET-OC: all original _in-situ_ data from AERONET Version 3 sites

- Fully normalized _in-situ_ Rrs at OLCI nominal bands obtained through **band-shifting** (when Δλ>1 in the visible)

- _in-situ_ measurements for cruises (HPLC or TSM or ADG443 or KD490 or Rrs or selected fluorometrically/spectrophotometrically derived chl-a), quality checked and optically weighted in case of profiles

Note that MDB content is **extended** beyond the data required for the baseline validations. The goal is to facilitate any additional investigation.
Users have to apply their own analyses to extract matchups, that are not screened neither for pixel validity nor applying any other criteria than the 24 hour time difference limit.
For baseline validations, the **recommended matchup protocols** should be followed.

## MDBs naming convention
Each MDB file is named using the following template:
MDB_[PLATFORM]_[LEVEL]_[TYPE]_[YYYYMMDD_YYYYMMDD].nc
where:
- PLATFORM indicates satellite: A or B
- LEVEL indicates OLCI products level: 'L1' for EFR products or 'L2' for WFR products
- TYPE indicates in itu data type: it could be 'AERONET_V3', 'MOBY', 'HPLC', 'KD490', 'TSM', 'ADG' depending on the in situ data type
- YYYYMMDD_YYYYMMDD indicates the time range covered by the file.

So for example, MDB_A_L2_AERONET_version3_20160401_20160430.nc includes all matchups for AERONET-OC (version 3) for April 2016, with OLCI A Level 2 products.

## MDBs data access policy
Any time a file is downloaded, user is requested to accept the following policy.

-------------------------------------------------------------------------------------------------------------------------------
### **OLCI-in situ Matchup Database Download Terms and Conditions**
The in situ data, contained in the Matchup Database files you are about to download, were derived from _in-situ_ data in the Copernicus Database of Ocean Colour In Situ Fiducial Reference Measurements. The data are contributed, on a voluntary basis, by different Principal Investigators (PIs) responsible for data collection and processing. The Database and the Matchup Database are maintained by EUMETSAT. See Matchup Database description for more information about matchup retrieval.

### **Using data**
Please consult with the PIs via e-mail on the use of the data. PIs’ names, affiliations, projects, and contacts are provided together with the data. 

### Guidelines for data use and publication
It is requested that every practical attempt is made to honour the following guidelines:
•	Always acknowledge the data providers! The acknowledgement may read: We thank the PI(s) for their effort in collecting the data used in this investigation and for making them available.
•	Publishing data from a 'few’ selected projects, sites or cruises: Please consider co-authorship for the PI(s).
•	If the in situ data are a principal component of the publication: Offer co-authorship to the PI(s).

If you accept the above conditions, please click the "Accept" button below to proceed downloading. If you do not agree with the above conditions, click "Do Not Accept" to return to the website.
EUMETSAT will not be held responsible for any data misuse.

-------------------------------------------------------------------------------------------------------------------------------
### **OLCI-AERONET-OC Matchups Database Download Terms and Conditions**
The AERONET-OC in situ data, contained in the Matchups Database files you are about to download, were derived from AERONET-OC network (Zibordi et al., 2009), available at https://aeronet.gsfc.nasa.gov/cgi-bin/draw_map_display_seaprism_v3. They are contributed by the International AERONET Federation. Each site has a Principal Investigator(s) (PI), responsible for deployment, maintenance and data collection. The PI has priority use of the data collected at the site. The PI is entitled to be informed of any other use of that site data. See Matchup Database description for more information about matchup retrieval.

### **Using data**
The Principal Investigator(s) name and contacts are indicated for each matchup in the Matchups Database files. If you intend to use the following data please consult with him/her/them via e-mail(s).
If you accept the above conditions, please click the "Accept" button below to download the file. If you do not agree with the above conditions, click "Do Not Accept" to return to the website. 
EUMETSAT will not be held responsible for any data misuse.

-------------------------------------------------------------------------------------------------------------------------------
### **OLCI-MOBY Matchups Database Download Terms and Conditions**
The _in-situ_ data, contained in the Matchups Database files you are about to download, were derived from NOAA CoastWatch/OceanWatch Marine Optical BuoY (MOBY) measurements, available at https://www.star.nesdis.noaa.gov/sod/moby/gold/. MOBY (Clark et al., 1997) is a NOAA funded project to provide vicarious calibration of ocean colour satellites (SeaWiFS, MODIS, and VIIRS). See Matchup Database description for more information about matchup retrieval.

### **Guidelines for data use and publication**
Always acknowledge NOAA CoastWatch – OceanWatch when using them and cite Marine Optical BuoY (MOBY, Clark et al., 1997).
If you accept the above conditions, please click the "Accept" button below to download the file. If you do not agree with the above conditions, click "Do Not Accept" to return to the website. 
EUMETSAT will not be held responsible for any data misuse.


## References
- Clark, D.K., H.R. Gordon, K.J. Voss, Y. Ge, W. Broenkow, C. Trees. 1997. Validation of atmospheric correction over the oceans. Journal of Geophysical Research 102(D14): 17209-17217.
- Zibordi, G., F. Mélin, J. Berthon, B. Holben, I. Slutsker, D. Giles, D. D’Alimonte, D. Vandemark, H. Feng, G. Schuster, B.E. Fabbri, S. Kaitala, and J. Seppälä (2009). AERONET-OC: A Network for the Validation of Ocean Color Primary Products. J. Atmos. Oceanic Technol. 26: 1634–1651.

## MDB variables list

