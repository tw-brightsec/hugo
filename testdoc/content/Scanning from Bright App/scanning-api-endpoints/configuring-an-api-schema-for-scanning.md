---
title: "Configuring an API Schema"
slug: "configuring-an-api-schema-for-scanning"
hidden: false
metadata: 
  description: "To scan API endpoints, you need to upload the relevant schema file to NeuraLegion."
createdAt: "2021-09-01T07:11:20.973Z"
updatedAt: "2022-03-03T06:42:45.867Z"
---
To scan API endpoints, you need to upload an API schema file to Bright. For a scan to be successful, please make sure that you are using a valid schema which is configured in compliance with the original specification ([OpenAPI/ Swagger](https://swagger.io/specification/) or [Postman](https://schema.postman.com/) respectively). 

Bright validates the API schemas you upload for a new scan, either via the Bright storage or directly during the scan setup. If the schema is configured incorrectly (breaks the specification rules), the Bright Schema Editor (Linter) will mark the file as “not ready for scanning”, display an error message and prevent the user from running a scan.

You can easily detect invalid files which cannot be used for a scan by the following indicators: 
* If an uploaded file contains an error (for example, a host/server is not specified in the schema, or some parameters are specified incorrectly), then it will be indicated as NOT ready for scanning in the relevant column of the Bright storage. 



[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/8801d6c-not-ready.png",
        "not-ready.png",
        1891,
        673,
        "#22292c"
      ],
      "sizing": "80"
    }
  ]
}
[/block]
* The API schemas that are not ready for scanning are also marked with a warning icon (meaning that fixes are required) when selecting a pre-uploaded file during the scan setup.

[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/1af4ea0-select-invalid-file.png",
        "select-invalid-file.png",
        1564,
        846,
        "#232a2d"
      ],
      "sizing": "80"
    }
  ]
}
[/block]
* If a file that requires fixes is selected during the scan setup, the following warning message appears below **API settings**: “The selected specification file cannot be used to start a scan. Please use the Schema Editor to fix the issues”. 


[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/af7e7a1-file-invalid.png",
        "file-invalid.png",
        1559,
        834,
        "#242a2d"
      ],
      "sizing": "80"
    }
  ]
}
[/block]
If an API schema is not ready for scanning, then you should first correct it according to the specifications using the Schema Editor. See [Edit an Uploaded API Schema](https://docs.neuralegion.com/docs/edit-an-uploaded-api-schema) for more information. 

The **Start** scan button will be disabled until you fix all the errors in the schema. You can find the detailed information about configuration requirements and error types in the [Troubleshooting](/docs/troubleshooting) section. 

The examples of API schemas that can be properly defined and accepted for scanning by Bright are given below.

### **_Example 1:_ Swagger.json**
[block:code]
{
  "codes": [
    {
      "code": "{\n \"swagger\": \"2.0\",\n \"info\": {\n   \"title\": \"schema\",\n   \"description\": \"My API Schema\",\n   \"version\": \"0.4.5\"\n },\n \"host\": \"brokencrystals.com\",\n \"basePath\": \"/home\",\n \"schemes\": [\n   \"https\"\n ],\n \"paths\": {\n   \"/user/{userEmail}\": {\n     \"get\": {\n       \"parameters\": [\n         {\n           \"in\": \"path\",\n           \"name\": \"userEmail\",\n           \"required\": true,\n           \"type\": \"string\",\n           \"default\": \"docs@neuralegion.com\"\n         }\n       ],\n       \"produces\": [\n         \"application/json\"\n       ],\n       \"responses\": {\n         \"200\": {\n           \"description\": \"OK\"\n         }\n       }\n     }\n   }\n }\n}",
      "language": "json"
    }
  ]
}
[/block]
### **_Example 2:_ Swagger.yaml**
[block:code]
{
  "codes": [
    {
      "code": "swagger: \"2.0\"\ninfo:\n title: schema\n description: My API Schema\n version: 0.4.5\nhost: brokencrystals.com\nbasePath: /home\nschemes:\n - https\npaths:\n /user/{userEmail}:\n   get:\n     parameters:\n     - in: path\n       name: userEmail\n       required: true\n       type: \"string\"\n       default: \"docs@neuralegion.com\"\n     produces:\n       - application/json\n     responses:\n       200:\n         description: OK\n",
      "language": "php"
    }
  ]
}
[/block]
### **_Example 3:_ OpenAPI.json**
[block:code]
{
  "codes": [
    {
      "code": "{\n \"openapi\": \"3.0.1\",\n \"info\": {\n   \"title\": \"schema\",\n   \"description\": \"My API Schema\",\n   \"version\": \"0.4.5\"\n },\n \"servers\": [\n   {\n     \"url\": \"https://brokencrystals.com/{basePath}\",\n     \"variables\": {\n       \"basePath\": {\n         \"default\": \"/home\"\n       }\n     }\n   }\n ],\n \"paths\": {\n   \"/user/{userEmail}\": {\n     \"post\": {\n       \"operationId\": \"userEmail\",\n       \"parameters\": [\n         {\n           \"name\": \"userEmail\",\n           \"in\": \"path\",\n           \"required\": true,\n           \"schema\": {\n             \"type\": \"string\",\n             \"default\": \"docs@neuralegion.com\"\n           }\n         }\n       ],\n       \"responses\": {\n         \"200\": {\n           \"description\": \"200 response\",\n           \"content\": {\n             \"application/json\": {\n               \"schema\": {\n                 \"$ref\": \"#\"\n               }\n             }\n           }\n         }\n       }\n     }\n   }\n }\n}\n",
      "language": "json"
    }
  ]
}
[/block]
### **_Example 4:_ OpenAPI.yaml**
[block:code]
{
  "codes": [
    {
      "code": "openapi: \"3.0.1\"\ninfo:\n title: \"schema\"\n description: \"My API Schema\"\n version: \"0.4.5\"\nservers:\n- url: \"https://brokencrystals.com/{basePath}\"\n  variables:\n   basePath:\n     default: \"/home\"\npaths:\n /user/{userEmail}:\n   post:\n     operationId: \"userEmail\"\n     parameters:\n     - name: \"userEmail\"\n       in: \"path\"\n       required: true\n       schema:\n         type: \"string\"\n         default: \"docs@neuralegion.com\"\n     responses:\n       \"200\":\n         description: \"200 response\"\n         content:\n           application/json:\n             schema:\n               $ref: \"#\"\n",
      "language": "php"
    }
  ]
}
[/block]
### **_Example 5:_ Postman**
[block:code]
{
  "codes": [
    {
      "code": "{\n  \"info\": {\n     \"name\": \"schema\",\n     \"description\": \"My API Schema\",\n     \"schema\": \"https://schema.getpostman.com/json/collection/v2.1.0/collection.json\"\n  },\n  \"item\": [\n     {\n        \"name\": \"/user/:userEmail\",\n        \"request\": {\n           \"method\": \"GET\",\n           \"header\": [],\n           \"url\": {\n              \"raw\": \"{{baseUrl}}/user/:userEmail\",\n              \"host\": [\n                 \"{{baseUrl}}\"\n              ],\n              \"path\": [\n                 \"user\",\n                 \":userEmail\"\n              ],\n              \"variable\": [\n                 {\n                    \"key\": \"userEmail\",\n                    \"value\": \"docs@neuralegion.com\",\n                    \"description\": \"(Required) \"\n                 }\n              ]\n           }\n        },\n        \"response\": [\n           {\n              \"name\": \"OK\",\n              \"originalRequest\": {\n                 \"method\": \"GET\",\n                 \"header\": [],\n                 \"url\": {\n                    \"raw\": \"{{baseUrl}}/user/:userEmail\",\n                    \"host\": [\n                       \"{{baseUrl}}\"\n                    ],\n                    \"path\": [\n                       \"user\",\n                       \":userEmail\"\n                    ],\n                    \"variable\": [\n                       {\n                          \"key\": \"userEmail\"\n                       }\n                    ]\n                 }\n              },\n              \"status\": \"OK\",\n              \"code\": 200,\n              \"header\": [\n                 {\n                    \"key\": \"Content-Type\",\n                    \"value\": \"text/plain\"\n                 }\n              ],\n              \"cookie\": [],\n              \"body\": \"\"\n           }\n        ]\n     }\n  ],\n  \"variable\": [\n     {\n        \"key\": \"baseUrl\",\n        \"value\": \"https://brokencrystals.com/home\",\n        \"type\": \"string\"\n     }\n  ]\n}\n ",
      "language": "json"
    }
  ]
}
[/block]