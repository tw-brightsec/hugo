---
title: "Troubleshooting"
slug: "troubleshooting"
hidden: false
metadata: 
  description: "If you get a parsing error when uploading an OpenAPI schema to NeuraLegion, validate and correct the schema configuration according to the following checklist"
createdAt: "2021-09-01T07:53:08.847Z"
updatedAt: "2022-10-18T07:21:54.577Z"
---
Bright parses an uploaded API schema to define the attack surface of the scanned target. If the schema is configured improperly, Bright displays the corresponding warnings and error messages in the Schema Editor.

This section provides the guidelines on how to deal with the configuration issues which may occur while uploading an API schema for a new scan and editing it in the Schema Editor. To learn how to work with the Schema Editor, see [Edit an Uploaded API Schema](/docs/edit-an-uploaded-api-schema).

### Configuration issues overview

All configuration issues can be divided in to two groups: 

- **The issues that may affect the scan results, but do not prevent running a scan**. Such issues are indicated with yellow warning icons in the navigation tree and the smart view of the Schema Editor, and are usually caused by some missing values. To ensure the best scan results, it is recommended to resolve all the warnings that the Schema Editor points out.

[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/5ce5024-warnings.png",
        "warnings.png",
        1554
      ],
      "sizing": "80"
    }
  ]
}
[/block]



- **Critical issues (errors) that prevent using the schema for a scan**. Such issues are indicated with red error icons in the navigation tree and the smart view of the Schema Editor. They are also accompanied with the corresponding error messages at the bottom of the Schema Editor. The messages usually contain a link (path) to the place in the schema view where the issue is found and a short description of the error cause. 

[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/f691ccc-errors.png",
        "errors.png",
        1566
      ],
      "sizing": "80"
    }
  ]
}
[/block]



Hierarchically, there are several levels of errors depending on their cause:

- **Syntax errors**. Have the highest priority, and therefore are displayed first in case of multiple errors of different origin. You will be able to see other errors only after you fix the syntax errors.

[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/62ffa88-syntax-error.png",
        "syntax-error.png",
        1565
      ],
      "sizing": "80"
    }
  ]
}
[/block]



- **Validation errors**. Mostly involve incorrect specification of property names and their values. Structurally, they are presented as `<location_prefix>: <error_message>`, where:

  - `<location_prefix>` is either "Error at <u>/path</u>" or "Error at the <u>schema root</u>", where the underlined part is a link to a specific place in the schema. An external path (to an endpoint, an object) starts from `/`, while all items inside an object (internal path) are separated with `.`
  - `<error_message>` is a short description of the error cause.

  Below is an example of a validation error caused by incorrect data type of a value. On the screenshot, the host (`url`) is expected to be a string, but an additional character was added to demonstrate the error.

[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/8de10a9-url-string.png",
        "url-string.png",
        1555
      ],
      "sizing": "80"
    }
  ]
}
[/block]



- **Converting errors**. Such errors may occur when the converter cannot generate a .HAR file based on the schema due to invalid configuration. For example:
  - When a sample value cannot be generated due to incorrect (contradicting) conditions. On the screenshot below the minimum number was set to 30, and the maximum number was set to 10. No number can meet these conditions, which resulted in a converting error.

[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/c6ae979-max-min.png",
        "max-min.png",
        1403
      ],
      "sizing": "80"
    }
  ]
}
[/block]



- When prefixing item-level `host` property with a character like `^` in a Postman collection. 

[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/057a984-converting-error.png",
        "converting-error.png",
        1554
      ],
      "sizing": "80"
    }
  ]
}
[/block]



### OpenAPI/Swagger schema validation checklist

If you get a parsing error when uploading an OpenAPI schema to Bright, validate and correct the schema configuration according to the following checklist: 

1. A **target server (host)** must be specified:
   - If you are using OpenAPI  3+,  include the `servers` property.
   - _(For OAS 3)_. If the `servers` values contain variables, it is recommended to define them explicitly (use variable substitutions) to ensure correct scan results. See item 4 for more information. 
   - If you are using a Swagger 2+ schema, include the `host` property.

2. OAS 3 may include **multiple servers**. Here is an example taken from the  [Swagger documentation](https://swagger.io/specification/#server-object):

```json
}
 "servers": [
   {
     "url": "https://development.gigantic-server.com/v1",
     "description": "Development server"
   },
   {
     "url": "https://staging.gigantic-server.com/v1",
     "description": "Staging server"
   },
   {
     "url": "https://api.gigantic-server.com/v1",
     "description": "Production server"
   }
 ]
}
```



Bright uses the FIRST element in the `servers` array as a scan target. If the first server in your schema is not the scan target, you need to change the order of the servers manually in the schema view, or use the Server field in the smart view. Once you select the server to be placed first in the smart view, the order of the servers will be updated automatically in the schema view. 

[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/a487eac-select-server.png",
        "select-server.png",
        843
      ],
      "sizing": "80"
    }
  ]
}
[/block]



3. Values for all parameters should be specified to ensure correct and complete scan results. You can either add the values directly to the raw schema or enter them in the corresponding **Value** fields in the smart view. 

   If no parameter value is provided:

- The corresponding value field in the Schema Editor is left empty, resulting in a warning icon next to the endpoint.

[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/99768d3-warning-icon.png",
        "warning-icon.png",
        1410
      ],
      "sizing": "80"
    }
  ]
}
[/block]



- Bright automatically defines the data type and generates a random alternate value when parsing the schema.  
  By specifying the substitutions, you ensure correct and complete scan results. 

> 👍 Tip
> 
> During generation of a random value, Bright takes in to account all the constraints defined for a certain data type in the schema. By specifying the constraints, you ensure better results of alternate values generation. For example, you can use the following constraints:
> 
> - For numbers – `minimum`, `maximum`
> - For strings – `pattern` , `minLength`, `maxLength`
> - For arrays – `maxItems`,  `minItems`,  `uniqueItems`
> - For objects – `additionalProperties`,   `minProperties`,   `maxProperties` 
> 
> For more information, see the [Swagger documentation](https://swagger.io/specification/).

4. _(For OAS 3)_. If variables are used for a server configuration, you should specify substitutions for them to ensure correct scan results. If no substitution is used, Bright automatically detects the data type and generates a random alternate value when parsing the schema.  

   The values in the smart view are displayed with the variables applied. In the example below, we set the `domain` and `apiVersion` variables for a server in the schema view:

```json
"servers": [
   {
     "url": "https://{domain}/apis/{apiVersion}",
     "description": "Code API",
     "variables": {
      "domain": {
       "default": "coda.io"
     },
     "apiVersion": {
      "default": "v1"
     }
    }
   }
  ]
```



In this case, the server in the smart view will be displayed as follows: `<https://coda.io/apis/v1`>.

### Postman collection validation checklist

If you get a parsing error when uploading a Postman collection to Bright, validate and correct the schema configuration according to the following checklist: 

1. The `URL` item must be specified properly, for example: <p>

- Literal

```http
{{url}}/.well-known/openid-configuration?client_id={{clientId}}
```



- Broken-down

```json
{
 "url": {
   "raw": "{{url}}/.well-known/openid-configuration?client_id={{clientId}}",
   "host": [
     "{{url}}"
   ],
   "path": [
     ".well-known",
     "openid-configuration"
   ],
   "query": [
     {
       "key": "client_id",
       "value": "{{clientId}}"
     }
   ]
 }
}
```



   A problem may arise when the structure of a broken-down URL is incorrect, or the required (expected) fields are missing. Please refer to the [Postman documentation](https://schema.postman.com/) for more information.

   Here is an example of incomplete URL:

```json
"url": { 
    "raw": "{{url}}/.well-known/openid-configuration?client_id={{clientId}}"
    }
```



2. Every  environmental variable must have a value. 

   The Schema Editor supports the [Postman feature of dynamic variables](https://learning.postman.com/docs/writing-scripts/script-references/variables-list/). This allows you to generate random values per request, for example:

```json
"variable": [
                {
                  "key": "batchResultId",
                  "value": "{{$guid}}"
                }
```



   The dynamic variables can also be used to generate values when converting a Postman collection in to a .HAR file.