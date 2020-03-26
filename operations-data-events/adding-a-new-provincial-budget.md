# April: Adding a new provincial budget

## Steps

1. [Create the provincial departments for the new financial year using the bulk-upload process](adding-a-new-national-budget/adding-new-year-sphere-government-departments.md#add-new-departments)
2. [Upload the Estimates of Provincial Revenue structured fiscal data](../operations-actions/adding-modifying-information-on-the-site/adding-structured-fiscal-data-to-openspending.md#estimates-of-provincial-expenditure)
3. [Upload the Budget vs Actual Provincial Expenditure structured fiscal data](../operations-actions/adding-modifying-information-on-the-site/adding-structured-fiscal-data-to-openspending.md#budgeted-and-actual-provincial-expenditure)
4. [Upload the per-department EPRE PDF and XLSX files using the bulk upload too](../operations-actions/adding-modifying-information-on-the-site/bulk-uploading-department-specific-documents.md)

## Responsible roles

* Metadata Manager
* ETL Developer

## Data Requirements

* [Structured EPRE Expenditure data for the new financial year](../operations-actions/adding-modifying-information-on-the-site/adding-structured-fiscal-data-to-openspending.md#estimates-of-provincial-expenditure) - Public Finance Statistics
* [The authoritative list of provincial departments, their descriptions](https://github.com/vulekamali/datamanager#loading-departments-in-bulk) - ETL Developer
  * For provincial government we used the sections Vision, Mission and Core functions in the past.
* [The metadata for provincial department budget documents \(PDF and Excel\)](https://maintenance.vulekamali.gov.za/operations/adding-modifying-information-on-the-site/bulk-uploading-department-specific-documents#estimates-of-provincial-revenue-and-expenditure-vote-chapters) - ETL Developer + Metadata Manager

