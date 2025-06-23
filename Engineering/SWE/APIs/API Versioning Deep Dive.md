API Versioning
===

## Table of Contents
- [Introduction](#introduction)
- [Overview](#overview)
    - [What is API Versioning](#what-is-api-versioning)
    - [Common Approaches](#common-approaches)
- [Sources](#sources)
- [Summary](#summary)

# Introduction

Key Questions to be Answered:
1. What is API Versioning?
2. In Spring; how is it generally implemented?
3. Where, when and why should we apply versioning?
4. Is versioning applied to the entire API portfolio and granular to the resource level?
    - What about across code bases?
    - E.g., If our topics API has an upgrade but our Flink API does not, do both upgrade to v2 or just topics?

# Overview
## What is API Versioning?


## Common Approaches
|Version Approach|Description|Pros|Cons|Example Use Case|
|---|---|---|---|---|
|No Versioning|No versioning is applied. Changes will be deployed to clients immediately|Pros|Cons|UC|
|URI Versioning|The HTTP URI will be prepended with a version that dictates which version of the API is called (e.g., `/v2/products/{id}`)|Pros|Cons|UC|
|Query String Versioning|HTTP URI has a query parameter that also specifies version (e.g., `/products/{id}?category=books&version=2`)|Pros|Cons|UC|
|Header Versioning|Include a custom header that specifies the version as apart of the HTTP request (e.g, `GET /product/{id}` includes `Custom-header: api-version=2`)|Pros|Cons|UC|
|Media Type Versioning|Include the version in the `Accept` header (e.g, `GET https://api.myapi.com/product/{id}` includes `Accept: application/vnd.myapi.v2+json`)|Pros|Cons|UC|

## Pitfalls
Version Lock
Version Promiscuity

# Sources
- https://restfulapi.net/rest-api-best-practices/ (section 5)
- https://learn.microsoft.com/en-us/azure/architecture/best-practices/api-design#implement-versioning
- https://cloud.google.com/blog/products/api-management/restful-api-design-tips-versioning?utm_source=chatgpt.com

# Summary