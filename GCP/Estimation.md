# Permissions Management Resource Estimation for GCP

## Get Resources
* Open GCP Cloud Shell at 
https://shell.cloud.google.com/?hl=en_US&fromcloudshell=true&show=terminal

* Paste the following script and run:
``` bash
#!/bin/bash
echo -n """" > gcpresources.csv
for project in $(gcloud projects list --format=""value(projectId)"")
    do
        for api in $(gcloud asset list --content-type='resource' --project $project --format='csv(name,asset_type,resource.discovery_name,resource.data.name,resource.location)')
           do
             echo "${project}, ${api}" >> gcpresources.csv
        done 
done
cloudshell download gcpresources.csv
```

> **If you get an API access permission prompt, click 'Authorize'**

* When the download prompt appears, click 'Download'

## Calculate Ballpark Price Estimate
* Download the [Estimation Template for GCP](https://github.com/microsoft/EPMEstimator/raw/main/EPM%20Pricing%20Estimator%20for%20GCP.xlsx)
* Open the exported CSV file in excel and Paste it's content in the 'Query Export' sheet of download template in Columns A to E
* Go to 'Resources and Pricing' sheet
* Right click one of the tables and click 'Refresh'. 
* See the pricing Estimate in 'Resources and Pricing' sheet."
