# logicapp-azure-resourcemgmt
Logic App that calls Azure Resource Management REST API to get information about resources in a subscription

## Pre-Requisites
- Enable Managed Identity (MI) for Logic App
- Grant MI of Logic App Reader access to Subscription

## Deploy project to Azure using Powershell Az module
From PowerShell console execute the following commands
```console
cd 'bin folder'
Connect-AzAccount -Tenant XX-YY-ZZ -Subscription XX-YY-ZZ
.\Deploy-AzureResourceGroup.ps1 -ArtifactStagingDirectory . -TemplateFile LogicApp.json -TemplateParametersFile LogicApp.parameters.json
```

## HTTP Trigger POST payload
```json
{
    "schema": {
        "type": "object",
        "properties": {
            "subscriptionId": {
                "type": "string"
            },
            "resourceType": {
                "type": "string"
            },
            "apiVersion": {
                "type": "string"
            }
        }
    },
    "method": "POST"
}
```

For example the payload body will look like this:
```json
 {
   "subscriptionId": "XXX-YYY-ZZZ",
   "resourceType": "Microsoft.Synapse/workspaces/sqlPools",
   "apiVersion": "2021-04-01"
 }
```
