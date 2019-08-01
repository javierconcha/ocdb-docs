# Contribute Data

The Database has been designed in order to guarantee easy access to data, a strong search engine, automation via command line access and interoperability with other Databases (in particular NASA SeaBASS Database).
For this reason, data can be contributed through the same simple data format, easily expandable and flexible, selected by NASA Ocean Biology Processing Group for the SeaBASS Database.

Users need to be registered to the Database in order to submit data.

Data submission can be done either via the [Database webUI ](ocdb-webui.md) or the [Command Line Interface as well as the Python API](ocdb-api-cli.md).

## Data Submission Policy
For data submission policy please refers to Data Policy terms available [here](ocdb-data-access-policy.md)


## Data Format

In the data submission process, any file is automatically checked for its own format and completeness (the list of rules can be found in the jason file validation_rules.json).

* Submitted data files need to be two-dimensional ASCII text files
* Data are preceded by metadata headers. The list of optional and requested metadata headers is available [here](ocdb-metadata-headers.md)
* Metadata headers section is introduced by 'begin_header' and closed by 'end_header' headers
* Any metadata header is preceded by '/'
* Comments can also be added inside the metadata headers section, but using a exclamation mark ('!') at the beginning of each comment line
* Headers should not include any white space. Separate words with an underscore. The only exception is for comment lines
* Columns may be delimited by spaces, tabs, or commas, as indicated in the 'delimiter' headers
* Field names and units are defined as a list using respectively 'fields' and 'units' headers. The complete list of standard field names and units is available [here](ocdb-standard-field-unit.md). Field names and units are not case sensitive.
* File names must not contain spaces or special characters (except for hyphens, underscores, and periods) and must be unique within a submission. Descriptive names including cruise and experiment names as well as date, depth or any other significant information is strongly recommended but not required.

## Documentation

For each submission, data files should be accompanied by documentation describing any measurement protocols adopted and Calibration/Instrument Reports and any other information useful to gather the quality of the data provided.
The reports should describe calibration equations and values, how the instruments were calibrated, and what types of corrections or data analysis were applied to derive the values submitted to the Database.
Users are also encouraged to submit any other information about deployments and/or cruises, they consider useful for data quality evaluation.

Documents can be submitted at the same time of data files via the [Database webUI ](ocdb-webui.md) or the [Command Line Interface as well as the Python API](ocdb-api-cli.md).

## Data Quality

Data submitted to the Database should be calibrated, depth-adjusted, unbinned, after quality checked analysis has been performed and bad quality measurements have been excluded. The process used to derive values provided and to perform the quality check analysis should be fully desribed in the documentation.
Any correction applied to data (e.g. normalization by surface irradiance, self-shading effect corrections etc.) should be listed and methods described.

On the other hand, a further analysis is done by Database administrators, after data has been submitted to the system and before it is processed into the Database. 
This analysis allow to label each measurement or set of measurements with a good quaity flag, adding a boolean variable to the data '[field_name]_qa' being 1 for 'good' data and 0 for 'questionable' data.
The analysis is based on the completeness of protocol and quality check analysis description as well as some few further checks for:
- data satus (should be the final version of data)
- clear sun and low cloudiness conditions and low Irradiance variability (for each cast) for radiometric measurements
- outliers removal

For this reason, users are strongly recommended to submit together with data, complete protocols and analysis descriptions, as well as any ancillary data they could provide.

Finally, information about uncertainty and/or replicates, should be reported (e.g. as standard deviation fiels (e.g., <measurement>_sd, like "chl_sd"), together with bincount (e.g. <measurement>_bincount). 

Users submitting data could be of course involved in the quality check process by the administrator, whenever additional information or feedback are required.

