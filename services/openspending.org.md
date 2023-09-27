# openspending-dedicated.vulekamali.gov.za

We use OpenSpending to provide an API to the fiscal data. When uploaded, dataset columns must be classified according to the [Fiscal Data Package](https://specs.frictionlessdata.io/fiscal-data-package/) types.

OpenSpending was previously hosted at openspending.org. The version of OpenSpending used by vulekamali has since been replaced by a modified implementation.

While it was unavailable, a fork of the code was deployed for National Treasury to provide continuity. OpenSpending is open source software allowing for the continued hosting despite discontinuation by the original vendor.

We extended the types available for classifying columns to support more of the South African Government Standard Chart of Accounts (SCOA). See [https://github.com/vulekamali/os-types](https://github.com/vulekamali/os-types)

We add the datasets under the info@vulekamai.gov.za user.

### Development and operations

Most of the key repositories have been forked, and some needed modifications, to ensure they can continue to be deployed.&#x20;

Original high level deployment information is at [https://github.com/vulekamali/openspending#openspending](https://github.com/vulekamali/openspending#openspending)

OpenSpending is built according to a service-oriented architecture. See the forks of the repositories for the services:

* [os-nginx-frontend](https://github.com/vulekamali/os-nginx-frontend) - provides a reverse proxy for the other services, serving them all at various paths under the same domain. That is the server to proxy all public HTTP traffic to.
* [os-conductor](https://github.com/vulekamali/os-conductor)
* [os-explorer](https://github.com/vulekamali/os-explorer)
* [os-api](https://github.com/vulekamali/os-api)
* [os-packager](https://github.com/vulekamali/os-packager)

See configuration and deployment details at [https://github.com/OpenUpSA/ansible-config/tree/master/apps/openspending](https://github.com/OpenUpSA/ansible-config/tree/master/apps/openspending) for the dedicated instance.

