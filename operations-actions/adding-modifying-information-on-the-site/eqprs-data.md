# EQPRS data

The EQPRS data is available on vulekamali as tabular data that can be searched and filtered for relevant indicators. This shows the Quarterly Performance Reporting indicators shown in the Annual Performance Plans, Strategic Plans, ENE and EPRE documents, as well as Annual Reports.

The data looks like this on vulekamali&#x20;

<figure><img src="../../.gitbook/assets/Screenshot_2023-02-06_18-06-00.png" alt=""><figcaption></figcaption></figure>

It looks like this in EQPRS:

<figure><img src="../../.gitbook/assets/Screenshot_2023-02-06_18-08-23.png" alt=""><figcaption></figcaption></figure>

## Uploading EQPRS data

Uploading EQPRS data to vulekamali involves downloading a few departments at a time, and uploading each file to vulekamali. Vulekamali automatically figures out which financial year, sphere, government and department each indicator belongs to.

Every time you upload data for a given department in a given financial year (in the national or a given provicial government), all the indicators for that department in that year are deleted. This allows the data to be updated without the risk of duplicating indicators.

The video below shows the end-to-end process, and below it are step by step instructions.

{% embed url="https://youtu.be/g2k0sHtytng" %}

### Download data from EQPRS

1. Log in at [https://eqprs.dpme.gov.za/](https://eqprs.dpme.gov.za/) (Request an account if you don't have one yet)
2. Open the report form
   1. For National departments, select **National Institutions Oversight Report**
   2. For provincial departments, select **Provincial Institutions Oversight Report**
3. Select the relevant financial year
4. Select 1-3 departments under Institution

{% hint style="info" %}
**Select only 1-3 departments at a time**

The EQPRS reports sometimes time out when trying to download to much data at once. When it has timed out, It remains stuck showing the Loading... indicator for over 1 minute.

When this happens, all you can do is reload the page and start again, selecting less data this time.
{% endhint %}

5. Select the relevant Location
   1. National for national departments
   2. The relevant province for provincial departments
6. Click `View Report` and wait for the data to load
7. When the indicator table has loaded, click the Download menu, and select CSV

<figure><img src="../../.gitbook/assets/Screenshot_2023-02-06_17-11-49.png" alt=""><figcaption></figcaption></figure>

### Upload data to vulekamali

1. In the **Performance** > **EQPRS File Uploads** section of the Admin site, click **Add EQPRS file upload**.

<figure><img src="../../.gitbook/assets/2023-02-06_17-46.png" alt=""><figcaption></figcaption></figure>

2. Select the CSV file that was dowloaded from EQPRS and click Save

<figure><img src="../../.gitbook/assets/2023-02-06_17-37.png" alt=""><figcaption></figcaption></figure>

After clicking Save, the list of EQPRS file uploads is shown. The Processing completed column shows a question mark (?) for items where processing has not completed yet.

3. Reload the page every few seconds until the question mark changes to a tick or a cross.

A green tick is shown when a file has been completely processed. This does not mean all its data was imported - only that the file was fully processed.&#x20;

A red cross is shown when there was some error and the file could not be fully processed. In this case,&#x20;

* check whether you followed the instructions correctly, and try it again
* check for errors in relevant tasks in the **Django Q** > **Failed Tasks** section in admin and see if the error report helps you to troubleshoot the issue
* contact the developers if you fail to solve it yourself.

4. If a green tick is indicating that the file was fully processed, check if the **Number of rows we could not import column is zero**.&#x20;
5. If it is not zero, open the upload task detail by clicking on the creation date.

<figure><img src="../../.gitbook/assets/Screenshot_2023-02-06_18-00-30.png" alt=""><figcaption></figcaption></figure>

6. Check the import report and note that the indicators for the departments listed here were not imported because the names in EQPRS do not match the names in Vuelakamli.

{% hint style="danger" %}
**Do not change the department names in vulekamali to match EQPRS**

Vulekamali reflects official department names as per the appropriation acts of each financial years. Budget and actual spending data should be normalised to match these names. Support for non-matching names in EQPRS may be added to vulekamali in future.
{% endhint %}
