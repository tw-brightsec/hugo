---
title: "Use Cases"
slug: "use-cases"
excerpt: "Below are some examples how you can use Repeater scripts during scanning of a local target."
hidden: false
metadata: 
  description: "Below are some examples how you can use Repeater scripts during scanning of a local target."
createdAt: "2021-09-06T15:15:18.815Z"
updatedAt: "2022-10-11T17:18:28.537Z"
---
## Sample HMAC code

The following script provides an example of how to compute an HMAC authorization token. 

The example is taken from the [Amazon S3 documentation](http://s3.amazonaws.com/doc/s3-developer-guide/RESTAuthentication.html).

Suppose your AWS Access Key ID is `44CF9590006BF252F707`,  AWS Secret Access Key is `OtxrzxIsfpFjA7SwPzILwy8Bw21TLhquhboDYROV`, and authorization label is `AWS`.

The authorization token is a composite of a secure cryptographic algorithm, the AWS Access Key ID and a hash-encoded signature.

Then you could compute the authorization token as follows:

```javascript
const { createHmac } = require('crypto');
const { URL } = require('url');
const AWS_ACCESS_KEY_ID = '44CF9590006BF252F707';
const AWS_SECRET_KEY = 'OtxrzxIsfpFjA7SwPzILwy8Bw21TLhquhboDYROV';
const HEADER_PREFIX = 'x-amz'.toLowerCase();
const LABEL = 'AWS';
const handle = ({ method, url, headers, body }) => {
 // headers must be in lower-case
 const caseInsensitiveHeaders = Object.fromEntries(
   Object.entries(headers).map(([key, value]) => [key.toLowerCase(), value])
 );
 // x-amz headers must be sorted by header name
 const headersByPrefix = Object.entries(caseInsensitiveHeaders)
   .filter(([key]) => key.startsWith(HEADER_PREFIX))
   .map(
     ([key, value]) =>
       // The values of headers whose names occur more than once should be white space-trimmed and concatenated with comma separators to be compliant with section 4.2 of RFC 2616.
       `${key}:${
         Array.isArray(value) ? value.map((x) => x.trim()).join(',') : value
       }`
   )
   .sort();
 const normalizedUrl = url.replace(/\/$/, '');
 const { pathname } = new URL(normalizedUrl);
 const message = [
   method,
   caseInsensitiveHeaders['content-md5'],
   caseInsensitiveHeaders['content-type'],
   // You have to include the PREFIX-date header in your request and ignore date header
   !caseInsensitiveHeaders[`${HEADER_PREFIX}-date`]
     ? caseInsensitiveHeaders.date
     : undefined,
   ...headersByPrefix,
   pathname || normalizedUrl
 ];
 const signature = createHmac('sha1', AWS_SECRET_KEY)
   .update(message.join('\n'))
   .digest('base64');
 const authorization = `${LABEL} ${AWS_ACCESS_KEY_ID}:${signature}`;
 return {
   url,
   method,
   body,
   headers: {
     ...headers,
     authorization
   }
 };
};
exports.handle = handle;
```



Which results in an HTTP request, with the headers looking like this:

```javascript
{
 method: 'PUT',
 url: 'https://example.com/quotes/nelson',
 headers: {
   'Content-MD5': 'c8fdb181845a4ca6b8fec737b3581d76',
   'Content-Type': 'text/html',
   'Date': 'Thu, 17 Nov 2005 18:49:58 GMT',
   'X-Amz-Meta-Author': 'foo@bar.com',
   'X-Amz-Magic': 'abracadabra'
 }
}
```



The server response for this request will look like this:

```javascript
{
 url: 'https://example.com/quotes/nelson',
 method: 'PUT',
 body: undefined,
 headers: {
   'Content-MD5': 'c8fdb181845a4ca6b8fec737b3581d76',
   'Content-Type': 'text/html',
   Date: 'Thu, 17 Nov 2005 18:49:58 GMT',
   'X-Amz-Meta-Author': 'foo@bar.com',
   'X-Amz-Magic': 'abracadabra',
   authorization: 'AWS 44CF9590006BF252F707:jZNOcbfWmD/A/f3hSvVzXZjM2HU='
 }
}
```



## Sending custom values

Sometimes you may need to provide the server with additional values to get access to the targets. Or you may need to to get the tokens of some specific headers. You can realize it by creating scripts with custom requests.

The following script is an example of how to apply host-specific static header tokens:

```javascript
const { URL } = require('url');
const HEADER_NAME = 'Some-Custom-Header';
const HOST_KEY_PAIRS = new Map()
 .set('sub-domain1.host.com', 'TOKEN_1')
 .set('sub-domain2.host.com', 'TOKEN_2')

const handle = ({ method, url, headers, body }) => {
 const { hostname } = new URL(url);
 const customHeaderValue = HOST_KEY_PAIRS.get(hostname);
 return {
   url,
   method,
   body,
   headers: {
     ...headers,
     ...(customHeaderValue ? { [HEADER_NAME]: customHeaderValue } : {})
   }
 };
};
exports.handle = handle;
```



## Using external dependency with HMAC script in repeater scripts

Generally, using external dependency is not possible in HMAC script. Therefore, to use external dependency, you need to "bundle (pack)" everything – HMAC script with its internal dependencies and external dependencies – in a single JavaScript file. For that purpose, you can use the “rollup” command, which will automate the process. 

Here is a quick guide on how to bundle external dependency needed for [AWS Signature 4 signing process](https://docs.aws.amazon.com/general/latest/gr/signature-version-4.html) with the HMAC script:

1. Check the following HMAC script and save it as a file to some place on your machine (for example, `/home/username/scripts`)

```javascript
import { SignatureV4 } from '@aws-sdk/signature-v4';
import { Sha256 } from '@aws-crypto/sha256-js';
import { URL } from 'url';

const createSigner = () => {
  const service = 'execute-api';
  const accessKeyId = 'XXXX';
  const secretAccessKey = 'XXXX';
  const sessionToken = 'XXXX';
  const region = 'AWS REGION';

  return new SignatureV4({
    region,
    service,
    sha256: Sha256,
    credentials: {
      sessionToken,
      accessKeyId,
      secretAccessKey
    }
  });
}

const handle = async ({ method, url, headers, body, ...rest }) => {
  const signer = createSigner();

  const {
    host,
    hostname,
    port,
    protocol,
    pathname,
    search = ''
  } = new URL(url);

  const signedReq = await signer.sign({
    hostname,
    protocol,
    port,
    method,
    query: search,
    path: pathname,
    headers: {
      ...headers,
      host
    }
  });

  return {
    ...rest,
    url,
    body,
    method,
    headers: signedReq.headers
  };
};
exports.handle = handle;
```



2. Install the internal dependencies of the HMAC script:

```curl
npm i -s @aws-sdk/signature-v4 @aws-crypto/sha256-js
```



3. Prepare a bundler (`rollup`) to build a single JavaScript module by installing the corresponding external dependencies:

```curl
npm i -S @rollup/plugin-node-resolve @rollup/plugin-commonjs @rollup/plugin-json rollup
```



4. Issue the following command, which will create a single file with the HMAC script and all dependencies:

```curl
rollup -p 'commonjs={include:/node_modules/}' -p 'json' -p 'node-resolve={preferBuiltins: true}' --strict --input ./path-to-your-file --format cjs --file ./path-to-output-file
```



5. Use the created  file in the Repeater script.

> 🚧 Important
> 
> While using “rollup”, make sure that you use the `es` modules instead of `cj`s: `import 'something'` VS `require('something')`:
> 
> - Before:  
>   `const { SignatureV4 } = require('@aws-sdk/signature-v4');`
> - After:  
>   `import { SignatureV4 } from '@aws-sdk/signature-v4';`