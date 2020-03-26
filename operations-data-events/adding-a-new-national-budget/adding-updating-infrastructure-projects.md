---
description: >-
  This page describes the process of uploading and updating Public Privrate
  Partnership and major (featured) Infrastructure Projects.
---

# Adding/updating PPP and major National Infrastructure Projects

Since February 2019, a small number \(about 25\) projects administered by national departments were featured on vulekamali.

In 2020, 50 projects were uploaded - updating some of the existing projects, and adding some new ones.

In 2020, Public Private Partnership \(PPP\) projects were added.

## Updating National Infrastructure Projects displayed on vulekamali

1. Use the Import functionality on _**Infrastructure Project Parts**_ to import the new dataset
   1. Each row matching the slug and financial year of existing data will update that data with the changes in the new file \(e.g. revised amount, change in phase for the available data\)
2. Upload the CSV to CKAN and add to the infrastructure project data group.
   1. This makes it available for download in the Vulekamali Datasets section.

## Dataset metadata in CKAN

The  `National Departmental Infrastructure Projects 2019-20` 

Add the dataset to the group with the slug `infrastructure-projects`  in CKAN.

The dataset should have a single `Excel` resource with the Infrastructure Projects data

## Dataset Structure

### See the examples below.

Key requirements:

* Column names must match exactly
* PPP and Major National Departmental projects have some overlap in column names, and some differences. Note the unit used in amount column names.
* Project slugs must be consistent year-on-year otherwise duplicates will be introduced.
* Budget phases must be capitalised precisely as in the existing data.

### 

{% file src="../../.gitbook/assets/ppp-data-05.04-jd-format-tweaks.xlsx" caption="2020 PPP projects upload" %}

National projects file is included in case this feature is still needed in 202021

{% file src="../../.gitbook/assets/upload-format-2020-21-new-headings.csv" caption="2020 Major National Department projects upload" %}



