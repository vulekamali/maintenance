# Adding/modifying information on the site

## Dataset names and descriptions

Dataset names and descriptions, and resources that are part of a dataset, are maintained in the [DataStore](../../services/vulekamali-datastore/).

If you want to upload lots of new documents, please have a look at the [Bulk-uploading](bulk-uploading-department-specific-documents.md) feature.

### Delay in updates reflecting on vulekamali.gov.za

Changes to public datasets in the DataStore, e.g. their title, description or resources, result in automatic rebuilds of the data presented in the [vulekamali.gov.za static site](../../services/vulekamali.gov.za.md). **This takes about 25 minutes** to complete and for the changes to reflect on vulekamali.gov.za.

Progress of data updates can be monitored by finding builds titled `Rebuild with new/modified dataset` on the [build list](https://travis-ci.org/vulekamali/static-budget-portal/builds).

Note: Since each change triggers a rebuild, two builds might be triggered shortly after one another if multiple changes are saved to datasets. This is because the first change triggers a build, and subsequent changes trigger another build in case the first build has already progressed past the part of the site that was modified shortly after the first change. In that case, the changes will be reflected after the second build succeeds.

## Data summaries and charts on department pages

Data summaries and charts are based on

* One or more datasets in the [Datastore](../../services/vulekamali-datastore/)
* The[ Data Manager](../../services/vulekamali-data-manager/) making the summary or chart data available in [Page Data](../../services/vulekamali.gov.za.md#page-data) for vulekamali.gov.za
  * querying the relevant Data API\(s\) for the right data for that page
  * perhaps transforming the data to be easy to use in vulekamali.gov.za
* vulekamali.gov.za presenting the data found in Page Data to the user

Data summaries and charts that depend on custom processing for presentation on vulekamali in the DataManager require a software developer to modify or add, unless it is simply a case of updating the source data or adding another period of data and annotating it properly in the DataStore as documented in this manual.

