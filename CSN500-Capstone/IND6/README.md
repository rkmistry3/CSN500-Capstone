# Summary of checkpoint 3

# List
```
1) To configure the vms to use our custom dns servers
2) To set the iptables and firewall such that it can allow traffic from
our network
3) Install and configure various services on our servers
```
# commaand line single line commands

`az group export -n myresourcegroup`
# bash or shell scripts
```
iptables start script
iptables -F
iptables -X
iptables -P INPUT DROP
iptables -P FORWARD DROP
iptables -P OUTPUT DROP
```

# json objects

```
{
    "$schema": "https://schema.management.azure.com/schemas/2019-04-01/deploymentTemplate.json#",
    "contentVersion": "1.0.0.0",
    "parameters": {
        "images_WS_28ci_name": {
            "defaultValue": "WS-28ci",
            "type": "String"
        },
        "disks_WS_28_externalid": {
            "defaultValue": "/subscriptions/bd627181-5ddb-4bb6-b03f-5297c3be4e1e/resourceGroups/CSN50-28-WS-28-882518/providers/Microsoft.Compute/disks/WS-28",
            "type": "String"
        }
    },
    "variables": {},
    "resources": [
        {
            "type": "Microsoft.Compute/images",
            "apiVersion": "2022-03-01",
            "name": "[parameters('images_WS_28ci_name')]",
            "location": "canadacentral",
            "tags": {
                "hidden-DevTestLabs-LabUId": "cd7fea13-b747-4c30-9761-979bd88197de",
                "DeploymentId": "634382",
                "LaunchId": "24248",
                "LaunchType": "ON_DEMAND_LAB",
                "TemplateId": "4678",
                "TenantId": "353"
            },
            "properties": {
                "storageProfile": {
                    "osDisk": {
                        "osType": "Windows",
                        "osState": "Generalized",
                        "diskSizeGB": 127,
                        "managedDisk": {
                            "id": "[parameters('disks_WS_28_externalid')]"
                        },
                        "caching": "None",
                        "storageAccountType": "Standard_LRS"
                    },
                    "dataDisks": []
                },
                "hyperVGeneration": "V1"
            }
        }
    ]
}
```
# Tables

Below is the table of the vnets and the vms:
```
| Name of the VM | Vnet |
|:-------------- |:---- |
| WC-28 | Student vnet |
| LS-28 | server vnet |
| WS-28 | server vnet |
| LR-28 | router vnet |
```
# Hyperlinks
Links that may be used for guidance:

-[The ultimate markdown cheatsheet](https://towardsdatascience.com/the-ultimate-markdown-cheat-sheet-3d3976b31a0)



