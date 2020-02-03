# Uploading provincial infrastructure project data

### BadZipfile: File is not a zip file

Make sure you uploaded a `.xlsx` file. xlsx files are really zip files with Excel data in them.

### ValueError: year is out of range \(datetime.datetime\(\*parts\[:3\]\) + diff \)

We've gotten this when there were extra digits in the year part of date columns - e.g. see this screenshot:

![Year is 21019 when they probably meant 2019](../../.gitbook/assets/irm-date-error.png)

We've deleted these rows by adding conditional formatting to highlight the odd dates, then deleting those rows. This is error-prone and time-consuming so it would be better to restrict the input of dates to realistic years.



