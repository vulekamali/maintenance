# vulekamali CKAN

## Usage on vulekamali

The [CKAN ](https://data.vulekamali.gov.za/)is used to manage the data displayed on Vulekamali, for example \(but not limited to\):

### [Datasets](https://data.vulekamali.gov.za/dataset)

Datasets contain Resources and metadata.

Metadata is just data about data, e.g. the description of what's contained in the dataset, and also classifying information like a specific financial year, sphere, department, or government that the dataset relates to.

Resources can be files \(structured data, semi-structured data, documents\), or links \(URLs\) to these or just to other websites.

Examples of structured data on vulekamali:

* Adjusted Estimates of Expenditure data
* Annual Report data
* Estimates of Provincial Expenditure data

### [Groups ](https://data.vulekamali.gov.za/group)\(Vulekamali categories\)

Groups allow us to categorise datasets

* Adjusted Budget Vote Documents
* Bills of Revenue
* Estimates of Provincial Expenditure

## Best Practices

* If your dataset exists across multiple financial years, create one dataset per financial year.
* It is better to upload documents rather than link to them - links can go stale.
* Dataset **titles** and **slugs** should be human readable i.e. contain full names instead of acronyms.
* No duplication.
* Include data for each financial year available.
* If you've deleted a dataset or resource - be sure to purge it afterwards, otherwise it won't actually be deleted and you'll get a message like "That URL is already in use" when trying to recreate it.

## Code and configuration

The [github repository](https://github.com/vulekamali/treasury-ckan) contains the code for the vulekamali CKAN installation.

