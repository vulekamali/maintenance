# Adding/modifying data and data descriptions

## Dataset names and descriptions

Dataset names and descriptions, and resources that are part of a dataset, are maintained in the [DataStore](../../services/vulekamali-ckan/).

If you want to upload lots of new documents, please have a look at the [Bulk-uploading](bulk-uploading-department-specific-documents.md) feature.

### Delay in updates reflecting on vulekamali.gov.za

Changes to public datasets in the DataStore, e.g. their title, description or resources may not reflect immediately due to caching. Some pages are cached to make them load faster for most users, but that means that they can take some time to reflect changes.

## Data summaries and charts on department pages

Data summaries and charts are based on

* One or more datasets in the [Datastore](../../services/vulekamali-ckan/)
* The[ Data Manager](../../services/vulekamali-data-manager/) making the summary or chart data available in [Page Data](../../services/vulekamali.gov.za.md#page-data) for vulekamali.gov.za
  * querying the relevant Data API\(s\) for the right data for that page
  * perhaps transforming the data to be easy to use in vulekamali.gov.za
* vulekamali.gov.za presenting the data found in Page Data to the user

Data summaries and charts that depend on custom processing for presentation on vulekamali in the DataManager require a software developer to modify or add, unless it is simply a case of updating the source data or adding another period of data and annotating it properly in the DataStore as documented in this manual.

