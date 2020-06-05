---
description: >-
  How to add a new national budget when it is tabled in February in advance of a
  new financial year
---

# February: Adding a new national budget

## Steps

When the budget speech starts, and again when the data is available on vulekamali, [the homepage notices need to be updated.](update-the-homepage-state.md)

The following is required to add a new national budget to vulekamali

### Immediately upload key budget documents

1. [Upload the Division of Revenue bill resources](../../operations-actions/adding-modifying-information-on-the-site/adding-a-new-division-of-revenue-bill.md)
2. [Upload the key budget documents](../../operations-actions/adding-modifying-information-on-the-site/uploading-key-budget-documents.md#original-budget)

### Structured data for updated charts and department pages

1. The [new financial year, sphere, government, and departments must be added to the ma](adding-new-year-sphere-government-departments.md)in site Admin
2. The ENE Vote e-publications and accompanying per-vote Excel files must be added to the Datastore
   * Follow the [bulk-uploading procedure](../../operations-actions/adding-modifying-information-on-the-site/bulk-uploading-department-specific-documents.md) to upload the documents, and
   * see the [section for specifics on ENE conventions](../../operations-actions/adding-modifying-information-on-the-site/bulk-uploading-department-specific-documents.md#estimates-of-national-expenditure-vote-chapters) to ensure you upload them correctly
3. The [ENE  structured fiscal dataset must be added to OpenSpending, and the data on OpenSpending added to CKAN ](../../operations-actions/adding-modifying-information-on-the-site/adding-structured-fiscal-data-to-openspending/#estimates-of-national-expenditure)
4. The[ new CPI Inflation dataset must be added to the CKAN Datastore ](adding-cpi-inflation-data.md)
5. The Budget vs Actual dataset must be updated with the new Main Appropriation data from the ENE
6. The Consolidated budget structured fiscal data must be added to OpenSpending, and the data on OpenSpending added to CKAN
7. [National Infrastructure Projects must be updated](adding-updating-infrastructure-projects.md)

### Publish the new financial year

When all the above is completed, the [new financial year](adding-new-year-sphere-government-departments.md) can be marked as `published`. This will result in the homepage and department pages showing data using the newly-updated data.

## Dataset checklist

These are all the datasets needed to upload a new national budget to vulekamali and where to source them.

| Dataset \(link is example structured for vulekamali\) | Source \(link is source format\) |
| :--- | :--- |
| [Department metadata \(name, purpose, etc\)](adding-new-year-sphere-government-departments.md#adding-editing-departments-in-bulk) | [Public Finance Statistics](adding-new-year-sphere-government-departments.md#adding-editing-departments-in-bulk) |
| [URLs and metadata for ENE Vote ePublication PDFs and XLSX file per budget vote](../../operations-actions/adding-modifying-information-on-the-site/bulk-uploading-department-specific-documents.md#metadata-spreadsheet-template) | [Scraped from Financial year budget page on www.treasury.gov.za &gt; Estimates of National Expenditure &gt; ePublications](http://www.treasury.gov.za/documents/national%20budget/2019/booklets.aspx) |
| [ENE structured fiscal dataset](http://datastore.openspending.org/b9d2af843f3a7ca223eea07fb608e62a/estimates-of-national-expenditure-2019-20-uploaded-2019-02-20t1910/final/data/ene-2019-20.csv) | [Public Finance Statistics](../../operations-actions/adding-modifying-information-on-the-site/adding-structured-fiscal-data-to-openspending/#examples) |
| [CPI Inflation structured dataset](https://vulekamali.gov.za/datasets/cpi-inflation) | [Public Finance Statistics](adding-cpi-inflation-data.md) |
| [Consolidated expenditure budget structured dataset](https://data.vulekamali.gov.za/dataset/d190dad6-45fc-499c-a808-459b3cfe909b/resource/be6eff6c-35c6-4a9b-a81e-d7f2c9c5de68/download/consolidated-2019-20.csv) | [Financial year budget page on www.treasury.gov.za &gt; Budget Data and Time Series in Excel Format &gt; Consolidated accoutn of government in excel format](http://www.treasury.gov.za/documents/national%20budget/2019/review/Budget%202019%20-%20Consolidated%20account%20Pivot.xlsx) |
| [Division of Revenue Bill, Schedules, Annexures, and Allocations structured table](https://vulekamali.gov.za/datasets/division-of-revenue-bills/division-of-revenue-bill-2020-21) | [Intergovernmental Relations](../../operations-actions/adding-modifying-information-on-the-site/adding-a-new-division-of-revenue-bill.md) |

