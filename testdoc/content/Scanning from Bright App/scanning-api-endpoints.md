---
title: "Scanning API Endpoints"
slug: "scanning-api-endpoints"
hidden: false
metadata: 
  description: "To scan API endpoints using a predefined schema, follow these steps"
createdAt: "2021-09-01T06:52:54.882Z"
updatedAt: "2022-07-29T08:44:48.637Z"
---
[block:embed]
{
  "html": "<iframe class=\"embedly-embed\" src=\"//cdn.embedly.com/widgets/media.html?src=https%3A%2F%2Fwww.youtube.com%2Fembed%2FBg0ko2Rx_nM%3Ffeature%3Doembed&display_name=YouTube&url=https%3A%2F%2Fwww.youtube.com%2Fwatch%3Fv%3DBg0ko2Rx_nM&image=https%3A%2F%2Fi.ytimg.com%2Fvi%2FBg0ko2Rx_nM%2Fhqdefault.jpg&key=f2aa6fc3595946d0afc3d76cbbd25dc3&type=text%2Fhtml&schema=youtube\" width=\"854\" height=\"480\" scrolling=\"no\" title=\"YouTube embed\" frameborder=\"0\" allow=\"autoplay; fullscreen\" allowfullscreen=\"true\"></iframe>",
  "url": "https://www.youtube.com/embed/Bg0ko2Rx_nM%22%20title=%22YouTube%20video%20player%22%20frameborder=%220%22%20allow=%22accelerometer",
  "title": "Scanning APIs Using an OpenAPI Schema",
  "favicon": "https://www.youtube.com/favicon.ico",
  "image": "https://i.ytimg.com/vi/Bg0ko2Rx_nM/hqdefault.jpg"
}
[/block]
To scan API endpoints using a predefined schema, follow these steps:
1. In the **Attack surface discovery** section, select **Via API schema (for API endpoints)** to use either an Open API specification (Swagger) or a Postman collection: `*.yml` / `*.yaml` / `*.json`.
[block:callout]
{
  "type": "warning",
  "body": "Bright supports the following versions of the API schemas: Swagger 2+, OpenAPI 3+, Postman 2+. To ensure proper scanning of an API, you must configure the schema according to the general specification and specific Bright requirements. Find more information about the configuration validation [here](/docs/troubleshooting).",
  "title": "Important"
}
[/block]

[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/333d8a1-api-option.png",
        "api-option.png",
        1405,
        678,
        "#232a2d"
      ],
      "sizing": "80"
    }
  ]
}
[/block]
2. Select a schema file for the scan. You can either upload the file from a disk or use a pre-uploaded file from the Bright storage. You can also import a schema from a cloud by specifying the relative URL.
[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/adf27b5-select-api-schema.png",
        "select-api-schema.png",
        1556,
        842,
        "#212a2d"
      ],
      "sizing": "80"
    }
  ]
}
[/block]
Once you upload the schema file, you can open it in the Schema Editor (Linter). Use this option to validate and [edit the uploaded schema](/docs/edit-an-uploaded-api-schema) before running a scan. Some schema files may contain configuration errors that block scanning. To learn how to identify the files with configuration errors, see [Configuring an API Schema](https://docs.neuralegion.com/docs/configuring-an-api-schema-for-scanning).
[block:callout]
{
  "type": "info",
  "title": "Note",
  "body": "Some hosts specified in the uploaded schema may be unreachable or unauthorized for direct scanning from the cloud. In this case, you may need to connect the local Repeater for the scan or change the hosts in the schema using the **Schema editor** functionality."
}
[/block]

[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/ce16587-open-schema-editor.png",
        "open-schema-editor.png",
        1401,
        682,
        "#21292c"
      ],
      "sizing": "80"
    }
  ]
}
[/block]