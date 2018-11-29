# Simultaneous user story development in front and backend

## Story-driven branching

When working on a new story, it's important to adhere to a general branching procedure to prevent merge conflicts and avoid data anomalies.

Stories usually include a bit of front- and back end development. The typical story should look like the following structure

![](../.gitbook/assets/staticbudgetportal-branch-workflow%20%281%29.png)

From the **master** branch, checkout a new branch for the data. From the **data-branch**, check out the **UI-changes** branch. The **data branch** should only have changes to the _\_data/_ directory and **UI-changes** should only have changes for the HTML, CSS and JS \(front-end specific\).

The motivation behind this structure is:

* The **data-branch** can be merged into the **UI-changes** branch continuously during testing and development, which allows you to run a Jekyll server and test the site locally.
* A pull request can be opened to merge **UI-changes** into **data-branch** which, in theory, should only show the changes made to frontend code

{% hint style="info" %}
Please include screenshots of the static site in the **UI-changes** PR to showcase what's changed, and that the data is rendering correctly.
{% endhint %}



## Pivotal \(source of truth, stories\)

When planning, designing and developing a new story, it is very important to have a single source of truth in order for multiple team members to be able to work together effectively.

During the planning phase:

* Include virements and other visual planning aids
* Clearly define the expected outcome of the story, i.e. what the expected outcome is.
* Further, narrow down to expected outcomes for front-end and backend:
  * What data is expected, and in which format?
  * ..

During the development phase:

* Create tasks for items that can be 'ticked off' 
* Indicate which items are blocking others
* ..

During the staging phase:

* When you find a bug:
  * Screenshot and add as a comment
  * Create task and link to screenshot
  * Ping developer to notify them of the task

