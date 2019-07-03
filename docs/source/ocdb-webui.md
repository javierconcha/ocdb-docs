# User Manual for the OCDB WebUI

The aim of the __Copernicus Ocean Colour Database (OCDB)__ is to provide a platform to collect, organize and make available to ocean colour community ocean colour related _in-situ_ measurements, useful for satellite derived ocean colour products validation and algorithm development. 
This tool enables researchers to store in a organised Database their own _in-situ_ data, in a standard format (to guarantee interoperavility [Seabass data format](https://earthdata.nasa.gov/esdis/eso/standards-and-references/ascii-file-format-guidelines-for-earth-science-data/seabass-data-file-format) is used). 

The main features of the OCDB database system are the provision of the data to the research community with an enhanced search facility. 
__Quality check__ on format, measurements as well as on protocols complience is performed, and a quality flag is provided for each measurement. 
__Only when agreed__, _in-situ_ measurements are __published__ in the Database and made available to the public.  

Published, best quality data will be used to generate __Matchup files__ with Sentinel-3 Level 2 Ocean Colour OLCI A and B products.
In addition, when interested, registered users will be able to ask for the generation of matchup files for Sentinel-3 Level 2 Ocean Colour OLCI A and B for their own submitted data.

## Search

Any data the submitter has agreed to publish is searchable for the public. 
The OCDB WebUI offers a _Search_ interface. 
Data can be searched by acquisition date, product groups (listed in 'Groups' section [here](ocdb-variables-list.md)) and a _Search_ text field. In the _Search_ text field Users can enter a single keyword which will attempt to find data using the meta
data fields provided by the submitter. This field also allows to use the so-called Lucene syntax which enables you to search for specific field values and also allows chaining.

Please refer to the search chapter in OCDB Command Line Client and Python API section, for more details around the Lucene search syntax.

### Set region
Region for search can be set both either entering coordinates clicking on 'MANUALLY ENTER COORDINATES' button, or selecting a drawing a polygon on the map.

![advanced](docs/source/static/webui/select_region.png)

### Advanced options

In adavnced options menu, __single products__ (listed in 'Variables' section [here](ocdb-variables-list.md)) can be selected, the wavelength option allows to filter __hyperspectral__ and __multispectral__ measurements. __Water depth__ threshold could also be set (when provided in metadata). Finally measurements taken in optically shallow waters van be either excluded or selected. 

![advanced](docs/source/static/webui/advanced_options.png)

### Save search
Any query can be saved by any user, for replicating the same search in the feature (search otpions are saved, not the results!). Clicking on _SAVE SEARCH_ and assigning a name to it. Search qyery can be edited and/or shared clicking on _<>_ button.

![advanced](docs/source/static/webui/save_search.png)

## Submissions

In this section data submission process is described.
Only registered users are allowed to submit data. Please contact ops@eumetsat.int to be registered. 
Any registered user, after login in, can manage new and past submission in the _Submit_ page.

### New Submission

To add a __new submission__, click on _NEW SUBMISSION_ on the top right corner.
A new dialog will open. Please add an identifier (_Submission Label_) for the submission and a path (_affiliation/experiment/cruise_)
where submissions files will be stored under. The submissin label will univocally refers to a submission, while submission path could be the same for multiple submissions.

Clicking on _Publish Data (Y)_ user agree in publishing the data right after the submission and quality check process. 
Select a date in _Publication Date_ instaed to delay the publication of the data belonging to this submission or leave the field empty to not allow publication at all.
Data for which publication is not agreed are ingested by the Database but accessible only to the Database administrators and the users. Publication agreement could be also provided anytime in the future.


Once you initiate the submission by pushing "Submit" your data will be validated
using plausibility and validation rules (link to rules).

If the validation succeeds, the status of your submission will be VALIDATED 
otherwise SUBMITTED. If the system finds errors you can view them in the 
submission file table by clicking 'list files' on the submission table item. 


![submission](static/webui/submission_dialog.png)

![list](static/webui/submission_validation_results.png)

![list](static/webui/submission_process.png)

### Submission Actions

__List Submission Files__:

Views a table of submissions files and enables you to apply actions (see
chapter Submission File Actions). 

![list](static/webui/list.png)
![list](static/webui/submission_list.png)

__Process Data__:

Until now, the data listed in the submission is not visible in the database.
The button __Process Data__ will start the processing action. When finished,
the data will be visible, burt __ONLY__ to the submitting user and admins. 

![list](static/webui/process.png)

When pushing this button, the data will be processed into the database and, 
therefore, available for searching ONLY for administrators and the submittor.

__Publish Data__:

__Publish Data__ will do exactly the same as __Process Data__, but will set
the status of the data to __PUBLISHED__ and is, therefore, visible and
downloadable by the public. The publishing process will check whether the
data has been processed already to avoid data duplication. 

![list](static/webui/publish.png)

__Delete Submission__:

The whole submission will be deleted including processed/published data from the search database.

![list](static/webui/delete.png)
 
__Halt Restart Submission__:

![list](static/webui/play.png)

The user is able to halt a submission. This will denote the administrators that the
user wished that the is __NOT__ to be processed. Once the process is halted, the user 
can a __Restart__ button will appear. 

__Cancel Submission__:

Cancelling the submission will delete the database entries linked to this submission.

![list](static/webui/cancel.png)

### Submission Statuses

From the above actions the following statuses for submissions derive.

- Submitted
- Validated
- Cancelled
- Processed
- Published

### Submission File Actions

When clicking on listing files for a submission the data and document
files are listed. This new table provides the following actions:

__List Validation Issues__:

List issues the system encountered when validating the data file.

![list](static/webui/list.png)

__Delete File__:

Remove the file from the submission.

![delete](static/webui/delete.png)

__Download File__:

Download the file if a changed to the submission file is required.

![download](static/webui/download.png)


__Upload File__:

Reupload a new version of the file. The old one will be overwritten. The 
validation will be re-run.

![reupload](static/webui/upload.png)


### Submission File Statuses

- ERROR
- VALIDATED
- WARNING


