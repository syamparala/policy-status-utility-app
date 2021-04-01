# policy-status-utility-app


# What?
This Mule app can be used to generate a report of all the polices applied on an Application across all the Environments in a Business Group, Sub-Business Group based on the Org Id provided as a query param provided.

# Why?
* One of the reasons for developing this custom app is to Audit and Verify polices are using  the latest releases and using same version of policy across all apps.
* Current UI does not display the versions of the policies applied
* Even if the versions can be viewd but it wolld be very difficult to view each api one by one manually across all environments and business groups
* This utility makes it easy as this a simple Mule App and can be easily maitained by a Mule Developer.
* Uses Anypoint Platform API's under the hood.

# How?
This custom utlity app uses the Platform API's to Login, Retrive Business Group Id's, all Environment Id's, API Id's in an Environment and all the policies applied on an API 
* Has 2 login options, update _**login**_ flow reference in the _**policy-status-utility-appFlow**_ to reference appropriate login flows
    * Service Account
    * Connected APP
* Update the dev.properties file in src/main/resources with appropriate credentials.

Use the following resource path and query param to send the request once the utility is successfully deployed
```json
/policies/status?orgId={yourOrgId}
```

Sample Response.
```json
[
    {
        "orgName": "Test",
        "orgId": "954f5f25-81fd-4733-bbfb-aee5693053b0",
        "isMaster": true,
        "environments": [
            {
                "envId": "954f5f25-81fd-4733-bbfb-aee5693053b0",
                "name": "Design",
                "orgId": "954f5f25-81fd-4733-bbfb-aee5693053b0",
                "isProduction": false,
                "apis": []
            },
            {
                "envId": "954f5f25-81fd-4733-bbfb-aee5693053b0",
                "name": "DEV",
                "orgId": "954f5f25-81fd-4733-bbfb-aee5693053b0",
                "isProduction": false,
                "apis": [
                    {
                        "exchangeAssetName": "American Flights",
                        "assetId": "american-flights",
                        "autoDiscoveryId": 11111111,
                        "autodiscoveryApiName": "groupId:954f5f25-81fd-4733-bbfb-aee5693053b0:assetId:american-flights",
                        "assetVersion": "1.0.0",
                        "productVersion": "v1.0",
                        "instanceLabel": null,
                        "policies": [
                            {
                                "policyName": "client-id-enforcement",
                                "version": "1.1.3"
                            }
                        ]
                    },
                    {
                        "exchangeAssetName": "American Flights",
                        "assetId": "american-flights",
                        "autoDiscoveryId": 11111111,
                        "autodiscoveryApiName": "groupId:954f5f25-81fd-4733-bbfb-aee5693053b0:assetId:american-flights",
                        "assetVersion": "2.0.0",
                        "productVersion": "v2.0",
                        "instanceLabel": null,
                        "policies": [
                            {
                                "policyName": "json-threat-protection",
                                "version": "1.1.4"
                            },
                            {
                                "policyName": "client-id-enforcement",
                                "version": "1.2.3"
                            }
                        ]
                    }
                ]
            },
            {
                "envId": "954f5f25-81fd-4733-bbfb-aee5693053b0",
                "name": "PROD",
                "orgId": "954f5f25-81fd-4733-bbfb-aee5693053b0",
                "isProduction": true,
                "apis": [
                    {
                        "exchangeAssetName": "Orders PAPI",
                        "assetId": "orders-papi",
                        "autoDiscoveryId": 11111111,
                        "autodiscoveryApiName": "groupId:954f5f25-81fd-4733-bbfb-aee5693053b0:assetId:orders-papi",
                        "assetVersion": "1.0.0",
                        "productVersion": "v1",
                        "instanceLabel": null,
                        "policies": [
                            {
                                "policyName": "spike-control",
                                "version": "1.1.5"
                            },
                            {
                                "policyName": "xml-threat-protection",
                                "version": "1.1.4"
                            }
                        ]
                    }
                ]
            },
            {
                "envId": "954f5f25-81fd-4733-bbfb-aee5693053b0",
                "name": "QA",
                "orgId": "954f5f25-81fd-4733-bbfb-aee5693053b0",
                "isProduction": false,
                "apis": [
                    {
                        "exchangeAssetName": "American Flights",
                        "assetId": "american-flights",
                        "autoDiscoveryId": 11111111,
                        "autodiscoveryApiName": "groupId:954f5f25-81fd-4733-bbfb-aee5693053b0:assetId:american-flights",
                        "assetVersion": "1.0.0",
                        "productVersion": "v1.0",
                        "instanceLabel": null,
                        "policies": [
                            {
                                "policyName": "cors",
                                "version": "1.2.0"
                            }
                        ]
                    },
                    {
                        "exchangeAssetName": "Orders EAPI",
                        "assetId": "orders-eapi",
                        "autoDiscoveryId": 11111111,
                        "autodiscoveryApiName": "groupId:954f5f25-81fd-4733-bbfb-aee5693053b0:assetId:orders-eapi",
                        "assetVersion": "1.0.0",
                        "productVersion": "v1",
                        "instanceLabel": "eapi",
                        "policies": [
                            {
                                "policyName": "http-basic-authentication",
                                "version": "1.2.2"
                            }
                        ]
                    }
                ]
            }
        ]
    },
    {
        "orgName": "Test1",
        "orgId": "954f5f25-81fd-4733-bbfb-aee5693053b0",
        "isMaster": false,
        "environments": [
            {
                "envId": "954f5f25-81fd-4733-bbfb-aee5693053b0",
                "name": "Design",
                "orgId": "954f5f25-81fd-4733-bbfb-aee5693053b0",
                "isProduction": false,
                "apis": []
            },
            {
                "envId": "954f5f25-81fd-4733-bbfb-aee5693053b0",
                "name": "Sandbox",
                "orgId": "954f5f25-81fd-4733-bbfb-aee5693053b0",
                "isProduction": false,
                "apis": [
                    {
                        "exchangeAssetName": "Card Connect",
                        "assetId": "card-connect",
                        "autoDiscoveryId": 11111111,
                        "autodiscoveryApiName": "groupId:954f5f25-81fd-4733-bbfb-aee5693053b0:assetId:card-connect",
                        "assetVersion": "1.0.0",
                        "productVersion": "v1.0.0",
                        "instanceLabel": null,
                        "policies": [
                            {
                                "policyName": "jwt-validation",
                                "version": "1.1.4"
                            }
                        ]
                    }
                ]
            }
        ]
    }    
]
```
**Important**: This utility is still in the intial phase and do not provide commitment, please use this as starting point and feel free to customize the as per your requirement. At this point we do not have any estimated for the below enhancements completion 

**Planed Features**:
* Adding a query param that can be used to change the reponse to a CSV to generate a report
* Adding a RAML Schema for all the resources available
* New Reource that accpets the required parameters and updates a policy on a given app to the latest version
* Email the report to the required parties on a scheduled basis

