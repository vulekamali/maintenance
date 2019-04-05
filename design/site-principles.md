# Data principles

* Initial assumption: Departments only change at the boundaries of financial years. 
  * That means we could have a department instance repeated for each financial year it exists, and where it doesn't exist in cross-year navigation, we could detect it quite easily and link to the government where it might have existed instead.
  * We could also have added a manual mapping to the department\(s\) in the other year that are related to the change in government structure.
* Potentially upcoming: Departments might change within a financial year.
* vulekamali is focused on National and Provincial data
  * It's often important to acknowledge how local government data fits in here
  * vulekamali doesn't want to duplicate Municipal Money
  * vulekamali might incorporate local government data in the future but it's not clear when or how

