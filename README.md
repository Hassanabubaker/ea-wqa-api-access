11/11/2025



# **Fetching EA's New API Data**





#### 🧭 Overview:

This repository is useful to interact with the new Environment Agency [Water Quality Archive (WQA) API](https://environment.data.gov.uk/water-quality-beta/api-docs), launched in November 2025, enabling efficient programmatic access to determinands concentration data across monitoring sites in England.





#### ⚙️ Features:

* The workflow is designed to support both short- and long-term data retrieval and structured data inspection by fetching the data into a set of nested dictionaries, where the first level corresponds to determinands by their notations (e.g '0117'), and the second level contains site specific records for each determinand defined by notations as well (e.g AN-WEN250). 
* The workflow uses the observations endpoint of the new WQA API (**/sampling-point/{pointNotation}/observation**), which replaces the measurements endpoint used in the previous API version. This endpoint returns determinand-specific concentration records for a given monitoring site (pointNotation) and is the core of the data retrieval process.
* The new WQA API has a limit of 250 rows per request. This workflow handles that constraint using the API’s skip pagination parameter within a while True loop to retrieve data for each site-determinand combination in multiple chunks. This ensures complete data extraction for long monitoring records.
* The workflow standardises the datetime field (phenomenonTime) by splitting it into separate date and time columns.
* Measurement strings in the result column are parsed using a regex pattern to separate censoring qualifiers (e.g. <) from the numeric value.
* Once all data are retrieved, the nested dictionaries are flattened and melted into a single DataFrame, suitable for downstream analysis and aggregation.







#### 📌 Project:



This repository contains code developed as part of ongoing PhD research at the University of East Anglia (UEA). It is under active development and may change. Use at your own discretion.



This work was supported by UK Research and Innovation (UKRI) through the ARIES Doctoral Training Partnership (ARIES).

