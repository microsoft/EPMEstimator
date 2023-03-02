# Azure Estimation for Permissoins Management
Here's how to estimate the cost for Azure subscription(s):

## Open Resource Graph Explorer
* Open Azure Resource Graph Explorer at [Azure Resource Graph Explorer](https://ms.portal.azure.com/#blade/HubsExtension/ArgQueryBlade)

## Get Resources 
* Create a new query.
* Make sure that Authorization Scope is set to 'None'
![Azure Authorization Scope](https://github.com/microsoft/EPMEstimator/blob/main/Azure/AzureAuthScope.png)
* Paste the following query and click 'Run Query'
```
resources
| project name, resourceGroup, location, type, kind, subscriptionId, tags
| join kind=leftouter  (resourcecontainers
        | where type == "microsoft.resources/subscriptions"
        | project SubID=subscriptionId, SubName = name)
    on $left.subscriptionId == $right.SubID
| project name, resourceGroup, location, type, kind, SubID, tags, SubName
| where type in~ ("microsoft.compute/virtualmachines","microsoft.batch/batchaccounts","microsoft.web/sites","microsoft.containerlnstance/containergroups","microsoft.servicefabric/clusters","microsoft.kubernetes/connectedclusters","microsoft.containerservice/managedclusters","microsoft.redhatopenshift/openshiftclusters","microsoft.sql/servers/databases","microsoft.dbformysql/servers","microsoft.dbformariadb/servers","microsoft.dbforpostgresql/servers","microsoft.sqlvirtualmachine/sqlvirtualmachines","microsoft.sql/managedlnstances","microsoft.datamigration/services","microsoft.documentdb/databaseaccounts","microsoft.documentdb/cassandraclusters","microsoft.hdlnsight/clusters","microsoft.streamanalytics/clusters","microsoft.cache/redis","microsoft.datafactory/factories")
```

### Download Results

>  **Important!** Make sure that formatted results are turned 'Off'.

* Export the results to CSV by clicking 'Downloaded as CSV'
![Download as CSV](https://github.com/microsoft/EPMEstimator/blob/main/Azure/AzureResultsDownload.png)

## Import Results
* Download the [Azure Estimation Template](https://github.com/microsoft/EPMEstimator/raw/main/EPM%20Pricing%20Estimator%20for%20Azure.xlsx) (You can right-click <-- this link and click 'Save Link As' to download)
* Open the 'Query Export' sheet in the downloaded file. 
* Open the exported CSV file in excel and Paste the it's contents in Columns A to H of downloaded template

## Calculate Ballpark Price Estimate
* Go to 'Resources and Pricing' sheet. 
* Right-click one of the tables and click 'Refresh'. 
* See the pricing Estimate in 'Resources and Pricing' sheet.
