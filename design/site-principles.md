---
description: >-
  What people need to know to be able to effectively make changes to the
  structure and design of the site. This page should be updated as those ideas
  develop.
---

# Data principles

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

