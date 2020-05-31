---
description: >-
  What people need to know to be able to effectively make changes to the
  structure and design of the site. This page should be updated as those ideas
  develop.
---

# Classifying public finance data and documents in CKAN

## Data classification

How we classify data and why. How we map public finance concepts to CKAN classification mechanisms and why.

CKAN provides the following classification mechanisms:

### Title

We try to give titles that can stand on their own to identify a dataset. The title to use for standard documents is documented specifically.

E.g. for the full \(all votes\) Estimates of National Expenditure we include the financial year in the title, i.e. `Estimates of National Expenditure 2019-20`. Two ENE datasets coming up in search results are then easy to distinguish. For Estimates of Provincial Expenditure for a specific department, we include the department name and financial year, i.e.  `North West EPRE 2019-20 - Vote 06 - Economy and Entreprise Development`

* If it's specific to national government, include the term National.
* If it's specific to a provincial government, include the province name, e.g. Eastern Cape
* If it's for the whole provincial sphere, include the term Provincial
* If it's specific to a department, include the department name.
* If it's specific to a financial year, include the financial year.

### Groups

* Groups can in theory be nested, but in practise the UI and search API don't do anything with that fact out of the box. A plugin could be built to do something useful with nested groups. See ckanext-hierarchy for how this is done with organizations.
* CKAN provides some access control over who can add datasets to specific groups
* Groups and membership of datasets in groups can be maintained via the GUI and API

**We use** groups to distinguish different kinds of datasets and documents, in the sense that we might have one group for budgeted spending data, another group for actual spending data, another group for budgeted revenue data. Each dataset in the group can then be distinguished via organisation, tag vocabularies, and Extras variables.

If you're adding something to vulekamali that has never been added before, there's a good chance you want a new group for it. Especially if this sort of thing will be added periodically, and if there is one of these for the national/each provincial government or each sphere.

Avoid using groups to distinguish between things that the other facilities below can do - especially sphere, province, government, or financial year. Just put the different datasets in one group, then use the other classification facilities to be able to query for specific sets.

### Organizations

**We use** organizations to indicate the owner OR custodian of a dataset. National Treasury might not be the owner of departmental data, but when National Treasury uploads data that it has collected and curates, it is selected as the organization. Think about who should answer questions about a dataset. A provincial treasury can't answer questions about the provincial sphere-wide EPRE dataset or the definition of the column names in it, despite being responsible for their budget rows in it. It is curated by National Treasury so National Treasury should be the first port of call, and then redirect questions as needed.

### Tags

Freeform, in the sense of hashtags.

**We don't currently use this.**

### Tag vocabularies

Curated named tagsets

* Shown in the admin, public and search if enabled by a plugin
* Useful for variables with a finite number of options
* Good for user-entered values, since they can only select from predefined values
* Not clear when only one option should be selected at a time
* Adding value options requires API calls.
* Adding variables \(vocabularies\) requires plugin code changes

**We have defined:**

* Financial year
* Sphere of government \(National, Provincial\)
* Province
  * Watch out - most of the rest of the system distinguishes province using a "Government" field, of which South Africa is a member as the National government. Province was added in CKAN before we modeled things using Government. To map between CKAN and the main site, the main site queries for Province if sphere is provincial.
* Government Functions
  * Was added for linking to relevant contributed datasets on department pages but not maintained since functions changed in 2018 budget.
* Dimensions
  * Effectively the columns in the dataset
  * Useful if one group has some granular datasets, and some less granular. We needed this specifically when provincial data didn't have one dataset that disaggregated by both Economic Classification 4 AND Subprogramme, but national data did. We could then query programmatically for the dataset that had what was needed for a given chart.

How to populate these is generally defined for each dataset in the documentation for maintaining that dataset.

### Extras 

arbitrarily-named properties of a dataset that take a text value

* Shown in the admin interface, dataset page, and API
* Can be edited in the Admin interface and API
* Useful to search by via the API but not the GUI
* Not good to maintain this by hand - clerical errors will break searches for specific values
* Good for variables that can take many different values

We use this for 

* Department name for department-specific documents, to then look up the department's datasets
* Budget Vote Number \(We ended up not using this\)
* Organisational Unit of the relevant entity \(e.g. the department, not the dataset CKAN organization\) - Not currently used by anything.

These fields are set by the bulk upload interface in the main website admin.

### Special groups

The groups `budget-vote-documents` and `adjusted-budget-vote-documents` are considered "special":

* They are not shown as Dataset Categories because there are 40 documents each year - the data category view is not well-suited to this at the moment.
* Their datasets are treated as "departement" search results using the department metadata associated with those datasets, rather than as dataset search results in vulekamali.

### Non-treasury datasest without groups

Datasets where the owner is not National Treasury that are not in a group are assumed to be "Contributed Datasets". If you forget to add a dataset to a group, it will show up in the Contributed Dataset list on vulekamali.

This is because non-treasury contributors do not have permission to add their datasets to any group. They may only add datasets to one of the organisations they are a member of - only then can their datasets be made public. So the system assumes non-treasury datasets that are not in groups are contributed datasets.

### Resources

Resources are the list of files and URLs to online datasets and APIs on a dataset.

Use different resources on the same dataset for different formats or views of the same dataset. E.g. you could have a resource for each

* file format, e.g. CSV, XLSX, XLSB
* Different views, e.g. the full dataset, a couple of interesting slices of the data, some charts generated from the dataset, a document explaining how to use a dataset, and a report providing your analysis from the dataset.

There's no dedicated field for programmatic distinction of a resource, e.g. to let a programmatic agent get the full raw file, or a specific API endpoint, so **we usually use a combination of the Format and Title fields, and document that those should be filled very precisely.**

We prefer using distinct datasets for datasets published at different times, e.g. different financial years or quarters, rather than adding resources to one dataset. We therefore include the period or point in time in the dataset title.

#### Title

If two different resources are the exact same data, but one is CSV and one is XLS, it's best to give them the same title.

If one resources is the full dataset and another is just a slice or view of the data, indicate that using the resource title.

#### Description

You can use this to explain briefly how you made a distinct slice or view of a dataset, or important things to expect from a specific format version

#### Format

This is generally set automatically from the file extension. Pay attention that it was detected correctly.

For APIs, it can be useful to specify a format that can be used for programmatic lookup. For OpenSpending APIs, the format MUST be `OpenSpending API`, capitalised exactly that way.

## Assumptions about public finance

Beware of these assumptions - there might be implementation decisions based on these - if these assumptions change, code changes might be needed.

* Initial assumption: Departments only change at the boundaries of financial years. 
  * That means we could have a department instance repeated for each financial year it exists, and where it doesn't exist in cross-year navigation, we could detect it quite easily and link to the government where it might have existed instead.
  * We could also have added a manual mapping to the department\(s\) in the other year that are related to the change in government structure.
* Potentially upcoming: Departments might change within a financial year.
* vulekamali is focused on National and Provincial data
  * It's often important to acknowledge how local government data fits in here
  * vulekamali doesn't want to duplicate Municipal Money
  * vulekamali might incorporate local government data in the future but it's not clear when or how



* Government budgets are structured as follows
  * National and Provincial spheres \(Local sphere not shown on vulekamali\)
  * National and Provincial governments in the relevant spheres
    * E.g. Northern Cape is a government, South Africa is a government
  * Departments corresponding to one government
    * The top level of disaggregation of the fiscal budget data \(other than consolidated\) is Departments, Economic Classifications, Functions
  * Budget Programmes are the next level of budget disaggregation below Departments
* Province names remain the same from year to year \(Names and codes are assumed in some places\)
* Department names may change from one financial year to the next, but not during a year
* Budget data loaded on vulekamali is out of embargo - it may be accessed by anyone
  * This is assumed as the data is publicly accessible from the beginning of the upload process
* Published original budget data is the Main Appropriation
  * It is assumed that changes between tabling and appropriation do not affect the data on the site.

