# Matchup Database files
Matchups Database (MDB) netCDF files, including matchups between OLCI and _in situ_ data from AERONET-OC network, MOBY buoy or downloaded from Copernicus OCDB or NAA SeaBASS Databases.

MDB files are provided through FTP, directly accesible from the Copernicus OCDB webpage.

For AERONET-OC and MOBY they are organised by month and updated at least on a monthly basis.

For _in-situ_ data downloaded from OCDB or SeaBASS, they are organised by products and updated on a monthly basis as well.

A short description of the content as well as the format follows.

## MDBs content
Each MDB file contains: 

- All OLCI level-2 or Level-1 Full Resolution products, **25x25 pixels** centered on site/measurement point

- For Level-2 MDB only: **Fully normalized** OLCI Remote Sensing Reflectance (Rrs) values up to 709 nm 

- For Level-2 MDB only: BRDF factors provided to retrieve original directional reflectance of OLCI products

- _In-situ_ measurements available for each point/site within **24 hours** OLCI acquisition

- For AERONET-OC MDB only: all original Version 3 data from AERONET-OC network

- For MOBY MDB only: all original data from MOBY Gold directory (from top and middle arms measurements if available, from top and bottom arms otherwise)

- Fully normalized _in-situ_ Rrs at OLCI nominal bands obtained through **band-shifting** (when Δλ>1 in the visible) and BRDF correction, when not applied already at source

- _in-situ_ measurements for cruises (chlorophyll HPLC or TSM or ADG443 or KD490 or Rrs or selected fluorometrically/spectrophotometrically derived chl-a), quality checked and optically weighted in case of profiles

Note that MDB content is **extended** beyond the data required for the baseline validations. The goal is to facilitate any additional investigation.
Users have to apply their own analyses to extract matchups, that are not screened neither for pixel validity nor applying any other criteria than the 24 hour time difference limit.
For baseline validations, the **recommended matchup protocols** should be followed.

## MDBs naming convention
Each MDB file is named using the following template:
MDB [PLATFORM] [LEVEL] [TYPE] [startDate] [endDate].nc
where:
- PLATFORM indicates satellite: A or B
- LEVEL indicates OLCI products level: 'L1' for EFR products or 'L2' for WFR products
- TYPE indicates _in-situ_ data type: 'AERONET_version3', 'MOBY', 'HPLC' (for chlorophyll HPLC measurements only), 'KD490', 'TSM', 'ADG', or CHL (for fluorometrically/spectrophotometrically derived chl-a) 
- [startDate]_[endDate] indicates the time range covered by the file

For example, MDB_A_L2_AERONET_version3_20160401_20160430.nc includes all matchups for AERONET-OC (version 3) for April 2016, with OLCI-A Level-2 products.

## MDB preparation
Monthly, MDB files are genereted through a Python module (called MDB_Builder).

The diagram below shows at high level the workflow followed in order to build MDB files.

![](static/webui/mdb_flow.png)

### Preparing OLCI data
OLCI Level-1 and Level-2 FR NTC products are systematically extracted over AERONET-OC sites and MOBY position (the second one, updated on a daily basis), stored as a single NetCDF files (one for each extraction).
The extraction is also performed occasionally, based on _in-situ_ measurement time and location, derived from SeaBASS and Copernicus OCDB Databases.
If for an extraction exists at least one _in-situ_ measurement within 24 hours before and after its acquisition time, the extraction is included in the MDB.
NetCDF files contain all the original products excepted for, for Level-2 MDB files, water reflectance, converted into Rrs, after BRDF correction for the first 11 bands. BRDF factors are retrieved using the same algorithm implemented in OLCI Level-2 Ocean Colour algorithm (chlorophyll concentration based), using Look-Up Tables (LUTs) provided in S3A Ocean colour parameters (OCP) Auxiliary Data File (ADF). Iteration is not required, since CHL_OC4ME product is used as input.

### Preparing in situ data: AERONET-OC
AERONET-OC data (downloaded from https://aeronet.gsfc.nasa.gov/cgi-bin/draw_map_display_seaprism_v3) are stored, for each site, in three different csv files containing original data up to, respectively, level 1.0, level 1.5 and level 2.0 quality assured data, as distributed from AERONET-OC network.

As for each station normalized water leaving reflectance (corrected for f/Q factor) Lwn_fQ at several bands is provided, with different number of channels or slight different central wavelengths for same band, sometimes different from OLCI bands, data need to be reorganised to provide Remote Sensing Reflectance (Rrs) at OLCI corresponding bands, before being ingested into MDB files. The whole dataset is thus prepared through the following steps:
- Level 1.5 and 2.0 data are merged together
- Rrs at each band "λ"  is obtained dividing Lwn_fQ by extra-atmospheric solar irradiance F0 (Thuillier et al., 2003), as in Eq. 1, for bands with central wavelength deviating from OLCI nominal central bands up to 1 nm in the visible. For longer wavelength the limit is relaxed up to 5 nm.
```
Equation 1: Lw_fQn(λ)/F0(λ)
```
- Band-shift correction (Mélin & Sclep, 2015) is applied when distance between central OLCI band and AERONET-OC central band wavelength is larger. 

### Preparing in situ data: MOBY
MOBY data are stored in ascii files, downloaded from MOBY Gold Directory (https://www.star.nesdis.noaa.gov/sod/moby/gold/). Normalised water leaving reflectance (Lwn) from MOBY is already provided at OLCI bands from 1 to 12, resampled according to S3A average OLCI Spectral Response Functions (SRFs). In order to retrieve Rrs, Lwn is thus divided by extraterrestrial solar irradiance (F0), and corrected for BRDF effect, as in Equation 2:

```
Equation 2: Lwn(λ)/F0(λ)*BRDF(λ)
```

where Lwn(λ) is MOBY Lwn2 for each band, provided in the Gold directory files, derived from top and middle arm measurements, when available, from top and bottom arm measurements otherwise. F0(λ) values are provided in OLCI L2 SRFs files. BBRDF factors are retrieved using the same algorithm implemented in OLCI Level-2 Ocean Colour algorithm (chlorophyll concentration based), using Look-Up Tables (LUTs) provided in S3A Ocean colour parameters (OCP) Auxiliary Data File (ADF). For the calculation of BRDF factors, wind speed provided in OLCI products is used (the mean values for the 25*25 pixels extraction); solar position is obtained by MOBY measurement time and location through _astropy_ Python package (Price-Whelan et al., 2018); chlorophyll concentration is obtained applying OLCI OC4ME algorithm on Rrs values (Lwn(λ)/F0(λ)) before BRDF correction. 

## References
- Clark, D.K., H.R. Gordon, K.J. Voss, Y. Ge, W. Broenkow, C. Trees. (1997). Validation of atmospheric correction over the oceans. Journal of Geophysical Research 102(D14): 17209-17217.
- Thuillier, G., M. Hers´e, P. C. Simon, D. Labs, H. Mandel, D. Gillotay, & T. Foujols. (2003). The solar spectral irradiance from 200 to 2400 nm as measured by the SOLSPEC spectrometer from the ATLAS 1-2-3 and EURECA missions. Solar Physics 214: 1-22.
- Zibordi, G., F. Mélin, J. Berthon, B. Holben, I. Slutsker, D. Giles, D. D’Alimonte, D. Vandemark, H. Feng, G. Schuster, B.E. Fabbri, S. Kaitala, and J. Seppälä (2009). AERONET-OC: A Network for the Validation of Ocean Color Primary Products. J. Atmos. Oceanic Technol. 26: 1634–1651.
- Price-Whelan et al. (2018). The Astropy Project: Building an Open-science Project and Status of the v2.0 Core Package. The Astronomical Journal 156: 123-141.
