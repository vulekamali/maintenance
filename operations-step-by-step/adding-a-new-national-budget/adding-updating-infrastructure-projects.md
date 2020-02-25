---
description: >-
  This page describes the process of uploading and updating the data related to
  Infrastructure Projects.
---

# Adding/updating National Infrastructure Projects

## Updating National Infrastructure Projects displayed on vulekamali

1. Delete the existing project data in vulekamali Admin
2. Use the Import functionality on Infrastructure Project Parts to import the new dataset
3. Upload the CSV to CKAN and add to the infrastructure project data group.

## Dataset metadata in CKAN

The  `National Departmental Infrastructure Projects 2019-20` dataset should be in a group with the slug `infrastructure-projects`  in CKAN.

The dataset should have a single `CSV` resource with the Infrastructure Projects data

## Dataset Structure

### Structure required for dataset from National Treasury

The `Featured` column should be marked `TRUE` for projects that are to be featured on the Infrastructure Projects Overview page. All other projects \(not indicated with `Featured='TRUE'` will not be listed on vulekamali.

| Sphere | Department | Sector | Project name | Project description | GPS code | Nature of investment | Infrastructure type | Current project stage | SIP category | Total project cost | 2015/16 | 2016/17 | 2017/18 | 2018/19 | 2019/20 | 2020/21 | Featured |
| :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- |
| National | Health | Social Services | Eastern Cape: Bambisana hospital \(emergency repairs\) | Emergency repairs | -31.45019, 29.45397 | Maintenance and repair | District Hospital | Hand over | SIP 12: Revitalisation of public hospitals and other health facilities | 100 | 100 | 100 | 100 | 100 | 100 | 100 | TRUE |

### Structure required for dataset uploaded in vulekamali Admin and [CKAN](../../services/vulekamali-ckan/).

The structure of the processed dataset \(after it's been through our pipeline\) and when uploaded to CKAN, should look like this:

| sphere | department | sector | project\_name | project\_description | gps\_code | nature\_of\_investment | infrastructure\_type | current\_project\_stage | sip\_category | total\_project\_cost | financial\_year | budget\_phase | featured | project\_slug | amount |
| :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- |
| National | Health | Social Services | Eastern Cape: Bambisana hospital \(emergency repairs\) | Emergency repairs | -31.45019, 29.45397 | Maintenance and repair | District Hospital | Hand over | SIP 12: Revitalisation of public hospitals and other health facilities | 100 | 2015 | Audited Outcome | TRUE | health-eastern-cape-bambisana-hospital-emergency-repairs | 100 |
| National | Health | Social Services | Eastern Cape: Bambisana hospital \(emergency repairs\) | Emergency repairs | -31.45019, 29.45397 | Maintenance and repair | District Hospital | Hand over | SIP 12: Revitalisation of public hospitals and other health facilities | 100 | 2016 | Audited Outcome | TRUE | health-eastern-cape-bambisana-hospital-emergency-repairs | 100 |
| National | Health | Social Services | Eastern Cape: Bambisana hospital \(emergency repairs\) | Emergency repairs | -31.45019, 29.45397 | Maintenance and repair | District Hospital | Hand over | SIP 12: Revitalisation of public hospitals and other health facilities | 100 | 2017 | Audited Outcome | TRUE | health-eastern-cape-bambisana-hospital-emergency-repairs | 100 |
| National | Health | Social Services | Eastern Cape: Bambisana hospital \(emergency repairs\) | Emergency repairs | -31.45019, 29.45397 | Maintenance and repair | District Hospital | Hand over | SIP 12: Revitalisation of public hospitals and other health facilities | 100 | 2018 | Adjusted Appropriation | TRUE | health-eastern-cape-bambisana-hospital-emergency-repairs | 100 |
| National | Health | Social Services | Eastern Cape: Bambisana hospital \(emergency repairs\) | Emergency repairs | -31.45019, 29.45397 | Maintenance and repair | District Hospital | Hand over | SIP 12: Revitalisation of public hospitals and other health facilities | 100 | 2019 | MTEF | TRUE | health-eastern-cape-bambisana-hospital-emergency-repairs | 100 |
| National | Health | Social Services | Eastern Cape: Bambisana hospital \(emergency repairs\) | Emergency repairs | -31.45019, 29.45397 | Maintenance and repair | District Hospital | Hand over | SIP 12: Revitalisation of public hospitals and other health facilities | 100 | 2020 | MTEF | TRUE | health-eastern-cape-bambisana-hospital-emergency-repairs | 100 |
| National | Health | Social Services | Eastern Cape: Bambisana hospital \(emergency repairs\) | Emergency repairs | -31.45019, 29.45397 | Maintenance and repair | District Hospital | Hand over | SIP 12: Revitalisation of public hospitals and other health facilities | 100 | 2021 | MTEF | TRUE | health-eastern-cape-bambisana-hospital-emergency-repairs | 100 |

The expected structure of the dataset received from National Treasury looks like this. This is also the schema that our automated pipeline expects the dataset to be received in, before it processes it into the dataset above.

