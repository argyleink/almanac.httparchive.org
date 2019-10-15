---
part_number: II
chapter_number: 8
title: Security
description: State of Security 2019
hero_image: ''
authors: [scotthelme]
reviewers: [paulcalvano, bazzadp, ghedo, ndrnmnn]
translaters: []
---

# Chapter 8: Security

## Intro
The Security chapter of the Web Almanac looks at the progress made in securing the web. With security and privacy becoming increasingly more important online there has been and increase in the availability of features to protect site operators and users. We're going to look at the adoption of these new features across the Web.

## TLS
Perhaps the largest push to increasing security and privacy online we're seeing at present is the widespread adoption of Transport Layer Security. TLS is the protocol that gives us the 'S' in HTTPS and allows secure and private browsing of websites. Not only are we seeing a great increase in the use of HTTPS across the Web, but also an increase in more modern versions of TLS like TLSv1.2 and TLSv1.3, which is also important.  

### Protocol Versions
Looking at the support for various protocol versions we can see that the use of legacy TLS versions like TLSv1.0 and TLSv1.1 is minimal and almost all support is for the newer TLSv1.2 and TLSv1.3 versions of the protocol. Not only that but even though TLSv1.3 is still very young as a standard, over 40% of requests using TLS are using the latest version!

<br/>

| client  | tls_version | requests | total    | pct   |
|---------|-------------|----------|----------|-------|
| mobile  | TLS 1.2     | 51909891 | 90232813 | 57.53 |
| desktop | TLS 1.2     | 46414404 | 79586221 | 58.32 |
| mobile  | TLS 1.3     | 37689500 | 90232813 | 41.77 |
| desktop | TLS 1.3     | 32547410 | 79586221 | 40.9  |
| mobile  | TLS 1.0     | 623695   | 90232813 | 0.69  |
| desktop | TLS 1.0     | 616926   | 79586221 | 0.78  |
| mobile  | TLS 1.1     | 9727     | 90232813 | 0.01  |
| desktop | TLS 1.1     | 7481     | 79586221 | 0.01  |

### Certificate Authorities 
Of course, if we want to use HTTPS on our website then we need a certificate from a Certificate Authority. With the increase in the use of HTTPS comes the increase in use of CAs and their products/services. Here are the top 10 certificate issuers based on the volume of TLS requests that use their certificate.

<br/>

| client  | issuer                                 | requests | total    | pct   |
|---------|----------------------------------------|----------|----------|-------|
| mobile  | Google Internet Authority G3           | 15177834 | 77109521 | 19.68 |
| desktop | Google Internet Authority G3           | 10760946 | 55866534 | 19.26 |
| desktop | Let's Encrypt Authority X3             | 5698524  | 55866534 | 10.2  |
| desktop | DigiCert SHA2 High Assurance Server CA | 5491199  | 55866534 | 9.83  |
| mobile  | DigiCert SHA2 High Assurance Server CA | 7141087  | 77109521 | 9.26  |
| mobile  | Let's Encrypt Authority X3             | 7085319  | 77109521 | 9.19  |
| mobile  | DigiCert SHA2 Secure Server CA         | 6727708  | 77109521 | 8.72  |
| mobile  | GTS CA 1O1                             | 6497589  | 77109521 | 8.43  |
| desktop | GTS CA 1O1                             | 4395585  | 55866534 | 7.87  |
| desktop | DigiCert SHA2 Secure Server CA         | 4217289  | 55866534 | 7.55  |

<br/>

The rise of Let's Encrypt has been meteoric after their launch in early 2016, since then they've become one of the top certificate issuers in the world. The availability of free certificates and automated tooling has been critically important to the adoption of HTTPS on the Web and Let's Encrypt certainly had a significant part to play in both of those.

### Authentication key type
Alongside the important requirement to use HTTPS is the requirement to also use a good configuration. With so many configuration options and choices to make, this is a careful balance. Looking first of all the keys used for authentication purposes, we still see a large % of the Web using RSA.

<br/>

| client  | is_ecdsa | is_rsa   | total    | pct_ecdsa | pct_rsa |
|---------|----------|----------|----------|-----------|---------|
| mobile  | 23832006 | 53056268 | 90232714 | 26.41     | 58.8    |
| desktop | 17090634 | 38734846 | 79586141 | 21.47     | 48.67   |

<br/>

Whilst ECDSA keys are stronger and demonstrate better performance than their RSA counterparts, concerns around backwards compatibility do prevent some website operators from migrating. 

### Forward Secrecy
The importance of Forward Secrecy is now well understood. It was introduced as an optional configuration in 2008 with TLSv1.2 and has become mandatory in 2018 with TLSv1.3 requiring it.

<br/>

| client  | forward_secrecy_count | total    | pct   |
|---------|-----------------------|----------|-------|
| desktop | 54148540              | 55866534 | 96.92 |
| mobile  | 74405592              | 77109521 | 96.49 |

<br/>

Looking at the % of TLS requests that utilised Forward Secrecy, we can see that support is tremendous. We'd expect that the continuing increase in the adoption of TLSv1.3 will further increase these numbers.

### Cipher Suites
With the simplification of the available cipher suites in TLSv1.3, and the drive to use better cipher suites created by sites like [SSL Labs](https://www.ssllabs.com/), we can see that the majority of cipher suites negotiated for TLS requests were indeed excellent.

<br/>

| client  | cipher            | cipher_count | total    | pct   |
|---------|-------------------|--------------|----------|-------|
| mobile  | AES_128_GCM       | 59148056     | 77109521 | 76.71 |
| desktop | AES_128_GCM       | 42385458     | 55866534 | 75.87 |
| mobile  | AES_256_GCM       | 14258912     | 77109521 | 18.49 |
| desktop | AES_256_GCM       | 11022581     | 55866534 | 19.73 |
| mobile  | AES_256_CBC       | 1741346      | 77109521 | 2.26  |
| mobile  | AES_128_CBC       | 1324594      | 77109521 | 1.72  |
| desktop | AES_256_CBC       | 1238047      | 55866534 | 2.22  |
| desktop | AES_128_CBC       | 801139       | 55866534 | 1.43  |
| mobile  | CHACHA20_POLY1305 | 608567       | 77109521 | 0.79  |
| desktop | CHACHA20_POLY1305 | 386219       | 55866534 | 0.69  |
| desktop | 3DES_EDE_CBC      | 33090        | 55866534 | 0.06  |
| mobile  | 3DES_EDE_CBC      | 28046        | 77109521 | 0.04  |

## Mixed Content
Most sites on the Web originally existed as HTTP websites and have had to migrate their site to HTTPS. This 'lift and shift' operation can be difficult and sometimes things get missed or left behind. This results in sites having Mixed Content, where their pages load over HTTPS but something on the page, perhaps an image or a style, is loaded over HTTP. Mixed Content is bad for security and privacy, and can be difficult to find and fix.

<br/>

| client  | mixed_content_sites | active_mixed_content_sites | total   | pct_mixed | pct_active_mixed |
|---------|---------------------|----------------------------|---------|-----------|------------------|
| desktop | 476965              | 117107                     | 2931828 | 16.27     | 3.99             |
| mobile  | 508724              | 136761                     | 3309605 | 15.37     | 4.13             |

<br/>

We can see that almost 20% of sites across mobile and desktop present some form of mixed content. Whilst passive mixed content, something like an image, is less dangerous, we can still see that almost a quarter of sites with mixed content have active mixed content. Active mixed content, like javascript, is more dangerous as an attacker can insert their own hostile code into a page easily.

## Security Headers
Many new and recent features for site operators to better protect their users have come in the form of new HTTP response headers that can configure and control security protections built into the browser. Some of these features are easy to enable and provide a huge level of protection whilst others require a little more work from site operators.

### HTTP Strict Transport Security
The HSTS header allows a website to instruct a User Agent that it should only ever communicate with the site over a secure HTTPS connection. Given that over 40% of requests were capable of using TLS, we see a much lower % of requests instructing the UA to require it.

<br/>

| client  | directive         | freq   | total   | pct   |
|---------|-------------------|--------|---------|-------|
| desktop | max-age           | 647149 | 4371973 | 14.8  |
| mobile  | max-age           | 678566 | 5297442 | 12.81 |
| desktop | includeSubDomains | 168909 | 4371973 | 3.86  |
| mobile  | includeSubDomains | 174295 | 5297442 | 3.29  |
| desktop | preload           | 99335  | 4371973 | 2.27  |
| mobile  | preload           | 105648 | 5297442 | 1.99  |

<br/>

Less than 15% of mobile and desktop page are issuing a HSTS with the minimum requirement of a max-age directive. Fewer still are including subdomains in their policy with the includeSubDomains directive and even fewer still are HSTS preloading. Looking at the median value for a HSTS max-age we can see that on both desktop and mobile it is 15768000, a strong configuration.

<br/>

| percentile | client  | max_age  |
|------------|---------|----------|
| 10         | desktop | 300      |
| 10         | mobile  | 300      |
| 25         | desktop | 7889238  |
| 25         | mobile  | 7889238  |
| 50         | desktop | 15768000 |
| 50         | mobile  | 15768000 |
| 75         | desktop | 31536000 |
| 75         | mobile  | 31536000 |
| 90         | desktop | 63072000 |
| 90         | mobile  | 63072000 |

#### HSTS Preloading
With the HSTS policy delivered via a HTTP Response Header, when visiting a site for the first time a UA will not know whether a policy is configured. To avoid this Trust On First Use problem, a site operator can have the policy prelaoded into the UA.

<br/>

| client  | freq  | total   | pct  |
|---------|-------|---------|------|
| desktop | 13345 | 4371973 | 0.31 |
| mobile  | 13707 | 5297442 | 0.26 |

<br/>

The requirements to do so are outlined on the [HSTS Preload](https://hstspreload.org/) site but we can see that only a small number of sites are eligible according to current criteria.

### Content Security Policy

#### Hash/Nonce

#### strict-dynamic

#### trusted-types

#### Unsafe inline/eval

#### upgrade-insecure-requests

#### frame-ancestors

### Referrer Policy

### Feature Policy

### X-Frame-Options

### X-Content-Type-Options

### X-Xss-Protection

### Report-To

### Network Error Logging

### Clear Site Data

## Cookies

### Secure

### HttpOnly

### SameSite

### Prefixes

## Subresource Integrity

## Vulnerable JS Libraries