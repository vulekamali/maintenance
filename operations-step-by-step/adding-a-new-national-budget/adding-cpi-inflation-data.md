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

Add a CSV version of the file as a resource of a dataset specific to this new year

Add it to the group CPI Inflation

Get the resource ID as you did for the [revenue sources data]()

Add the resource ID to `CPI_RESOURCE_IDS` in the Data Manager's `models.py`

Now the Data Manager can adjust for inflation using the latest CPI data.

Finally update the CPI dataset URL in the vulekamali static site repository `static-budget-portal/_data/global_values.yaml`

