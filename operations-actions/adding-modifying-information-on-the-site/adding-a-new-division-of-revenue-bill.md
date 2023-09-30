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

1. Division of Revenue Bill Schedules in Excel Format
2. DETERMINATION OF EACH PROVINCE'S EQUITABLE SHARE OF THE PROVINCIAL SPHERE'S SHARE OF REVENUE RAISED NATIONALLY&#x20;
3. extra column "Allocation (thou. rands)"
4. mark the financial year column as non-aggregatable
5. name dataset Equitable Share to Provinces up to 2022-23
6.



