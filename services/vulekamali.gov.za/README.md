# vulekamali.gov.za \(Main site\)

## Environments

### Production

[vulekamali.gov.za/admin](https://vulekamali.gov.za/admin)

The production instance of Data Manager must always be running the master branch, unless critical for debugging an urgent issue. Where possible, do such debugging using the Staging instance instead.

```text
dokku dokku@treasury1.openup.org.za:budgetportal
dokku2 dokku@treasury3.openup.org.za:budgetportal
```

### Sandbox

[sandbox.vulekamali.gov.za/admin](https://sandbox.vulekamali.gov.za/admin)

### Staging

A staging instance of Data Manager is deployed at the git remote

```text
dokku-staging dokku@treasury1.openup.org.za:budgetportal-staging
```

_**Staging normally uses the Production database, so be careful what data changes you make there to troubleshoot things.**_

## Procedure to deploy to staging

To try a change out online before deploying to production, it can be deployed to staging.

In order to deploy to staging, you must push your local branch to the `dokku@treasury1.openup.org.za:budgetportal-staging`repository under the `master` branch.

**Server permissions**

You require sufficient permissions to push to the machine where the staging app is built.

As of this writing, the machine is located at `treasury1.openup.org.za`

Generate a local SSH public-private key and share the public key with the server administrator. The administrator must ensure that you have access to push to that machine.

If you encounter a permission issue with ssh-agent, run the following:

`ssh-add`

**Set up dokku-staging remote repository**

First, you'll need to add a remote repository

`git remote add dokku-staging dokku@treasury1.openup.org.za:budgetportal-staging`

Make sure your local branch is up to date with your new changes, then push this branch to staging

`git push -f dokku-staging YOUR-BRANCH-NAME:master`

You should see output in your console from the server, indicating the status of the deployment.

Once this deployment is finished, you should be able to see the changes \(YAML format\) at `https://datamanager-staging.vulekamali.gov.za`

**Static & templates**

In order to view the changes as they would appear in production, with templating, a Travis CI build will need to be initiated for static-budget-portal.

## Procedure to deploy to production

Check out the latest master locally.

From your repo, run

```text
git push dokku master
```

