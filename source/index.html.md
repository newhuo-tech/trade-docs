**---
title: Huobi Brokerage API Document

language_tabs: # must be one of https://git.io/vQNgJ
- json

toc_footers:
- <a href='http://fed-brokerage-trust.test-18.huobiapps.com/zh-hk/user/api'>Create API Key </a>
  includes:

search: true
---

# Change Log

<style>
table {
    max-width:100%
}
table th {
    white-space: nowrap; /*Header must display in one single line*/
}
</style>



| Valid from<br>(UTC +8) | Interface     | Change      | Abstract         |
| ---------- | --------- | --------- | --------------- |
| 2022.01.17 | - | - | - |


# Introduction
---
title: Huobi Brokerage API Document

language_tabs: # must be one of https://git.io/vQNgJ
- json

toc_footers:
- <a href='http://fed-brokerage-trust.test-18.huobiapps.com/zh-hk/user/api'>Create API Key </a>
  includes:

search: true
---

# Change Log

<style>
table {
    max-width:100%
}
table th {
    white-space: nowrap; /*Header must display in one single line*/
}
</style>



| Valid from<br>(UTC +8) | Interface     | Change      | Abstract         |
| ---------- | --------- | --------- | --------------- |
| 2022.01.17 | - | - | - |


# Introduction

Welcome to use Huobi Brokerage API!

This Document is the one and only official Doc of Huobi Brokerage API. Any updates regarding functions and services provided by Huobi Brokerage API will be posted here in an ongoing way.

Please read the following contents of Brokerage OTC API in detail

Chapter I: Overview

- **Quick Start**: This section provides a brief but all-round introduction of Huobi Brokerage API. It is of great help for first-time users of Huobi Brokerage API.
- **FAQs**: This section lists frequently asked questions in the course of using Huobi Brokerage API, as well as general queries without regard to API.
- **Contact Us**: This section guides you to contact us for solutions to various questions.

Chapter II consists of detailed introduction of interface types, each type explained in one section:

- **Introduction**: Briefly introduce such type of interface, together with relevant notes and descriptions.
- ***APIs***: Introduce in detail the purpose, rate limit, request, parameter, response amongst others of each API.
- **Error Code**: Introduce common error codes and their descriptions under such interface.
- **FAQs**: Introduce frequently asked questions and solutions to them under such interface.

# Quick Start

## Preparations

To use API, sign in from the webpage, apply for API key and complete authorization setting, before making development and transactions in accordance with this document.

Click <a href='http://fed-brokerage-trust.test-18.huobiapps.com/zh-hk/user/api '>here </a> to create API Key。

Each user may create up to 20 Api Keys, with each Api Key may be set with specific access authorization.

To understand more about authorization setting:

- Access authorization: the access authorization is for data-enquiring interface, such as Enquire Asset List.

After API creation, make sure the following information are memorized or noted down:

- `Access Key`  API Access Key

- `Secret Key`  The Key for encrypted signature verification (applicable only upon request)

<aside class="notice">
Each API Key may be bound up to 20 IP addresses (Host Address or Network Address).
</aside>
<aside class="warning">
<red><b>Warning</b></red>: These two keys are inextricably related to your account security! Do NOT disclose <b>both</b> to anyone. Disclosure of your API Key may lead to asset loss, even when the withdrawal authorization is not given. Delete such API Key immediately if it is found to be leaked.
</aside>

## SDK and Code Demonstration

[Java](https://github.com/huobitech/huobi_Java) | [Python3](https://github.com/huobitech/huobi_Python) | [C++](https://github.com/huobitech/huobi_Cpp) | [C#](https://github.com/huobitech/huobi_CSharp) | [Go](https://github.com/huobitech/huobi_golang)

**Other Code Demo**

[https://github.com/huobitech?tab=repositories](https://github.com/huobitech?tab=repositories)

## Interface Type

Brokerage OTC presently provides RESTFUL interface to users. Feel comfortable to use it for your scenarios.

### REST API

REST, aka Representational State Transfer, is a popular communication mechanism based on HTTP, with each URL representing a type of resource.

Developers are advised to use REST API for their work.

**Interface Authentication**

Currently we support only private interfaces, which may be used for transaction management and account management. Every private request has to be signature-verified with your API Key.

## Access URLs
You may use the domain: api.huobi-brokerage.com.

**REST API**

**`https://api.huobi-brokerage.com`**

<aside class="notice">
Visit Huobi Brokerage API with an IP other than from mainland China.
</aside>
<aside class="notice">
It is not recommended to visit Huobi Brokerage API via proxy, out of concerns of the latter's long latency and poor stability.
</aside>
<aside class="notice">
To ensure API service stability, it is recommended to use Japanese AWS cloud server for visits. Connection stability may not be guaranteed if client servers from mainland China are used.
</aside>

## Signature Authentication

### A Description of Signature

API request, carried through internet, is likely to be tampered. To guarantee that the request is not falsified, all private interfaces, aside from public interfaces (basic information, market data), must be signature-verified with your API Key to verify if any tampering of parameters or values was made in the course of transmission.
Each API Key may access certain interface only after it's assigned with corresponding authorization. A newly created API Key shall be assigned with proper authorization. Check the type of authorization required by an interface and make sure your API Key is properly authorized for it before using that interface.
805
A legal request shall consist of the following components:

- Request Address: i.e. Server Address api.huobi-brokerage.com, such as api.huobi-brokerage.com/v1/open/apiKeyDemo.
- API Access Id (AccessKeyId): The Access Key in your requested API Key.
- Signature Method (SignatureMethod): The Hash based Protocol for computing signature. HmacSHA256 will be used here.
- Signature Version (SignatureVersion): Version of signature protocol. It's Version 2 here.
- Timestamp (Timestamp): The UTC time when you made the request. For instance, 2017-05-11T16:22:06. Including this time value in your query request will help prevent interception attempts from third parties.
- Mandatory and optional parameters: Each method contains both mandatory and optional parameters that define API call. Please refer to descriptions of methods for their definitions and functions.
  - For GET request, each method's self-contained parameters shall be signature-computed.
  - For POST request, each method's self-contained parameters are not signature-verified, but they shall be included in the body.
- Signature: The value as a result of signature-computation, used to ensure the signature is valid and not tampered with.

### Signature Steps

Normalize the requests to be signature-computed. As when HMAC is used for signature computation, different inputs may generate totally different outputs. Therefore, normalize requests before carrying out signature computation. Please see the following example of a request to query an order detail.

The complete request URL for an enquiry of order details:

`https://api.huobi-brokerage.com/v1/open/apiKeyDemo?`

`AccessKeyId=e2xxxxxx-99xxxxxx-84xxxxxx-7xxxx`

`&SignatureMethod=HmacSHA256`

`&SignatureVersion=2`

`&Timestamp=2017-05-11T15:19:30`

`&order-id=1234567890`

**1. Method for making a request (GET or POST) is appending the request with link break 「\n」**

As in:
`GET\n`

**2. Add the domain in lower case, appended with link break 「\n」**

As in:
`
api.huobi-brokerage.com\n
`

**3. The path is appended with line break 「\n」**

As in apiKeyDemo：<br>
`
/v1/open/apiKeyDemo\n
`

Also as in WebSocket v2<br>
`
/ws/v2
`

**4. Apply URL encoding to parameters and sort them by ASCII code.**

For example, the following are the original order of URL-encoded request parameters:


`AccessKeyId=e2xxxxxx-99xxxxxx-84xxxxxx-7xxxx`

`demo-id=1234567890`

`SignatureMethod=HmacSHA256`

`SignatureVersion=2`

`Timestamp=2017-05-11T15%3A19%3A30`

<aside class="notice">
Use UTF-8 encoding. They are also URL encoded. All hexadecimal characters shall be in upper case, such as 「:」 will be encoded as 「%3A」, and space encoded as 「%20」.
</aside>
<aside class="notice">
Timestamp (Timestamp) shall be in the format of YYYY-MM-DDThh:mm:ss and URL encoded. Timestamp's validity lasts 5 minutes.
</aside>

Once sorted, the parameters are as follows:

`AccessKeyId=e2xxxxxx-99xxxxxx-84xxxxxx-7xxxx`

`SignatureMethod=HmacSHA256`

`SignatureVersion=2`

`Timestamp=2017-05-11T15%3A19%3A30`

`demo-id=1234567890`

**5. Concatenate the above lines sequentially with character 「&」**


`AccessKeyId=e2xxxxxx-99xxxxxx-84xxxxxx-7xxxx&SignatureMethod=HmacSHA256&SignatureVersion=2&Timestamp=2017-05-11T15%3A19%3A30&demo-id=1234567890`

**6. Assemble the strings as follows that need to be signature-computed.**

`GET\n`

`api.huobi-brokerage.com\n`

`v1/open/apiKeyDemo\n`

`AccessKeyId=e2xxxxxx-99xxxxxx-84xxxxxx-7xxxx&SignatureMethod=HmacSHA256&SignatureVersion=2&Timestamp=2017-05-11T15%3A19%3A30&demo-id=1234567890`


**7. Generate a digital signature with the 「Request Strings」 in the previous step and your Secret Key.**


1. Generate a Hash value by calling HmacSHA256 hash function and applying the parameters of the Request Strings and private API key.
2. Encode that Hash with base-64 and get the value that is the digital signature required by this interface.

`4F65x5A2bLyMWVQj3Aqp+B4w+ivaA7n5Oi2SuYtCJ9o=`

**8. Include the digital signature in the request.**

For the Rest interface:

1. Include all necessary parameters in the Path Parameter to be called by interface.
2. Include the URL-encoded digital signature in the Path Parameter with the name 「Signature」.

Eventually, the API Request to be sent to server should be:

`https://api.huobi-brokerage.com/v1/open/apiKeyDemo?AccessKeyId=e2xxxxxx-99xxxxxx-84xxxxxx-7xxxx&demo-id=1234567890&SignatureMethod=HmacSHA256&SignatureVersion=2&Timestamp=2017-05-11T15%3A19%3A30&Signature=4F65x5A2bLyMWVQj3Aqp%2BB4w%2BivaA7n5Oi2SuYtCJ9o%3D`


# Description of Interfacing

## Overview of Interface

| Categories       | Category Links                     | Overview                                             |
| -------------- | ---------------------------- | ------------------------------------------------ |



This is only a general categorization that does not necessarily mandate all interfaces. Please refer to relevant interface document as per your demand.

## New Rate-Limit Rules

- As of now, new rate-limit rules are being introduced, and will apply to interfaces that are separately marked with a rate-limit value labelled as NEW.

- Based on UID mechanism, the new rate-limit rules require that the combined rate of requests made by all API Keys concurrently under the same UID to a single endpoint shall not exceed the maximum rate-limit on number of visits allowed by this endpoint.

- Users may check out the rate-limit status in Http Header's "X-HB-RateLimit-Requests-Remain" and "X-HB-RateLimit-Requests-Expire" as well as the expiry time of the concerned time window, and adjust rate of requesting accordingly in a dynamic manner.

## Rate-Limit Rules

For interface endpoints other than those already separately marked as NEW -<br>
* Each API Key is limited up to 10 times per second<br>
* In the event API Key is not required, each IP is limited up to 10 times per second<br>

For instance:

* Rate-limit API Key for calling asset and order interfaces to: 10 times per second


## Format of Requesting

All API requests are restful, and are applicable in only two methods: GET and POST

* GET Request: all parameters are in Path Parameter
* POST Request: all parameters are in the format JSON and are sent in the request body

## Format of Responses

All interface responses are in JSON format, where there are minor differences in JSON definitions for v1 and v2.

**Interface response format**: At top tier there are three fields:`code`, `message` and `data`, with response code and error message expressed by the first two fields, and actual body data included in `data`.

Please see below as an example of response format:

```json
{
  "code": 200,
  "message": "",
  "data": // per API response data in nested JSON object
}
```

| Name     | data type | description      |
| -------- | -------- | ------------------ |
| code     | int      | API response code  |
| message  | string   | error message (if any) |
| data     | object   | response body data  |

## Data Type

This document defines data types of JSON as follows:

- `string`: type of string, cited with double quotation marks
- `int`: 32-bit integer that describes status code, size and count
- `long`: 64-bit integer that describes ID and timestamp
- `float`: floating-point number that describes amount and price. High-precision floats are recommended to be used in programming
- `object`: object that includes a sub-object{}
- `array`: array that includes multiple objects

## Best Practice

###Security
- We strongly advise against disclosure of API Key to anyone, including any third-party software or agency. API Key holds authorization to your account. Disclosure of API Key may lead to damages and losses to your information and assets. In case of API Key leak, delete it promptly and create a new one.

###General
**API access**

- It's NOT recommended to access Huobi Brokerage API from mainland China via temporary domain or proxy, which do not guarantee stable connection.
- Japanese AWS cloud server is recommended to be used in accessing.
- The official domain is: api.huobi-brokerage.com.


**New rate-limit rules**

- As of now, new rate-limit rules are being introduced, and will apply to interfaces that are separately marked with a rate-limit value.

- Users may check out the rate-limit status in Http Header's "X-HB-RateLimit-Requests-Remain" and "X-HB-RateLimit-Requests-Expire" as well as the expiry time of the concerned time window, and adjust rate of requesting accordingly in a dynamic manner.

- It is required that the combined rate of requests made by all API Keys concurrently under the same UID to a single endpoint shall not exceed the maximum rate-limit on number of visits allowed by this endpoint.


# FAQs

This section lists other frequently asked questions irrelevant to a certain API, such as questions on network, signature, and general errors etc.

For questions concerning a certain type of API or a certain API, please refer to the error codes and FAQs under relevant API sections.

### Q1: How many API Keys can a user request?

Each user may create up to 20 Api Keys, with each Api Key may be set with specific access authorization.

To understand more about authorization setting:

- Access authorization: the access authorization is for data-enquiring interface, such as Enquire Asset List.

### Q2: Why are there frequent disconnection or timeout?

Please check if:

1. the client server is located in mainland China, which does not guarantee stable connection. Japanese AWS cloud server is recommended.

### Q3: Why does the signature authentication always fail?

Please check for the following potential causes:


1. Signature parameters shall be sorted and ordered as per ASCII, which requires the following original parameters:

`AccessKeyId=e2xxxxxx-99xxxxxx-84xxxxxx-7xxxx`

`order-id=1234567890`

`SignatureMethod=HmacSHA256`

`SignatureVersion=2`

`Timestamp=2017-05-11T15%3A19%3A30`

to be sorted and ordered as:

`AccessKeyId=e2xxxxxx-99xxxxxx-84xxxxxx-7xxxx`

`SignatureMethod=HmacSHA256`

`SignatureVersion=2`

`Timestamp=2017-05-11T15%3A19%3A30`

`order-id=1234567890`

2. Signature strings should be URL-encoded, as such:

- Colon `:` be encoded as `%3A` and space be encoded as `%20`
- Timestamp be formatted as `YYYY-MM-DDThh:mm:ss`, before they are URL-encoded as `2017-05-11T15%3A19%3A30`

3. Signature should be base64 encoded

4. Get-request parameters should be in Signature string

5. Time should be UTC and in the format of YYYY-MM-DDTHH:mm:ss

6. Check for the difference between your timestamp and the standard time (the discrepancy shall be within 1 minute)

7. The Host in signature shall be same as the Host in your API request.

The proxy, if used, may change the Host in request. You can try without proxy;

or, the network library may include the port in the Host, in which case you may try including the port in the Host used in signature, e.g. 「api.huobi-brokerage.com:443"

8. Check for any hidden special characters in Access Key and Secret Key.

At present, [SDK](https://github.com/huobitech) in multiple programming languages are officially supported. You may refer to SDK signature, or signature sample codes in the following three languages:

<a href='https://github.com/huobitech/huobi_Java/blob/master/java_signature_demo.md'>JAVAsignaturesamplecode</a> | <a href='https://github.com/huobitech/huobi_Python/blob/master/example/python_signature_demo.md'>Pythonsignaturesamplecode</a>   | <a href='https://github.com/huobitech/huobi_Cpp/blob/master/examples/cpp_signature_demo.md'>C++signaturesamplecode</a>

### Q7: Why does the interface return the error message Incorrect Access Key?

Check if Access Key in URL request is correctly transmitted, specifically:

1. Access Key not transmitted
2. Access Key not in correct number of digits
3. Access Key deleted
4. Incorrect parsing of AccessKey by server, caused by improper assembly of parameters or failure to encoding special characters in URL request.

### Q8: Why does the interface return error message gateway-internal-error?

Check for the following potential causes:

1. Network or internal server error: please try again later
2. If data was sent in correct format (must be standard JSON)
3. Header of POST request shall be declared as `Content-Type:application/json`

### Q9: Whey does the interface return error message login-required?

Check for the following potential causes:

1. AccessKey parameter not included in URL
2. Signature parameter not included in URL

### Q10: Why does the Rest interface return HTTP 405 error message method-not-allowed?

Such error indicates a nonexistent Rest interface was called. Please check if Rest interface path is correct. Please literally follow the upper-lower case requirement for Path which is case sensitive.

# Contac Us

## Technical Support

If you have any questions or suggestions, please contact us via:

- Help Center on our website, or sending emails to support@huobi-brokerage.com for further support.

For API errors, please refer to and follow the below template in your feedback:

`1. Problem description`
`2. The concerned User ID (UID), Account Id and Order Id(if the latter two are also involved)`
`3. The complete URL request`
`4. The complete request parameters in JSON format (if any)`
`5. The complete response in JSON format`
`6. The time and frequency of the problem (When does the problem occur and if it's recurring)`
`7. the character strings before the signature (if it's signature authentication error)`


See the following as a sample template:

`1. Problem description: signature error`
`2. UID: 123456`
`3. Complete URL request: GET https://api.huobi-brokerage.com/v1/open/apiKeyDemo/forRead?&SignatureVersion=2&SignatureMethod=HmacSHA256&Timestamp=2019-11-06T03%3A25%3A39&AccessKeyId=rfhxxxxx-950000847-boooooo3-432c0&Signature=HhJwApXKpaLPewiYLczwfLkoTPnFPHgyF61iq0iTFF8%3D`
`4. Complete parameter in JSON: N/A`
`5. Complete response in JSON: {"status":"error","err-code":"api-signature-not-valid","err-msg":"Signature not valid: Incorrect Access key [Access key error]","data":null}`
`6. Frequency: recur at each try`
`7. Character strings before signature`
`GET\n`
`api.huobi-brokerage.com\n`
`/v1/open/apiKeyDemo/forRead\n`
`AccessKeyId=rfhxxxxx-950000847-boooooo3-432c0&SignatureMethod=HmacSHA256&SignatureVersion=2&Timestamp=2019-11-06T03%3A26%3A13`

Note: Access Key only verifies your identity and doesn't affect your account security. Keep in mind **NEVER** share your Secret Key to anyone. In case your Secret Key is disclosed, [DELETE] immediately (https://www.hbg.com/zh-cn/apikey/) the corresponding API Key, to prevent from asset losses.

# Users Related

## Y/N a user granted with credit line?
A user may query whether oneself is granted with credit via this interface

### HTTP Request

- GET `/open/otc/api/user/isCreditUser`

API Key authorization: Read<br>

Rate limit: 10times/1s<br>

### Request Parameters

> Response:

```json
{"code":200,"message":"success","data":true,"success":true,"messageArgs":[]}
```
### Response Data

<html>
 <head></head>
 <body>
  <table> 
   <thead class="ant-table-thead"> 
    <tr> 
     <th key="name">Name</th>
     <th key="type">Type</th>
     <th key="required">Required?</th>
     <th key="default">Default</th>
     <th key="desc">Note</th>
     <th key="sub">Other Info</th> 
    </tr> 
   </thead>
   <tbody classname="ant-table-tbody">
    <tr key="0-0">
     <td key="0"><span style="padding-left: 0px"><span style="color: #8c8a8a"></span> code</span></td>
     <td key="1"><span>integer</span></td>
     <td key="2">Not required</td>
     <td key="3"></td>
     <td key="4"><span style="white-space: pre-wrap">Service status code</span></td>
     <td key="5"></td>
    </tr>
    <tr key="0-1">
     <td key="0"><span style="padding-left: 0px"><span style="color: #8c8a8a"></span> message</span></td>
     <td key="1"><span>string</span></td>
     <td key="2">Not required</td>
     <td key="3"></td>
     <td key="4"><span style="white-space: pre-wrap">Error message (in English)</span></td>
     <td key="5"></td>
    </tr>
    <tr key="0-2">
     <td key="0"><span style="padding-left: 0px"><span style="color: #8c8a8a"></span> data</span></td>
     <td key="1"><span>boolean</span></td>
     <td key="2">Not required</td>
     <td key="3"></td>
     <td key="4"><span style="white-space: pre-wrap">Response data - Generic. All formats of response data are supported</span></td>
     <td key="5"></td>
    </tr>
    <tr key="0-3">
     <td key="0"><span style="padding-left: 0px"><span style="color: #8c8a8a"></span> success</span></td>
     <td key="1"><span>boolean</span></td>
     <td key="2">Not required</td>
     <td key="3"></td>
     <td key="4"><span style="white-space: pre-wrap">Successful?</span></td>
     <td key="5"></td>
    </tr>
    <tr key="0-4">
     <td key="0"><span style="padding-left: 0px"><span style="color: #8c8a8a"></span> messageArgs</span></td>
     <td key="1"><span>object []</span></td>
     <td key="2">Not required</td>
     <td key="3">new ArrayList&lt;&gt;()</td>
     <td key="4"><span style="white-space: pre-wrap"></span></td>
     <td key="5"></td>
    </tr> 
   </tbody> 
  </table>
 </body>
</html>

## Y/N on the whitelist?
A user may query whether oneself is whitelisted via this interface

### HTTP Request

- GET `/open/otc/api/user/isWhiteUser`

API Key authorization: Read<br>

Rate limit: 10times/1s<br>

### Request Parameters

> Response:

```json
{"code":200,"message":"success","data":false,"success":true,"messageArgs":[]}
```
### Response Data
<html>
 <head></head>
 <body>
  <table> 
   <thead class="ant-table-thead"> 
    <tr> 
     <th key="name">Name</th>
     <th key="type">Type</th>
     <th key="required">Required?</th>
     <th key="default">Default</th>
     <th key="desc">Description</th>
     <th key="sub">Sublist</th> 
    </tr> 
   </thead>
   <tbody classname="ant-table-tbody">
    <tr key="0-0">
     <td key="0"><span style="padding-left: 0px"><span style="color: #8c8a8a"></span> code</span></td>
     <td key="1"><span>integer</span></td>
     <td key="2">Not required</td>
     <td key="3"></td>
     <td key="4"><span style="white-space: pre-wrap">Service status code</span></td>
     <td key="5"></td>
    </tr>
    <tr key="0-1">
     <td key="0"><span style="padding-left: 0px"><span style="color: #8c8a8a"></span> message</span></td>
     <td key="1"><span>string</span></td>
     <td key="2">Not required</td>
     <td key="3"></td>
     <td key="4"><span style="white-space: pre-wrap">Error message (in English)</span></td>
     <td key="5"></td>
    </tr>
    <tr key="0-2">
     <td key="0"><span style="padding-left: 0px"><span style="color: #8c8a8a"></span> data</span></td>
     <td key="1"><span>boolean</span></td>
     <td key="2">Not required</td>
     <td key="3"></td>
     <td key="4"><span style="white-space: pre-wrap">Response data - Generic. All formats of response data are supported</span></td>
     <td key="5"></td>
    </tr>
    <tr key="0-3">
     <td key="0"><span style="padding-left: 0px"><span style="color: #8c8a8a"></span> success</span></td>
     <td key="1"><span>boolean</span></td>
     <td key="2">Not required</td>
     <td key="3"></td>
     <td key="4"><span style="white-space: pre-wrap">Successful?</span></td>
     <td key="5"></td>
    </tr>
    <tr key="0-4">
     <td key="0"><span style="padding-left: 0px"><span style="color: #8c8a8a"></span> messageArgs</span></td>
     <td key="1"><span>object []</span></td>
     <td key="2">Not required</td>
     <td key="3">new ArrayList&lt;&gt;()</td>
     <td key="4"><span style="white-space: pre-wrap"></span></td>
     <td key="5"></td>
    </tr> 
   </tbody> 
  </table>
 </body>
</html>


# Credit Users Related

## Get Uncleared Trades Records
Users may query records of their uncleared trades via this interface

### HTTP request

- POST `/open/otc/api/clearing/query`

API Key authorization: Read<br>

Rate limit: 10times/1s<br>

### Request Parameters
<html>
 <head></head>
 <body>
  <table> 
   <thead class="ant-table-thead"> 
    <tr> 
     <th key="name">Name</th>
     <th key="type">Type</th>
     <th key="required">Required?</th>
     <th key="default">Default</th>
     <th key="desc">Description</th>
     <th key="sub">Sublist</th> 
    </tr> 
   </thead>
   <tbody classname="ant-table-tbody">
    <tr key="0-0">
     <td key="0"><span style="padding-left: 0px"><span style="color: #8c8a8a"></span> page</span></td>
     <td key="1"><span>object</span></td>
     <td key="2">Required</td>
     <td key="3"></td>
     <td key="4"><span style="white-space: pre-wrap">query pagination</span></td>
     <td key="5"></td>
    </tr>
          <tr key="0-0-2">
     <td key="0"><span style="padding-left: 20px"> size</span></td>
     <td key="1"><span>integer</span></td>
     <td key="2">Required</td>
     <td key="3"></td>
     <td key="4"><span style="white-space: pre-wrap">page size</span></td>
     <td key="5"></td>
    </tr>
    <tr key="0-0-3">
     <td key="0"><span style="padding-left: 20px"> page</span></td>
     <td key="1"><span>integer</span></td>
     <td key="2">Required</td>
     <td key="3"></td>
     <td key="4"><span style="white-space: pre-wrap">current page</span></td>
     <td key="5"></td>
    </tr>
    <tr key="0-1">
     <td key="0"><span style="padding-left: 0px"><span style="color: #8c8a8a"></span> side</span></td>
     <td key="1"><span>string</span></td>
     <td key="2">Not required</td>
     <td key="3"></td>
     <td key="4"><span style="white-space: pre-wrap">trade side</span></td>
     <td key="5"></td>
    </tr>
    <tr key="0-2">
     <td key="0"><span style="padding-left: 0px"><span style="color: #8c8a8a"></span> baseCurrency</span></td>
     <td key="1"><span>string</span></td>
     <td key="2">Not required</td>
     <td key="3"></td>
     <td key="4"><span style="white-space: pre-wrap">base Currency</span></td>
     <td key="5"></td>
    </tr>
    <tr key="0-3">
     <td key="0"><span style="padding-left: 0px"><span style="color: #8c8a8a"></span> quoteCurrency</span></td>
     <td key="1"><span>string</span></td>
     <td key="2">Not required</td>
     <td key="3"></td>
     <td key="4"><span style="white-space: pre-wrap">quote Currency</span></td>
     <td key="5"></td>
    </tr>
    <tr key="0-4">
     <td key="0"><span style="padding-left: 0px"><span style="color: #8c8a8a"></span> timeInForce</span></td>
     <td key="1"><span>integer</span></td>
     <td key="2">Not required</td>
     <td key="3"></td>
     <td key="4"><span style="white-space: pre-wrap"></span></td>
     <td key="5"></td>
    </tr>
    <tr key="0-5">
     <td key="0"><span style="padding-left: 0px"><span style="color: #8c8a8a"></span> startTime</span></td>
     <td key="1"><span>integer</span></td>
     <td key="2">Not required</td>
     <td key="3"></td>
     <td key="4"><span style="white-space: pre-wrap">order time - startTime</span></td>
     <td key="5"></td>
    </tr>
    <tr key="0-6">
     <td key="0"><span style="padding-left: 0px"><span style="color: #8c8a8a"></span> endTime</span></td>
     <td key="1"><span>integer</span></td>
     <td key="2">Not required</td>
     <td key="3"></td>
     <td key="4"><span style="white-space: pre-wrap">order time - endTime</span></td>
     <td key="5"></td>
    </tr>
    <tr key="0-7">
     <td key="0"><span style="padding-left: 0px"><span style="color: #8c8a8a"></span> orderId</span></td>
     <td key="1"><span>string</span></td>
     <td key="2">Not required</td>
     <td key="3"></td>
     <td key="4"><span style="white-space: pre-wrap">Order id</span></td>
     <td key="5"></td>
    </tr>
    <tr key="0-8">
     <td key="0"><span style="padding-left: 0px"><span style="color: #8c8a8a"></span> clearingStatus</span></td>
     <td key="1"><span>integer</span></td>
     <td key="2">Not required</td>
     <td key="3"></td>
     <td key="4"><span style="white-space: pre-wrap">Clearing status (0, uncleared| 1, automatic clearing when filled| 2, partial clearing| 3, clearing completed| 4, clearing failed)</span></td>
     <td key="5"></td>
    </tr>
    <tr key="0-9">
     <td key="0"><span style="padding-left: 0px"><span style="color: #8c8a8a"></span> tradeStatusList</span></td>
     <td key="1"><span>integer []</span></td>
     <td key="2">Not required</td>
     <td key="3"></td>
     <td key="4"><span style="white-space: pre-wrap">Trade Status List</span></td>
     <td key="5"><p key="3"><span style="font-weight: '700'"> </span><span></span></p></td>
    </tr>
    <tr key="0-10">
     <td key="0"><span style="padding-left: 0px"><span style="color: #8c8a8a"></span> clearingStatusList</span></td>
     <td key="1"><span>integer []</span></td>
     <td key="2">Not required</td>
     <td key="3"></td>
     <td key="4"><span style="white-space: pre-wrap">Clearing Status List</span></td>
     <td key="5"><p key="3"><span style="font-weight: '700'"> </span><span></span></p></td>
    </tr>
     <tr key="0-11">
     <td key="0"><span style="padding-left: 0px"><span style="color: #8c8a8a"></span> ascending</span></td>
     <td key="1"><span>string</span></td>
     <td key="2">Not required</td>
     <td key="3"></td>
     <td key="4"><span style="white-space: pre-wrap">ascending(&quot;asc&quot;) or descending(&quot;desc&quot;), default as descending</span></td>
     <td key="5"></td>
    </tr> 
   </tbody> 
  </table>
 </body>
</html>

> Response:

```json
{
    "code":200,
    "message":"success",
    "data":{
        "items":[
            {
                "id":2087,
                "orderId":1458097497309248,
                "side":1,
                "timeInForce":4,
                "baseCurrency":"ETH",
                "quoteCurrency":"HUSD",
                "quantity":"0.100000",
                "cumQuantity":"0.100000",
                "avgPx":"3238.948367",
                "lastPx":"3238.948367",
                "lastQty":"0.100000",
                "lastTurnover":"323.894837",
                "commission":"0 ETH",
                "transactionTime":1641959867582,
                "userId":11433212,
                "status":2,
                "symbolDisplayName":"ETHHUSD",
                "clearingStatus":0,
                "clearingAt":0,
                "clearingSourceId":"",
                "clearedQty":"0.000000",
                "clearedTurnover":"0.000000",
                "unClearedQty":"0.100000",
                "unClearedTurnover":"323.894837",
                "quantityPrecision":6,
                "amountPrecision":6
            },
            {
                "id":2089,
                "orderId":1458097518280768,
                "side":1,
                "timeInForce":4,
                "baseCurrency":"BTC",
                "quoteCurrency":"USDT",
                "quantity":"0.010000",
                "cumQuantity":"0.010000",
                "avgPx":"42645.422360",
                "lastPx":"42645.422360",
                "lastQty":"0.010000",
                "lastTurnover":"426.454223",
                "commission":"0 BTC",
                "transactionTime":1641959878075,
                "userId":11433212,
                "status":2,
                "symbolDisplayName":"BTCUSDT",
                "clearingStatus":0,
                "clearingAt":0,
                "clearingSourceId":"",
                "clearedQty":"0.000000",
                "clearedTurnover":"0.000000",
                "unClearedQty":"0.010000",
                "unClearedTurnover":"426.454223",
                "quantityPrecision":6,
                "amountPrecision":6
            }
        ],
        "total":2,
        "size":10,
        "page":1
    },
    "success":true,
    "messageArgs":[

    ]
}
```
### Response Data


<html>
 <head></head>
 <body>
  <table> 
   <thead class="ant-table-thead"> 
    <tr> 
     <th key="name">Name</th>
     <th key="type">Type</th>
     <th key="required">Required?</th>
     <th key="default">Default</th>
     <th key="desc">Description</th>
     <th key="sub">Sublist</th> 
    </tr> 
   </thead>
   <tbody classname="ant-table-tbody">
    <tr key="0-0">
     <td key="0"><span style="padding-left: 0px"> code</span></td>
     <td key="1"><span>integer</span></td>
     <td key="2">Required</td>
     <td key="3"></td>
     <td key="4"><span style="white-space: pre-wrap"><span style="white-space: pre-wrap">service code</span></span></td>
     <td key="5"></td>
    </tr>
    <tr key="0-1">
     <td key="0"><span style="padding-left: 0px"> message</span></td>
     <td key="1"><span>string</span></td>
     <td key="2">Not required</td>
     <td key="3"></td>
     <td key="4"><span style="white-space: pre-wrap">error message</span></td>
     <td key="5"></td>
    </tr>
    <tr key="0-2">
     <td key="0"><span style="padding-left: 0px"> data</span></td>
     <td key="1"><span>object</span></td>
     <td key="2">Not required</td>
     <td key="3"></td>
     <td key="4"><span style="white-space: pre-wrap">service data</span></td>
     <td key="5"></td>
    </tr>
    <tr key="0-2-0">
     <td key="0"><span style="padding-left: 20px"> items</span></td>
     <td key="1"><span>object []</span></td>
     <td key="2">Not required</td>
     <td key="3"></td>
     <td key="4"><span style="white-space: pre-wrap">page data</span></td>
     <td key="5"><p key="3"><span style="font-weight: '700'"></p></td>
    </tr>
    <tr key="0-2-0-0">
     <td key="0"><span style="padding-left: 40px"> id</span></td>
     <td key="1"><span>integer</span></td>
     <td key="2">Not required</td>
     <td key="3"></td>
     <td key="4"><span style="white-space: pre-wrap">id</span></td>
     <td key="5"></td>
    </tr>
    <tr key="0-2-0-1">
     <td key="0"><span style="padding-left: 40px"> orderId</span></td>
     <td key="1"><span>integer</span></td>
     <td key="2">Not required</td>
     <td key="3"></td>
     <td key="4"><span style="white-space: pre-wrap">order id</span></td>
     <td key="5"></td>
    </tr>
    <tr key="0-2-0-2">
     <td key="0"><span style="padding-left: 40px"> side</span></td>
     <td key="1"><span>integer</span></td>
     <td key="2">Not required</td>
     <td key="3"></td>
     <td key="4"><span style="white-space: pre-wrap">trade side: 1 buy, 2 sell</span></td>
     <td key="5"></td>
    </tr>
    <tr key="0-2-0-3">
     <td key="0"><span style="padding-left: 40px"> timeInForce</span></td>
     <td key="1"><span>integer</span></td>
     <td key="2">Not required</td>
     <td key="3"></td>
     <td key="4"><span style="white-space: pre-wrap">trade type</span></td>
     <td key="5"></td>
    </tr>
    <tr key="0-2-0-4">
     <td key="0"><span style="padding-left: 40px"> baseCurrency</span></td>
     <td key="1"><span>string</span></td>
     <td key="2">Not required</td>
     <td key="3"></td>
     <td key="4"><span style="white-space: pre-wrap">base Currency</span></td>
     <td key="5"></td>
    </tr>
    <tr key="0-2-0-5">
     <td key="0"><span style="padding-left: 40px"> quoteCurrency</span></td>
     <td key="1"><span>string</span></td>
     <td key="2">Not required</td>
     <td key="3"></td>
     <td key="4"><span style="white-space: pre-wrap">quote Currency</span></td>
     <td key="5"></td>
    </tr>
    <tr key="0-2-0-6">
     <td key="0"><span style="padding-left: 40px"> quantity</span></td>
     <td key="1"><span>string</span></td>
     <td key="2">Not required</td>
     <td key="3"></td>
     <td key="4"><span style="white-space: pre-wrap">order quantity</span></td>
     <td key="5"></td>
    </tr>
    <tr key="0-2-0-7">
     <td key="0"><span style="padding-left: 40px"> cumQuantity</span></td>
     <td key="1"><span>string</span></td>
     <td key="2">Not required</td>
     <td key="3"></td>
     <td key="4"><span style="white-space: pre-wrap">cumulated traded order quantity</span></td>
     <td key="5"></td>
    </tr>
    <tr key="0-2-0-8">
     <td key="0"><span style="padding-left: 40px"> avgPx</span></td>
     <td key="1"><span>string</span></td>
     <td key="2">Not required</td>
     <td key="3"></td>
     <td key="4"><span style="white-space: pre-wrap">traded order average price</span></td>
     <td key="5"></td>
    </tr>
    <tr key="0-2-0-9">
     <td key="0"><span style="padding-left: 40px"> lastPx</span></td>
     <td key="1"><span>string</span></td>
     <td key="2">Not required</td>
     <td key="3"></td>
     <td key="4"><span style="white-space: pre-wrap">last price</span></td>
     <td key="5"></td>
    </tr>
    <tr key="0-2-0-10">
     <td key="0"><span style="padding-left: 40px"> lastQty</span></td>
     <td key="1"><span>string</span></td>
     <td key="2">Not required</td>
     <td key="3"></td>
     <td key="4"><span style="white-space: pre-wrap">last quantity</span></td>
     <td key="5"></td>
    </tr>
    <tr key="0-2-0-11">
     <td key="0"><span style="padding-left: 40px"> lastTurnover</span></td>
     <td key="1"><span>string</span></td>
     <td key="2">Not required</td>
     <td key="3"></td>
     <td key="4"><span style="white-space: pre-wrap">last turnover=lastPx*lastQty</span></td>
     <td key="5"></td>
    </tr>
    <tr key="0-2-0-12">
     <td key="0"><span style="padding-left: 40px"> commission</span></td>
     <td key="1"><span>string</span></td>
     <td key="2">Not required</td>
     <td key="3"></td>
     <td key="4"><span style="white-space: pre-wrap">trading fee/commission</span></td>
     <td key="5"></td>
    </tr>
    <tr key="0-2-0-13">
     <td key="0"><span style="padding-left: 40px"> transactionTime</span></td>
     <td key="1"><span>integer</span></td>
     <td key="2">Not required</td>
     <td key="3"></td>
     <td key="4"><span style="white-space: pre-wrap">transaction timestamp</span></td>
     <td key="5"></td>
    </tr>
    <tr key="0-2-0-14">
     <td key="0"><span style="padding-left: 40px"> userId</span></td>
     <td key="1"><span>integer</span></td>
     <td key="2">Not required</td>
     <td key="3"></td>
     <td key="4"><span style="white-space: pre-wrap">user id</span></td>
     <td key="5"></td>
    </tr>
    <tr key="0-2-0-15">
     <td key="0"><span style="padding-left: 40px"> status</span></td>
     <td key="1"><span>integer</span></td>
     <td key="2">Not required</td>
     <td key="3"></td>
     <td key="4"><span style="white-space: pre-wrap">order status</span></td>
     <td key="5"></td>
    </tr>
    <tr key="0-2-0-16">
     <td key="0"><span style="padding-left: 40px"> symbolDisplayName</span></td>
     <td key="1"><span>string</span></td>
     <td key="2">Not required</td>
     <td key="3"></td>
     <td key="4"><span style="white-space: pre-wrap">trade symbol Display Name</span></td>
     <td key="5"></td>
    </tr>
    <tr key="0-2-0-17">
     <td key="0"><span style="padding-left: 40px"> clearingStatus</span></td>
     <td key="1"><span>integer</span></td>
     <td key="2">Not required</td>
     <td key="3"></td>
     <td key="4"><span style="white-space: pre-wrap">clearing Status</span></td>
     <td key="5"></td>
    </tr>
    <tr key="0-2-0-18">
     <td key="0"><span style="padding-left: 40px"> clearingAt</span></td>
     <td key="1"><span>integer</span></td>
     <td key="2">Not required</td>
     <td key="3"></td>
     <td key="4"><span style="white-space: pre-wrap">clearing Time</span></td>
     <td key="5"></td>
    </tr>
    <tr key="0-2-0-19">
     <td key="0"><span style="padding-left: 40px"> clearingSourceId</span></td>
     <td key="1"><span>string</span></td>
     <td key="2">Not required</td>
     <td key="3"></td>
     <td key="4"><span style="white-space: pre-wrap">clearing Source id</span></td>
     <td key="5"></td>
    </tr>
    <tr key="0-2-0-20">
     <td key="0"><span style="padding-left: 40px"> clearedQty</span></td>
     <td key="1"><span>string</span></td>
     <td key="2">Not required</td>
     <td key="3"></td>
     <td key="4"><span style="white-space: pre-wrap">cleared quantity</span></td>
     <td key="5"></td>
    </tr>
    <tr key="0-2-0-21">
     <td key="0"><span style="padding-left: 40px"> clearedTurnover</span></td>
     <td key="1"><span>string</span></td>
     <td key="2">Not required</td>
     <td key="3"></td>
     <td key="4"><span style="white-space: pre-wrap">cleared Turnover</span></td>
     <td key="5"></td>
    </tr>
    <tr key="0-2-0-22">
     <td key="0"><span style="padding-left: 40px"> unClearedQty</span></td>
     <td key="1"><span>string</span></td>
     <td key="2">Not required</td>
     <td key="3"></td>
     <td key="4"><span style="white-space: pre-wrap">unCleared quantity</span></td>
     <td key="5"></td>
    </tr>
    <tr key="0-2-0-23">
     <td key="0"><span style="padding-left: 40px"> unClearedTurnover</span></td>
     <td key="1"><span>string</span></td>
     <td key="2">Not required</td>
     <td key="3"></td>
     <td key="4"><span style="white-space: pre-wrap">unCleared turnover</span></td>
     <td key="5"></td>
    </tr>
    <tr key="0-2-0-24">
     <td key="0"><span style="padding-left: 40px"> quantityPrecision</span></td>
     <td key="1"><span>integer</span></td>
     <td key="2">Not required</td>
     <td key="3"></td>
     <td key="4"><span style="white-space: pre-wrap">quantity precision (base)</span></td>
     <td key="5"></td>
    </tr>
    <tr key="0-2-0-25">
     <td key="0"><span style="padding-left: 40px"> amountPrecision</span></td>
     <td key="1"><span>integer</span></td>
     <td key="2">Not required</td>
     <td key="3"></td>
     <td key="4"><span style="white-space: pre-wrap">amount precision (quote)</span></td>
     <td key="5"></td>
    </tr>
    <tr key="0-2-1">
     <td key="0"><span style="padding-left: 20px"> total</span></td>
     <td key="1"><span>integer</span></td>
     <td key="2">Not required</td>
     <td key="3"></td>
     <td key="4"><span style="white-space: pre-wrap">total</span></td>
     <td key="5"></td>
    </tr>
    <tr key="0-2-2">
     <td key="0"><span style="padding-left: 20px"> size</span></td>
     <td key="1"><span>integer</span></td>
     <td key="2">Not required</td>
     <td key="3"></td>
     <td key="4"><span style="white-space: pre-wrap">page size</span></td>
     <td key="5"></td>
    </tr>
    <tr key="0-2-3">
     <td key="0"><span style="padding-left: 20px"> page</span></td>
     <td key="1"><span>integer</span></td>
     <td key="2">Not required</td>
     <td key="3"></td>
     <td key="4"><span style="white-space: pre-wrap">current page</span></td>
     <td key="5"></td>
    </tr>
    <tr key="0-3">
     <td key="0"><span style="padding-left: 0px"> success</span></td>
     <td key="1"><span>boolean</span></td>
     <td key="2">Required</td>
     <td key="3"></td>
     <td key="4"><span style="white-space: pre-wrap">Successful?</span></td>
     <td key="5"></td>
    </tr>
    <tr key="0-4">
     <td key="0"><span style="padding-left: 0px"> messageArgs</span></td>
     <td key="1"><span>object []</span></td>
     <td key="2">Not required</td>
     <td key="3">new ArrayList&lt;&gt;()</td>
     <td key="4"><span style="white-space: pre-wrap"></span></td>
     <td key="5"></td>
    </tr> 
   </tbody> 
  </table> 
 </body>
</html>

## Credit Users Submit for Clearing

Clearing of multiple orders submitted by a user in one single time is suported. The orders may also be partially cleared, i.e. one order a time. <BR>1) If multiple orders need to be cleared: leave amount blank<br>
2) Or select individual order for partial clearing
### HTTP Request

- POST `/open/otc/api/clearing/manual/clearing`

API Key authorization: Write<br>

Rate limit: 10times/1s<br>

| Name       | Required? | Type   | Description                                                | Default | Sublist
| ---------- | -------- | ------ | ------------------------------------------------------------ | ------ | -------- |
| tradeIds | true     | Intege | Id list of completed trades |        |          |
| amount | false     | string | If one individual order is selected for clearing, an amount that defines return shall be inputted. If multiple orders are selected for clearing, leave the amount box blank. |        |          |




> Response:

```json
{"code":200,"message":"success","data":true,"success":true,"messageArgs":[]}
```

### Response Data

| Name | Required? | Trade type | Description     | Sublist                                                     |
| -------- | -------- | -------- | -------- | ------------------------------------------------------------ |
| code         | true    | integer     | status code | |
| message      | false   | string    | error description (if any)| |
| data         | false   | object    | service data ||

## Get Users' Clearing History

Users' clearing history may be obtained via this interface


### HTTP Request

- POST `/open/otc/api/clearing/history`

API Key authorization: Read<br>

Rate limit: 10times/1s<br>

<table>
  <thead class="ant-table-thead">
    <tr>
      <th key=name>Name</th><th key=type>Type</th><th key=required>Required?</th><th key=default>Default</th><th key=desc>Description</th><th key=sub>Sublist</th>
    </tr>
  </thead><tbody className="ant-table-tbody"><tr key=0-0><td key=0><span style="padding-left: 0px"><span></span> page</span></td><td key=1><span>object</span></td><td key=2>true</td><td key=3></td><td key=4><span style="white-space: pre-wrap">page query parameter</span></td><td key=5></td></tr><tr key=0-0-0><td key=0><span style="padding-left: 20px"><span >size</span></td><td key=1><span>integer</span></td><td key=2>true</td><td key=3></td><td key=4><span style="white-space: pre-wrap">page quantity</span></td><td key=5></td></tr><tr key=0-0-3><td key=0><span style="padding-left: 20px"><span >page</span></td><td key=1><span>integer</span></td><td key=2>true</td><td key=3></td><td key=4><span style="white-space: pre-wrap">current page</span></td><td key=5></td></tr><tr key=0-1><td key=0><span style="padding-left: 0px"><span ></span> startTime</span></td><td key=1><span>integer</span></td><td key=2>false</td><td key=3></td><td key=4><span style="white-space: pre-wrap">order time - query startTime</span></td><td key=5></td></tr><tr key=0-2><td key=0><span style="padding-left: 0px"><span ></span> endTime</span></td><td key=1><span>integer</span></td><td key=2>false</td><td key=3></td><td key=4><span style="white-space: pre-wrap">order time - query endTime</span></td><td key=5></td></tr>
               </tbody>
              </table>




> Response:

```json
{
    "code":200,
    "message":"success",
    "data":{
        "items":[
            {
                "id":212,
                "time":1642589918281,
                "tradeCount":1,
                "tradeSymbols":[
                    "BTCUSDT"
                ],
                "tradeSides":[
                    1
                ]
            },
            {
                "id":211,
                "time":1641960130626,
                "tradeCount":1,
                "tradeSymbols":[
                    "ETHUSDT"
                ],
                "tradeSides":[
                    1
                ]
            }         
        ],
        "total":16,
        "size":2,
        "page":1
    },
    "success":true,
    "messageArgs":[

    ]
}
```


### Response Data

<html>
 <head></head>
 <body>
  <table> 
   <thead class="ant-table-thead"> 
    <tr> 
     <th key="name">Name</th>
     <th key="type">Type</th>
     <th key="required">Required?</th>
     <th key="default">Default</th>
     <th key="desc">Description</th>
     <th key="sub">Sublist</th> 
    </tr> 
   </thead>
   <tbody classname="ant-table-tbody">
    <tr key="0-0">
     <td key="0"><span style="padding-left: 0px"> code</span></td>
     <td key="1"><span>integer</span></td>
     <td key="2">Required</td>
     <td key="3"></td>
     <td key="4"><span style="white-space: pre-wrap">service code</span></td>
     <td key="5"></td>
    </tr>
    <tr key="0-1">
     <td key="0"><span style="padding-left: 0px"> message</span></td>
     <td key="1"><span>string</span></td>
     <td key="2">Not required</td>
     <td key="3"></td>
     <td key="4"><span style="white-space: pre-wrap">message</span></td>
     <td key="5"></td>
    </tr>
    <tr key="0-2">
     <td key="0"><span style="padding-left: 0px"> data</span></td>
     <td key="1"><span>object</span></td>
     <td key="2">Not required</td>
     <td key="3"></td>
     <td key="4"><span style="white-space: pre-wrap">service data</span></td>
     <td key="5"></td>
    </tr>
    <tr key="0-2-0">
     <td key="0"><span style="padding-left: 20px"> items</span></td>
     <td key="1"><span>object []</span></td>
     <td key="2">Not required</td>
     <td key="3"></td>
     <td key="4">page data</td>
     <td key="5"></td>
    </tr>
    <tr key="0-2-0-0">
     <td key="0"><span style="padding-left: 40px"> id</span></td>
     <td key="1"><span>integer</span></td>
     <td key="2">Not required</td>
     <td key="3"></td>
     <td key="4"><span style="white-space: pre-wrap">id</span></td>
     <td key="5"></td>
    </tr>
    <tr key="0-2-0-1">
     <td key="0"><span style="padding-left: 40px"> time</span></td>
     <td key="1"><span>integer</span></td>
     <td key="2">Not required</td>
     <td key="3"></td>
     <td key="4"><span style="white-space: pre-wrap">time</span></td>
     <td key="5"></td>
    </tr>
    <tr key="0-2-0-2">
     <td key="0"><span style="padding-left: 40px"> tradeCount</span></td>
     <td key="1"><span>integer</span></td>
     <td key="2">Not required</td>
     <td key="3"></td>
     <td key="4"><span style="white-space: pre-wrap">trade count</span></td>
     <td key="5"></td>
    </tr>
    <tr key="0-2-0-3">
     <td key="0"><span style="padding-left: 40px"> tradeSymbols</span></td>
     <td key="1"><span>string []</span></td>
     <td key="2">Not required</td>
     <td key="3"></td>
     <td key="4"><span style="white-space: pre-wrap">trade symbols</span></td>
     <td key="5"></td>
    </tr>
    <tr key="0-2-0-4">
     <td key="0"><span style="padding-left: 40px"> tradeSides</span></td>
     <td key="1"><span>integer []</span></td>
     <td key="2">Not required</td>
     <td key="3"></td>
     <td key="4"><span style="white-space: pre-wrap">trade sides</span></td>
     <td key="5"></td>
    </tr>
     <tr key="0-2-1">
     <td key="0"><span style="padding-left: 20px"> total</span></td>
     <td key="1"><span>integer</span></td>
     <td key="2">Not required</td>
     <td key="3"></td>
     <td key="4"><span style="white-space: pre-wrap">total</span></td>
     <td key="5"></td>
    </tr>
    <tr key="0-2-2">
     <td key="0"><span style="padding-left: 20px"> size</span></td>
     <td key="1"><span>integer</span></td>
     <td key="2">Not required</td>
     <td key="3"></td>
     <td key="4"><span style="white-space: pre-wrap">page size</span></td>
     <td key="5"></td>
    </tr>
    <tr key="0-2-3">
     <td key="0"><span style="padding-left: 20px"> page</span></td>
     <td key="1"><span>integer</span></td>
     <td key="2">Not required</td>
     <td key="3"></td>
     <td key="4"><span style="white-space: pre-wrap">current page</span></td>
     <td key="5"></td>
    </tr>
    <tr key="0-3">
     <td key="0"><span style="padding-left: 0px"> success</span></td>
     <td key="1"><span>boolean</span></td>
     <td key="2">Required</td>
     <td key="3"></td>
     <td key="4"><span style="white-space: pre-wrap">Successful?</span></td>
     <td key="5"></td>
    </tr>
    <tr key="0-4">
     <td key="0"><span style="padding-left: 0px"> messageArgs</span></td>
     <td key="1"><span>object []</span></td>
     <td key="2">Not required</td>
     <td key="3">new ArrayList&lt;&gt;()</td>
     <td key="4"><span style="white-space: pre-wrap"></span></td>
     <td key="5"></td>
    </tr> 
   </tbody> 
  </table>
 </body>
</html>


## Get Users' Clearing Record Details

Detailed clearing records of Credit Users may be obtained via this interface

### HTTP Request

- GET `/open/otc/api/clearing/details/{clearingId}`

API Key authorization: Read<br>

Rate limit: 10times/1 sec<br>
### Request Parameters

| Name     | example    | Description  |
| ------------ | ------------ | ------------ |
| clearingId |   |   |

> Response:

```json
{
    "code": 200,
    "message": "success",
    "data": {
        "id": 212,
        "time": 1642589918281,
        "tradeCount": 1,
        "tradeSymbols": [
            "BTCUSDT"
        ],
        "tradeSides": [
            1
        ],
        "payouts": {
            "USDT": 23
        },
        "receivables": {
            "BTC": 0.000539
        },
        "trades": [
            {
                "tradeId": 2089,
                "time": 1641959878075,
                "symbol": "BTCUSDT",
                "baseCurrency": "BTC",
                "quoteCurrency": "USDT",
                "side": 1,
                "avgPx": 42645.422360010000000000,
                "cumQuantity": 0.010000000000000000,
                "cumTurnover": 426.454223600000000000,
                "clearedQty": 0.000539,
                "clearedTurnover": 23
            }
        ]
    },
    "success": true,
    "messageArgs": []
}
```

### Response data

<html>
 <head></head>
 <body>
  <table> 
   <thead class="ant-table-thead"> 
    <tr> 
     <th key="name">Name</th>
     <th key="type">Type</th>
     <th key="required">Required?</th>
     <th key="default">Default</th>
     <th key="desc">Description</th>
     <th key="sub">Sublist</th> 
    </tr> 
   </thead>
   <tbody classname="ant-table-tbody">
    <tr key="0-0">
     <td key="0"><span style="padding-left: 0px"> code</span></td>
     <td key="1"><span>integer</span></td>
     <td key="2">Required</td>
     <td key="3"></td>
     <td key="4"><span style="white-space: pre-wrap">service code</span></td>
     <td key="5"></td>
    </tr>
    <tr key="0-1">
     <td key="0"><span style="padding-left: 0px"> message</span></td>
     <td key="1"><span>string</span></td>
     <td key="2">Not required</td>
     <td key="3"></td>
     <td key="4"><span style="white-space: pre-wrap">message</span></td>
     <td key="5"></td>
    </tr>
    <tr key="0-2">
     <td key="0"><span style="padding-left: 0px"> data</span></td>
     <td key="1"><span>object</span></td>
     <td key="2">Not required</td>
     <td key="3"></td>
     <td key="4"><span style="white-space: pre-wrap">service data</span></td>
     <td key="5"></td>
    </tr>
    <tr key="0-2-0">
     <td key="0"><span style="padding-left: 20px"> id</span></td>
     <td key="1"><span>integer</span></td>
     <td key="2">Not required</td>
     <td key="3"></td>
     <td key="4"><span style="white-space: pre-wrap">clearing id</span></td>
     <td key="5"></td>
    </tr>
    <tr key="0-2-1">
     <td key="0"><span style="padding-left: 20px"> time</span></td>
     <td key="1"><span>integer</span></td>
     <td key="2">Not required</td>
     <td key="3"></td>
     <td key="4"><span style="white-space: pre-wrap">clearing Time</span></td>
     <td key="5"></td>
    </tr>
    <tr key="0-2-2">
     <td key="0"><span style="padding-left: 20px"> tradeCount</span></td>
     <td key="1"><span>integer</span></td>
     <td key="2">Not required</td>
     <td key="3"></td>
     <td key="4"><span style="white-space: pre-wrap">Trade count contained</span></td>
     <td key="5"></td>
    </tr>
    <tr key="0-2-3">
     <td key="0"><span style="padding-left: 20px"> tradeSymbols</span></td>
     <td key="1"><span>string []</span></td>
     <td key="2">Not required</td>
     <td key="3"></td>
     <td key="4"><span style="white-space: pre-wrap">Trade symbols contained</span></td>
     <td key="5"></td>
    <tr key="0-2-4">
     <td key="0"><span style="padding-left: 20px"> tradeSides</span></td>
     <td key="1"><span>integer []</span></td>
     <td key="2">Not required</td>
     <td key="3"></td>
     <td key="4"><span style="white-space: pre-wrap">trade sides contained</span></td>
     <td key="5"></td>
    </tr>
    <tr key="0-2-5">
     <td key="0"><span style="padding-left: 20px"> payouts</span></td>
     <td key="1"><span>Map</span></td>
     <td key="2">Not required</td>
     <td key="3"></td>
     <td key="4"><span style="white-space: pre-wrap">payouts</span></td>
     <td key="5"></td>
    </tr>
    <tr key="0-2-6">
     <td key="0"><span style="padding-left: 20px"> receivables</span></td>
     <td key="1"><span>Map</span></td>
     <td key="2">Not required</td>
     <td key="3"></td>
     <td key="4"><span style="white-space: pre-wrap">receivable</span></td>
     <td key="5"></td>
    </tr>
    <tr key="0-2-7">
     <td key="0"><span style="padding-left: 20px"> trades</span></td>
     <td key="1"><span>object []</span></td>
     <td key="2">Not required</td>
     <td key="3"></td>
     <td key="4"><span style="white-space: pre-wrap">trade records</span></td>
     <td key="5"></td>
    </tr>
    <tr key="0-2-7-0">
     <td key="0"><span style="padding-left: 40px"> tradeId</span></td>
     <td key="1"><span>integer</span></td>
     <td key="2">Not required</td>
     <td key="3"></td>
     <td key="4"><span style="white-space: pre-wrap">trade id</span></td>
     <td key="5"></td>
    </tr>
    <tr key="0-2-7-1">
     <td key="0"><span style="padding-left: 40px"> time</span></td>
     <td key="1"><span>integer</span></td>
     <td key="2">Not required</td>
     <td key="3"></td>
     <td key="4"><span style="white-space: pre-wrap">Time when trade is cleared</span></td>
     <td key="5"></td>
    </tr>
    <tr key="0-2-7-2">
     <td key="0"><span style="padding-left: 40px"> symbol</span></td>
     <td key="1"><span>string</span></td>
     <td key="2">Not required</td>
     <td key="3"></td>
     <td key="4"><span style="white-space: pre-wrap">trade symbols</span></td>
     <td key="5"></td>
    </tr>
    <tr key="0-2-7-3">
     <td key="0"><span style="padding-left: 40px"> baseCurrency</span></td>
     <td key="1"><span>string</span></td>
     <td key="2">Not required</td>
     <td key="3"></td>
     <td key="4"><span style="white-space: pre-wrap">base Currency</span></td>
     <td key="5"></td>
    </tr>
    <tr key="0-2-7-4">
     <td key="0"><span style="padding-left: 40px"> quoteCurrency</span></td>
     <td key="1"><span>string</span></td>
     <td key="2">Not required</td>
     <td key="3"></td>
     <td key="4"><span style="white-space: pre-wrap">quote Currency</span></td>
     <td key="5"></td>
    </tr>
    <tr key="0-2-7-5">
     <td key="0"><span style="padding-left: 40px"> side</span></td>
     <td key="1"><span>integer</span></td>
     <td key="2">Not required</td>
     <td key="3"></td>
     <td key="4"><span style="white-space: pre-wrap">side</span></td>
     <td key="5"></td>
    </tr>
    <tr key="0-2-7-6">
     <td key="0"><span style="padding-left: 40px"> avgPx</span></td>
     <td key="1"><span>BigDecimal</span></td>
     <td key="2">Not required</td>
     <td key="3"></td>
     <td key="4"><span style="white-space: pre-wrap">average price</span></td>
     <td key="5"></td>
    </tr>
    <tr key="0-2-7-7">
     <td key="0"><span style="padding-left: 40px"> cumQuantity</span></td>
     <td key="1"><span>BigDecimal</span></td>
     <td key="2">Not required</td>
     <td key="3"></td>
     <td key="4"><span style="white-space: pre-wrap">cumulated quantity</span></td>
     <td key="5"></td>
    </tr>
    <tr key="0-2-7-8">
     <td key="0"><span style="padding-left: 40px"> cumTurnover</span></td>
     <td key="1"><span>BigDecimal</span></td>
     <td key="2">Not required</td>
     <td key="3"></td>
     <td key="4"><span style="white-space: pre-wrap">cumulated turnover</span></td>
     <td key="5"></td>
    </tr>
    <tr key="0-2-7-9">
     <td key="0"><span style="padding-left: 40px"> clearedQty</span></td>
     <td key="1"><span>BigDecimal</span></td>
     <td key="2">Not required</td>
     <td key="3"></td>
     <td key="4"><span style="white-space: pre-wrap">cleared quantity</span></td>
     <td key="5"></td>
    </tr>
    <tr key="0-2-7-10">
     <td key="0"><span style="padding-left: 40px"> clearedTurnover</span></td>
     <td key="1"><span>BigDecimal</span></td>
     <td key="2">Not required</td>
     <td key="3"></td>
     <td key="4"><span style="white-space: pre-wrap">cleared turnover</span></td>
     <td key="5"></td>
    </tr>
    <tr key="0-3">
     <td key="0"><span style="padding-left: 0px"> success</span></td>
     <td key="1"><span>boolean</span></td>
     <td key="2">Required</td>
     <td key="3"></td>
     <td key="4"><span style="white-space: pre-wrap">Successful?</span></td>
     <td key="5"></td>
    </tr>
    <tr key="0-4">
     <td key="0"><span style="padding-left: 0px"> messageArgs</span></td>
     <td key="1"><span>object []</span></td>
     <td key="2">Not required</td>
     <td key="3"></td>
     <td key="4"><span style="white-space: pre-wrap"></span></td>
     <td key="5"></td>
    </tr> 
   </tbody> 
  </table> 
 </body>
</html>

## Get User Credit Information
Users may query their accounts' credit summary via this interface

### HTTP Request

- GET `/open/otc/api/clearing/query-account-summary`

API Key authorization: Read<br>

Rate limit: 10times/1s<br>
### Request Parameters

> Response:

```json
{
    "code":200,
    "message":"success",
    "data":{
        "totalCredit":"20000000.00",
        "spentCredit":"1051.09",
        "availableCredit":"19998948.90",
        "payouts":[
            {
                "id":"USDT",
                "currency":"USDT",
                "amount":403.4542236,
                "total":"403.45"
            },
            {
                "id":"HUSD",
                "currency":"HUSD",
                "amount":647.642482,
                "total":"647.64"
            }
        ]
    },
    "success":true,
    "messageArgs":[

    ]
}
```
### Response Data

<html>
 <head></head>
 <body>
  <table> 
   <thead class="ant-table-thead"> 
    <tr> 
     <th key="name">Name</th>
     <th key="type">Type</th>
     <th key="required">Required?</th>
     <th key="default">Default</th>
     <th key="desc">Description</th>
     <th key="sub">Sublist</th> 
    </tr> 
   </thead>
   <tbody classname="ant-table-tbody">
    <tr key="0-0">
     <td key="0"><span style="padding-left: 0px"> code</span></td>
     <td key="1"><span>integer</span></td>
     <td key="2">Required</td>
     <td key="3"></td>
     <td key="4"><span style="white-space: pre-wrap"</span> service code </td>
     <td key="5"></td>
    </tr>
    <tr key="0-1">
     <td key="0"><span style="padding-left: 0px"> message</span></td>
     <td key="1"><span>string</span></td>
     <td key="2">Not required</td>
     <td key="3"></td>
     <td key="4"><span style="white-space: pre-wrap">message</span></td>
     <td key="5"></td>
    </tr>
    <tr key="0-2">
     <td key="0"><span style="padding-left: 0px"> data</span></td>
     <td key="1"><span>object</span></td>
     <td key="2">Not required</td>
     <td key="3"></td>
     <td key="4"><span style="white-space: pre-wrap">service data</span></td>
     <td key="5"></td>
    </tr>
    <tr key="0-2-0">
     <td key="0"><span style="padding-left: 20px"> totalCredit</span></td>
     <td key="1"><span>string</span></td>
     <td key="2">Not required</td>
     <td key="3"></td>
     <td key="4"><span style="white-space: pre-wrap">total Credit</span></td>
     <td key="5"></td>
    </tr>
    <tr key="0-2-1">
     <td key="0"><span style="padding-left: 20px"> spentCredit</span></td>
     <td key="1"><span>string</span></td>
     <td key="2">Not required</td>
     <td key="3"></td>
     <td key="4"><span style="white-space: pre-wrap">spent Credit</span></td>
     <td key="5"></td>
    </tr>
    <tr key="0-2-2">
     <td key="0"><span style="padding-left: 20px"> availableCredit</span></td>
     <td key="1"><span>string</span></td>
     <td key="2">Not required</td>
     <td key="3"></td>
     <td key="4"><span style="white-space: pre-wrap">available Credit</span></td>
     <td key="5"></td>
    </tr>
    <tr key="0-2-3">
     <td key="0"><span style="padding-left: 20px"> payouts</span></td>
     <td key="1"><span>object []</span></td>
     <td key="2">Not required</td>
     <td key="3"></td>
     <td key="4"><span style="white-space: pre-wrap">payouts</span></td>
     <td key="5"></td>
    </tr>
    <tr key="0-2-3-0">
     <td key="0"><span style="padding-left: 40px"> id</span></td>
     <td key="1"><span>string</span></td>
     <td key="2">Not required</td>
     <td key="3"></td>
     <td key="4"><span style="white-space: pre-wrap">id</span></td>
     <td key="5"></td>
    </tr>
    <tr key="0-2-3-1">
     <td key="0"><span style="padding-left: 40px"> currency</span></td>
     <td key="1"><span>string</span></td>
     <td key="2">Not required</td>
     <td key="3"></td>
     <td key="4"><span style="white-space: pre-wrap">currency</span></td>
     <td key="5"></td>
    </tr>
    <tr key="0-2-3-2">
     <td key="0"><span style="padding-left: 40px"> amount</span></td>
     <td key="1"><span>BigDecimal</span></td>
     <td key="2">Not required</td>
     <td key="3"></td>
     <td key="4"><span style="white-space: pre-wrap">payout amount</span></td>
     <td key="5"></td>
    </tr>
    <tr key="0-2-3-3">
     <td key="0"><span style="padding-left: 40px"> total</span></td>
     <td key="1"><span>string</span></td>
     <td key="2">Not required</td>
     <td key="3"></td>
     <td key="4"><span style="white-space: pre-wrap">total in USD</span></td>
     <td key="5"></td>
    </tr>
    <tr key="0-3">
     <td key="0"><span style="padding-left: 0px"> success</span></td>
     <td key="1"><span>boolean</span></td>
     <td key="2">Required</td>
     <td key="3"></td>
     <td key="4"><span style="white-space: pre-wrap">Successful?</span></td>
     <td key="5"></td>
    </tr>
    <tr key="0-4">
     <td key="0"><span style="padding-left: 0px"> messageArgs</span></td>
     <td key="1"><span>object []</span></td>
     <td key="2">Not required</td>
     <td key="3">new ArrayList&lt;&gt;()</td>
     <td key="4"><span style="white-space: pre-wrap"></span></td>
     <td key="5"></td>
    </tr> 
   </tbody> 
  </table> 
 </body>
</html> 

# User Account Related

## Get Users Assets Information
Users may query their accounts' asset information via this interface

### HTTP Request

- GET `/open/otc/api/user/accountSummary`

API Key authorization: Read<br>

Rate limit: 10times/1s<br>
### Request Parameters

> Response:

```json
{
  "code":200,
  "message":"success",
  "data":{
    "financeAccounts":[
      {
        "currencyId":"usd",
        "currencyDisplayName":"USD",
        "currencyFullName":"USD",
        "sortWeight":8,
        "balance":"6929.280000000000000000",
        "frozenAmount":"1893.750000000000000000",
        "creditedAmount":"0",
        "receivableAmount":"0",
        "virtualFrozenAmount":null,
        "withdrawAmount":null,
        "balanceToPlaceOrder":null,
        "stable":"false",
        "inCurrencyBlackList":false,
        "spotBalance":null
      },
      {
        "currencyId":"btc",
        "currencyDisplayName":"BTC",
        "currencyFullName":"BTC",
        "sortWeight":1,
        "balance":"0.020000000000000000",
        "frozenAmount":"0.000000000000000000",
        "creditedAmount":"0",
        "receivableAmount":"0.000000000000000000",
        "virtualFrozenAmount":null,
        "withdrawAmount":null,
        "balanceToPlaceOrder":null,
        "stable":"false",
        "inCurrencyBlackList":false,
        "spotBalance":null
      },
      {
        "currencyId":"usdt",
        "currencyDisplayName":"USDT",
        "currencyFullName":"USDT",
        "sortWeight":1,
        "balance":"2941.033920000000000000",
        "frozenAmount":"4100.000000000000000000",
        "creditedAmount":"0",
        "receivableAmount":"0.000000000000000000",
        "virtualFrozenAmount":null,
        "withdrawAmount":null,
        "balanceToPlaceOrder":null,
        "stable":"false",
        "inCurrencyBlackList":false,
        "spotBalance":null
      }
    ],
    "totalDigitalCurrency":"BTC",
    "totalConvertedDigitalCurrencyBalance":"0.39445219",
    "sumLegalCurrency":"USD",
    "sumConvertedLegalCurrencyBalance":"16711.38512000",
    "sumLegalCurrencyBalance":"8823.03000000",
    "totalLegalCurrencyBalance":"0.20825703",
    "sumDigitalCurrencyBalance":"7888.35512000",
    "totalDigitalCurrencyBalance":"0.18619516",
    "defaultCreditCategory":false,
    "unstableCreditLimit":null,
    "unstableCreditUsed":null,
    "unstableCreditUsedWithoutLocked":null,
    "unstableCreditAvailable":null,
    "unstableCreditCurrencyDisplay":null
  },
  "success":true,
  "messageArgs":[

  ]
}
```
### Response Data

<html>
 <head></head>
 <body>
  <table> 
   <thead class="ant-table-thead"> 
    <tr> 
     <th key="name">Name</th>
     <th key="type">Type</th>
     <th key="required">Required?</th>
     <th key="default">Default</th>
     <th key="desc">Description</th>
     <th key="sub">Sublist</th> 
    </tr> 
   </thead>
   <tbody classname="ant-table-tbody">
    <tr key="0-0">
     <td key="0"><span style="padding-left: 0px"><span style="color: #8c8a8a"></span> code</span></td>
     <td key="1"><span>integer</span></td>
     <td key="2">Required</td>
     <td key="3"></td>
     <td key="4"><span style="white-space: pre-wrap">service status code</span></td>
     <td key="5"></td>
    </tr>
    <tr key="0-1">
     <td key="0"><span style="padding-left: 0px"><span style="color: #8c8a8a"></span> message</span></td>
     <td key="1"><span>string</span></td>
     <td key="2">Not required</td>
     <td key="3"></td>
     <td key="4"><span style="white-space: pre-wrap">error message (in English)</span></td>
     <td key="5"></td>
    </tr>
    <tr key="0-2">
     <td key="0"><span style="padding-left: 0px"><span style="color: #8c8a8a"></span> data</span></td>
     <td key="1"><span>object</span></td>
     <td key="2">Not required</td>
     <td key="3"></td>
     <td key="4"><span style="white-space: pre-wrap">service data</span></td>
     <td key="5"></td>
    </tr>
    <tr key="0-2-0">
     <td key="0"><span style="padding-left: 20px"> financeAccounts</span></td>
     <td key="1"><span>object []</span></td>
     <td key="2">Not required</td>
     <td key="3"></td>
     <td key="4"><span style="white-space: pre-wrap">finance Accounts list</span></td>
     <td key="5"></td>
    </tr>
    <tr key="0-2-0-0">
     <td key="0"><span style="padding-left: 40px"> currencyId</span></td>
     <td key="1"><span>string</span></td>
     <td key="2">Not required</td>
     <td key="3"></td>
     <td key="4"><span style="white-space: pre-wrap">currency ID</span></td>
     <td key="5"></td>
    </tr>
    <tr key="0-2-0-1">
     <td key="0"><span style="padding-left: 40px"> currencyDisplayName</span></td>
     <td key="1"><span>string</span></td>
     <td key="2">Not required</td>
     <td key="3"></td>
     <td key="4"><span style="white-space: pre-wrap">currency Display Name</span></td>
     <td key="5"></td>
    </tr>
    <tr key="0-2-0-2">
     <td key="0"><span style="padding-left: 40px"> currencyFullName</span></td>
     <td key="1"><span>string</span></td>
     <td key="2">Not required</td>
     <td key="3"></td>
     <td key="4"><span style="white-space: pre-wrap">currency Full Name</span></td>
     <td key="5"></td>
    </tr>
    <tr key="0-2-0-3">
     <td key="0"><span style="padding-left: 40px"> sortWeight</span></td>
     <td key="1"><span>integer</span></td>
     <td key="2">Not required</td>
     <td key="3"></td>
     <td key="4"><span style="white-space: pre-wrap">sorting weight</span></td>
     <td key="5"></td>
    </tr>
    <tr key="0-2-0-4">
     <td key="0"><span style="padding-left: 40px"> balance</span></td>
     <td key="1"><span>string</span></td>
     <td key="2">Not required</td>
     <td key="3"></td>
     <td key="4"><span style="white-space: pre-wrap">balance</span></td>
     <td key="5"></td>
    </tr>
    <tr key="0-2-0-5">
     <td key="0"><span style="padding-left: 40px"> frozenAmount</span></td>
     <td key="1"><span>string</span></td>
     <td key="2">Not required</td>
     <td key="3"></td>
     <td key="4"><span style="white-space: pre-wrap">frozen Amount</span></td>
     <td key="5"></td>
    </tr>
    <tr key="0-2-0-6">
     <td key="0"><span style="padding-left: 40px"> creditedAmount</span></td>
     <td key="1"><span>string</span></td>
     <td key="2">Not required</td>
     <td key="3"></td>
     <td key="4"><span style="white-space: pre-wrap">used credit Amount</span></td>
     <td key="5"></td>
    </tr>
    <tr key="0-2-0-7">
     <td key="0"><span style="padding-left: 40px"> receivableAmount</span></td>
     <td key="1"><span>string</span></td>
     <td key="2">Not required</td>
     <td key="3"></td>
     <td key="4"><span style="white-space: pre-wrap">receivable Amount</span></td>
     <td key="5"></td>
    </tr>
    <tr key="0-2-0-8">
     <td key="0"><span style="padding-left: 40px"> virtualFrozenAmount</span></td>
     <td key="1"><span>string</span></td>
     <td key="2">Not required</td>
     <td key="3"></td>
     <td key="4"><span style="white-space: pre-wrap">credit frozen</span></td>
     <td key="5"></td>
    </tr>
    <tr key="0-2-0-9">
     <td key="0"><span style="padding-left: 40px"> withdrawAmount</span></td>
     <td key="1"><span>string</span></td>
     <td key="2">Not required</td>
     <td key="3"></td>
     <td key="4"><span style="white-space: pre-wrap">transferable balance</span></td>
     <td key="5"></td>
    </tr>
    <tr key="0-2-0-10">
     <td key="0"><span style="padding-left: 40px"> balanceToPlaceOrder</span></td>
     <td key="1"><span>string</span></td>
     <td key="2">Not required</td>
     <td key="3"></td>
     <td key="4"><span style="white-space: pre-wrap">balance to place order = balance + receivable</span></td>
     <td key="5"></td>
    </tr>
    <tr key="0-2-0-11">
     <td key="0"><span style="padding-left: 40px"> stable</span></td>
     <td key="1"><span>string</span></td>
     <td key="2">Not required</td>
     <td key="3"></td>
     <td key="4"><span style="white-space: pre-wrap">stablecoin? true or false</span></td>
     <td key="5"></td>
    </tr>
    <tr key="0-2-0-12">
     <td key="0"><span style="padding-left: 40px"> inCurrencyBlackList</span></td>
     <td key="1"><span>boolean</span></td>
     <td key="2">Not required</td>
     <td key="3"></td>
     <td key="4"><span style="white-space: pre-wrap">is User Citizenship in Currency Black List?</span></td>
     <td key="5"></td>
    </tr>
    <tr key="0-2-0-13">
     <td key="0"><span style="padding-left: 40px"> spotBalance</span></td>
     <td key="1"><span>string</span></td>
     <td key="2">Not required</td>
     <td key="3"></td>
     <td key="4"><span style="white-space: pre-wrap">spot Account Balance</span></td>
     <td key="5"></td>
    </tr>
    <tr key="0-2-1">
     <td key="0"><span style="padding-left: 20px"> totalDigitalCurrency</span></td>
     <td key="1"><span>string</span></td>
     <td key="2">Not required</td>
     <td key="3"></td>
     <td key="4"><span style="white-space: pre-wrap">total Digital Currency</span></td>
     <td key="5"></td>
    </tr>
    <tr key="0-2-2">
     <td key="0"><span style="padding-left: 20px"> totalConvertedDigitalCurrencyBalance</span></td>
     <td key="1"><span>string</span></td>
     <td key="2">Not required</td>
     <td key="3"></td>
     <td key="4"><span style="white-space: pre-wrap">total Converted Digital Currency Balance (digital to BTC)</span></td>
     <td key="5"></td>
    </tr>
    <tr key="0-2-3">
     <td key="0"><span style="padding-left: 20px"> sumLegalCurrency</span></td>
     <td key="1"><span>string</span></td>
     <td key="2">Not required</td>
     <td key="3"></td>
     <td key="4"><span style="white-space: pre-wrap">sum Legal Currency</span></td>
     <td key="5"></td>
    </tr>
    <tr key="0-2-4">
     <td key="0"><span style="padding-left: 20px"> sumConvertedLegalCurrencyBalance</span></td>
     <td key="1"><span>string</span></td>
     <td key="2">Not required</td>
     <td key="3"></td>
     <td key="4"><span style="white-space: pre-wrap">sum Converted Legal Currency Balance</span></td>
     <td key="5"></td>
    </tr>
    <tr key="0-2-5">
     <td key="0"><span style="padding-left: 20px"> sumLegalCurrencyBalance</span></td>
     <td key="1"><span>string</span></td>
     <td key="2">Not required</td>
     <td key="3"></td>
     <td key="4"><span style="white-space: pre-wrap">sum Legal Currency Balance</span></td>
     <td key="5"></td>
    </tr>
    <tr key="0-2-6">
     <td key="0"><span style="padding-left: 20px"> totalLegalCurrencyBalance</span></td>
     <td key="1"><span>string</span></td>
     <td key="2">Not required</td>
     <td key="3"></td>
     <td key="4"><span style="white-space: pre-wrap">total Legal Currency Balance (legal to BTC)</span></td>
     <td key="5"></td>
    </tr>
    <tr key="0-2-7">
     <td key="0"><span style="padding-left: 20px"> sumDigitalCurrencyBalance</span></td>
     <td key="1"><span>string</span></td>
     <td key="2">Not required</td>
     <td key="3"></td>
     <td key="4"><span style="white-space: pre-wrap">sum Digital Currency Balance</span></td>
     <td key="5"></td>
    </tr>
    <tr key="0-2-8">
     <td key="0"><span style="padding-left: 20px"> totalDigitalCurrencyBalance</span></td>
     <td key="1"><span>string</span></td>
     <td key="2">Not required</td>
     <td key="3"></td>
     <td key="4"><span style="white-space: pre-wrap">total Digital Currency Balance (digital to BTC)</span></td>
     <td key="5"></td>
    </tr>
    <tr key="0-2-9">
     <td key="0"><span style="padding-left: 20px"> defaultCreditCategory</span></td>
     <td key="1"><span>boolean</span></td>
     <td key="2">Not required</td>
     <td key="3"></td>
     <td key="4"><span style="white-space: pre-wrap">default Credit Category</span></td>
     <td key="5"></td>
    </tr>
    <tr key="0-2-10">
     <td key="0"><span style="padding-left: 20px"> unstableCreditLimit</span></td>
     <td key="1"><span>string</span></td>
     <td key="2">Not required</td>
     <td key="3"></td>
     <td key="4"><span style="white-space: pre-wrap">non-stablecoin Credit Limit</span></td>
     <td key="5"></td>
    </tr>
    <tr key="0-2-11">
     <td key="0"><span style="padding-left: 20px"> unstableCreditUsed</span></td>
     <td key="1"><span>string</span></td>
     <td key="2">Not required</td>
     <td key="3"></td>
     <td key="4"><span style="white-space: pre-wrap">non-stablecoin Credit Used</span></td>
     <td key="5"></td>
    </tr>
    <tr key="0-2-12">
     <td key="0"><span style="padding-left: 20px"> unstableCreditUsedWithoutLocked</span></td>
     <td key="1"><span>string</span></td>
     <td key="2">Not required</td>
     <td key="3"></td>
     <td key="4"><span style="white-space: pre-wrap">non-stablecoin Credit Used Without Locked</span></td>
     <td key="5"></td>
    </tr>
    <tr key="0-2-13">
     <td key="0"><span style="padding-left: 20px"> unstableCreditAvailable</span></td>
     <td key="1"><span>string</span></td>
     <td key="2">Not required</td>
     <td key="3"></td>
     <td key="4"><span style="white-space: pre-wrap">non-stablecoin Credit Available</span></td>
     <td key="5"></td>
    </tr>
    <tr key="0-2-14">
     <td key="0"><span style="padding-left: 20px"> unstableCreditCurrencyDisplay</span></td>
     <td key="1"><span>string</span></td>
     <td key="2">Not required</td>
     <td key="3"></td>
     <td key="4"><span style="white-space: pre-wrap">non-stablecoin Credit Currency Display</span></td>
     <td key="5"></td>
    </tr>
    <tr key="0-3">
     <td key="0"><span style="padding-left: 0px"><span style="color: #8c8a8a"></span> success</span></td>
     <td key="1"><span>boolean</span></td>
     <td key="2">Required</td>
     <td key="3"></td>
     <td key="4"><span style="white-space: pre-wrap">Successful?</span></td>
     <td key="5"></td>
    </tr>
    <tr key="0-4">
     <td key="0"><span style="padding-left: 0px"><span style="color: #8c8a8a"></span> messageArgs</span></td>
     <td key="1"><span>object []</span></td>
     <td key="2">Not required</td>
     <td key="3"></td>
     <td key="4"><span style="white-space: pre-wrap"></span></td>
     <td key="5"></td>
    </tr> 
   </tbody> 
  </table>
 </body>
</html>

# Currency and Symbols Related

## Get All Listed Currencies
Users may query all listed currencies via this interface

### HTTP Request

- GET `/open/otc/api/currency/queryCurrency`

API Key authorization: Read<br>

Rate limit: 10times/1s<br>
### Request Parameters

> Response:

```json
{
  "code":200,
  "message":"success",
  "data":[
    {
      "currencyId":"eth",
      "fullName":"ETH_2",
      "amountPrecision":4,
      "type":null,
      "currencyType":0
    },
    {
      "currencyId":"gbp",
      "fullName":"GBP",
      "amountPrecision":2,
      "type":null,
      "currencyType":1
    },
    {
      "currencyId":"btc",
      "fullName":"BTC",
      "amountPrecision":8,
      "type":null,
      "currencyType":0
    },
    {
      "currencyId":"usdt",
      "fullName":"USDT",
      "amountPrecision":8,
      "type":null,
      "currencyType":0
    }
  ],
  "success":true,
  "messageArgs":[

  ]
}
```
### Response Data
<html>
 <head></head>
 <body>
  <table> 
   <thead class="ant-table-thead"> 
    <tr> 
     <th key="name">Name</th>
     <th key="type">Type</th>
     <th key="required">Required?</th>
     <th key="default">Default</th>
     <th key="desc">Description</th>
     <th key="sub">Sublist</th> 
    </tr> 
   </thead>
   <tbody classname="ant-table-tbody">
    <tr key="0-0">
     <td key="0"><span style="padding-left: 0px"><span style="color: #8c8a8a"></span> code</span></td>
     <td key="1"><span>integer</span></td>
     <td key="2">Required</td>
     <td key="3"></td>
     <td key="4"><span style="white-space: pre-wrap">service status code</span></td>
     <td key="5"></td>
    </tr>
    <tr key="0-1">
     <td key="0"><span style="padding-left: 0px"><span style="color: #8c8a8a"></span> message</span></td>
     <td key="1"><span>string</span></td>
     <td key="2">Not required</td>
     <td key="3"></td>
     <td key="4"><span style="white-space: pre-wrap">error message</span></td>
     <td key="5"></td>
    </tr>
    <tr key="0-2">
     <td key="0"><span style="padding-left: 0px"><span style="color: #8c8a8a"></span> data</span></td>
     <td key="1"><span>object []</span></td>
     <td key="2">Not required</td>
     <td key="3"></td>
     <td key="4"><span style="white-space: pre-wrap">service data</span></td>
     <td key="5"></td>
    </tr>
    <tr key="0-2-0">
     <td key="0"><span style="padding-left: 20px"> currencyId</span></td>
     <td key="1"><span>string</span></td>
     <td key="2">Not required</td>
     <td key="3"></td>
     <td key="4"><span style="white-space: pre-wrap">Currency ID: lower-case btc</span></td>
     <td key="5"></td>
    </tr>
    <tr key="0-2-1">
     <td key="0"><span style="padding-left: 20px">fullName</span></td>
     <td key="1"><span>string</span></td>
     <td key="2">Not required</td>
     <td key="3"></td>
     <td key="4"><span style="white-space: pre-wrap">currency full name: Bitcoin</span></td>
     <td key="5"></td>
    </tr>
    <tr key="0-2-2">
     <td key="0"><span style="padding-left: 20px"> amountPrecision</span></td>
     <td key="1"><span>integer</span></td>
     <td key="2">Not required</td>
     <td key="3"></td>
     <td key="4"><span style="white-space: pre-wrap">amount Precision display</span></td>
     <td key="5"></td>
    </tr>
    <tr key="0-3">
     <td key="0"><span style="padding-left: 0px"><span style="color: #8c8a8a"></span> success</span></td>
     <td key="1"><span>boolean</span></td>
     <td key="2">Required</td>
     <td key="3"></td>
     <td key="4"><span style="white-space: pre-wrap">Successful?</span></td>
     <td key="5"></td>
    </tr>
    <tr key="0-4">
     <td key="0"><span style="padding-left: 0px"><span style="color: #8c8a8a"></span> messageArgs</span></td>
     <td key="1"><span>object []</span></td>
     <td key="2">Not required</td>
     <td key="3">new ArrayList&lt;&gt;()</td>
     <td key="4"><span style="white-space: pre-wrap"></span></td>
     <td key="5"></td>
    </tr> 
   </tbody> 
  </table>
 </body>
</html>

## Get All Listed Symbols
Users may query all listed trading symbols via this interface

### HTTP Request

- GET `/open/otc/api/symbol`

API Key authorization: Read<br>

Rate limit: 10times/1s<br>
### Request Parameters

> Response:

```json
{
  "code":200,
  "message":"success",
  "data":[
    {
      "symbol":"btcusdt",
      "baseCurrency":"BTC",
      "quoteCurrency":"USDT",
      "pricePrecision":6,
      "quantityPrecision":6,
      "amountPrecision":6,
      "fokEligible":1,
      "iocEligible":0,
      "gtcEligible":0
    },
    {
      "symbol":"ethusd",
      "baseCurrency":"ETH",
      "quoteCurrency":"USD",
      "pricePrecision":8,
      "quantityPrecision":8,
      "amountPrecision":8,
      "fokEligible":1,
      "iocEligible":0,
      "gtcEligible":0
    }
  ],
  "success":true,
  "messageArgs":[

  ]
}
```
### Response Data
<html>
 <head></head>
 <body>
  <table> 
   <thead class="ant-table-thead"> 
    <tr> 
     <th key="name">Name</th>
     <th key="type">Type</th>
     <th key="required">Required?</th>
     <th key="default">Default</th>
     <th key="desc">Description</th>
     <th key="sub">Sublist</th> 
    </tr> 
   </thead>
   <tbody classname="ant-table-tbody">
    <tr key="0-0">
     <td key="0"><span style="padding-left: 0px"><span style="color: #8c8a8a"></span> code</span></td>
     <td key="1"><span>integer</span></td>
     <td key="2">Not required</td>
     <td key="3"></td>
     <td key="4"><span style="white-space: pre-wrap">service status code</span></td>
     <td key="5"></td>
    </tr>
    <tr key="0-1">
     <td key="0"><span style="padding-left: 0px"><span style="color: #8c8a8a"></span> message</span></td>
     <td key="1"><span>string</span></td>
     <td key="2">Not required</td>
     <td key="3"></td>
     <td key="4"><span style="white-space: pre-wrap">error message (in English)</span></td>
     <td key="5"></td>
    </tr>
    <tr key="0-2">
     <td key="0"><span style="padding-left: 0px"><span style="color: #8c8a8a"></span> data</span></td>
     <td key="1"><span>object []</span></td>
     <td key="2">Not required</td>
     <td key="3"></td>
     <td key="4"><span style="white-space: pre-wrap">service data</span></td>
     <td key="5"></td>
    </tr>
    <tr key="0-2-0">
     <td key="0"><span style="padding-left: 20px"> symbol</span></td>
     <td key="1"><span>string</span></td>
     <td key="2">Not required</td>
     <td key="3"></td>
     <td key="4"><span style="white-space: pre-wrap">trading symbols id, e.g. btcusdt</span></td>
     <td key="5"></td>
    </tr>
    <tr key="0-2-1">
     <td key="0"><span style="padding-left: 20px"> baseCurrency</span></td>
     <td key="1"><span>string</span></td>
     <td key="2">Not required</td>
     <td key="3"></td>
     <td key="4"><span style="white-space: pre-wrap">base Currency, e.g. BTC</span></td>
     <td key="5"></td>
    </tr>
    <tr key="0-2-2">
     <td key="0"><span style="padding-left: 20px"> quoteCurrency</span></td>
     <td key="1"><span>string</span></td>
     <td key="2">Not required</td>
     <td key="3"></td>
     <td key="4"><span style="white-space: pre-wrap">quote Currency, e.g. USDT</span></td>
     <td key="5"></td>
    </tr>
    <tr key="0-2-3">
     <td key="0"><span style="padding-left: 20px"> pricePrecision</span></td>
     <td key="1"><span>integer</span></td>
     <td key="2">Not required</td>
     <td key="3"></td>
     <td key="4"><span style="white-space: pre-wrap">symbols price Precision</span></td>
     <td key="5"></td>
    </tr>
    <tr key="0-2-4">
     <td key="0"><span style="padding-left: 20px"> quantityPrecision</span></td>
     <td key="1"><span>integer</span></td>
     <td key="2">Not required</td>
     <td key="3"></td>
     <td key="4"><span style="white-space: pre-wrap">symbols quantity Precision</span></td>
     <td key="5"></td>
    </tr>
    <tr key="0-2-5">
     <td key="0"><span style="padding-left: 20px"> amountPrecision</span></td>
     <td key="1"><span>integer</span></td>
     <td key="2">Not required</td>
     <td key="3"></td>
     <td key="4"><span style="white-space: pre-wrap">symbols amount Precision</span></td>
     <td key="5"></td>
    </tr>
    <tr key="0-2-6">
     <td key="0"><span style="padding-left: 20px"> fokEligible</span></td>
     <td key="1"><span>integer</span></td>
     <td key="2">Not required</td>
     <td key="3"></td>
     <td key="4"><span style="white-space: pre-wrap">support fok? 1 support, 0 not support</span></td>
     <td key="5"></td>
    </tr>
    <tr key="0-2-7">
     <td key="0"><span style="padding-left: 20px"> iocEligible</span></td>
     <td key="1"><span>integer</span></td>
     <td key="2">Not required</td>
     <td key="3"></td>
     <td key="4"><span style="white-space: pre-wrap">support ioc? 1 support, 0 not support</span></td>
     <td key="5"></td>
    </tr>
    <tr key="0-2-8">
     <td key="0"><span style="padding-left: 20px"> gtcEligible</span></td>
     <td key="1"><span>integer</span></td>
     <td key="2">Not required</td>
     <td key="3"></td>
     <td key="4"><span style="white-space: pre-wrap">support gtc? 1 support, 0 not support</span></td>
     <td key="5"></td>
    </tr>
    <tr key="0-3">
     <td key="0"><span style="padding-left: 0px"><span style="color: #8c8a8a"></span> success</span></td>
     <td key="1"><span>boolean</span></td>
     <td key="2">Required</td>
     <td key="3"></td>
     <td key="4"><span style="white-space: pre-wrap">Successful?</span></td>
     <td key="5"></td>
    </tr>
    <tr key="0-4">
     <td key="0"><span style="padding-left: 0px"><span style="color: #8c8a8a"></span> messageArgs</span></td>
     <td key="1"><span>object []</span></td>
     <td key="2">Not required</td>
     <td key="3">new ArrayList&lt;&gt;()</td>
     <td key="4"><span style="white-space: pre-wrap"></span></td>
     <td key="5"></td>
    </tr> 
   </tbody> 
  </table>
 </body>
</html>

## Get Symbols Setting
Users may query symbols setting via this interface

### HTTP Request

- GET `/open/otc/api/symbol/{symbol}/setting`

API Key authorization: Read<br>

Rate limit:10times/1s<br>
### Request Parameters

> Response:

```json
{
  "code":200,
  "message":"success",
  "data":[
    {
      "symbol":"btcusdt",
      "ruleName":"FOK_AMOUNT",
      "ruleType":"MIN_VALUE",
      "ruleValue":"0.01"
    },
    {
      "symbol":"btcusdt",
      "ruleName":"FOK_QUANTITY",
      "ruleType":"MAX_VALUE",
      "ruleValue":"10"
    },
    {
      "symbol":"btcusdt",
      "ruleName":"FOK_QUANTITY",
      "ruleType":"MIN_VALUE",
      "ruleValue":"0.01"
    },
    {
      "symbol":"btcusdt",
      "ruleName":"FOK_AMOUNT",
      "ruleType":"MAX_VALUE",
      "ruleValue":"1000"
    }
  ],
  "success":true,
  "messageArgs":[

  ]
}
```
### Response Data
<html>
 <head></head>
 <body>
  <table> 
   <thead class="ant-table-thead"> 
    <tr> 
     <th key="name">Name</th>
     <th key="type">Type</th>
     <th key="required">Required?</th>
     <th key="default">Default</th>
     <th key="desc">Description</th>
     <th key="sub">Sublist</th> 
    </tr> 
   </thead>
   <tbody classname="ant-table-tbody">
    <tr key="0-0">
     <td key="0"><span style="padding-left: 0px"><span style="color: #8c8a8a"></span> code</span></td>
     <td key="1"><span>integer</span></td>
     <td key="2">Not required</td>
     <td key="3"></td>
     <td key="4"><span style="white-space: pre-wrap">service status code</span></td>
     <td key="5"></td>
    </tr>
    <tr key="0-1">
     <td key="0"><span style="padding-left: 0px"><span style="color: #8c8a8a"></span> message</span></td>
     <td key="1"><span>string</span></td>
     <td key="2">Not required</td>
     <td key="3"></td>
     <td key="4"><span style="white-space: pre-wrap">error message (in English)</span></td>
     <td key="5"></td>
    </tr>
    <tr key="0-2">
     <td key="0"><span style="padding-left: 0px"><span style="color: #8c8a8a"></span> data</span></td>
     <td key="1"><span>object []</span></td>
     <td key="2">Not required</td>
     <td key="3"></td>
     <td key="4"><span style="white-space: pre-wrap">service data</span></td>
     <td key="5"></td>
    </tr>
    <tr key="0-2-0">
     <td key="0"><span style="padding-left: 20px"> symbol</span></td>
     <td key="1"><span>string</span></td>
     <td key="2">Not required</td>
     <td key="3"></td>
     <td key="4"><span style="white-space: pre-wrap">symbols id in lower-case, e.g. btcusdt</span></td>
     <td key="5"></td>
    </tr>
    <tr key="0-2-1">
     <td key="0"><span style="padding-left: 20px"> ruleName</span></td>
     <td key="1"><span>string</span></td>
     <td key="2">Not required</td>
     <td key="3"></td>
     <td key="4"><span style="white-space: pre-wrap">rule Name</span></td>
     <td key="5"></td>
    </tr>
    <tr key="0-2-2">
     <td key="0"><span style="padding-left: 20px"> ruleType</span></td>
     <td key="1"><span>string</span></td>
     <td key="2">Not required</td>
     <td key="3"></td>
     <td key="4"><span style="white-space: pre-wrap">rule Type</span></td>
     <td key="5"></td>
    </tr>
    <tr key="0-2-3">
     <td key="0"><span style="padding-left: 20px"> ruleValue</span></td>
     <td key="1"><span>string</span></td>
     <td key="2">Not required</td>
     <td key="3"></td>
     <td key="4"><span style="white-space: pre-wrap">rule Value</span></td>
     <td key="5"></td>
    </tr>
    <tr key="0-3">
     <td key="0"><span style="padding-left: 0px"><span style="color: #8c8a8a"></span> success</span></td>
     <td key="1"><span>boolean</span></td>
     <td key="2">Required</td>
     <td key="3"></td>
     <td key="4"><span style="white-space: pre-wrap">Successful?</span></td>
     <td key="5"></td>
    </tr>
    <tr key="0-4">
     <td key="0"><span style="padding-left: 0px"><span style="color: #8c8a8a"></span> messageArgs</span></td>
     <td key="1"><span>object []</span></td>
     <td key="2">Not required</td>
     <td key="3">new ArrayList&lt;&gt;()</td>
     <td key="4"><span style="white-space: pre-wrap"></span></td>
     <td key="5"></td>
    </tr> 
   </tbody> 
  </table>
 </body>
</html>


# RFQ Trades

## Request For Quotation
Users may request for quotation via this interface

### HTTP Request

- POST `/open/otc/api/order/rfq/quote/request`

API Key authorization: Read<br>

Rate limit: 10times/1s<br>

Request parameters

<html>
 <head></head>
 <body>
  <table> 
   <thead class="ant-table-thead"> 
    <tr> 
     <th key="name">Name</th>
     <th key="type">Type</th>
     <th key="required">Required?</th>
     <th key="default">Default</th>
     <th key="desc">Description</th>
     <th key="sub">Sublist</th> 
    </tr> 
   </thead>
   <tbody classname="ant-table-tbody">
    <tr key="0-0">
     <td key="0"><span style="padding-left: 0px"><span style="color: #8c8a8a"></span> baseCurrency</span></td>
     <td key="1"><span>string</span></td>
     <td key="2">Required</td>
     <td key="3"></td>
     <td key="4"><span style="white-space: pre-wrap">base Currency</span></td>
     <td key="5"></td>
    </tr>
    <tr key="0-1">
     <td key="0"><span style="padding-left: 0px"><span style="color: #8c8a8a"></span> quoteCurrency</span></td>
     <td key="1"><span>string</span></td>
     <td key="2">Required</td>
     <td key="3"></td>
     <td key="4"><span style="white-space: pre-wrap">quote Currency</span></td>
     <td key="5"></td>
    </tr>
    <tr key="0-2">
     <td key="0"><span style="padding-left: 0px"><span style="color: #8c8a8a"></span> side</span></td>
     <td key="1"><span>integer</span></td>
     <td key="2">Required</td>
     <td key="3"></td>
     <td key="4"><span style="white-space: pre-wrap">trade side: 1-BUY 2-SELL</span></td>
     <td key="5"></td>
    </tr>
    <tr key="0-3">
     <td key="0"><span style="padding-left: 0px"><span style="color: #8c8a8a"></span> baseCurrencySize</span></td>
     <td key="1"><span>BigDecimal</span></td>
     <td key="2">Not required</td>
     <td key="3"></td>
     <td key="4"><span style="white-space: pre-wrap">Base Currency Size (null or larger than 0) Note: Base Currency and Quote Currency sizes do not coexist. When place RFQ, select either: a) baseCurrency size, or b) quoteCurrency size</span></td>
     <td key="5"></td>
    </tr>
    <tr key="0-4">
     <td key="0"><span style="padding-left: 0px"><span style="color: #8c8a8a"></span> quoteCurrencySize</span></td>
     <td key="1"><span>BigDecimal</span></td>
     <td key="2">Not required</td>
     <td key="3"></td>
     <td key="4"><span style="white-space: pre-wrap">Quote Currency Size (null or larger than 0) Note: Base Currency and Quote Currency sizes do not coexist. When place RFQ, select either: a) baseCurrency size, or b) quoteCurrency size (use baseCurrencySize when both base and quote are available)</span></td>
     <td key="5"></td>
    </tr> 
   </tbody> 
  </table>
 </body>
</html>

> Response:

```json
{
  "code":200,
  "message":"success",
  "data":{
    "requestId":"98cdbcfbce2e7ff7d14786a1c8ed409040a1e9f1",
    "price":41944.861407,
    "timestamp":1642658651145
  },
  "success":true,
  "messageArgs":[

  ]
}
```
### Response Data

<html>
 <head></head>
 <body>
  <table> 
   <thead class="ant-table-thead"> 
    <tr> 
     <th key="name">Name</th>
     <th key="type">Type</th>
     <th key="required">Required?</th>
     <th key="default">Default</th>
     <th key="desc">Description</th>
     <th key="sub">Sublist</th> 
    </tr> 
   </thead>
   <tbody classname="ant-table-tbody">
    <tr key="0-0">
     <td key="0"><span style="padding-left: 0px"><span style="color: #8c8a8a"></span> code</span></td>
     <td key="1"><span>integer</span></td>
     <td key="2">Not required</td>
     <td key="3"></td>
     <td key="4"><span style="white-space: pre-wrap">service status code</span></td>
     <td key="5"></td>
    </tr>
    <tr key="0-1">
     <td key="0"><span style="padding-left: 0px"><span style="color: #8c8a8a"></span> message</span></td>
     <td key="1"><span>string</span></td>
     <td key="2">Not required</td>
     <td key="3"></td>
     <td key="4"><span style="white-space: pre-wrap">error message</span></td>
     <td key="5"></td>
    </tr>
    <tr key="0-2">
     <td key="0"><span style="padding-left: 0px"><span style="color: #8c8a8a"></span> data</span></td>
     <td key="1"><span>object</span></td>
     <td key="2">Not required</td>
     <td key="3"></td>
     <td key="4"><span style="white-space: pre-wrap">service data</span></td>
     <td key="5"></td>
    </tr>
    <tr key="0-2-0">
     <td key="0"><span style="padding-left: 20px"> requestId</span></td>
     <td key="1"><span>string</span></td>
     <td key="2">Not required</td>
     <td key="3"></td>
     <td key="4"><span style="white-space: pre-wrap">request ID</span></td>
     <td key="5"></td>
    </tr>
    <tr key="0-2-1">
     <td key="0"><span style="padding-left: 20px"> price</span></td>
     <td key="1"><span>BigDecimal</span></td>
     <td key="2">Not required</td>
     <td key="3"></td>
     <td key="4"><span style="white-space: pre-wrap">RFQ price</span></td>
     <td key="5"></td>
    </tr>
    <tr key="0-2-2">
     <td key="0"><span style="padding-left: 20px"> timestamp</span></td>
     <td key="1"><span>integer</span></td>
     <td key="2">Not required</td>
     <td key="3"></td>
     <td key="4"><span style="white-space: pre-wrap">timestamp</span></td>
     <td key="5"></td>
    </tr>
    <tr key="0-3">
     <td key="0"><span style="padding-left: 0px"><span style="color: #8c8a8a"></span> success</span></td>
     <td key="1"><span>boolean</span></td>
     <td key="2">Required</td>
     <td key="3"></td>
     <td key="4"><span style="white-space: pre-wrap"></span></td>
     <td key="5"></td>
    </tr>
    <tr key="0-4">
     <td key="0"><span style="padding-left: 0px"><span style="color: #8c8a8a"></span> messageArgs</span></td>
     <td key="1"><span>object []</span></td>
     <td key="2">Not required</td>
     <td key="3">new ArrayList&lt;&gt;()</td>
     <td key="4"><span style="white-space: pre-wrap"></span></td>
     <td key="5"></td>
    </tr> 
   </tbody> 
  </table>
 </body>
</html>



## Lock Price and Place Orders
Users may request to lock price and place orders via this interface

### HTTP Request

- POST `/open/otc/api/order/rfq/quote/accept`

API Key authorization: write<br>

Rate limit: 10times/1s<br>

### Request Parameters
<html>
 <head></head>
 <body>
  <table> 
   <thead class="ant-table-thead"> 
    <tr> 
     <th key="name">Name</th>
     <th key="type">Type</th>
     <th key="required">Required?</th>
     <th key="default">Default</th>
     <th key="desc">Description</th>
     <th key="sub">Sublist</th> 
    </tr> 
   </thead>
   <tbody classname="ant-table-tbody">
    <tr key="0-0">
     <td key="0"><span style="padding-left: 0px"><span style="color: #8c8a8a"></span> rfqQuotationId</span></td>
     <td key="1"><span>string</span></td>
     <td key="2">Required</td>
     <td key="3"></td>
     <td key="4"><span style="white-space: pre-wrap">RFQ quotation ID (valid within 6 minutes)</span></td>
     <td key="5"></td>
    </tr> 
   </tbody> 
  </table> 
 </body>
</html>

> Response:

```json
{"code":200,"message":"success","data":1459564954255424,"success":true,"messageArgs":[]}
```
### Response Data

<html>
 <head></head>
 <body>
  <table> 
   <thead class="ant-table-thead"> 
    <tr> 
     <th key="name">Name</th>
     <th key="type">Type</th>
     <th key="required">Required?</th>
     <th key="default">Default</th>
     <th key="desc">Description</th>
     <th key="sub">Sublist</th> 
    </tr> 
   </thead>
   <tbody classname="ant-table-tbody">
    <tr key="0-0">
     <td key="0"><span style="padding-left: 0px"><span style="color: #8c8a8a"></span> code</span></td>
     <td key="1"><span>integer</span></td>
     <td key="2">Required</td>
     <td key="3"></td>
     <td key="4"><span style="white-space: pre-wrap">service status code</span></td>
     <td key="5"></td>
    </tr>
    <tr key="0-1">
     <td key="0"><span style="padding-left: 0px"><span style="color: #8c8a8a"></span> message</span></td>
     <td key="1"><span>string</span></td>
     <td key="2">Not required</td>
     <td key="3"></td>
     <td key="4"><span style="white-space: pre-wrap">error message</span></td>
     <td key="5"></td>
    </tr>
    <tr key="0-2">
     <td key="0"><span style="padding-left: 0px"><span style="color: #8c8a8a"></span> data</span></td>
     <td key="1"><span>integer</span></td>
     <td key="2">Not required</td>
     <td key="3"></td>
     <td key="4"><span style="white-space: pre-wrap">service data</span></td>
     <td key="5"></td>
    </tr>
    <tr key="0-3">
     <td key="0"><span style="padding-left: 0px"><span style="color: #8c8a8a"></span> success</span></td>
     <td key="1"><span>boolean</span></td>
     <td key="2">Required</td>
     <td key="3"></td>
     <td key="4"><span style="white-space: pre-wrap">Successful?</span></td>
     <td key="5"></td>
    </tr>
    <tr key="0-4">
     <td key="0"><span style="padding-left: 0px"><span style="color: #8c8a8a"></span> messageArgs</span></td>
     <td key="1"><span>object []</span></td>
     <td key="2">Not required</td>
     <td key="3">new ArrayList&lt;&gt;()</td>
     <td key="4"><span style="white-space: pre-wrap"></span></td>
     <td key="5"></td>
    </tr> 
   </tbody> 
  </table>
 </body>
</html>

## Get Users' Trade Records
Users may access records of traded orders via this interface

### HTTP Request

- POST `/open/otc/api/order/rfq/query`

API Key authorization: Read<br>

Rate limit: 10times/1s<br>
### Request Parameters
<html>
 <head></head>
 <body>
  <table> 
   <thead class="ant-table-thead"> 
    <tr> 
     <th key="name">Name</th>
     <th key="type">Type</th>
     <th key="required">Required?</th>
     <th key="default">Default</th>
     <th key="desc">Description</th>
     <th key="sub">Sublist</th> 
    </tr> 
   </thead>
   <tbody classname="ant-table-tbody">
    <tr key="0-0">
     <td key="0"><span style="padding-left: 0px"><span style="color: #8c8a8a"></span> page</span></td>
     <td key="1"><span>object</span></td>
     <td key="2">Not required</td>
     <td key="3"></td>
     <td key="4"><span style="white-space: pre-wrap">page parameters</span></td>
     <td key="5"></td>
    </tr>
    <tr key="0-0-2">
     <td key="0"><span style="padding-left: 20px"> size</span></td>
     <td key="1"><span>integer</span></td>
     <td key="2">Required</td>
     <td key="3"></td>
     <td key="4"><span style="white-space: pre-wrap">page size</span></td>
     <td key="5"></td>
    </tr>
    <tr key="0-0-3">
     <td key="0"><span style="padding-left: 20px"> page</span></td>
     <td key="1"><span>integer</span></td>
     <td key="2">Required</td>
     <td key="3"></td>
     <td key="4"><span style="white-space: pre-wrap">current page</span></td>
     <td key="5"></td>
    </tr>
    <tr key="0-1">
     <td key="0"><span style="padding-left: 0px"><span style="color: #8c8a8a"></span> side</span></td>
     <td key="1"><span>string</span></td>
     <td key="2">Not required</td>
     <td key="3"></td>
     <td key="4"><span style="white-space: pre-wrap">trade side</span></td>
     <td key="5"></td>
    </tr>
    <tr key="0-2">
     <td key="0"><span style="padding-left: 0px"><span style="color: #8c8a8a"></span> baseCurrency</span></td>
     <td key="1"><span>string</span></td>
     <td key="2">Not required</td>
     <td key="3"></td>
     <td key="4"><span style="white-space: pre-wrap">base Currency</span></td>
     <td key="5"></td>
    </tr>
    <tr key="0-3">
     <td key="0"><span style="padding-left: 0px"><span style="color: #8c8a8a"></span> quoteCurrency</span></td>
     <td key="1"><span>string</span></td>
     <td key="2">Not required</td>
     <td key="3"></td>
     <td key="4"><span style="white-space: pre-wrap">quote Currency</span></td>
     <td key="5"></td>
    </tr>
    <tr key="0-4">
     <td key="0"><span style="padding-left: 0px"><span style="color: #8c8a8a"></span> timeInForce</span></td>
     <td key="1"><span>integer</span></td>
     <td key="2">Not required</td>
     <td key="3"></td>
     <td key="4"><span style="white-space: pre-wrap"></span>Trade type:<BR>
    GTC(1): Good-Till-Cancelled orders, which may be partially traded and are good till users submit cancel instruction.<BR>
    IOC(3): Immediate-or-Cancel orders, which are traded immediately. Partial fill is allowed with the rest cancelled.<BR>
    FOK(4): Fill-or-Kill orders, which are traded immediately in full or cancelled in full.<BR>
    </td>
     <td key="5"></td>
    </tr>
    <tr key="0-5">
     <td key="0"><span style="padding-left: 0px"><span style="color: #8c8a8a"></span> startTime</span></td>
     <td key="1"><span>integer</span></td>
     <td key="2">Not required</td>
     <td key="3"></td>
     <td key="4"><span style="white-space: pre-wrap">order time - query startTime</span></td>
     <td key="5"></td>
    </tr>
    <tr key="0-6">
     <td key="0"><span style="padding-left: 0px"><span style="color: #8c8a8a"></span> endTime</span></td>
     <td key="1"><span>integer</span></td>
     <td key="2">Not required</td>
     <td key="3"></td>
     <td key="4"><span style="white-space: pre-wrap">order time - query endTime</span></td>
     <td key="5"></td>
    </tr>
    <tr key="0-7">
     <td key="0"><span style="padding-left: 0px"><span style="color: #8c8a8a"></span> orderId</span></td>
     <td key="1"><span>string</span></td>
     <td key="2">Not required</td>
     <td key="3"></td>
     <td key="4"><span style="white-space: pre-wrap">order id</span></td>
     <td key="5"></td>
    </tr>
    <tr key="0-8">
     <td key="0"><span style="padding-left: 0px"><span style="color: #8c8a8a"></span> clearingStatus</span></td>
     <td key="1"><span>integer</span></td>
     <td key="2">Not required</td>
     <td key="3"></td>
     <td key="4"><span style="white-space: pre-wrap">clearing Status</span></td>
     <td key="5"></td>
    </tr>
    <tr key="0-9">
     <td key="0"><span style="padding-left: 0px"><span style="color: #8c8a8a"></span> tradeStatusList</span></td>
     <td key="1"><span>integer []</span></td>
     <td key="2">Not required</td>
     <td key="3"></td>
     <td key="4"><span style="white-space: pre-wrap">trade Status List</span></td>
     <td key="5"></td>
    </tr>
    <tr key="0-10">
     <td key="0"><span style="padding-left: 0px"><span style="color: #8c8a8a"></span> clearingStatusList</span></td>
     <td key="1"><span>integer []</span></td>
     <td key="2">Not required</td>
     <td key="3"></td>
     <td key="4"><span style="white-space: pre-wrap">clearing Status List</span></td>
     <td key="5"></td>
    </tr>
    <tr key="0-11">
     <td key="0"><span style="padding-left: 0px"><span style="color: #8c8a8a"></span> ascending</span></td>
     <td key="1"><span>string</span></td>
     <td key="2">Not required</td>
     <td key="3"></td>
     <td key="4"><span style="white-space: pre-wrap">ascending (&quot;asc&quot;), or descending (&quot;desc&quot;), default as descending</span></td>
     <td key="5"></td>
    </tr> 
   </tbody> 
  </table> 
 </body>
</html>

> Response:

```json
{
  "code":200,
  "message":"success",
  "data":{
    "items":[
      {
        "id":2107,
        "orderId":1459028660060224,
        "side":2,
        "timeInForce":4,
        "baseCurrency":"BTC",
        "quoteCurrency":"USDT",
        "quantity":"0.010000",
        "cumQuantity":"0.010000",
        "avgPx":"42763.112689",
        "lastPx":"42763.112689",
        "lastQty":"0.010000",
        "lastTurnover":"427.631127",
        "commission":"0 USDT",
        "transactionTime":1642403881442,
        "userId":11433560,
        "status":"2",
        "symbolDisplayName":"BTCUSDT",
        "clearingStatus":1,
        "clearingAt":1642403881442,
        "clearingSourceId":"",
        "clearedQty":"0.010000",
        "clearedTurnover":"427.631127",
        "unClearedQty":"0.000000",
        "unClearedTurnover":"0.000000",
        "quantityPrecision":6,
        "amountPrecision":6
      },
      {
        "id":2105,
        "orderId":1459028332904512,
        "side":1,
        "timeInForce":4,
        "baseCurrency":"BTC",
        "quoteCurrency":"USDT",
        "quantity":"0.010000",
        "cumQuantity":"0.010000",
        "avgPx":"42876.586450",
        "lastPx":"42876.586450",
        "lastQty":"0.010000",
        "lastTurnover":"428.765864",
        "commission":"0 BTC",
        "transactionTime":1642403724601,
        "userId":11433560,
        "status":"2",
        "symbolDisplayName":"BTCUSDT",
        "clearingStatus":1,
        "clearingAt":1642403724601,
        "clearingSourceId":"",
        "clearedQty":"0.010000",
        "clearedTurnover":"428.765864",
        "unClearedQty":"0.000000",
        "unClearedTurnover":"0.000000",
        "quantityPrecision":6,
        "amountPrecision":6
      }
    ],
    "total":2,
    "size":10,
    "page":1
  },
  "success":true,
  "messageArgs":[

  ]
}
```
### Response data

<html>
 <head></head>
 <body>
  <table> 
   <thead class="ant-table-thead"> 
    <tr> 
     <th key="name">Name</th>
     <th key="type">Type</th>
     <th key="required">Required?</th>
     <th key="default">Default</th>
     <th key="desc">Description</th>
     <th key="sub">Sublist</th> 
    </tr> 
   </thead>
   <tbody classname="ant-table-tbody">
    <tr key="0-0">
     <td key="0"><span style="padding-left: 0px"><span style="color: #8c8a8a"></span> code</span></td>
     <td key="1"><span>integer</span></td>
     <td key="2">Not required</td>
     <td key="3"></td>
     <td key="4"><span style="white-space: pre-wrap">service status code</span></td>
     <td key="5"></td>
    </tr>
    <tr key="0-1">
     <td key="0"><span style="padding-left: 0px"><span style="color: #8c8a8a"></span> message</span></td>
     <td key="1"><span>string</span></td>
     <td key="2">Not required</td>
     <td key="3"></td>
     <td key="4"><span style="white-space: pre-wrap">error message</span></td>
     <td key="5"></td>
    </tr>
    <tr key="0-2">
     <td key="0"><span style="padding-left: 0px"><span style="color: #8c8a8a"></span> data</span></td>
     <td key="1"><span>object</span></td>
     <td key="2">Not required</td>
     <td key="3"></td>
     <td key="4"><span style="white-space: pre-wrap">service data</span></td>
     <td key="5"></td>
    </tr>
    <tr key="0-2-0">
     <td key="0"><span style="padding-left: 20px"> items</span></td>
     <td key="1"><span>object []</span></td>
     <td key="2">Not required</td>
     <td key="3"></td>
     <td key="4"><span style="white-space: pre-wrap">page data</span></td>
     <td key="5"></td>
    </tr>
    <tr key="0-2-0-0">
     <td key="0"><span style="padding-left: 40px"> id</span></td>
     <td key="1"><span>integer</span></td>
     <td key="2">Not required</td>
     <td key="3"></td>
     <td key="4"><span style="white-space: pre-wrap">id</span></td>
     <td key="5"></td>
    </tr>
    <tr key="0-2-0-1">
     <td key="0"><span style="padding-left: 40px"> orderId</span></td>
     <td key="1"><span>integer</span></td>
     <td key="2">Not required</td>
     <td key="3"></td>
     <td key="4"><span style="white-space: pre-wrap">order ID</span></td>
     <td key="5"></td>
    </tr>
    <tr key="0-2-0-2">
     <td key="0"><span style="padding-left: 40px"> side</span></td>
     <td key="1"><span>integer</span></td>
     <td key="2">Not required</td>
     <td key="3"></td>
     <td key="4"><span style="white-space: pre-wrap">trade side: 1 buy, 2 sell</span></td>
     <td key="5"></td>
    </tr>
    <tr key="0-2-0-3">
     <td key="0"><span style="padding-left: 40px"> timeInForce</span></td>
     <td key="1"><span>integer</span></td>
     <td key="2">Not required</td>
     <td key="3"></td>
     <td key="4"><span style="white-space: pre-wrap">trade type</span></td>
     <td key="5"></td>
    </tr>
    <tr key="0-2-0-4">
     <td key="0"><span style="padding-left: 40px"> baseCurrency</span></td>
     <td key="1"><span>string</span></td>
     <td key="2">Not required</td>
     <td key="3"></td>
     <td key="4"><span style="white-space: pre-wrap">base Currency</span></td>
     <td key="5"></td>
    </tr>
    <tr key="0-2-0-5">
     <td key="0"><span style="padding-left: 40px"> quoteCurrency</span></td>
     <td key="1"><span>string</span></td>
     <td key="2">Not required</td>
     <td key="3"></td>
     <td key="4"><span style="white-space: pre-wrap">quote Currency</span></td>
     <td key="5"></td>
    </tr>
    <tr key="0-2-0-6">
     <td key="0"><span style="padding-left: 40px"> quantity</span></td>
     <td key="1"><span>string</span></td>
     <td key="2">Not required</td>
     <td key="3"></td>
     <td key="4"><span style="white-space: pre-wrap">order quantity</span></td>
     <td key="5"></td>
    </tr>
    <tr key="0-2-0-7">
     <td key="0"><span style="padding-left: 40px"> cumQuantity</span></td>
     <td key="1"><span>string</span></td>
     <td key="2">Not required</td>
     <td key="3"></td>
     <td key="4"><span style="white-space: pre-wrap">cumulated traded order quantity</span></td>
     <td key="5"></td>
    </tr>
    <tr key="0-2-0-8">
     <td key="0"><span style="padding-left: 40px"> avgPx</span></td>
     <td key="1"><span>string</span></td>
     <td key="2">Not required</td>
     <td key="3"></td>
     <td key="4"><span style="white-space: pre-wrap">traded order average price</span></td>
     <td key="5"></td>
    </tr>
    <tr key="0-2-0-9">
     <td key="0"><span style="padding-left: 40px"> lastPx</span></td>
     <td key="1"><span>string</span></td>
     <td key="2">Not required</td>
     <td key="3"></td>
     <td key="4"><span style="white-space: pre-wrap">last price</span></td>
     <td key="5"></td>
    </tr>
    <tr key="0-2-0-10">
     <td key="0"><span style="padding-left: 40px"> lastQty</span></td>
     <td key="1"><span>string</span></td>
     <td key="2">Not required</td>
     <td key="3"></td>
     <td key="4"><span style="white-space: pre-wrap">last quantity</span></td>
     <td key="5"></td>
    </tr>
    <tr key="0-2-0-11">
     <td key="0"><span style="padding-left: 40px"> lastTurnover</span></td>
     <td key="1"><span>string</span></td>
     <td key="2">Not required</td>
     <td key="3"></td>
     <td key="4"><span style="white-space: pre-wrap">last turnover =lastPx*lastQty</span></td>
     <td key="5"></td>
    </tr>
    <tr key="0-2-0-12">
     <td key="0"><span style="padding-left: 40px"> commission</span></td>
     <td key="1"><span>string</span></td>
     <td key="2">Not required</td>
     <td key="3"></td>
     <td key="4"><span style="white-space: pre-wrap">trading fee/commission</span></td>
     <td key="5"></td>
    </tr>
    <tr key="0-2-0-13">
     <td key="0"><span style="padding-left: 40px"> transactionTime</span></td>
     <td key="1"><span>integer</span></td>
     <td key="2">Not required</td>
     <td key="3"></td>
     <td key="4"><span style="white-space: pre-wrap">transaction Timestamp</span></td>
     <td key="5"></td>
    </tr>
    <tr key="0-2-0-14">
     <td key="0"><span style="padding-left: 40px"> userId</span></td>
     <td key="1"><span>integer</span></td>
     <td key="2">Not required</td>
     <td key="3"></td>
     <td key="4"><span style="white-space: pre-wrap">user id</span></td>
     <td key="5"></td>
    </tr>
    <tr key="0-2-0-15">
     <td key="0"><span style="padding-left: 40px"> status</span></td>
     <td key="1"><span>string</span></td>
     <td key="2">Not required</td>
     <td key="3"></td>
     <td key="4"><span style="white-space: pre-wrap">Order status of RFQ trades: 2-completed, 4-cancelled, 8-failed</span></td>
     <td key="5"></td>
    </tr>
    <tr key="0-2-0-16">
     <td key="0"><span style="padding-left: 40px"> symbolDisplayName</span></td>
     <td key="1"><span>string</span></td>
     <td key="2">Not required</td>
     <td key="3"></td>
     <td key="4"><span style="white-space: pre-wrap">trade symbol Display Name</span></td>
     <td key="5"></td>
    </tr>
    <tr key="0-2-0-17">
     <td key="0"><span style="padding-left: 40px"> clearingStatus</span></td>
     <td key="1"><span>integer</span></td>
     <td key="2">Not required</td>
     <td key="3"></td>
     <td key="4"><span style="white-space: pre-wrap">clearing Status</span></td>
     <td key="5"></td>
    </tr>
    <tr key="0-2-0-18">
     <td key="0"><span style="padding-left: 40px"> clearingAt</span></td>
     <td key="1"><span>integer</span></td>
     <td key="2">Not required</td>
     <td key="3"></td>
     <td key="4"><span style="white-space: pre-wrap">clearing time</span></td>
     <td key="5"></td>
    </tr>
    <tr key="0-2-0-19">
     <td key="0"><span style="padding-left: 40px"> clearingSourceId</span></td>
     <td key="1"><span>string</span></td>
     <td key="2">Not required</td>
     <td key="3"></td>
     <td key="4"><span style="white-space: pre-wrap">clearing source ID</span></td>
     <td key="5"></td>
    </tr>
    <tr key="0-2-0-20">
     <td key="0"><span style="padding-left: 40px"> clearedQty</span></td>
     <td key="1"><span>string</span></td>
     <td key="2">Not required</td>
     <td key="3"></td>
     <td key="4"><span style="white-space: pre-wrap">cleared quantity</span></td>
     <td key="5"></td>
    </tr>
    <tr key="0-2-0-21">
     <td key="0"><span style="padding-left: 40px"> clearedTurnover</span></td>
     <td key="1"><span>string</span></td>
     <td key="2">Not required</td>
     <td key="3"></td>
     <td key="4"><span style="white-space: pre-wrap">cleared turnover</span></td>
     <td key="5"></td>
    </tr>
    <tr key="0-2-0-22">
     <td key="0"><span style="padding-left: 40px"> unClearedQty</span></td>
     <td key="1"><span>string</span></td>
     <td key="2">Not required</td>
     <td key="3"></td>
     <td key="4"><span style="white-space: pre-wrap">unCleared quantity</span></td>
     <td key="5"></td>
    </tr>
    <tr key="0-2-0-23">
     <td key="0"><span style="padding-left: 40px"> unClearedTurnover</span></td>
     <td key="1"><span>string</span></td>
     <td key="2">Not required</td>
     <td key="3"></td>
     <td key="4"><span style="white-space: pre-wrap">unCleared turnover</span></td>
     <td key="5"></td>
    </tr>
    <tr key="0-2-0-24">
     <td key="0"><span style="padding-left: 40px"> quantityPrecision</span></td>
     <td key="1"><span>integer</span></td>
     <td key="2">Not required</td>
     <td key="3"></td>
     <td key="4"><span style="white-space: pre-wrap">quantity Precision (base)</span></td>
     <td key="5"></td>
    </tr>
    <tr key="0-2-0-25">
     <td key="0"><span style="padding-left: 40px"> amountPrecision</span></td>
     <td key="1"><span>integer</span></td>
     <td key="2">Not required</td>
     <td key="3"></td>
     <td key="4"><span style="white-space: pre-wrap">amount Precision (quote)</span></td>
     <td key="5"></td>
    </tr>
    <tr key="0-2-1">
     <td key="0"><span style="padding-left: 20px"> total</span></td>
     <td key="1"><span>integer</span></td>
     <td key="2">Not required</td>
     <td key="3"></td>
     <td key="4"><span style="white-space: pre-wrap">total pages</span></td>
     <td key="5"></td>
    </tr>
    <tr key="0-2-2">
     <td key="0"><span style="padding-left: 20px"> size</span></td>
     <td key="1"><span>integer</span></td>
     <td key="2">Not required</td>
     <td key="3"></td>
     <td key="4"><span style="white-space: pre-wrap">page size</span></td>
     <td key="5"></td>
    </tr>
    <tr key="0-2-3">
     <td key="0"><span style="padding-left: 20px"> page</span></td>
     <td key="1"><span>integer</span></td>
     <td key="2">Not required</td>
     <td key="3"></td>
     <td key="4"><span style="white-space: pre-wrap">current page</span></td>
     <td key="5"></td>
    </tr>
    <tr key="0-3">
     <td key="0"><span style="padding-left: 0px"><span style="color: #8c8a8a"></span> success</span></td>
     <td key="1"><span>boolean</span></td>
     <td key="2">Required</td>
     <td key="3"></td>
     <td key="4"><span style="white-space: pre-wrap">Successful?</span></td>
     <td key="5"></td>
    </tr>
    <tr key="0-4">
     <td key="0"><span style="padding-left: 0px"><span style="color: #8c8a8a"></span> messageArgs</span></td>
     <td key="1"><span>object []</span></td>
     <td key="2">Not required</td>
     <td key="3">new ArrayList&lt;&gt;()</td>
     <td key="4"><span style="white-space: pre-wrap"></span></td>
     <td key="5"></td>
    </tr> 
   </tbody> 
  </table>
 </body>
</html>

## Get Users' History Orders
Users may access history orders via this interface

### HTTP Request

- POST `/open/otc/api/order/rfq/queryHistoryOrder`

API Key authorization: Read<br>
### Request Parameters

<html>
 <head></head>
 <body>
  <table> 
   <thead class="ant-table-thead"> 
    <tr> 
     <th key="name">Name</th>
     <th key="type">Type</th>
     <th key="required">Required?</th>
     <th key="default">Default</th>
     <th key="desc">Description</th>
     <th key="sub">Sublist</th> 
    </tr> 
   </thead>
   <tbody classname="ant-table-tbody">
    <tr key="0-0">
     <td key="0"><span style="padding-left: 0px"><span style="color: #8c8a8a"></span> page</span></td>
     <td key="1"><span>object</span></td>
     <td key="2">Not required</td>
     <td key="3"></td>
     <td key="4"><span style="white-space: pre-wrap">page parameters</span></td>
     <td key="5"></td>
    </tr>
    <tr key="0-0-2">
     <td key="0"><span style="padding-left: 20px"> size</span></td>
     <td key="1"><span>integer</span></td>
     <td key="2">Not required</td>
     <td key="3"></td>
     <td key="4"><span style="white-space: pre-wrap">page size</span></td>
     <td key="5"></td>
    </tr>
    <tr key="0-0-3">
     <td key="0"><span style="padding-left: 20px"> page</span></td>
     <td key="1"><span>integer</span></td>
     <td key="2">Not required</td>
     <td key="3"></td>
     <td key="4"><span style="white-space: pre-wrap">current page</span></td>
     <td key="5"></td>
    </tr>
    <tr key="0-1">
     <td key="0"><span style="padding-left: 0px"><span style="color: #8c8a8a"></span> side</span></td>
     <td key="1"><span>string</span></td>
     <td key="2">Not required</td>
     <td key="3"></td>
     <td key="4"><span style="white-space: pre-wrap">trade side</span></td>
     <td key="5"></td>
    </tr>
    <tr key="0-2">
     <td key="0"><span style="padding-left: 0px"><span style="color: #8c8a8a"></span> export</span></td>
     <td key="1"><span>boolean</span></td>
     <td key="2">Not required</td>
     <td key="3">false</td>
     <td key="4"><span style="white-space: pre-wrap"></span>Export or Not</td>
     <td key="5"></td>
    </tr>
    <tr key="0-3">
     <td key="0"><span style="padding-left: 0px"><span style="color: #8c8a8a"></span> baseCurrency</span></td>
     <td key="1"><span>string</span></td>
     <td key="2">Not required</td>
     <td key="3"></td>
     <td key="4"><span style="white-space: pre-wrap">base Currency</span></td>
     <td key="5"></td>
    </tr>
    <tr key="0-4">
     <td key="0"><span style="padding-left: 0px"><span style="color: #8c8a8a"></span> quoteCurrency</span></td>
     <td key="1"><span>string</span></td>
     <td key="2">Not required</td>
     <td key="3"></td>
     <td key="4"><span style="white-space: pre-wrap">quote Currency</span></td>
     <td key="5"></td>
    </tr>
    <tr key="0-5">
     <td key="0"><span style="padding-left: 0px"><span style="color: #8c8a8a"></span> excludeCancelled</span></td>
     <td key="1"><span>boolean</span></td>
     <td key="2">Not required</td>
     <td key="3"></td>
     <td key="4"><span style="white-space: pre-wrap">exclude Cancelled Orders?  「obsolete」</span></td>
     <td key="5"></td>
    </tr>
    <tr key="0-6">
     <td key="0"><span style="padding-left: 0px"><span style="color: #8c8a8a"></span> orderId</span></td>
     <td key="1"><span>integer</span></td>
     <td key="2">Not required</td>
     <td key="3"></td>
     <td key="4"><span style="white-space: pre-wrap">order ID</span></td>
     <td key="5"></td>
    </tr>
    <tr key="0-7">
     <td key="0"><span style="padding-left: 0px"><span style="color: #8c8a8a"></span> startTime</span></td>
     <td key="1"><span>integer</span></td>
     <td key="2">Not required</td>
     <td key="3"></td>
     <td key="4"><span style="white-space: pre-wrap">order time - query startTime</span></td>
     <td key="5"></td>
    </tr>
    <tr key="0-8">
     <td key="0"><span style="padding-left: 0px"><span style="color: #8c8a8a"></span> endTime</span></td>
     <td key="1"><span>integer</span></td>
     <td key="2">Not required</td>
     <td key="3"></td>
     <td key="4"><span style="white-space: pre-wrap">order time - query endTime</span></td>
     <td key="5"></td>
    </tr>
    <tr key="0-9">
     <td key="0"><span style="padding-left: 0px"><span style="color: #8c8a8a"></span> orderStateList</span></td>
     <td key="1"><span>integer []</span></td>
     <td key="2">Not required</td>
     <td key="3"></td>
     <td key="4"><span style="white-space: pre-wrap">order State List</span></td>
     <td key="5"></td>
    </tr>
   </tbody> 
  </table> 
 </body>
</html>
> Response:

```json
{
  "code":200,
  "message":"success",
  "data":{
    "items":[
      {
        "orderId":1459028660060224,
        "userId":11433560,
        "timeInForce":4,
        "symbol":"BTCUSDT",
        "baseCurrency":"BTC",
        "quoteCurrency":"USDT",
        "side":2,
        "cumTurnover":427.631127,
        "quantity":0.01,
        "price":42763.112689,
        "createAt":1642403880381,
        "lastQty":0.01,
        "lastPx":42763.112689,
        "cumQuantity":0.01,
        "avgPx":42763.112689,
        "commissionFee":0,
        "updatedAt":1642403881488,
        "status":2,
        "clOrdId":"1459028660060192",
        "orderType":null,
        "source":1,
        "accountOperateType":1,
        "amount":"427.631126",
        "unComQuantity":"0.000000",
        "quantityStr":"0.010000",
        "priceStr":"42763.112689",
        "comQuantityStr":"0.010000",
        "avgPxStr":"42763.112689",
        "commissionFeeStr":null,
        "sideStr":null,
        "timeInForceStr":null,
        "statusStr":null,
        "orderIdStr":"1459028660060224"
      },
      {
        "orderId":1459028332904512,
        "userId":11433560,
        "timeInForce":4,
        "symbol":"BTCUSDT",
        "baseCurrency":"BTC",
        "quoteCurrency":"USDT",
        "side":1,
        "cumTurnover":428.765864,
        "quantity":0.01,
        "price":42876.58645,
        "createAt":1642403724093,
        "lastQty":0.01,
        "lastPx":42876.58645,
        "cumQuantity":0.01,
        "avgPx":42876.58645,
        "commissionFee":0,
        "updatedAt":1642403724650,
        "status":2,
        "clOrdId":"1459028332904480",
        "orderType":null,
        "source":1,
        "accountOperateType":1,
        "amount":"428.765864",
        "unComQuantity":"0.000000",
        "quantityStr":"0.010000",
        "priceStr":"42876.586450",
        "comQuantityStr":"0.010000",
        "avgPxStr":"42876.586450",
        "commissionFeeStr":null,
        "sideStr":null,
        "timeInForceStr":null,
        "statusStr":null,
        "orderIdStr":"1459028332904512"
      }
    ],
    "total":2,
    "size":10,
    "page":1
  },
  "success":true,
  "messageArgs":[

  ]
}
```
### Response Data
<html>
 <head></head>
 <body>
  <table> 
   <thead class="ant-table-thead"> 
    <tr> 
     <th key="name">Name</th>
     <th key="type">Type</th>
     <th key="required">Required?</th>
     <th key="default">Default</th>
     <th key="desc">Description</th>
     <th key="sub">Sublist</th> 
    </tr> 
   </thead>
   <tbody classname="ant-table-tbody">
    <tr key="0-0">
     <td key="0"><span style="padding-left: 0px"><span style="color: #8c8a8a"></span> code</span></td>
     <td key="1"><span>integer</span></td>
     <td key="2">Required</td>
     <td key="3"></td>
     <td key="4"><span style="white-space: pre-wrap"></span>service status code</td>
     <td key="5"></td>
    </tr>
    <tr key="0-1">
     <td key="0"><span style="padding-left: 0px"><span style="color: #8c8a8a"></span> message</span></td>
     <td key="1"><span>string</span></td>
     <td key="2">Not required</td>
     <td key="3"></td>
     <td key="4"><span style="white-space: pre-wrap">error message</span></td>
     <td key="5"></td>
    </tr>
    <tr key="0-2">
     <td key="0"><span style="padding-left: 0px"><span style="color: #8c8a8a"></span> data</span></td>
     <td key="1"><span>object</span></td>
     <td key="2">Not required</td>
     <td key="3"></td>
     <td key="4"><span style="white-space: pre-wrap">service data</span></td>
     <td key="5"></td>
    </tr>
    <tr key="0-2-0">
     <td key="0"><span style="padding-left: 20px"> items</span></td>
     <td key="1"><span>object []</span></td>
     <td key="2">Not required</td>
     <td key="3"></td>
     <td key="4"><span style="white-space: pre-wrap">page data</span></td>
     <td key="5"></td>
    </tr>
    <tr key="0-2-0-0">
     <td key="0"><span style="padding-left: 40px"> orderId</span></td>
     <td key="1"><span>integer</span></td>
     <td key="2">Not required</td>
     <td key="3"></td>
     <td key="4"><span style="white-space: pre-wrap">*order id</span></td>
     <td key="5"></td>
    </tr>
    <tr key="0-2-0-1">
     <td key="0"><span style="padding-left: 40px"> userId</span></td>
     <td key="1"><span>integer</span></td>
     <td key="2">Not required</td>
     <td key="3"></td>
     <td key="4"><span style="white-space: pre-wrap">user id</span></td>
     <td key="5"></td>
    </tr>
    <tr key="0-2-0-2">
     <td key="0"><span style="padding-left: 40px"> timeInForce</span></td>
     <td key="1"><span>integer</span></td>
     <td key="2">Not required</td>
     <td key="3"></td>
     <td key="4"><span style="white-space: pre-wrap">GTC, IOC, FOK; only FOK for RFQ trades</span></td>
     <td key="5"></td>
    </tr>
    <tr key="0-2-0-3">
     <td key="0"><span style="padding-left: 40px"> symbol</span></td>
     <td key="1"><span>string</span></td>
     <td key="2">Not required</td>
     <td key="3"></td>
     <td key="4"><span style="white-space: pre-wrap">trade symbols</span></td>
     <td key="5"></td>
    </tr>
    <tr key="0-2-0-4">
     <td key="0"><span style="padding-left: 40px"> baseCurrency</span></td>
     <td key="1"><span>string</span></td>
     <td key="2">Not required</td>
     <td key="3"></td>
     <td key="4"><span style="white-space: pre-wrap">base Currency</span></td>
     <td key="5"></td>
    </tr>
    <tr key="0-2-0-5">
     <td key="0"><span style="padding-left: 40px"> quoteCurrency</span></td>
     <td key="1"><span>string</span></td>
     <td key="2">Not required</td>
     <td key="3"></td>
     <td key="4"><span style="white-space: pre-wrap">quote Currency</span></td>
     <td key="5"></td>
    </tr>
    <tr key="0-2-0-6">
     <td key="0"><span style="padding-left: 40px"> side</span></td>
     <td key="1"><span>integer</span></td>
     <td key="2">Not required</td>
     <td key="3"></td>
     <td key="4"><span style="white-space: pre-wrap">trade side: 1 buy, 2 sell</span></td>
     <td key="5"></td>
    </tr>
    <tr key="0-2-0-7">
     <td key="0"><span style="padding-left: 40px"> cumTurnover</span></td>
     <td key="1"><span>BigDecimal</span></td>
     <td key="2">Not required</td>
     <td key="3"></td>
     <td key="4"><span style="white-space: pre-wrap">cumulated Turnover</span></td>
     <td key="5"></td>
    </tr>
    <tr key="0-2-0-8">
     <td key="0"><span style="padding-left: 40px"> quantity</span></td>
     <td key="1"><span>BigDecimal</span></td>
     <td key="2">Not required</td>
     <td key="3"></td>
     <td key="4"><span style="white-space: pre-wrap">quantity</span></td>
     <td key="5"></td>
    </tr>
    <tr key="0-2-0-9">
     <td key="0"><span style="padding-left: 40px"> price</span></td>
     <td key="1"><span>BigDecimal</span></td>
     <td key="2">Not required</td>
     <td key="3"></td>
     <td key="4"><span style="white-space: pre-wrap">price</span></td>
     <td key="5"></td>
    </tr>
    <tr key="0-2-0-10">
     <td key="0"><span style="padding-left: 40px"> createAt</span></td>
     <td key="1"><span>integer</span></td>
     <td key="2">Not required</td>
     <td key="3"></td>
     <td key="4"><span style="white-space: pre-wrap">create time</span></td>
     <td key="5"></td>
    </tr>
    <tr key="0-2-0-11">
     <td key="0"><span style="padding-left: 40px"> lastQty</span></td>
     <td key="1"><span>BigDecimal</span></td>
     <td key="2">Not required</td>
     <td key="3"></td>
     <td key="4"><span style="white-space: pre-wrap">last quantity</span></td>
     <td key="5"></td>
    </tr>
    <tr key="0-2-0-12">
     <td key="0"><span style="padding-left: 40px"> lastPx</span></td>
     <td key="1"><span>BigDecimal</span></td>
     <td key="2">Not required</td>
     <td key="3"></td>
     <td key="4"><span style="white-space: pre-wrap">last price</span></td>
     <td key="5"></td>
    </tr>
    <tr key="0-2-0-13">
     <td key="0"><span style="padding-left: 40px"> cumQuantity</span></td>
     <td key="1"><span>BigDecimal</span></td>
     <td key="2">Not required</td>
     <td key="3"></td>
     <td key="4"><span style="white-space: pre-wrap">cumulated trade quantity in base currency</span></td>
     <td key="5"></td>
    </tr>
    <tr key="0-2-0-14">
     <td key="0"><span style="padding-left: 40px"> avgPx</span></td>
     <td key="1"><span>BigDecimal</span></td>
     <td key="2">Not required</td>
     <td key="3"></td>
     <td key="4"><span style="white-space: pre-wrap">traded order average price</span></td>
     <td key="5"></td>
    </tr>
    <tr key="0-2-0-15">
     <td key="0"><span style="padding-left: 40px"> commissionFee</span></td>
     <td key="1"><span>BigDecimal</span></td>
     <td key="2">Not required</td>
     <td key="3"></td>
     <td key="4"><span style="white-space: pre-wrap">commission fee</span></td>
     <td key="5"></td>
    </tr>
    <tr key="0-2-0-16">
     <td key="0"><span style="padding-left: 40px"> updatedAt</span></td>
     <td key="1"><span>integer</span></td>
     <td key="2">Not required</td>
     <td key="3"></td>
     <td key="4"><span style="white-space: pre-wrap">updated time</span></td>
     <td key="5"></td>
    </tr>
    <tr key="0-2-0-17">
     <td key="0"><span style="padding-left: 40px"> status</span></td>
     <td key="1"><span>integer</span></td>
     <td key="2">Not required</td>
     <td key="3"></td>
     <td key="4"><span style="white-space: pre-wrap">order status of RFQ trades: 2-completed, 4-rejected, 8-failed</span></td>
     <td key="5"></td>
    </tr>
    <tr key="0-2-0-18">
     <td key="0"><span style="padding-left: 40px"> clOrdId</span></td>
     <td key="1"><span>string</span></td>
     <td key="2">Not required</td>
     <td key="3"></td>
     <td key="4"><span style="white-space: pre-wrap">user OrderId, place order</span></td>
     <td key="5"></td>
    </tr>
    <tr key="0-2-0-19">
     <td key="0"><span style="padding-left: 40px"> orderType</span></td>
     <td key="1"><span>integer</span></td>
     <td key="2">Not required</td>
     <td key="3"></td>
     <td key="4"><span style="white-space: pre-wrap">order type</span></td>
     <td key="5"></td>
    </tr>
    <tr key="0-2-0-20">
     <td key="0"><span style="padding-left: 40px"> source</span></td>
     <td key="1"><span>integer</span></td>
     <td key="2">Not required</td>
     <td key="3"></td>
     <td key="4"><span style="white-space: pre-wrap">source of order</span></td>
     <td key="5"></td>
    </tr>
    <tr key="0-2-0-21">
     <td key="0"><span style="padding-left: 40px"> accountOperateType</span></td>
     <td key="1"><span>integer</span></td>
     <td key="2">Not required</td>
     <td key="3"></td>
     <td key="4"><span style="white-space: pre-wrap">account type for placing orders</span></td>
     <td key="5"></td>
    </tr>
    <tr key="0-2-0-22">
     <td key="0"><span style="padding-left: 40px"> amount</span></td>
     <td key="1"><span>string</span></td>
     <td key="2">Not required</td>
     <td key="3"></td>
     <td key="4"><span style="white-space: pre-wrap">order amount</span></td>
     <td key="5"></td>
    </tr>
    <tr key="0-2-0-23">
     <td key="0"><span style="padding-left: 40px"> unComQuantity</span></td>
     <td key="1"><span>string</span></td>
     <td key="2">Not required</td>
     <td key="3"></td>
     <td key="4"><span style="white-space: pre-wrap">*unCompleted quantity</span></td>
     <td key="5"></td>
    </tr>
    <tr key="0-2-0-24">
     <td key="0"><span style="padding-left: 40px"> quantityStr</span></td>
     <td key="1"><span>string</span></td>
     <td key="2">Not required</td>
     <td key="3"></td>
     <td key="4"><span style="white-space: pre-wrap">Quantity</span></td>
     <td key="5"></td>
    </tr>
    <tr key="0-2-0-25">
     <td key="0"><span style="padding-left: 40px"> priceStr</span></td>
     <td key="1"><span>string</span></td>
     <td key="2">Not required</td>
     <td key="3"></td>
     <td key="4"><span style="white-space: pre-wrap">price</span></td>
     <td key="5"></td>
    </tr>
    <tr key="0-2-0-26">
     <td key="0"><span style="padding-left: 40px"> comQuantityStr</span></td>
     <td key="1"><span>string</span></td>
     <td key="2">Not required</td>
     <td key="3"></td>
     <td key="4"><span style="white-space: pre-wrap">completed order quantity</span></td>
     <td key="5"></td>
    </tr>
    <tr key="0-2-0-27">
     <td key="0"><span style="padding-left: 40px"> avgPxStr</span></td>
     <td key="1"><span>string</span></td>
     <td key="2">Not required</td>
     <td key="3"></td>
     <td key="4"><span style="white-space: pre-wrap">traded order average price</span></td>
     <td key="5"></td>
    </tr>
    <tr key="0-2-0-28">
     <td key="0"><span style="padding-left: 40px"> commissionFeeStr</span></td>
     <td key="1"><span>string</span></td>
     <td key="2">Not required</td>
     <td key="3"></td>
     <td key="4"><span style="white-space: pre-wrap">commission fee</span></td>
     <td key="5"></td>
    </tr>
    <tr key="0-2-0-29">
     <td key="0"><span style="padding-left: 40px"> sideStr</span></td>
     <td key="1"><span>string</span></td>
     <td key="2">Not required</td>
     <td key="3"></td>
     <td key="4"><span style="white-space: pre-wrap">trade side</span></td>
     <td key="5"></td>
    </tr>
    <tr key="0-2-0-30">
     <td key="0"><span style="padding-left: 40px"> timeInForceStr</span></td>
     <td key="1"><span>string</span></td>
     <td key="2">Not required</td>
     <td key="3"></td>
     <td key="4"><span style="white-space: pre-wrap">GTC, IOC, FOK; only FOK for RFQ trades</span></td>
     <td key="5"></td>
    </tr>
    <tr key="0-2-0-31">
     <td key="0"><span style="padding-left: 40px"> statusStr</span></td>
     <td key="1"><span>string</span></td>
     <td key="2">Not required</td>
     <td key="3"></td>
     <td key="4"><span style="white-space: pre-wrap">order status of RFQ trades: 2-completed, 4-cancelled, 8-failed</span></td>
     <td key="5"></td>
    </tr>
    <tr key="0-2-0-32">
     <td key="0"><span style="padding-left: 40px"> orderIdStr</span></td>
     <td key="1"><span>string</span></td>
     <td key="2">Not required</td>
     <td key="3"></td>
     <td key="4"><span style="white-space: pre-wrap">orderID</span></td>
     <td key="5"></td>
    </tr>
    <tr key="0-2-1">
     <td key="0"><span style="padding-left: 20px"> total</span></td>
     <td key="1"><span>integer</span></td>
     <td key="2">Not required</td>
     <td key="3"></td>
     <td key="4"><span style="white-space: pre-wrap">total pages.</span></td>
     <td key="5"></td>
    </tr>
    <tr key="0-2-2">
     <td key="0"><span style="padding-left: 20px"> size</span></td>
     <td key="1"><span>integer</span></td>
     <td key="2">Not required</td>
     <td key="3"></td>
     <td key="4"><span style="white-space: pre-wrap">page size.</span></td>
     <td key="5"></td>
    </tr>
    <tr key="0-2-3">
     <td key="0"><span style="padding-left: 20px"> page</span></td>
     <td key="1"><span>integer</span></td>
     <td key="2">Not required</td>
     <td key="3"></td>
     <td key="4"><span style="white-space: pre-wrap">current page</span></td>
     <td key="5"></td>
    </tr>
    <tr key="0-3">
     <td key="0"><span style="padding-left: 0px"><span style="color: #8c8a8a"></span> success</span></td>
     <td key="1"><span>boolean</span></td>
     <td key="2">Required</td>
     <td key="3"></td>
     <td key="4"><span style="white-space: pre-wrap">Successful?</span></td>
     <td key="5"></td>
    </tr>
    <tr key="0-4">
     <td key="0"><span style="padding-left: 0px"><span style="color: #8c8a8a"></span> messageArgs</span></td>
     <td key="1"><span>object []</span></td>
     <td key="2">Not required</td>
     <td key="3">new ArrayList&lt;&gt;()</td>
     <td key="4"><span style="white-space: pre-wrap"></span></td>
     <td key="5"></td>
    </tr> 
   </tbody> 
  </table>
 </body>
</html>

  
  
