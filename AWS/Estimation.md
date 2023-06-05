# AWS Estimation for Permissoins Management
This page explains how to use the estimate the cost of using Permissions Management with AWS. Here's the list of billable resource types in AWS: [Test](http://tblah)

## Export resource list
The resources in AWS can be counted in two ways:

### Use AWS Tag Editor
1. Open AWS Tag Editor: https://console.aws.amazon.com/resource-groups/tag-editor
2. Update filters to search for All Resource Types in All Regions <Image>
3. Click 'Search resources' and allow some time for search to complete.
Note: This option does not use an indexed resource list and will take a while to complete.
4. Once the search completed, click "Export <N> resources to CSV" and select "Export all tags" <Image>
5. This will export the resource list in CSV

###  Use AWS Resouce Explorer
If you are estimating for only handful of selected accounts and have enabled AWS resource explorer, you can use this option. 
1. Open the Resource Search page by going to the below URL: [Resource search page](https://resource-explorer.console.aws.amazon.com/resource-explorer/home)
2. Update search settings to show ARN, show 100 resources per page and XXX 
3. Click Search
4. Once the search completes, export the search results by clicking YYY
  
Note: 
* It works off an indexed list and it manifold faster than Tag Editor
* Resource Explorer only supports Account-wise search and supports ^#^#^#% of billable resources. Supported resource types: https://docs.aws.amazon.com/resource-explorer/latest/userguide/supported-resource-types.html?icmp=docs_re_console_supported-resource-types
* Resource explorer can be enabled and used at no additional cost. Enable here: https://resource-explorer.console.aws.amazon.com/resource-explorer/home?region=us-east-2#/onboarding
https://resource-explorer.console.aws.amazon.com/resource-explorer/home?region=us-east-2#/onboarding

## Import Results
* Download the [AWS Estimation Template](https://github.com/microsoft/EPMEstimator/raw/main/EPM%20Pricing%20Estimator%20for%20AWS.xlsx) (You can right-click <-- this link and click 'Save Link As' to download)
* Open the 'Query Export' sheet in the downloaded file. 
* Open the exported CSV file in excel and Paste the it's contents in Columns A to H of downloaded template

## Calculate Ballpark Price Estimate
* Go to 'Resources and Pricing' sheet. 
* Right-click one of the tables and click 'Refresh'. 
* See the pricing Estimate in 'Resources and Pricing' sheet.

  
