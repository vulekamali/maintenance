# Adding CPI Inflation data

Get the spreadsheet of CPI Inflation from the Public Finance Statistics directorate in National treasury

Ensure it's structured like the 2018-19 example:

| Year | CPI |
| :--- | :--- |
| 2015/16 | 0.051669167291823 |
| 2016/17 | 0.062951404369147 |
| 2017/18 | 0.048877995764781 |
| 2018/19 | 0.054916143679306 |
| 2019/20 | 0.052912017285532 |

1. Create a dataset `Annual CPI Inflation 2018-19` but with the financial year you're adding
2. Add a CSV version of the file as a resource titled `CPI numbers from Budget Review 2018-19`, again with the correct financial year
3. Add it to the group `CPI Inflation`

[Check that it's successfully been imported to the Datastore](../../services/vulekamali-ckan/ckan-datastore.md#checking-that-a-resource-has-been-imported-successfully) to be available via the datastore API.

{% file src="../../.gitbook/assets/cpi-2019.xlsx" caption="Example of CPI data provided by Jeffery" %}



