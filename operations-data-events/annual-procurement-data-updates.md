# Annual procurement data updates

When you open the exported Excel file, the TotalTransAmount will be interpreted as Text by Excel. We need to change it to interpret it as numbers.

Select the TotalTransAmount column

![](../.gitbook/assets/screenshot_2020-03-20_09-48-12.png)

On the Data tab, click Text to Columns

![](../.gitbook/assets/text-to-columns-button.png)

Use the default data type Delimited

![](../.gitbook/assets/text-to-columns-form1.png)

We're just using one column so leave Delimiters on just Tab

![](../.gitbook/assets/text-to-columns-form2.png)

Use the default format General, and click the Advanced button to the right

![](../.gitbook/assets/text-to-columns-form3.png)

Ensure the Decimal separator is `.` not comma to match the separator in the data.

![](../.gitbook/assets/text-to-columns-form-decimal-separator.png)

Click finish. When done, the values will be right-aligned because they are now interpreted as numbers by Excel.

![](../.gitbook/assets/text-to-columns-done.png)

