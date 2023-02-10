---
title: "Error Messages in Schema Editor"
slug: "error-messages-in-schema-editor"
hidden: true
createdAt: "2021-11-10T07:29:31.479Z"
updatedAt: "2021-11-10T08:05:34.299Z"
---
## Error message format

All error messages can be represented as  `<location_prefix> <error_message>` where:

* `<location_prefix>` is either "the value at /some_path" or "the root value"

* `<error_message>` can either be hardcoded in schema or humanized from validator output.



## Hardcoded custom error messages

Hardcoded OAS custom error messages are taken from [swagger-editor](https://github.com/swagger-api/swagger-editor/tree/master/src/plugins/json-schema-validator); while original specifications are available here: [v2.0](https://github.com/OAI/OpenAPI-Specification/blob/main/schemas/v2.0/schema.json) &  [v3.0](https://github.com/OAI/OpenAPI-Specification/blob/main/schemas/v3.0/schema.json). 

oas v2 (swagger):
[block:parameters]
{
  "data": {
    "h-0": "error origin",
    "h-1": "`error_message`",
    "0-0": "names of path items",
    "0-1": "should only have path names that start with `/`",
    "1-0": "empty response object",
    "1-1": "should define at least one response, in addition to any vendor extension `(x-*)` fields",
    "2-0": "response object key names",
    "2-1": "should only have three-digit status codes, `default`, and vendor extensions `(x-*)` as properties",
    "3-0": "response object key names",
    "3-1": "should only have three-digit status codes, `default`, and vendor extensions `(x-*)` as properties",
    "4-0": "oauth2 authorization & token urls",
    "4-1": "should be an absolute URI"
  },
  "cols": 2,
  "rows": 5
}
[/block]
oas v3:
[block:parameters]
{
  "data": {
    "h-0": "error origin",
    "h-1": "`error_message`",
    "0-0": "user-defined schema \"required\" field format",
    "0-1": "should be an array of property names required within an object schema",
    "1-0": "names of path items",
    "1-1": "should only have path names that start with `/`",
    "2-0": "empty responses object",
    "2-1": "should define at least one response, in addition to any vendor extension `(x-*)` fields",
    "3-0": "responses object key names",
    "3-1": "should only have three-digit status codes, `default`, and vendor extensions `(x-*)` as properties",
    "4-0": "example/examples misuse",
    "4-1": "should not have both `example` and `examples`, as they are mutually exclusive",
    "5-0": "schema/content misuse",
    "5-1": "should have either a `schema` or `content` property",
    "6-0": "content extra misused fields",
    "6-1": "should not have `style`, `explode`, `allowReserved`, `example`, or `examples` when `content` is present",
    "7-0": "parameter location enum",
    "7-1": "Parameter location (`in`) must be one of the following: `path`, `query`, `header`, `cookie`"
  },
  "cols": 2,
  "rows": 8
}
[/block]
postman:

No any custom error messages were added to Postman ([v2.0](https://schema.postman.com/collection/json/v2.0.0/draft-07/collection.json) & [v2.1](https://schema.postman.com/collection/json/v2.1.0/draft-07/collection.json) schemas.


## "Humanized" messages

[block:parameters]
{
  "data": {
    "h-0": "schema constrain name",
    "h-1": "`error_message`",
    "0-0": "required",
    "0-1": "is missing the required field `field_name`",
    "1-0": "enum",
    "1-1": "must be one of: \"_item1_\", \"_item2_\", or \"_item3_\"",
    "2-0": "type1",
    "2-1": "must be of type _type_name_",
    "3-0": "maxLength",
    "3-1": "must be of length _N_ or fewer",
    "4-0": "minLength",
    "4-1": "must be of length _N_ or more",
    "5-0": "minimum",
    "5-1": "must be equal to or greater than _N_",
    "6-0": "maximum",
    "6-1": "must be equal to or less than _N_",
    "7-0": "exclusiveMinimum",
    "7-1": "must be greater than _N_",
    "8-0": "exclusiveMaximum",
    "8-1": "must be less than _N_",
    "9-0": "pattern",
    "9-1": "does not match pattern _regex_pattern_",
    "10-0": "format2",
    "10-1": "must be a valid _humanized_format_ string",
    "11-0": "additionalProperties",
    "11-1": "has an unexpected property `property_name`",
    "12-0": "uniqueItems",
    "12-1": "must be unique but elements _X_ and _Y_ are the same",
    "13-0": "minItems",
    "13-1": "must have _N_ or more items",
    "14-0": "maxItems",
    "14-1": "must have _N_ or fewer items",
    "15-0": "minProperties",
    "15-1": "must have _N_ or more properties",
    "16-0": "maxProperties",
    "16-1": "must have _N_ or fewer properties",
    "17-0": "const",
    "17-1": "must be equal to constant \"constant_value\""
  },
  "cols": 2,
  "rows": 18
}
[/block]
1 Some constrains like "type" could contain more than one allowed values. List of allowed values are also "humanized":

* two items list: item1 or item2 (e.g.: the value at /item/0/request/body/formdata/0/type must be one of: "text" or "file")

* three+ items list: item1, item2, ..., or itemN (e.g.: the value at /schemes/1 must be one of: "http", "https", "ws", or "wss")

2  String format humanization map:
[block:html]
{
  "html": "{\n  'date-time': 'date and time',\n  'time': 'time',\n  'date': 'date',\n  'duration': 'duration',\n  'email': 'email address',\n  'idn-email': 'internationalized email address',\n  'hostname': 'host name',\n  'idn-hostname': 'internationalized host name',\n  'ipv4': 'IPv4 address',\n  'ipv6': 'IPv6 address',\n  'uuid': 'unique identifier',\n  'uri': 'URI',\n  'uri-reference': 'URI reference',\n  'iri': 'internationalized URI',\n  'iri-reference': 'internationalized URI reference',\n  'uri-template': 'URI template',\n  'json-pointer': 'JSON pointer',\n  'relative-json-pointer': 'relative JSON pointer',\n  'regex': 'regular expression'\n}"
}
[/block]