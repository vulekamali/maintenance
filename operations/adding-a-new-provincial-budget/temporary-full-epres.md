---
description: >-
  How to link to the full EPREs before the full set of data is ready to be
  loaded
---

# Temporary full EPREs

EPREs are available before the budget data is ready to be loaded onto vulekamali.

To make it easier to find the EPREs until all the data is loaded onto vulekamali, we can show a link to them on the department list page:

For each province whose EPRE is available online, add an entry with the province's slug in the financial year's `epres.yaml` file in the static site, e.g. for 2020, that would be `2020-21/epres.yaml` as they get published. For example:

```text
western-cape: https://data.vulekamali.gov.za/dataset/cb84354c-18ad-4c24-b62f-d6659cc7d3a5/resource/973c7f7e-54bf-40d3-9ea9-ad20c9d50396/download/wc-epre-full-document.pdf
north-west: https://data.vulekamali.gov.za/dataset/adfbfe29-91a6-4a72-9e9e-7f28fe940bed/resource/e31d5138-b46d-4334-8ba4-38b8b24c7287/download/nw-epre-full-document.pdf

```

