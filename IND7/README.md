## IND7
## Name: Ritesh Mistry
```
# Creating Checkpoint2 Resources with bash

# Variable block

Location="Canada East",

RG_Name="Student-RG-634382"

Student_vnet="Student-634382-vnet"

Router_vnet="Router-28"

Server_vnet="Server-28"

SubNet="SN1"

RT_Name="RT-28"

Client_SN="Virtual-Desktop-Client"

Virtual_Appliance="192.168.28.36"

Server_SN1="172.17.28.32/27"

Virtual_Desktop="192.168.28.36/27"

DevTest_Lab="CSN500-28"

VM_Win_Client="WC-28"

VM_Win_Server="WS-28"

VM_Lnx_Router="LR-28

VM_Lnx_Server="LS-28"
```
```

# router-28.json
```{
    "$schema": "https://schema.management.azure.com/schemas/2019-04-01/deploymentTemplate.json#",
    "contentVersion": "1.0.0.0",
    "parameters": {
        "virtualNetworks_router_28_name": {
            "defaultValue": "router-28",
            "type": "String"
        },
        "virtualNetworks_server_28_externalid": {
            "defaultValue": "/subscriptions/bd627181-5ddb-4bb6-b03f-5297c3be4e1e/resourceGroups/Student-RG-634382/providers/Microsoft.Network/virtualNetworks/server-28",
            "type": "String"
        },
        "virtualNetworks_Student_634382_vnet_externalid": {
            "defaultValue": "/subscriptions/bd627181-5ddb-4bb6-b03f-5297c3be4e1e/resourceGroups/Student-RG-634382/providers/Microsoft.Network/virtualNetworks/Student-634382-vnet",
            "type": "String"
        }
    },
    "variables": {},
    "resources": [
        {
            "type": "Microsoft.Network/virtualNetworks",
            "apiVersion": "2020-11-01",
            "name": "[parameters('virtualNetworks_router_28_name')]",
            "location": "canadacentral",
            "tags": {
                "DeploymentId": "634382",
                "LaunchId": "24248",
                "LaunchType": "ON_DEMAND_LAB",
                "TemplateId": "4678",
                "TenantId": "353"
            },
            "properties": {
                "addressSpace": {
                    "addressPrefixes": [
                        "192.168.28.0/24"
                    ]
                },
                "subnets": [
                    {
                        "name": "SN1",
                        "properties": {
                            "addressPrefix": "192.168.28.32/27",
                            "delegations": [],
                            "privateEndpointNetworkPolicies": "Enabled",
                            "privateLinkServiceNetworkPolicies": "Enabled"
                        }
                    },
                    {
                        "name": "SN2",
                        "properties": {
                            "addressPrefix": "192.168.28.64/27",
                            "delegations": [],
                            "privateEndpointNetworkPolicies": "Enabled",
                            "privateLinkServiceNetworkPolicies": "Enabled"
                        }
                    },
                    {
                        "name": "SN3",
                        "properties": {
                            "addressPrefix": "192.168.28.96/27",
                            "delegations": [],
                            "privateEndpointNetworkPolicies": "Enabled",
                            "privateLinkServiceNetworkPolicies": "Enabled"
                        }
                    },
                    {
                        "name": "SN4",
                        "properties": {
                            "addressPrefix": "192.168.28.128/27",
                            "delegations": [],
                            "privateEndpointNetworkPolicies": "Enabled",
                            "privateLinkServiceNetworkPolicies": "Enabled"
                        }
                    }
                ],
                "virtualNetworkPeerings": [
                    {
                        "name": "router28-server28",
                        "properties": {
                            "peeringState": "Connected",
                            "remoteVirtualNetwork": {
                                "id": "[parameters('virtualNetworks_server_28_externalid')]"
                            },
                            "allowVirtualNetworkAccess": true,
                            "allowForwardedTraffic": true,
                            "allowGatewayTransit": false,
                            "useRemoteGateways": false,
                            "remoteAddressSpace": {
                                "addressPrefixes": [
                                    "172.17.28.0/24"
                                ]
                            }
                        }
                    },
                    {
                        "name": "router28-student634382",
                        "properties": {
                            "peeringState": "Connected",
                            "remoteVirtualNetwork": {
                                "id": "[parameters('virtualNetworks_Student_634382_vnet_externalid')]"
                            },
                            "allowVirtualNetworkAccess": true,
                            "allowForwardedTraffic": true,
                            "allowGatewayTransit": false,
                            "useRemoteGateways": false,
                            "remoteAddressSpace": {
                                "addressPrefixes": [
                                    "10.24.6.0/24"
                                ]
                            }
                        }
                    }
                ],
                "enableDdosProtection": false
            }
        },
        {
            "type": "Microsoft.Network/virtualNetworks/subnets",
            "apiVersion": "2020-11-01",
            "name": "[concat(parameters('virtualNetworks_router_28_name'), '/SN1')]",
            "dependsOn": [
                "[resourceId('Microsoft.Network/virtualNetworks', parameters('virtualNetworks_router_28_name'))]"
            ],
            "properties": {
                "addressPrefix": "192.168.28.32/27",
                "delegations": [],
                "privateEndpointNetworkPolicies": "Enabled",
                "privateLinkServiceNetworkPolicies": "Enabled"
            }
        },
        {
            "type": "Microsoft.Network/virtualNetworks/subnets",
            "apiVersion": "2020-11-01",
            "name": "[concat(parameters('virtualNetworks_router_28_name'), '/SN2')]",
            "dependsOn": [
                "[resourceId('Microsoft.Network/virtualNetworks', parameters('virtualNetworks_router_28_name'))]"
            ],
            "properties": {
                "addressPrefix": "192.168.28.64/27",
                "delegations": [],
                "privateEndpointNetworkPolicies": "Enabled",
                "privateLinkServiceNetworkPolicies": "Enabled"
            }
        },
        {
            "type": "Microsoft.Network/virtualNetworks/subnets",
            "apiVersion": "2020-11-01",
            "name": "[concat(parameters('virtualNetworks_router_28_name'), '/SN3')]",
            "dependsOn": [
                "[resourceId('Microsoft.Network/virtualNetworks', parameters('virtualNetworks_router_28_name'))]"
            ],
            "properties": {
                "addressPrefix": "192.168.28.96/27",
                "delegations": [],
                "privateEndpointNetworkPolicies": "Enabled",
                "privateLinkServiceNetworkPolicies": "Enabled"
            }
        },
        {
            "type": "Microsoft.Network/virtualNetworks/subnets",
            "apiVersion": "2020-11-01",
            "name": "[concat(parameters('virtualNetworks_router_28_name'), '/SN4')]",
            "dependsOn": [
                "[resourceId('Microsoft.Network/virtualNetworks', parameters('virtualNetworks_router_28_name'))]"
            ],
            "properties": {
                "addressPrefix": "192.168.28.128/27",
                "delegations": [],
                "privateEndpointNetworkPolicies": "Enabled",
                "privateLinkServiceNetworkPolicies": "Enabled"
            }
        },
        {
            "type": "Microsoft.Network/virtualNetworks/virtualNetworkPeerings",
            "apiVersion": "2020-11-01",
            "name": "[concat(parameters('virtualNetworks_router_28_name'), '/router28-server28')]",
            "dependsOn": [
                "[resourceId('Microsoft.Network/virtualNetworks', parameters('virtualNetworks_router_28_name'))]"
            ],
            "properties": {
                "peeringState": "Connected",
                "remoteVirtualNetwork": {
                    "id": "[parameters('virtualNetworks_server_28_externalid')]"
                },
                "allowVirtualNetworkAccess": true,
                "allowForwardedTraffic": true,
                "allowGatewayTransit": false,
                "useRemoteGateways": false,
                "remoteAddressSpace": {
                    "addressPrefixes": [
                        "172.17.28.0/24"
                    ]
                }
            }
        },
        {
            "type": "Microsoft.Network/virtualNetworks/virtualNetworkPeerings",
            "apiVersion": "2020-11-01",
            "name": "[concat(parameters('virtualNetworks_router_28_name'), '/router28-student634382')]",
            "dependsOn": [
                "[resourceId('Microsoft.Network/virtualNetworks', parameters('virtualNetworks_router_28_name'))]"
            ],
            "properties": {
                "peeringState": "Connected",
                "remoteVirtualNetwork": {
                    "id": "[parameters('virtualNetworks_Student_634382_vnet_externalid')]"
                },
                "allowVirtualNetworkAccess": true,
                "allowForwardedTraffic": true,
                "allowGatewayTransit": false,
                "useRemoteGateways": false,
                "remoteAddressSpace": {
                    "addressPrefixes": [
                        "10.24.6.0/24"
                    ]
                }
            }
        }
    ]
}
```
