# Special properties and assumptions

## Special groups

The groups `budget-vote-documents` and `adjusted-budget-vote-documents` are considered "special":

* They are not shown as Dataset Categories
* Their datasets are treated as "departement" search results using the department metadata associated with those datasets, rather than as dataset search results in vulekamali.

## Non-treasury datasest without groups

Datasets where the owner is not National Treasury that are not in a group are assumed to be "Contributed Datasets". If you forget to add a dataset to a group, it will show up in the Contributed Dataset list on vulekamali.

This is because non-treasury contributors do not have permission to add their datasets to any group. They may only add datasets to one of the organisations they are a member of - only then can their datasets be made public. So the system assumes non-treasury datasets that are not in groups are contributed datasets.

