# Adding Conditional Grant frameworks

Conditional Grant frameworks are added to vulekamali once they are gazetted, and not from the Division of Revenue Bill on budget day.

Each framework must be added as an individual Dataset in the DataStore, with one resource, which is the framework as a PDF file. That means the framework pages must be split out from the gazette PDF. [See below](adding-conditional-grant-frameworks.md#example-of-splitting-out-framework-pages) for an example of how to do that.

DataStore metadata:

* **Dataset title**: {financial year} {grant name} Framework
  * e.g. _2018-19 Ilima-Letsema Grant Framework_
* **Resource title**: {grant name}
  * e.g. _Ilima-Letsema Grant Framework_
* **Financial year**: {financial year}
  * e.g. _2018-19_
* **Group**: Frameworks for Conditional Grants to [Municipalities](https://data.vulekamali.gov.za/group/frameworks-for-conditional-grants-to-municipalities)/[Provinces](https://data.vulekamali.gov.za/group/frameworks-for-conditional-grants-to-provinces)

## Example of splitting out framework pages

On Windows:

[Various tools are available - it is possible with just the Google Chrome browser](https://superuser.com/questions/684769/how-to-split-pdf-file-in-windows)

On Linux:

1. Make a list of framework name, first page, last page
   1. page number must be the PDF page number, not that of the gazette
   2. Change any slashes in the name to hyphens or something that makes sense but can safely be a filename
2. Make a directory for grants towards municipalities, and another for provinces
3. Use a tool like pdftk to split out the pages for each framework
   1. ```text
      pdftk gazette.pdf cat 90-92 output "Ilima-Letsema Grant.pdf"
      ```

