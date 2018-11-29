---
description: >-
  The vulekamali website - user friendly access to budget data (AKA
  static-budget-portal)
---

# vulekamali.gov.za

{% embed url="https://vulekamali.gov.za" caption="The vulekamali website itself" %}

{% embed url="https://github.com/openupsa/static-budget-portal" caption="The GitHub repository for developing and deploying vulekamali.gov.za" %}

{% embed url="https://travis-ci.org/OpenUpSA/static-budget-portal/" caption="Travis CI page for this repository" %}

## Routes

Jekyll uses "routing files" to indicate which paths exist on the site, and how to build them. Routing files can be `.md` or `.html` files which a "front matter" section consisting of two rows of three hyphens \(`---`\), and optional `yaml` between them.

We put enough information into the front matter so that the page _layout_ can look up the right Page Data for the page.

## Page Data

Page data is primarily in the `_data` folder. Page Data can be `.yaml` or `.json`. We try to have the page data file for a given route \(web page path\) at the corresponding path under `_data`

Page data is generated via the `from_dynamic.py` script in the `generate/` directory. The data can be generated from:

* A local Data Manager instance \(for development\)
* Staging Data Manager  \(for staging prior to deploying to prod\)
* Production Data Manager \(for prod or near-prod deployments\)

## Data Generation

The [static-budget-portal](vulekamali.gov.za.md) is the front-end \(static site\) of [Vulekamali.gov.za](https://vulekamali.gov.za/) and does not generate or retrieve data.

The static-budget-portal requests data from the [Data Manager](vulekamali-data-manager/) and stores it locally in the `_data` directory, which it then uses to build the static site via Jekyll.

That means the actual data being served in production exists in the Git repository of the site. 

The static-budget-portal can be pointed towards any one of the following Data Manager states:

1. Local \(development\)
2. Staging
3. Production

The generated data will differ, depending on the code running in whichever Data Manager state you are building against.

#### Generate Data against Local \(development\)

You will need to run a local [Data Manager](vulekamali-data-manager/) instance for this to work.

After you've completed the setup for Data Manager, you can continue reading.

Set your PORTAL\_URL environment variable to point to your local app:

```text
export PORTAL_URL=http://localhost:8000/ 
python generate/from_dynamic.py
```

Generate data for each department and each financial year with the following:

```text
source env/bin/activate
python generate/from_dynamic.py
```

Then use `git status` and `git diff` to get an idea of what changed. If it looks sensible, add the updated files and commit and PR back into the branch where you want changes reflected.

When modifying the Dynamic Budget Portal server, you might want to point to your development server:

You can update one file at a time as follows:

```text
curl -o _data/2016-17/national/departments/planning-monitoring-and-evaluation.yaml https://dynamicbudgetportal.openup.org.za/2016-17/national/departments/planning-monitoring-and-evaluation.yaml
```

#### Generate data against Travis CI \(staging/production\)

[Travis CI](https://travis-ci.org/) is used to build page data for staging or production.

Every branch push results in a Travis CI build, but by default it won't regenerate data files.

Add `[ci]` to the commit message of the latest commit in the pushed branch to opt into generating data files.

Add `[staging]` to that commit message to use the staging web data server instead of production. This is useful if we want to see what the data will look like for a development branch of the web data server.

If any files changed, Travis CI will add and commit the changes and push that back to the branch. That means you'll need to pull the branch and perhaps use `pull --rebase` if you've since committed other changes. _**Don't trust the changes because it was a robot - check that the site works as expected and the diff looks reasonable before merging your PR**_

Best practise is to place these tags as the first part of the first line of the commit message. This makes it easy to see whether staging or production was used in the pull request list of commits.

To create a commit without any code changes to trigger a build, use `--allow-empty`. e.g.

```text
git commit -m "[ci][staging] trigger data regeneration for new department xyz data" --allow-empty
```

**Staging workflow**

[![Staging Branch Workflow](https://github.com/OpenUpSA/static-budget-portal/raw/eb0ce2e95c8d7e4363f64b14829a5455b51c89c1/docs/images/staging-branch-workflow.png)](https://github.com/OpenUpSA/static-budget-portal/blob/eb0ce2e95c8d7e4363f64b14829a5455b51c89c1/docs/images/staging-branch-workflow.png)

* Checkout a new `..-data-build` branch \(this branch must only contain `_data/` changes\)
* Checkout a new `..-ui-build` branch from the new `data-build` branch \(this branch must only contain JS, HTML, CSS etc. changes\)
* Switch back to the `..-data-build` branch
* Commit this new `..-data-build` branch with `[ci][staging] <message>`, if empty then include parameter `--allow-empty`
* Push this new commit to origin
* Check [Travis CI](https://travis-ci.org/) to see the status of the build and if there are any errors
* When Travis has completed, pull the branch \(`..-data-build`\) again to fetch the new data Travis built for us
* Merge `..-data-build` into `..-ui-build`
* Serve the site locally using Jekyll to confirm that the data generated by travis during staging is correct, and that the front-end renders correctly.
* If all is well, you should be clear to produce and deploy production data.

**Deploy to production**

Before deploying to production, ensure you've been through the Staging workflow described above.

* Checkout the existing `..-data-build` branch you've been working with
* Commit this branch to origin with `[ci]` \(no staging\) to build data against production
* If you've had any additional UI changes, follow step 7 from "Staging workflow"
* If all is well, open a pull request on Github to merge `..-ui-build` into `..-data-build`
  * In theory this PR should only show code changes to the UI
  * This PR should include screenshots of a local Jekyll server with the latest code/data, of the specific changes made
* Open a Github PR to merge `..-data-build` into `master`
  * This will kick off a Travis CI job, but it will not build the site \(should last ~30 sec\)

