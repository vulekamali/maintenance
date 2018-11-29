---
description: >-
  Content on vulekamali.gov.za is located in a couple of different
  locations/services. Where you need to change information depends on what type
  of information you're trying to change.
---

# Adding/modifying information on the site

## Dataset names and descriptions

Dataset names and descriptions, and resources that are part of a dataset, are maintained in the [DataStore](../services/vulekamali-datastore/). 

If you want to upload lots of new documents, please have a look at the [Bulk-uploading](bulk-uploading-department-specific-documents.md) feature.

## Data summaries and charts on department pages

Data summaries and charts are based on

* One or more datasets in the [Datastore](../services/vulekamali-datastore/)
* The[ Data Manager](../services/vulekamali-data-manager/) making the summary or chart data available in [Page Data](../services/vulekamali.gov.za.md#page-data) for vulekamali.gov.za
  * querying the relevant Data API\(s\) for the right data for that page
  * perhaps transforming the data to be easy to use in vulekamali.gov.za
* vulekamali.gov.za presenting the data found in Page Data to the user

### Verifying changes before deploying to production

We verify changes to the Data Manager by building the site data against staging because we'll see that all years are working properly, not just the years we've been testing against locally. 

We'll see if any errors turn up. We get a commit in the static-budget-portal repository showing all the data changes introduced by this change to see if there are any surprises. This helps us notice mistakes in how data is modeled in the Datastore as well.



Deploy [Data Manager](../services/vulekamali-data-manager/#staging) changes to staging

Rebuild vulekamali.gov.za against staging

Check that the changes are correct

* See if the Travis CI build was successful
* See if the Travis CI build committed changes to the build branch you pushed for this check
* look at the diff of these changes, check that there aren't any surprising changes - did only the things you expect to change change?
* Start jekyll locally using this branch and check some pages to make sure that it's presenting correctly
* Think of corner cases and check them:
  * Did you only load data for the last two years? Is it doing the right thing for the years for which data isn't available?
  * Did you only load national data? Is it doing the right thing for provincial data?

Deploy the DataManager changes to production

* Merge the DataManager change pull request
* Deploy the new master branch to production

Rebuild vulekamali.gov.za against production

Deploy the production static-budget-portal changes

* Rebuild static-budget-portal against the production Data Manager and merge those changes to master

