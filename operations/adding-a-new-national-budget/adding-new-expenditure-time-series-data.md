---
description: >-
  This page describes the process of adding new data to the Expenditure Time
  Series dataset.
---

# Adding new Expenditure Time Series data

## What is the Expenditure Time Series dataset?

The ETS is a dataset which combines all the ENE, AENE and AR datasets across all financial years into one dataset. 

## How to add the new data to the ETS dataset

### 1. Pipeline

The ETS is built with the datapackage-pipelines library, similar to how other datasets are structured and put together.

An example workflow for adding the 2019-20 ENE dataset to the ETS looks like this:

* Create pipeline to structure the 2019-20 ENE dataset received from National Treasury.
* Upload processed dataset to the DataStore.
* Add new section to ETS pipeline \(load, filter etc.\) and pull in the dataset from CKAN via the CSV download link.
* Run the new ETS pipeline and verify that the dataset has been processed correctly.

Remember to use the correct git workflow to manage your new additions, e.g. branching and opening PRs to merge into master.

### 2. OpenSpending

Upload the new ETS dataset to OpenSpending:

* With the correct column types
* With a new unique identifier, to avoid overwriting the original in case something goes wrong.

After the dataset has been uploaded and processed, you'll need to:

* Link vulekamali to the new dataset unique id
* Trigger a rebuild
* Verify the data is online \(e.g. check Actual vs Budgeted charts on department detail page\)

