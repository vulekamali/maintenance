# Adding structured fiscal data

At key budget events like the tabling of the Main Appropriation and Adjustments Appropriation, and release of Annual Report Expenditure data, we upload structured data OpenSpending and make it accessible via CKAN and vulekamali. This data is intended to support further analysis by the public, and is used for summaries and demonstration of the capability of the data on vulekamali.

To allow automated summaries of the data in vulekamali, the Data Manager has very specific expectations of the structure and values in the data, and how the [Fiscal Data Package](http://frictionlessdata.io/specs/fiscal-data-package/) types used when uploading the data to [OpenSpending](https://openspending-dedicated.vulekamali.gov.za/).

The consequence of not adhering to these requirements is that the summaries and demonstrations on vulekamali will not work, and will either be broken, or warn that data for the relevant demonstration is missing.

{% hint style="info" %}
**Updated datasets**

It is strongly recommended that updated datasets are uploaded to new unique identifieds, and that the previous version of the dataset is **not replaced or deleted**. Replacing or deleting datasets can break scripted analysis, or produce different results if someone's instructions or script is repeated. This leads to doubt about the reliability of the data.
{% endhint %}

{% hint style="info" %}
**Dataset timestamps**

It is strongly recommended that upload timestamps of the form 2019-08-12 01:18 (and 2019-08-01t0118 for unique identifiers) are included in the name and unique identified of datasets in OpenSpending. This facilitates better referencing of data in analyses and articles, and helps others know exactly which version of a dataset was used which produced a particular result.
{% endhint %}

## General requirements for data uploaded to OpenSpending

* At least one "measure" is needed, e.g. the value column - named `Value`
* The value column must be in Rands, **not** Thousands of Rands
* The combination of the non-measure columns must be unique on each row
* Financial year must be an integer - for National and Provincial budget data we use the starting year, as is convention. So for 2018-19, we use `2018`.
* Department names and budget phases must match what is used in the Data Manager precisely. That includes capitalisation and punctuation, including hyphenation and commas. Avoid stray spaces at the beginning and end of values. See dataset specifics below.
* Text and numeric values must be consistent. Occasional inconsistencies like stray spaces at the start or end of a value result in that category being treated as a different category, just like it would in a pivot table.
* [CSV files must be saved with UTF-8 encoding](https://www.ibm.com/support/knowledgecenter/SSWU4L/Data/imc\_Data/Data\_q\_a\_watson\_assistant/A\_Simple\_Way\_to\_UTF-8\_Encode\_your\_CSV\_fi191.html)

After adding the dataset to CKAN, [add it to the right group and add the right metadata](./#specific-dataset-requirements) so that the [Data Manager](../../../services/vulekamali.gov.za.md) can find each dataset to prepare the summaries for each financial year using the correct dataset.

## Automated data checks

Data sets can be checked for adherence to the requirements listed in the [Specific dataset requirements](https://maintenance.vulekamali.gov.za/operations/adding-modifying-information-on-the-site/adding-structured-fiscal-data-to-openspending#specific-dataset-requirements) section below on the vulekamali automated data checks [repository](https://github.com/vulekamali/data-checks).

#### Instruction Video

{% embed url="https://www.youtube.com/watch?v=m8HFtlSF4hY&feature=youtu.be" %}

#### Step-by-step guide

1. Log in or [sign up](https://github.com/join?source=header-home) for [github.com](https://github.com/)
2. Make sure your data is available on a publicly accessible url in "raw" format, e.g. uploaded to [https://s3.console.aws.amazon.com/s3/buckets/manual-uploads.vulekamali.gov.za/?region=eu-west-1\&tab=overview](https://s3.console.aws.amazon.com/s3/buckets/manual-uploads.vulekamali.gov.za/?region=eu-west-1\&tab=overview)
3. Go to [https://github.com/vulekamali/data-checks](https://github.com/vulekamali/data-checks)
4. Click on "Create new file"

![](<../../../.gitbook/assets/create-new-file-button (1).png>)

1. Type the file name as `datapackages/<financial year>/<dataset type>/datapackage.json`, for example `datapackages/2019-20/epre/datapackage.json`

![](<../../../.gitbook/assets/file-name (1).png>)

1. Copy the following text to the new file:

```
{
 "name": "<INSERT NAME OF YOUR DATA SET>",
 "schema": "tabular-data-package",
 "profile": "tabular-data-package",
 "resources": [
     {
         "path": "<INSERT URL TO YOUR DATA SET>",
         "profile": "tabular-data-resource",
         "name": "<INSERT NAME OF YOUR DATA SET>",
         "format": "csv",
         "mediatype": "text/csv",
         "encoding": "utf-8",
         "schema": "https://raw.githubusercontent.com/vulekamali/data-checks/master/schema/<INSERT TYPE OF YOUR DATA SET>.json"
     }
 ]
}
```

1. Update the `name` value and the `path`, `name` and `schema` values inside the `resources` value in your new file.

![](../../../.gitbook/assets/file-values.png)

1. Scroll down to the "Commit new file" heading. Select the "Create a new branch for this commit and start a pull request." option and click on "Propose new file".

![](../../../.gitbook/assets/commit-new-file.png)

1. On the next screen, give your pull request a descriptive title such as "Add 2019-20 EPRE data" and click on "Create pull request"

![](<../../../.gitbook/assets/pull-request (1).png>)

1. You should now see a section with yellow text that reads: "Some checks haven’t completed yet". Wait until the text turns either red or green.

![](../../../.gitbook/assets/checks-havent-completed.png)

{% hint style="warning" %}
**Verify that your new datapackage is being checked**

When adding a datapackage, verify that it's being checked. If you placed it in the wrong directory, it will not be checked and you might falsely think that your dataset was checked and passed the checks.
{% endhint %}

To verify that your package is being checked, click on _Details_ for the checks and look for `Checking ...your package path` in the checks log. If you don't see your packing being checked, double-check that the path to your datapackage is correct so that it can be picked up for checking automatically. _**If you don't see your datapackage path being checked in the log, your package is not being checked.**_

The following shows a successful check for the 2018-19 ENE package:

![](../../../.gitbook/assets/data-checks-successful.png)

The following shows an error for the 2019-20 ENE package:

![](../../../.gitbook/assets/data-checks-error.png)

*   If you see a section with green text reading "All checks have passed", your data set has passed all of the checks **successfully**:

    ![](../../../.gitbook/assets/success.png)
*   If you see a section with red text reading "All checks have failed", your data set did not pass all of the checks:

    ![](../../../.gitbook/assets/failure.png)
* If your data set did not pass all of the checks, you can click on "details" on the first item under "All checks have failed". On the next screen, scroll down to the bottom of the screen. You should see a list of error messages generated for your data set.

![Dataset error messages](../../../.gitbook/assets/errors.png)

## Specific dataset requirements

### Budgeted and Actual National Expenditure

This dataset consists of all of the following datasets, for each financial year available:

* Estimates of National Expenditure (only for rows where `Budget Phase` is equal to `Main appropriation`
* Adjusted Estimates of National Expenditure (only for rows where `Budget Phase` is equal to `Adjusted appropriation`)
* Audit Outcomes dataset (only for rows where `Budget Phase` is equal to `Audit Outcome` or `Final Appropriation`)

![](<../../../.gitbook/assets/Budget vs Actual dataset construction (2).png>)

When each of the above datasets are released, the new year's data is added to this dataset. Only the rows for where `Financial Year` is equal to the ENE, AENE or AR dataset's year is included in this combined dataset (e.g. for `ENE 2015-16` adds rows where `Financial Year` is equal to `2015` and `Budget Phase` is equal to `Main Appropriation`. AENE 2019-20 adds rows where `FinancialYear` is `2019` and `Budget Phase` is `Adjusted appropriation`).

Instead of adding a new dataset to CKAN each year, just update the existing dataset to the new links in OpenSpending.

#### CKAN Metadata

* Group: [Budgeted and Actual National Expenditure](https://data.vulekamali.gov.za/group/budgeted-and-actual-national-expenditure)
* Sphere: national
* Dimensions: as per the fields available

#### CKAN Resources

In this order:

* Excel file of the data, ideally with the following pivot table in the default worksheet:
  * Filters: AmountKind=Total, Government=South Africa
  * Rows: Department
  * Columns: FinancialYear, BudgetPhase
  * Measures: Amount
* CSV file of the data - we usually use the CSV hosted by OpenSpending
* OpenSpending dataset model URL

Fields:

| column name             | Fiscal Data Package type                           | Description                                                                                              |
| ----------------------- | -------------------------------------------------- | -------------------------------------------------------------------------------------------------------- |
| VoteNumber              | administrative-classification:generic:level1:code  |                                                                                                          |
| Department              | administrative-classification:generic:level1:label |                                                                                                          |
| ProgNumber              | activity:generic:program:code                      |                                                                                                          |
| Programme               | activity:generic:program:label                     |                                                                                                          |
| SubprogNumber           | activity:generic:subprogram:code:part              |                                                                                                          |
| Subprogramme            | activity:generic:subprogram:label                  |                                                                                                          |
| EconomicClassification1 | economic-classification:generic:level1:code        |                                                                                                          |
| EconomicClassification2 | economic-classification:generic:level2:code:part   |                                                                                                          |
| EconomicClassification3 | economic-classification:generic:level3:code:part   |                                                                                                          |
| EconomicClassification4 | economic-classification:generic:level4:code:part   |                                                                                                          |
| EconomicClassification5 | economic-classification:generic:level5:code:part   |                                                                                                          |
| FunctionGroup1          | functional-classification:generic:level1:code      |                                                                                                          |
| FinancialYear           | date:fiscal-year                                   |                                                                                                          |
| BudgetPhase             | phase:id                                           | Valid values are `Audit Outcome`, `Adjusted appropriation`, `Main appropriation`, `Final Appropriation`. |
| Value                   | value                                              | The Rand value of the row                                                                                |
| AmountKind              | value-kind:code                                    | A type like `Total` or `Adjustments - Roll-overs`                                                        |
| Government              | source:geo-source:code                             | Always `South Africa` for this national dataset.                                                         |

For example, as CSV

```
Budget Phase,Department,Econ1,Econ2,Econ3,Econ4,Financial Year,Function Group 1,Programme,Programme Number,Subprogramme,Subprogramme Number,Value,Vote Number,Amount Kind,Government
Main appropriation,Public Service and Administration,Current payments,Compensation of employees,Salaries and wages,Salaries and wages,2018,General public services,Administration,1,Ministry,1,31989000.0,10,Total,South Africa
Main appropriation,Public Service and Administration,Current payments,Compensation of employees,Social contributions,Social contributions,2018,General public services,Administration,1,Ministry,1,2213000.0,10,Total,South Africa
Main appropriation,Public Service and Administration,Current payments,Goods and services,Administrative fees,Administrative fees,2018,General public services,Administration,1,Ministry,1,393000.0,10,Total,South Africa
Main appropriation,Public Service and Administration,Current payments,Goods and services,Advertising,Advertising,2018,General public services,Administration,1,Ministry,1,27000.0,10,Total,South Africa
```

Example pivot table, with the following parameters:

* **Filter:** Financial Year = 2017
* **Columns:** Budget Phase
* **Rows:** Amount Kind
* **Values:** Amount

![](../../../.gitbook/assets/avsbnatpivottablescreenshotdocs.PNG)

### Budgeted and Actual Provincial Expenditure

Same as [Budgeted and Actual National Expenditure,](./#budgeted-and-actual-national-expenditure) but the Governments in this case are the provincial governments. The data sources are then the EPRE, AEPRE and Provincial Expenditure Audit Outcomes datasets.

#### OpenSpending Metadata

* **Human-readable name:** Budgeted and Actual Provincial Expenditure uploaded 2019-08-12 01:09
  * with appropriate upload timestamp
* **Unique identifier:** budgeted-and-actual-provincial-expenditure-uploaded-2019-08-12t0109
* You can skip the description, city and period fields.

#### CKAN Metadata

* Group: [Budgeted and Actual Provincial Expenditure](https://data.vulekamali.gov.za/group/budgeted-and-actual-provincial-expenditure)
* Sphere: provincial
* Dimensions: as per the fields available

#### CKAN Resources

In this order:

* Excel file of the data, ideally with the following pivot table in the default worksheet:
  * Filters: AmountKind=Total
  * Rows: Government, Department
  * Columns: FinancialYear, BudgetPhase
  * Measures: Amount
* CSV file of the data - we usually use the CSV hosted by OpenSpending
* OpenSpending dataset model URL

Fields:

| column name             | Fiscal Data Package type                          | Description                                                                                              |
| ----------------------- | ------------------------------------------------- | -------------------------------------------------------------------------------------------------------- |
| Department              | administrative-classification:generic:level1:code |                                                                                                          |
| ProgNumber              | activity:generic:program:code                     |                                                                                                          |
| Programme               | activity:generic:program:label                    |                                                                                                          |
| SubprogNumber           | activity:generic:subprogram:code:part             |                                                                                                          |
| Subprogramme            | activity:generic:subprogram:label                 |                                                                                                          |
| EconomicClassification1 | economic-classification:generic:level1:code       |                                                                                                          |
| EconomicClassification2 | economic-classification:generic:level2:code:part  |                                                                                                          |
| EconomicClassification3 | economic-classification:generic:level3:code:part  |                                                                                                          |
| EconomicClassification4 | economic-classification:generic:level4:code:part  |                                                                                                          |
| EconomicClassification5 | economic-classification:generic:level5:code:part  |                                                                                                          |
| FunctionGroup1          | functional-classification:generic:level1:code     |                                                                                                          |
| FunctionGroup2          | functional-classification:generic:level2:code     |                                                                                                          |
| FinancialYear           | date:fiscal-year                                  |                                                                                                          |
| BudgetPhase             | phase:id                                          | Valid values are `Audit Outcome`, `Adjusted appropriation`, `Main appropriation`, `Final Appropriation`. |
| Value                   | value                                             | The Rand value of the row                                                                                |
| AmountKind              | value-kind:code                                   | A type like `Total` or `Adjustments - Roll-overs`                                                        |
| Government              | source:geo-source:code                            | In this dataset, this is the Province name e.g. 'North West' or 'Western Cape'                           |

For example, as CSV

```
Budget Phase,Department,Econ1,Econ2,Econ3,Econ4,Financial Year,Function Group 1,Programme,Programme Number,Subprogramme,Subprogramme Number,Value,Vote Number,Amount Kind,Government
Main appropriation,Public Service and Administration,Current payments,Compensation of employees,Salaries and wages,Salaries and wages,2018,General public services,Administration,1,Ministry,1,31989000.0,10,Total,North West
Main appropriation,Public Service and Administration,Current payments,Compensation of employees,Social contributions,Social contributions,2018,General public services,Administration,1,Ministry,1,2213000.0,10,Total,Eastern Cape
Main appropriation,Public Service and Administration,Current payments,Goods and services,Administrative fees,Administrative fees,2018,General public services,Administration,1,Ministry,1,393000.0,10,Total,Western Cape
Main appropriation,Public Service and Administration,Current payments,Goods a
```

### Estimates of National Expenditure

#### OpenSpending Metadata

* **Human-readable name:** Estimates of National Expenditure of South Africa 2019-20 uploaded 2019-06-05 16:15
  * with appropriate financial year and upload timestamp
* **Unique Identifier:** estimates-of-national-expenditure-south-africa-2019-20-uploaded-2019-06-05-1615
* **Description:** This dataset includes expenditure data as published in the Estimates of National Expenditure. Departmental expenditure data in previous financial years have been aligned with the budget and programme structures of departments as they are structured in the current Medium Term Expenditure Framework. This means that the structure of historical expenditure data for a department, may not necessarily reflect the same structure of that department when expenditure was incurred during a particular financial year. This may be due to functions shifts which may have occurred within a particular department or a general change in a department’s budget programme structures (BPS) as departments are afforded an opportunity before the start of the Budget to change their BPS.This is to ensure a more economical, efficient and effective delivery of public services and performance by the department as a whole.
* You can skip the City and Period fields

**CKAN Metadata**

* Dataset Name: Estimates of National Expenditure 2019-20
  * or whatver the correct tabled financial year is
* Group: [Estimates of National Expenditure](https://data.vulekamali.gov.za/group/estimates-of-national-expenditure)
* Financial Years: Exactly one: the year being tabled
* Sphere: national
* Dimensions: as per the fields available

#### CKAN Resources

In this order:

* Excel file of the data, ideally with the following pivot table in the default worksheet:
  * Rows: Department
  * Columns: FinancialYear, BudgetPhase
  * Measures: Amount
* CSV file of the data - we usually use the CSV hosted by OpenSpending
* OpenSpending dataset model URL

Fields:

| column name             | Fiscal Data Package type                           | Description                                                                                                                                                                                                                                                                                                           |
| ----------------------- | -------------------------------------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| VoteNumber              | administrative-classification:generic:level1:code  |                                                                                                                                                                                                                                                                                                                       |
| Department              | administrative-classification:generic:level1:label |                                                                                                                                                                                                                                                                                                                       |
| ProgNumber              | activity:generic:program:code                      |                                                                                                                                                                                                                                                                                                                       |
| Programme               | activity:generic:program:label                     |                                                                                                                                                                                                                                                                                                                       |
| SubprogNumber           | activity:generic:subprogram:code:part              |                                                                                                                                                                                                                                                                                                                       |
| Subprogramme            | activity:generic:subprogram:label                  |                                                                                                                                                                                                                                                                                                                       |
| EconomicClassification1 | economic-classification:generic:level1:code        |                                                                                                                                                                                                                                                                                                                       |
| EconomicClassification2 | economic-classification:generic:level2:code:part   |                                                                                                                                                                                                                                                                                                                       |
| EconomicClassification3 | economic-classification:generic:level3:code:part   |                                                                                                                                                                                                                                                                                                                       |
| EconomicClassification4 | economic-classification:generic:level4:code:part   |                                                                                                                                                                                                                                                                                                                       |
| EconomicClassification5 | economic-classification:generic:level5:code:part   |                                                                                                                                                                                                                                                                                                                       |
| FunctionGroup1          | functional-classification:generic:level1:code      |                                                                                                                                                                                                                                                                                                                       |
| FinancialYear           | date:fiscal-year                                   |                                                                                                                                                                                                                                                                                                                       |
| BudgetPhase             | phase:id                                           | Valid values are `Audited Outcome`, `Adjusted appropriation`, `Main appropriation`, `Medium Term Estimates`. While the newly-tabled budget is classified under `Medium Term Estimates` in some tables in the ENE documents, we classify it under `Main appropriation` for the purposes of analysis from this dataset. |
| Value                   | value                                              | ZAR                                                                                                                                                                                                                                                                                                                   |

#### Examples

{% file src="../../../.gitbook/assets/nat-ene-2019-20.xlsx" %}
ENE Structured Data in format provided by Public Finance Statistics
{% endfile %}

CSV example as uploaded to OpenSpending:

```
BudgetPhase,Department,EconomicClassification1,EconomicClassification2,EconomicClassification3,EconomicClassification4,FinancialYear,Programme,ProgNumber,Subprogramme,SubprogNumber,Value,VoteNumber
Audited Outcome,Public Service and Administration,Capital,Payments for capital assets,Machinery and equipment,Other machinery and equipment,2011,Administration,1,Ministry,1,311000.0,10
Audited Outcome,Public Service and Administration,Capital,Payments for capital assets,Machinery and equipment,Other machinery and equipment,2012,Administration,1,Ministry,1,112000.0,10
Adjusted appropriation,Public Service and Administration,Capital,Payments for capital assets,Machinery and equipment,Other machinery and equipment,2013,Administration,1,Ministry,1,101000.0,10
```

### Estimates of Provincial Expenditure

{% hint style="info" %}
Note this dataset is called Estimates of Provincial Expenditure, not Estimates of Provincial Revenue and Expenditure because it only contains expenditure data. While it might throw those who know what the EPRE is, it tries to make sense to users of expenditure data and not leave users wondering where the revenue data is if it was called EPRE.
{% endhint %}

#### OpenSpending Metadata

* **Human-readable name:** Estimates of Provincial Expenditure of South Africa 2019-20 uploaded 2019-06-05 16:15
  * with appropriate financial year and upload timestamp
* **Unique Identifier:** estimates-of-provincial-expenditure-south-africa-2019-20-uploaded-2019-06-05-1615
* **Description:** This dataset includes expenditure data as published in the Estimates of Provincial Revenue and Expenditure. Departmental expenditure data in previous financial years have been aligned with the budget and programme structures of departments as they are structured in the current Medium Term Expenditure Framework. This means that the structure of historical expenditure data for a department, may not necessarily reflect the same structure of that department when expenditure was incurred during a particular financial year. This may be due to functions shifts which may have occurred within a particular department or a general change in a department’s budget programme structures (BPS) as departments are afforded an opportunity before the start of the Budget to change their BPS.This is to ensure a more economical, efficient and effective delivery of public services and performance by the department as a whole.
* You can skip the City and Period fields

#### CKAN Metadata

* Group: Estimates of Provincial Expenditure
* Financial Years: Exactly one: the year being tabled
* Sphere: provincial
* Dimensions: as per the fields available

#### CKAN Resources

In this order:

* Excel file of the data, ideally with the following pivot table in the default worksheet:
  * Rows: Government, Department
  * Columns: FinancialYear, BudgetPhase
  * Measures: Amount
* CSV file of the data - we usually use the CSV hosted by OpenSpending
* OpenSpending dataset model URL

#### Dataset columns and value requirements

| Column Name             | Description                                                                                                                                                                                                                                                                                                                                                                                                                                 | OpenSpending Fiscal Data type                                  |
| ----------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | -------------------------------------------------------------- |
| Government              | Spelled out and capitalised normally, i.e. one of `Eastern Cape`, `Free State`, `Gauteng`, `KwaZulu-Natal`, `Limpopo`, `Mpumalanga`, `Northern Cape`, `North West`, `Western Cape`                                                                                                                                                                                                                                                          | source:geo-source:code                                         |
| VoteNumber              | integer                                                                                                                                                                                                                                                                                                                                                                                                                                     | Administrative > Non-standard > Top Level >  Unique Identifier |
| Department              | Capitalised and hyphenated correctly - this must be consistent across all datasets on vulekamali otherwise undercounting or errors could occur.                                                                                                                                                                                                                                                                                             | Administrative > Non-standard > Top Level > Display Name       |
| ProgNumber              | integer                                                                                                                                                                                                                                                                                                                                                                                                                                     |                                                                |
| Programme               | Must be capitalised as it should be presented.                                                                                                                                                                                                                                                                                                                                                                                              |                                                                |
| SubprogNumber           | integer                                                                                                                                                                                                                                                                                                                                                                                                                                     |                                                                |
| Subprogramme            | Must be capitalised as it should be presented.                                                                                                                                                                                                                                                                                                                                                                                              |                                                                |
| EconomicClassification1 |                                                                                                                                                                                                                                                                                                                                                                                                                                             |                                                                |
| EconomicClassification2 |                                                                                                                                                                                                                                                                                                                                                                                                                                             |                                                                |
| EconomicClassification3 |                                                                                                                                                                                                                                                                                                                                                                                                                                             |                                                                |
| EconomicClassification4 |                                                                                                                                                                                                                                                                                                                                                                                                                                             |                                                                |
| EconomicClassification5 |                                                                                                                                                                                                                                                                                                                                                                                                                                             |                                                                |
| FunctionGroup1          | Must be capitalised and hyphenated consistently across all datasets on vulekamali (barring changes from one year to another) otherwise undercounting or other errors could occur.                                                                                                                                                                                                                                                           |                                                                |
| FunctionGroup2          |                                                                                                                                                                                                                                                                                                                                                                                                                                             |                                                                |
| FinancialYear           | Integer, e.g. `2018` for the year `2018-19`                                                                                                                                                                                                                                                                                                                                                                                                 |                                                                |
| BudgetPhase             | Valid values are `Audited Outcome`, `Adjusted appropriation`, `Main appropriation`, `Medium Term Estimates`. While the newly-tabled budget is classified under `Medium Term Estimates` in some tables in the budget documents, we classify it under `Main appropriation` for the purposes of analysis from this dataset. E.g. the EPRE 2019-20 dataset should have budget phase `Main appropriation` for rows where FinancialYear is `2019` |                                                                |
| Value                   | Rands, not thousands of rands                                                                                                                                                                                                                                                                                                                                                                                                               | Amount                                                         |
|                         |                                                                                                                                                                                                                                                                                                                                                                                                                                             |                                                                |

### Adjusted Estimates of National Expenditure

#### CKAN Metadata <a href="#ckan-metadata" id="ckan-metadata"></a>

* Group: Adjusted Estimates of National Expenditure
* Sphere: National
* Dimensions: As per fields below

#### CKAN Resources <a href="#ckan-resources" id="ckan-resources"></a>

In this order:

* Excel file of the data
* CSV file of the data - we usually use the CSV URL hosted by OpenSpending
* Openspending dataset model URL

#### Fields

| Column name             | Fiscal Data Package field type | Description |
| ----------------------- | ------------------------------ | ----------- |
| Department              |                                |             |
| ProgNumber              |                                |             |
| Programme               |                                |             |
| SubprogNumber           |                                |             |
| Subprogramme            |                                |             |
| EconomicClassification1 |                                |             |
| EconomicClassification2 |                                |             |
| EconomicClassification3 |                                |             |
| EconomicClassification4 |                                |             |
| EconomicClassification5 |                                |             |
| FinancialYear           |                                |             |
| BudgetPhase             |                                |             |
| AmountKind              |                                |             |
| Value                   |                                |             |

#### Examples

{% file src="../../../.gitbook/assets/aene-2019-20.csv" %}

{% file src="../../../.gitbook/assets/aene-2019-20.xlsx" %}

Example pivot table with the following parameters:

* **Filter**: none
* **Columns**: Budget Phase; Amount Kind
* **Rows**: Department
* **Values**: Amount (sum)

![](../../../.gitbook/assets/screenshot\_2020-07-22\_12-34-07.png)

### National Expenditure Audit Outcomes data

![A pivot table that can be made using this dataset. Note that the programme names should not be capitalised.](../../../.gitbook/assets/screenshot\_2019-08-21\_14-50-32.png)

#### OpenSpending Metadata

* **Human-readable name:** National Department Expenditure Audit Outcomes of South Africa 2019-20 uploaded 2019-06-05 16:15
  * with appropriate financial year and upload timestamp
* **Unique Identifier:** national-expenditure-audit-outcomes-south-africa-2019-20-uploaded-2019-06-05-1615
* You can skip the Description, City and Period fields

#### CKAN Metadata

* Title: National Department Expenditure Audit Outcomes 2019-20
  * if 2019-20 is the audit year being released
* Group: Expenditure Audit Outcomes Data
* Financial Years: Exactly one: the audit year being released
* Sphere: national

#### Dataset columns and value requirements

| Column Name             | Description                                                                                                                                     |                                                   |
| ----------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------- |
| VoteNumber              | integer                                                                                                                                         |                                                   |
| Department              | Capitalised and hyphenated correctly - this must be consistent across all datasets on vulekamali otherwise undercounting or errors could occur. |                                                   |
| ProgNumber              | integer                                                                                                                                         |                                                   |
| Programme               | Must be capitalised as it should be presented.                                                                                                  |                                                   |
| SubprogNumber           | integer                                                                                                                                         |                                                   |
| Subprogramme            | Must be capitalised as it should be presented.                                                                                                  |                                                   |
| EconomicClassification1 |                                                                                                                                                 |                                                   |
| EconomicClassification2 |                                                                                                                                                 |                                                   |
| EconomicClassification3 |                                                                                                                                                 |                                                   |
| EconomicClassification4 |                                                                                                                                                 |                                                   |
| EconomicClassification5 |                                                                                                                                                 |                                                   |
| FunctionGroup1          |                                                                                                                                                 |                                                   |
| FunctionGroup2          |                                                                                                                                                 |                                                   |
| FinancialYear           | Integer, e.g. `2018` for the year `2018-19`                                                                                                     |                                                   |
| BudgetPhase             | `Audited Outcome`, `Adjusted appropriation`, `Main appropriation`,                                                                              |                                                   |
| AmountKind              | value-kind:code                                                                                                                                 | A type like `Total` or `Adjustments - Roll-overs` |
| Value                   | value - Rands, not thousands of rands                                                                                                           |                                                   |
|                         |                                                                                                                                                 |                                                   |

### Provincial Expenditure Audit Outcomes

#### OpenSpending Metadata

* **Human-readable name:** Provincial Expenditure Audit Outcomes of South Africa 2019-20 uploaded 2019-06-05 16:15
  * with appropriate financial year and upload timestamp
* **Unique Identifier:** provincial-expenditure-audit-outcomes-south-africa-2019-20-uploaded-2019-06-05-1615
* You can skip the Description, City and Period fields

#### CKAN Metadata

* Title: Provincial Expenditure Audit Outcomes 2019-20
  * if 2019-20 is the audit year being released
* Group: Expenditure Audit Outcomes Data
* Financial Years: Exactly one: the audit year being released
* Sphere: provincial

#### Dataset columns and value requirements

| Column Name             | Description                                                                                                                                                                        |                                                   |
| ----------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------- |
| Government              | Spelled out and capitalised normally, i.e. one of `Eastern Cape`, `Free State`, `Gauteng`, `KwaZulu-Natal`, `Limpopo`, `Mpumalanga`, `Northern Cape`, `North West`, `Western Cape` |                                                   |
| VoteNumber              | integer                                                                                                                                                                            |                                                   |
| Department              | Capitalised and hyphenated correctly - this must be consistent across all datasets on vulekamali otherwise undercounting or errors could occur.                                    |                                                   |
| ProgNumber              | integer                                                                                                                                                                            |                                                   |
| Programme               | Must be capitalised as it should be presented.                                                                                                                                     |                                                   |
| SubprogNumber           | integer                                                                                                                                                                            |                                                   |
| Subprogramme            | Must be capitalised as it should be presented.                                                                                                                                     |                                                   |
| EconomicClassification1 |                                                                                                                                                                                    |                                                   |
| EconomicClassification2 |                                                                                                                                                                                    |                                                   |
| EconomicClassification3 |                                                                                                                                                                                    |                                                   |
| EconomicClassification4 |                                                                                                                                                                                    |                                                   |
| EconomicClassification5 |                                                                                                                                                                                    |                                                   |
| FunctionGroup1          |                                                                                                                                                                                    |                                                   |
| FunctionGroup2          |                                                                                                                                                                                    |                                                   |
| FinancialYear           | Integer, e.g. `2018` for the year `2018-19`                                                                                                                                        |                                                   |
| BudgetPhase             | `Audited Outcome`, `Adjusted appropriation`, `Main appropriation`,                                                                                                                 |                                                   |
| AmountKind              | value-kind:code                                                                                                                                                                    | A type like `Total` or `Adjustments - Roll-overs` |
| Value                   | Rands, not thousands of rands                                                                                                                                                      |                                                   |
|                         |                                                                                                                                                                                    |                                                   |

### Consolidated budget

#### Objective

![The homepage shows the consolidated budget for the latest published financial year](../../../.gitbook/assets/screenshot\_2021-06-17\_10-18-06.png)

#### OpenSpending Metadata

* **Human-readable name:** Consolidated Expenditure Budget of South Africa 2019-20 uploaded 2019-06-05 16:15
  * with appropriate financial year and upload timestamp
* **Unique Identifier:** consolidated-expenditure-south-africa-2019-20-uploaded-2019-06-05-1615
* You can skip the Description, City and Period fields

#### CKAN Metadata

* Title: Consolidated Expenditure 2019-20
  * if 2019-20 is the year being tabled
* Group: Consolidated Expenditure
* Financial Years: Exactly one: the financial year being tabled
* Sphere: national and provincial

#### Dataset columns and value requirements

| Column Name             | OpenSpending type | Description                            |
| ----------------------- | ----------------- | -------------------------------------- |
| FunctionGroup           |                   | Functional classification level 1      |
| EconomicClassification2 |                   | Economic Classification level 1        |
| EconomicClassification3 |                   | Economic Classification level 2        |
| FinancialYear           |                   | As an integer - e.g. 2019-20 is `2019` |
| Value                   | value             | Rands, not Thousands of Rands          |

## Adding a dataset to OpenSpending

Before adding a dataset to OpenSpending, it has to be cleaned and structured correctly and must meet the general and specific requirements above.

Any data transformation tools can be used to ensure the data meets the above requirements. We have been using [Datapackage Pipelines](https://github.com/frictionlessdata/datapackage-pipelines)&#x20;

### Uploading data to OpenSpending using OS Packager

{% embed url="https://www.youtube.com/watch?v=mahZfYxxCH8&feature=youtu.be" %}

Login to the vulekamali account on OS Packager and [follow the upload wizard](https://openspending.org/packager/provide-data).

#### Assign types to columns

This can be done per-column based on the table of column types shown above, or by uploading the data-checks schema file for the dataset (if available), which includes column type mappings.

![Selecting types manually](../../../.gitbook/assets/screenshot\_2021-08-16\_11-27-24.png)

![Upload a schema file to assign types to your columns](../../../.gitbook/assets/os-packager-column-types.png)

Enter the dataset metadata as per the [specifications for the dataset](./#specific-dataset-requirements).

![](../../../.gitbook/assets/os-packager-metadata.png)

Keep the upload tab open to be able to monitor progress if possible. This takes 20 minutes to an hour.

When the dataset is successfully loaded, it's ready to be added to CKAN:

## Adding OpenSpending datasets to CKAN

Create a dataset with the following resources, and metadata as per the [specification for the dataset](./#specific-dataset-requirements).

### Resource: OpenSpending API for programmatic access

Add the OpenSpending API Model URL as a resource of the dataset.

The model URL can be constructed by entering the dataset ID in OpenSpending in the following template:

```
https://openspending-dedicated.vulekamali.gov.za/api/3/cubes/...Dataset ID.../model/
```

The Dataset ID is the combination of the OpenSpending account ID (`owner` in the Fiscal Data Package JSON file), and the Fiscal Data Package `name`, with a colon in between.&#x20;

If the Viewer URL is&#x20;

```
https://openspending-dedicated.vulekamali.gov.za/viewer/b9d2af843f3a7ca223eea07fb608e62a:estimates-of-provincial-expenditure-of-south-africa-2021-22-uploaded-2021-05-28-1228?lang=en
```

the dataset ID is

```
b9d2af843f3a7ca223eea07fb608e62a:estimates-of-provincial-expenditure-of-south-africa-2021-22-uploaded-2021-05-28-1228
```

and thus the Model URL is

```
https://openspending-dedicated.vulekamali.gov.za/api/3/cubes/b9d2af843f3a7ca223eea07fb608e62a:estimates-of-provincial-expenditure-of-south-africa-2021-22-uploaded-2021-05-28-1228/model/
```

**OpenSpending metadata:**

* Resource name: Same as dataset title
* Format: `OpenSpending API`&#x20;

{% hint style="info" %}
It's important that the capitalisation, spelling and spacing of this is correct: `OpenSpending API`
{% endhint %}

![](../../../.gitbook/assets/vulekamali-datastore-openspending-api.png)

### CSV file for manual and programmatic analysis

Add the CSV link to download the full dataset as Comma Separated Variable data which can be opened in Excel and other common data analysis tools.

Find the link at the bottom of the dataset viewer page in OpenSpending - in this case _aene-2016-17_

![The full dataset as CSV under View Raw Source Data](../../../.gitbook/assets/vulekamali-datastore-openspending-csv.png)

Copy this link and add it as a CSV type resource of the dataset

![](../../../.gitbook/assets/vulekamali-datastore-csv.png)

These will then show up in vulekamali as a Dataset and in data summaries and demonstrations.

## Troubleshooting

### OpenSpending

#### Integrity Error: duplicate key value violates unique constraint

![](../../../.gitbook/assets/screenshot\_2021-06-01\_14-29-12.png)

This is caused by multiple rows in the uploaded dataset having the exact same values across all dimensions (also known as classifying columns).

Remember each row must be uniquely classified by the dimension columns.

The fix for this is usually to sum together the rows with the same classification (if you're going from more granular data to this set). This can for example be done with a pivot table that sums on the Value column.

#### KeyError: 'primaryKey'

![](../../../.gitbook/assets/Screenshot\_2022-07-21\_17-47-33.png)

We've seen this when including a column as "Unknown - String" type. Removing the column from the dataset and rolling up the data to the remaining columns for uniqueness solved it.
