---
title: "String Interpolation Syntax"
slug: "string-interpolation-syntax"
hidden: false
metadata: 
  description: "The string interpolation syntax is designed for configuring authentication objects. It controls data coordinating between the consequent requests and responses."
createdAt: "2021-09-03T09:37:56.328Z"
updatedAt: "2022-11-23T15:11:19.313Z"
---
The string interpolation syntax is designed for configuring authentication objects. It controls data coordinating between the consequent requests and responses. 

The syntax allows you to create a template (interpolation string) for the value to be extracted from the specified location. You can only create the template based on the previous authenticated requests and responses. 

The interpolation string uses the double curly braces `{{` and `}}` as delimiters and consists of two general parts:

1. **Location** of the data to be transformed.
2. **Functions** separated by the `|` operator. The functions support chaining with the same operator.

_Format:_ `{{ location | function 1 | function 2 }}`

The parts comprise the following components:

[block:parameters]
{
  "data": {
    "h-0": "Part",
    "h-1": "Components",
    "0-0": "**Location**",
    "0-1": "1. Stage name  \n2. Source: `response`  \n3. Location: `url`, `headers`, `body`  \n  \n_Format_: `{{ \\<stage_name>.<source>.<location> \\| <function> }}`  \n_Example_: `{{ stage1.response.headers | <function> }}`",
    "1-0": "**Function**",
    "1-1": "1. Pipe: get, match, encode  \n2. Parameter separated from the pipe by a colon  \n  \n_Format_:` {{ <location> \\| <pipe>: <parameter> }}`  \n_Example_:` {{ stage1.response.headers | get: '/Set-Cookie' }}`  \n  \n_Example with chained functions:_ `{{ stage1.response.headers | get: '/Set-Cookie' | match: /sid=(.+)/ : 1 }}`  \n  \n**Note:** The functions are applied in the relevant order. It means that in the example above, the first `get` will be applied and then `match`."
  },
  "cols": 2,
  "rows": 2,
  "align": [
    "left",
    "left"
  ]
}
[/block]

### Supported pipes

**get**<br>  
Returns the value associated with the XPath, or undefined if there is none.<br>

_Parameters:_

- `xpath` - xpath string<br>

_Format:_ `{{ <location> | get: <xpath> }}`<br>  
_Example:_ `{{ step1.response.headers | get: '/Set-Cookie' }}`

**match**<br>  
Retrieves the result of matching a string against a regular expression.<br>

_Parameters:_

- `regex` - regular expression
- `group` - number of the capture group (optional, default `1`)<br>

_Format:_ `{{ <location> | match: < regex> : <group> }}`<br>  
_Example:_ `{{ step1.response.body | match: /sid=(.+)/ : 1 }}`

**encode**<br>  
Encodes the value to some format.<br>

_Parameters:_

- format - `base64`, `url` or `none` (optional, default `none`)<br>

_Format:_ `{{ <location> | encode: <format> }}`<br>  
_Example:_ `{{ step1.response.body | encode: 'base64' }}`

**otpToken**<br>

Inserts an OTP (one-time password) with preconfigured parameters.

_Parameters:_

- OTP type - `No OTP`, `Time-based one-time password (TOTP)`,  `Hash-based one-time password (HOTP)`, `Google Authenticator (TOTP)`
- Secret key - non-zero length field, string
- Number of digits - integer, between` 1` and `8`
- Token duration - hidden for HOTP, between` 1` and `2147483647` (Int32 max)
- Algorithm - `Sha1` (default), `Sha256`, `Sha512`

_Format:_ {{otpToken}}  
_Example:_ {{otpToken}}

### Generating mock data

If you need to generate random data to use it during configuration of an authentication object, you can apply one of the following [Faker.js](https://github.com/faker-js/faker) data generators:

- `uuid`<br>  
  _Example:_  `{{ $faker.datatype.number }}`

- `number`<br>  
  _Example:_  `{{ <$faker>.datatype.uuid }}`