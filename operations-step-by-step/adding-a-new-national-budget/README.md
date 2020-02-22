---
description: >-
  How to add a new national budget when it is tabled in February in advance of a
  new financial year
---

# February: Adding a new national budget

## Steps

When the budget speech starts, and again when the data is available on vulekamali, [the homepage notices need to be updated.](update-the-homepage-state.md)

The following is required to add a new national budget to vulekamali

### Standard budget documents

1. The [Division of Revenue Bill must be added to ](adding-a-new-division-of-revenue-bill.md)CKAN
2. The links to standard budget documents must be added, e.g. Budget Review, People's Guide, Budget Highlights...

### Structured data for updated charts and department pages

1. The [new financial year, sphere, government, and departments must be added to the ma](adding-new-year-sphere-government-departments.md)in site Admin
2. The ENE Vote e-publications and accompanying per-vote Excel files must be added to the Datastore
   * Follow the [bulk-uploading procedure](../../operations-actions/adding-modifying-information-on-the-site/bulk-uploading-department-specific-documents.md) to upload the documents, and
   * see the [section for specifics on ENE conventions](../../operations-actions/adding-modifying-information-on-the-site/bulk-uploading-department-specific-documents.md#estimates-of-national-expenditure-vote-chapters) to ensure you upload them correctly
3. The [ENE  structured fiscal dataset must be added to OpenSpending, and the data on OpenSpending added to CKAN ](../../operations-actions/adding-modifying-information-on-the-site/adding-structured-fiscal-data-to-openspending.md#estimates-of-national-expenditure)
4. The[ new CPI Inflation dataset must be added to the CKAN Datastore ](adding-cpi-inflation-data.md)
5. The Budget vs Actual dataset must be updated with the new Main Appropriation data from the ENE
6. The Consolidated budget structured fiscal data must be added to OpenSpending, and the data on OpenSpending added to CKAN
7. National Infrastructure Projects must be updated

When the allocations and frameworks for conditional grants to municipalities and provinces are gazetted,

1. [Add the Conditional Grant Frameworks](adding-conditional-grant-frameworks.md)

## Dataset checklist

These are all the datasets needed to upload a new national budget to vulekamali and where to source them.

| Dataset \(link is example structured for vulekamali\) | Source \(link is source format\) |
| :--- | :--- |
| [Department metadata \(name, purpose, etc\)](adding-new-year-sphere-government-departments.md#adding-editing-departments-in-bulk) | Jeffery Smith, Public Finance Statistics |
| [URLs and metadata for ENE Vote ePublication PDFs and XLSX file per budget vote](../../operations-actions/adding-modifying-information-on-the-site/bulk-uploading-department-specific-documents.md#metadata-spreadsheet-template) | Scraped from www.treasury.gov.za |
| [ENE structured fiscal dataset](http://datastore.openspending.org/b9d2af843f3a7ca223eea07fb608e62a/estimates-of-national-expenditure-2019-20-uploaded-2019-02-20t1910/final/data/ene-2019-20.csv) | Jeffery Smith, Public Finance Statistics |
| [CPI Inflation structured dataset](https://vulekamali.gov.za/datasets/cpi-inflation) | Jeffery Smith, Public Finance Statistics |

