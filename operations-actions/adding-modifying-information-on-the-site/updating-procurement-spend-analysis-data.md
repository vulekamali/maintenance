# Updating procurement spend analysis data

## Export the data from the [OCPO Data Warehouse](https://github.com/vulekamali/maintenance/tree/da64355744caa0823b4135c9f0dc6f71eab19e6a/operations-actions/services/ocpo-data-warehouse.md)

Ensure the destination file `OCPO-supplier-spend-data-no-supplier-id.xlsx`does not exist in the destination folder `c:\Vulekamali Export`.

![](../../.gitbook/assets/ocpo_dw-export-1-ensure-file-doesnt-exist.png)

Open the `SQL Server Execute Package Utility`

![](../../.gitbook/assets/ocpo_dw-export-2-open-execute-package-utility.png)

Select the SQL Server Integration Services \(SSIS\) package in the export folder called `Vulekamali Supplier Demographic Spend analysis Export.dtsx`

![](../../.gitbook/assets/ocpo_dw-export-3-select-export-ssis-package.png)

Execute the package and check that no errors occurred in the Progress log.

![](../../.gitbook/assets/ocpo_dw-export-4-execution-completed.png)

Find the output file `OCPO-supplier-spend-data-no-supplier-id.xlsx` in the destination folder.

![](../../.gitbook/assets/ocpo_dw-export-5-output-file.png)

## Update the Excel data file

When you open the exported Excel file, the TotalTransAmount will be interpreted as Text by Excel. We need to change it to interpret it as numbers.

Select the TotalTransAmount column

![](../../.gitbook/assets/screenshot_2020-03-20_09-48-12.png)

On the Data tab, click Text to Columns

![](../../.gitbook/assets/text-to-columns-button.png)

Use the default data type Delimited

![](../../.gitbook/assets/text-to-columns-form1.png)

We're just using one column so leave Delimiters on just Tab

![](../../.gitbook/assets/text-to-columns-form2.png)

Use the default format General, and click the Advanced button to the right

![](../../.gitbook/assets/text-to-columns-form3.png)

Ensure the Decimal separator is `.` not comma to match the separator in the data.

![](../../.gitbook/assets/text-to-columns-form-decimal-separator.png)

Click finish. When done, the values will be right-aligned because they are now interpreted as numbers by Excel.

![](../../.gitbook/assets/text-to-columns-done.png)

## Update the PowerBI Report

Download the latest PowerBI report file from vulekamali.

Open the PowerBI report

![](../../.gitbook/assets/screenshot_2020-03-20_11-12-04.png)

Update the data source to the location of the Excel file

![](../../.gitbook/assets/powerbi-update-source.png)

Refresh the data from the new Excel file

Publish the file to the info@vulekamali.gov.za PowerBI workspace

![](../../.gitbook/assets/screenshot_2020-03-20_18-32-31.png)

Open the file there, and click Publish to web

![](../../.gitbook/assets/powerbi-embed.png)

Click Create embed code

![](../../.gitbook/assets/powerbi-embed2.png)

Click Publish

![](../../.gitbook/assets/powerbi-embed3.png)

Copy the HTML code to paste into vulekamali

![](../../.gitbook/assets/powerbi-embed4.png)

Find the HTML embed code in the Procurement Spend Analysis page editor in the vulekamali Content Management System.

Replace the old embed code with the new one.

Replace `width="800" height="600"` with `width="100%" style="height: 75vh"`

Save the page, and check that it is showing the updated data.

![](../../.gitbook/assets/screenshot_2020-03-20_18-26-22.png)

