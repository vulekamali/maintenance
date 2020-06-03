# In-year spending data

The in-year spending data is quarterly updates of monthly spend actuals. [See the dataset guide](https://vulekamali.gov.za/learning-resources/guides/-year-spending-data/) for details of fields and what's expected.

We upload the data in various forms to help users with different data tools access the data. The top priority is to get the data released - **the following shows the formats in priority order** - it is better to publish just some formats, rather than delaying publication.:

<table>
  <thead>
    <tr>
      <th style="text-align:left">Format</th>
      <th style="text-align:left">Use case</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td style="text-align:left">Excel with all data raw in a worksheet</td>
      <td style="text-align:left">
        <p>This is the most flexible format - it&apos;s compressed so it isn&apos;t
          a massive download, and many tools can open data in Excel form (including
          some that can&apos;t access PowerPivot data).</p>
        <p></p>
        <p>Save as XLSB for the smallest file size that is still usable by non-Excel
          tools.</p>
        <p></p>
        <p>If example pivot tables based on that data worksheet, that is very helpful
          to users, but don&apos;t delay publication for this.</p>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">Per-department files</td>
      <td style="text-align:left">Some users are interested in specific departments - department-specific
        slices of the data allow them to work a bit more efficiently without needing
        to download and open the entire dataset. See previous versions of the dataset
        on vulekamali for the selection of datasets.</td>
    </tr>
    <tr>
      <td style="text-align:left">Excel PowerPivot</td>
      <td style="text-align:left">Excel power users - this format is quite small and efficient, but is only
        usable in Microsoft Excel and is quite a power-user feature.</td>
    </tr>
    <tr>
      <td style="text-align:left">CSV</td>
      <td style="text-align:left">
        <p>This is useful for many data tools that don&apos;t support Excel, but
          do support massive tabular data - e.g. databases and OpenSpending.org</p>
        <p></p>
        <p>Compress this in a Zip file to reduce file size.</p>
      </td>
    </tr>
  </tbody>
</table>

See previous versions for the selection of departments provided individually.

Name the dataset according to the sphere and latest financial year and quarter included - e.g. `National in-year spending 2019-20 Quarter 2`

## Uploading the data

We keep historical versions so that reference links don't break. Storage space is not an issue on this platform.

Create the dataset in CKAN and add to the In-year spending group.

Upload each file as a resource, named as per previous datasets.

Set the Sphere and Financial year to match the dataset name.



