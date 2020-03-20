---
description: We extract aggregate spend data from the OCPO Data Warehouse
---

# OCPO Data Warehouse

The OCPO maintains a database of aggregate transaction data matched opportunistically to suppliers in the Central Supplier Database to be able to explore the effectiveness of procurement policy, among other things.

The payments data is enriched with:

* Supplier ownership/demographics data from the CSD
* Supplier location data by geocoding addresses in the CSD
* Industry classification of the supplier from CSD

We extract the data using a SQL Server Integration Services \(SSIS\) package that runs the following query, and saves the data to an Excel file:

```text
SELECT  CONCAT(FiscalYear-1, '-', FiscalYear % 2000) as FinancialYear
      ,[Department]
      ,dimDepartment.[Province] as OrganOfStateProvince
      ,[SCOAVersion]
      ,[GovernmentSphere]
      ,[ExtSupplierType]
      ,[ItemParentLvl1Descr]
      ,[ItemParentLvl2Descr]
      ,[ItemParentLvl3Descr]
      ,[ItemParentLvl4Descr]
      ,[CSDSupplierNumberSource]
      ,[SupplierType]
      ,[SupplierSubType]
      ,[Country]
      ,[BEELevel]
      ,[BEECertificateType]
      ,[Turnover]
      ,[BlackOwned]
      ,[RuralTownship]
      ,[Youth]
      ,[MilitaryVeteran]
      ,[Disabled]
      ,[Women]
      ,[GovernmentEmployee]
      ,[OrganOfStateType]
      ,[IndustryNameParent]
      ,[IndustryNameChild]
       ,[PhysicalCountry]
      ,[PhysicalProvince]
      ,[PhysicalDistrictName]
      ,[PhysicalMunicipalityName]
      ,[PhysicalCityName]
      ,[PhysicalSuburbName]
      ,sum([TotalTransAmount]) as TotalTransAmount
FROM [OCPO_DW].[dbo].[factSpendAnalysisBySupplier]
LEFT OUTER JOIN factCSD_SupplierAddress on (factSpendAnalysisBySupplier.SupplierNumber = factCSD_SupplierAddress.SupplierNumber)
LEFT OUTER JOIN [dimDepartment] on (factSpendAnalysisBySupplier.InstallationID = dimDepartment.InstallationID)
Group by CONCAT(FiscalYear-1, '-', FiscalYear % 2000) 
      ,[Department]
      ,dimDepartment.[Province]
      ,[SCOAVersion]
      ,[GovernmentSphere]
      ,[ExtSupplierType]
      ,[ItemParentLvl1Descr]
      ,[ItemParentLvl2Descr]
      ,[ItemParentLvl3Descr]
      ,[ItemParentLvl4Descr]
      ,[CSDSupplierNumberSource]
      ,[ExtSupplierName]
      ,[SupplierName]
      ,[SupplierType]
      ,[SupplierSubType]
      ,[Country]
      ,[BEELevel]
      ,[BEECertificateType]
      ,[Turnover]
      ,[BlackOwned]
      ,[RuralTownship]
      ,[Youth]
      ,[MilitaryVeteran]
      ,[Disabled]
      ,[Women]
      ,[GovernmentEmployee]
      ,[OrganOfStateType]
      ,[IndustryNameParent]
      ,[IndustryNameChild]
       ,[PhysicalCountry]
      ,[PhysicalProvince]
      ,[PhysicalDistrictName]
      ,[PhysicalMunicipalityName]
      ,[PhysicalCityName]
      ,[PhysicalSuburbName]

```

