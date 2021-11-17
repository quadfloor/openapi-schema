# openapi-schemas
Quadfloor OpenAPI 3.0 JSON schemas. 

<h2>This is a work in progress project</h2>
<h2>Please contact Quadfloor dev team</h2>

## Quadfloor APIs:
- Engineering API
- Production API
- Materials API
## Schema files

# Schema Details:

## Server

OpenApi describes the full endpoint for accessing the API as `{Server URL}` + `{endpoint Path}` + `{Path Parameters}`.
So a endpoint with `/api/getResults` as path in a schema with `https://example.com` as the url in the `server` object and no parameters will tell clients to send requests to `https://example.com/api/getResults`

Server Object Example: 

```json 
"servers": [
    {
        "url": "https://{accountName}.{environment}.com.br",
        "description": "Quadfloor server url",
        "variables": {
            "accountName": {
                "default": "apiexamples",
                "description": "Your Quadfloor account name"
            }
        }
    }
],
```
The `servers` key contains an array of server objects. But `Readme.io`, our documentation system, will select the first one and use default values for the variables

## Authentication

### Security Scheme

_Security schemes_ describe autentication types that are available in this API. you can check the all the options available int the [Security Scheme Spec](http://spec.openapis.org/oas/v3.0.0#security-scheme-object) 

**They should be inserted inside the _Components Object_** 

the ones we use for Quadfloor appKey and appToken are:

```json 
"securitySchemes": {
    "appKey": {
        "type": "apiKey",
        "in": "header",
        "name": "X-QUADFLOOR-API-AppKey"
    },
    "appToken": {
        "type": "apiKey",
        "in": "header",
        "name": "X-QUADFLOOR-API-AppToken"
    }
}
```

This tells the client that the request should have `X-QUADFLOOR-API-AppKey` and `X-QUADFLOOR-API-AppToken` as variables in the request header

### Security Requirement

If defined inside the _Open API Object_ the security requirement will define the required security schemes for all endpoints. If defined inside a path object, it will define a per-endpoint security scheme. 

The example we are currently using, defined inside the _Open API Object_, is:

```json 
"security": [
        {
            "appKey": [],
            "appToken": []
        }
    ]
```

## Examples

Example objects will be ignored by our documentation generator. If the desired outcome is to have the values as placeholders in the request parameters form, they should be inside the parameter schema object in the `default` key. 

