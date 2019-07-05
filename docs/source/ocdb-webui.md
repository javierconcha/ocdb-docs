# User Manual for the OCDB WebUI

The main feature of the OCDB Database system is the provision of the data to the research community with an enhanced search facility. 


## Search

Any data the submitter has agreed to publish is searchable for the public. 
The OCDB WebUI offers a _Search_ interface. 
Data can be searched by acquisition date, product groups (listed [here](ocdb-search.md#groups)) and a _Search_ text field. In the _Search_ text field Users can enter any word(s) that will be used to screen the Database for any file containing that word(s). This field also allows to use the so-called Lucene syntax which enables you to search for specific field values and also allows chaining.

Please refer to the [__Search__](ocdb-search.md) chapter, for more details around the Lucene search syntax.

### Set region
Region for search can be set both either entering coordinates clicking on 'MANUALLY ENTER COORDINATES' button, or selecting a drawing a polygon on the map.

![advanced](docs/source/static/webui/select_region.png)

### Advanced options

In adavnced options menu, __single products__ can be selected (a list of standard name for variables is available [here](ocdb-standard-field-unit.md)). The wavelength option allows to filter __hyperspectral__ and __multispectral__ measurements. __Water depth__ threshold can also be set (when provided in metadata). Finally measurements taken in optically shallow waters van be either excluded or selected. 

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

![submission](docs/source/static/webui/submission_dialog.png)

Clicking on _Publish Data (Y)_ user agree in publishing the data right after the submission and quality check process. 
Select a date in _Publication Date_ instaed to delay the publication of the data belonging to this submission or leave the field empty to not allow publication at all.
Data for which publication is not agreed are ingested by the Database but accessible only to the Database administrators and the users. Publication agreement could be also provided anytime in the future, contacting ops@eumetsat.

Drag and copy or Select measurement files and documentation in the dedicated windows. File format and documentation rquired are described [here](ocdb-submission-format.md).
Click on _SUBMIT_ to initiate the validation process.
Files containing measurments are immidiately automatically checked according to [validation rules](ocdb-validation-rules.md)
Click on _List Files_ available among _Actions_ tools to see the results of the validation, shown for each file.

![list](docs/source/static/webui/list_ex.png)

In case of errors or warnings, for each file, click on _List Import Issues_ ![list](docs/source/static/webui/list.png) to show the list of error and worning messages.
Single files can be thus download ![down](docs/source/static/webui/download.png) and re-uploaded ![up](docs/source/static/webui/upload.png) and validated again.

In case of errors the status of the submission is set to _SUBMITTED_. Submissions containning errors, are note further procesed into the Database. If you need assistance, please contact ops@eumetsat.int indicating the identifier (_Submission label_) of the submission. 

If the validation succeeds, the status of the submission is set to _VALIDATED_ and further processed by Database administrators.

The picture below, summurises the whole process for submission and data validation.

![list](docs/source/static/webui/submission_process.png)

### Submission Actions 
In _Submit_ page, any registered user, after login, can manage his own submissions and submission files.

Each submission is listed with its label, submission date, (if provided) publication date, publication agreement, submission status and available actions.

__List Files__: 

![list](docs/source/static/webui/list.png)

It shows a table of selected submission files. Actions are applicable for each file (see _Submission File Actions_ section below).

![list](docs/source/static/webui/list_ex.png)

__Process Data__ (Admin users only):

![list](docs/source/static/webui/process.png)

Before they are processed, validated data are still not visible in the Database to anyone. __Process Data__ allows to start the processing action, at the end of which the data are searchable in the Database, but __ONLY__ by admin users and the owner of the data. 

__Publish Data__ (Admin users only):

![list](docs/source/static/webui/publish.png)

With _Publish Data_ data are processed (if not processed yet) into the Database and the status of the data is set to __PUBLISHED__ and is, therefore, searchable by the public in the Database. The publishing process checks whether the data has been already processed, to avoid data duplication.

__Delete Submission__ (Admin users only):

![list](docs/source/static/webui/delete.png)

The whole submission is deleted, including processed/published data from the search database.
 
__Halt Restart Submission__:

![list](docs/source/static/webui/play.png)

The user is able to halt a submission. This will denote the administrators that the user wished that the submission is __NOT__ to be processed. Once the process is halted, a __Restart__ button will appear, and user can use it to comunicate submission can be now processed.

__Cancel Submission__ (Admin users only):

Cancelling the submission allows to delete the database entries linked to this submission, keeping submission files.
This data can be anytime re-processed into the Database from the _Submit_ page.

![list](docs/source/static/webui/cancel.png)

### Submission Statuses

Through the above actions, the following statuses for submissions can be set

- __SUBMITTED__: submission contains errors and could not be validated
- __VALIDATED__: all submission files passed file format check (no errors, warnings allowed)
- __CANCELLED__: database entries linked to this submission have been canceled from the Database
- __PROCESSED__: submission data are searchable in the Database by submission owner and admin users
- __PUBLISHED__: submission data are searchable in the Database by anyone

### Submission File Actions

When clicking on listing files for a submission the data and document
files are listed. This new table provides the following actions:

__List Import Issues__:

List issues the system encountered when validating the data file.

![list](static/webui/list.png)

__Delete File__:

Remove the file from the submission.

![delete](static/webui/delete.png)

__Download File__:

Download the file if a change to the submission file is required.

![download](static/webui/download.png)


__Upload File__:

Re-upload a new version of the file. The old one is overwritten. The validation is re-run.

![reupload](static/webui/upload.png)


### Submission File Statuses

For each file, the fllowing status can be set:

- __ERROR__: there are errors in the format of the file
- __WARNING__: there are warnings regarding the format of the file. 
- __VALIDATED__: the file passed the format quality check


