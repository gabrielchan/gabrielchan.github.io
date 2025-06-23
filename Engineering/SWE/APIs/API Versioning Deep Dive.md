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
#### No Versioning
- Description: No versioning is applied. Changes deployed are immediately consumed byclients
- Pros:
    - Very easy to implement
- Cons:
    - No backward compatibility -> Breaking changes impacts all clients immediately
- Example Use Case:
    - Small internal APIs or early-stage projects where breaking changes are managable

#### URI Versioning
- Description: The version is included in the URL path (e.g., `/v2/products/{id}`)
- Pros:
    - Straightforward to implement and understand
    - Very clear versioning to clients and in documentation
    - Well supported by HTTP caching mechanisms, making it cache-friendly
- Cons:
    - Individual versions of the same "item" are considered seperate resources
    - Technically not REST because a logical resource has many versions
    - Complicates HATEOAS principles
    - As there are more versions added and maintained, more overhead
- Example Use Case:
    - Common for public APIs due to clear versioning
    - Could be used for internal APIs when version clarity is critical

#### Query String Versioning
- Description: Version is included as a query parameter (e.g., /products/{id}?version=2)
- Pros:
    - Maintains a consistent URI path across versions
    - Cache-friendly (with proper proxy config)
- Cons:
    - Can complicate HATEOAS by making versioning less explicit in the resource path
    - Some caching layers and older browsers may not cache query-string URLs effectively, potentially reducing performance
- Example Use Case:
    - Internal APIs or scenarios where query parameters are already heavily used and manageable

#### Header Versioning
- Description: The version is specified in a custom HTTP header (e.g., X-API-VERSION: 2)
- Pros:
    - Clean and consistent URIs, preserving REST resource identity
    - Allows version negotiation without changing the URI structure
- Cons:
    - Version information is not visible in URLs, reducing discoverability
    - Requires client and server support for custom headers; harder to test manually without proper tools
- Example Use Case:
    - Controlled environments such as internal APIs where clients and servers are tightly coupled

#### Media Type Versioning (Content Negotiation)
- Description: Version is included in the Accept header as a custom media type (e.g., Accept: application/vnd.myapi.v2+json)
- Pros:
    - Aligns with REST principles by leveraging content negotiation
    - Enables fine-grained control over API responses and version evolution
- Cons:
    - Least visible to developers and requires clients to set and support custom headers correctly
    - Increases complexity for clients and servers
- Example Use Case:
    - Large-scale or enterprise APIs that demand strict version control and content negotiation capabilities

### Java Spring Implementation High-Level Notes/Differences
- URI Versioning requires a `@RestController` per version
- Query String, Header, and Media Type has a unique `@GetMapping` per version under the same `@RestController`
- Header and Media Type work by having additional information in the *HTTP headers*, thus both the client and server must support it

## Pitfalls
Version Lock
Version Promiscuity

# Sources
- https://restfulapi.net/rest-api-best-practices/ (section 5)
- https://learn.microsoft.com/en-us/azure/architecture/best-practices/api-design#implement-versioning
- https://cloud.google.com/blog/products/api-management/restful-api-design-tips-versioning?utm_source=chatgpt.com

# Summary