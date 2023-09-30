---
description: >-
  This page describes the process of adding a new Division of Revenue bill to
  vulekamali
---

# Adding a new Division of Revenue bill

## Locating the Division of Revenue bill

It can be found on[ National Treasury's website](http://www.treasury.gov.za) under "Budget Information -> National -> {YEAR}"

## Upload to CKAN

The Division of Revenue bill must be uploaded to the [CKAN](https://data.vulekamali.gov.za/).

On the dataset in CKAN, there should be:

* One DOR per financial year
* One dataset per DOR
* Resources
  * One for the full DOR PDF
  * Excel file(s) for the Schedules and Annexures
  * Excel file for the Alocation of Equitable Share - the resource title MUST be `Allocation of Equitable Share` and it MUST be an XLSX file.

Each year's Division of Revenue bill should be a separate dataset with:

* One PDF resource (Division of Revenue bill)
* One XLS resource (Annexes)
  * (in 2019-20 there were two excel files - Annexes and Schedules - we uploaded both.)
* Financial Year set to the correct year

Use the naming convention from previous years.

Each DOR should be in the "Division of Revenue Bills" group.

## Adding to vulekamali

After the dataset has been uploaded to CKAN, it should show up at [https://vulekamali.gov.za/datasets/division-of-revenue-bills](https://vulekamali.gov.za/datasets/division-of-revenue-bills).

## Format for the Allocation of Equitable Share for CKAN

This is a structured file that must be formatted precisely as specified for the charts using its data online to work properly.

* Column headings must be precisely as follows, including capitalisation and underscores
* Values must be precisely as per the options specified
* Values should not have any additional spacing

| Column name            | Value specification                                                                                            |
| ---------------------- | -------------------------------------------------------------------------------------------------------------- |
| sphere                 | `national`, `provincial`, or `local`                                                                           |
| parent\_name           | Only provided for local and provincial spheres, the province for municipalities, or South Africa for provinces |
| municipality\_type     | Only provided for local sphere: `metro`, `local`, or `district`                                                |
| geo\_code              | Country, province or municipal demarcation code.                                                               |
| geo\_name              | Human-readable name of the location                                                                            |
| amount\_rand\_thousand | Integer amount allocation to that geography (or to the sphere for national)                                    |

{% file src="../../.gitbook/assets/equitable-share-allocations-2020-03-15t1130.xlsx" %}
Example equitable share allocations
{% endfile %}

### Format for the Allocation of Equitable Share for Wazimap

#### Equitable Share to Provinces

Prepare the dataset

1. Open the latest version of this dataset, e.g. by downloading the file uploaded to the latest version of this dataset on Wazimap in Excel
2. Find the latest Division of Revenue Bill Schedules in Excel Format On the [National Treasury website](https://www.treasury.gov.za/documents/national%20budget/default.aspx) under _Division of Revenue and Provincial and Municipal Budget Information_
3. Copy the provinces and tabled budget year columns from _Schedule 2 - DETERMINATION OF EACH PROVINCE'S EQUITABLE SHARE OF THE PROVINCIAL SPHERE'S SHARE OF REVENUE RAISED NATIONALLY_
4. Paste these columns as new rows below the old ones
5. Fill in the Financial Year values for the new rows.
6. Ensure the formatting is consistent:

* Use the same province codes
* No decimal or thousand separator for amounts
* Amounts in thousands of rands

Create the dataset in Wazimap

1. name the dataset _Equitable Share to Provinces up to 2022-23_ (Updating to the correct latest year
2. Click through to the `financial year` _group_
3. Un-check _aggregatable_ and ensure the years are ordered, and save.

Create the Variable in Wazimap

1. name the variable _Equitable Share to Provinces up to 2022-23_ (Updating to the correct latest year
2. Select the dataset you just created.

Update the Profile indicator in Wazimap

1. Change the variable to the one you just created.
2. Ensure the profile indicator has the following configuration to format the numbers correctly:\
   `{ "types": { "Value": { "formatting": ",.0f" } } }`
3. Ensure the Profile Indicator has the following description:\
   The allocation of equitable share to each province.

#### Equitable Share to municipalities



