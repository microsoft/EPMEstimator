# Azure Estimation for Permissoins Management
Here's how to estimate the cost for Azure subscription(s):

## Open Resource Graph Explorer
* Open Azure Resource Graph Explorer at [Azure Resource Graph Explorer](https://ms.portal.azure.com/#blade/HubsExtension/ArgQueryBlade)
* Make sure that Authorization Scope is set to 'None'

![Azure Authorization Scope](https://github.com/microsoft/EPMEstimator/blob/main/Azure/AzureAuthScope.png)

## Get Resources 
* Create a new query.

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

>  **Important!** Make sure that formatted results are turned 'Off'.

* Export the results to CSV by clicking 'Downloaded as CSV'
![Download as CSV](https://github.com/microsoft/EPMEstimator/blob/main/Azure/AzureResultsDownload.png)

## Import Results
* Download the [Azure Estimation Template](https://github.com/microsoft/EPMEstimator/raw/main/EPM%20Pricing%20Estimator%20for%20Azure.xlsx) and Open the 'Query Export' sheet. 
* Paste the contents of the exported CSV in Columns A to H
* Open the exported CSV file in excel

## Calculate Ballpark Price Estimate
* Go to 'Resources and Pricing' sheet. 
* Right click the table and click 'Refresh'. 
* See the pricing Estimate in 'Resources and Pricing' sheet.
