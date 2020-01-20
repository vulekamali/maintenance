---
description: >-
  This page describes the process of uploading and updating the data related to
  Infrastructure Projects.
---

# Adding/updating Infrastructure Projects

## DataStore Structure

The  `National Departmental Infrastructure Projects 2019-20` dataset should be in a group with the slug `infrastructure-projects`  on the DataStore.

The dataset should have a single `CSV` resource with the Infrastructure Projects data

## Dataset Structures

### Structure required for dataset uploaded to the DataStore

The structure of the processed dataset \(after it's been through our pipeline\) and when uploaded to CKAN, should look like this:

| Sphere | Department | Sector | Project name | Project description | GPS code | Nature of investment | Infrastructure type | Current project stage | SIP category | Total project cost | Financial Y | Budget Phase | Featured | Project slug | Amount |
| :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- |
| National | Health | Social Services | Eastern Cape: Bambisana hospital \(emergency repairs\) | Emergency repairs | -31.45019, 29.45397 | Maintenance and repair | District Hospital | Hand over | SIP 12: Revitalisation of public hospitals and other health facilities | 100 | 2015 | Audited Outcome | TRUE | health-eastern-cape-bambisana-hospital-emergency-repairs | 100 |
| National | Health | Social Services | Eastern Cape: Bambisana hospital \(emergency repairs\) | Emergency repairs | -31.45019, 29.45397 | Maintenance and repair | District Hospital | Hand over | SIP 12: Revitalisation of public hospitals and other health facilities | 100 | 2016 | Audited Outcome | TRUE | health-eastern-cape-bambisana-hospital-emergency-repairs | 100 |
| National | Health | Social Services | Eastern Cape: Bambisana hospital \(emergency repairs\) | Emergency repairs | -31.45019, 29.45397 | Maintenance and repair | District Hospital | Hand over | SIP 12: Revitalisation of public hospitals and other health facilities | 100 | 2017 | Audited Outcome | TRUE | health-eastern-cape-bambisana-hospital-emergency-repairs | 100 |
| National | Health | Social Services | Eastern Cape: Bambisana hospital \(emergency repairs\) | Emergency repairs | -31.45019, 29.45397 | Maintenance and repair | District Hospital | Hand over | SIP 12: Revitalisation of public hospitals and other health facilities | 100 | 2018 | Adjusted Appropriation | TRUE | health-eastern-cape-bambisana-hospital-emergency-repairs | 100 |
| National | Health | Social Services | Eastern Cape: Bambisana hospital \(emergency repairs\) | Emergency repairs | -31.45019, 29.45397 | Maintenance and repair | District Hospital | Hand over | SIP 12: Revitalisation of public hospitals and other health facilities | 100 | 2019 | MTEF | TRUE | health-eastern-cape-bambisana-hospital-emergency-repairs | 100 |
| National | Health | Social Services | Eastern Cape: Bambisana hospital \(emergency repairs\) | Emergency repairs | -31.45019, 29.45397 | Maintenance and repair | District Hospital | Hand over | SIP 12: Revitalisation of public hospitals and other health facilities | 100 | 2020 | MTEF | TRUE | health-eastern-cape-bambisana-hospital-emergency-repairs | 100 |
| National | Health | Social Services | Eastern Cape: Bambisana hospital \(emergency repairs\) | Emergency repairs | -31.45019, 29.45397 | Maintenance and repair | District Hospital | Hand over | SIP 12: Revitalisation of public hospitals and other health facilities | 100 | 2021 | MTEF | TRUE | health-eastern-cape-bambisana-hospital-emergency-repairs | 100 |

### Structure required for dataset from National Treasury

The expected structure of the dataset received from National Treasury looks like this. This is also the schema that our automated pipeline expects the dataset to be received in, before it processes it into the dataset above.

| Sphere | Department | Sector | Project name | Project description | GPS code | Nature of investment | Infrastructure type | Current project stage | SIP category | Total project cost | 2015/16 | 2016/17 | 2017/18 | 2018/19 | 2019/20 | 2020/21 | Featured |
| :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- |
| National | Health | Social Services | Eastern Cape: Bambisana hospital \(emergency repairs\) | Emergency repairs | -31.45019, 29.45397 | Maintenance and repair | District Hospital | Hand over | SIP 12: Revitalisation of public hospitals and other health facilities | 100 | 100 | 100 | 100 | 100 | 100 | 100 | TRUE |

The `Featured` column should be marked `TRUE` for projects that are to be featured on the Infrastructure Projects Overview page. All other projects \(not indicated with `Featured='TRUE'` will not be listed on vulekamali.

## Updating Infrastructure Projects displayed on vulekamali

1. The initial dataset must have a structure as described on this page.
2. Upload the dataset to a public repository like Dropbox, Google Drive, S3 or similar and save the public URL.
3. This URL must be updated in the pipeline.
4. Run the pipeline.
5. Upload the processed dataset to CKAN, under the correct group.

A rebuild should automatically be triggered, and the new data should appear on vulekamali after the rebuild has completed.

