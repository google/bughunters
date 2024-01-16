# Domain tiers

In the spirit of transparency and in order to help security researchers validate
their knowledge of Google services and find new targets, we are
publishing a list of high sensitivity domains and their tiers.

## Why do we need domain tiers?

Google maintains **~10,000** different domains (not taking country-specific TLDs
into account), each one potentially containing a distinct software or product,
including acquired products, services, and offerings by Alphabet-owned entities.

To focus our security efforts on the right applications, we at the Google
Security Team introduced the internal concept of *domain tiers* in 2019, which
assigns a sensitivity factor to each domain.

## The domain tier concept

The primary use case of the domain tiers concept is to assign a sensitivity
factor/score to each domain that is hosting a web application. However, domain
tiers offer additional benefits such as enabling the discoverability of
applications with a given sensitivity score. The concept itself can also be
utilized for other identifiers as well, such as identifying domains leading to
infrastructure, in contrast to pure web applications that Google is using this
concept for. The decision of which tier a given domain belongs to is influenced
by the sensitivity metrics of the product(s) served on that domain. Ultimately,
this leads to a classification into one of 5 different tiers – where tier 0
represents the highest sensitivity. While this is true for all classified
domains, there are distinctions made between domains from acquired products and
Bets on the one hand, and Google domains on the other. The following table
illustrates the differences:


|            | Google classification| Acquisition / Bet classification
:----------- | :--------------------| :--------
**Tier0**|Domains where a critical vulnerability (e.g. XSS or authorization bypass) could lead to a compromise of a user's account or execution of code on their system.|Domains where a compromise may lead to extended access of highly sensitive information on other systems.
**Tier1**|Domains where a vulnerability could disclose particularly sensitive user data.|Domains where a compromise may lead to access of highly-sensitive information on a single system or service.
**Tier2**|Subdomains where the impact of a vulnerability may be damaging, but is less likely to lead to the disclosure of highly sensitive data.|Domains where a compromise may lead to potential disclosure of sensitive, but not highly-sensitive information.
**Tier3**|Lower-sensitivity domains where a vulnerability is unlikely to affect sensitive data.|If this domain is compromised, no sensitive user data is affected.
**Tier4**|Sandboxed domains explicitly meant to host untrusted user-controlled content, or domains controlled by third parties.|The domain is hosted and operated by a third party or contains only user-curated, maintained, or public content.

## Domain list

This directory contains [text-formatted protocol buffer](https://protobuf.dev/reference/protobuf/textformat-spec/) files with a list of *Tier0* and *Tier1* domains:

* [`external_domains_google.asciipb`](external_domains_google.asciipb) lists Google domains
* [`external_domains_acquisitions.asciipb`](external_domains_acquisitions.asciipb) lists acquisition and Bets domains

The files are redacted copies of the ones used by the Google Security team to categorize the sensitivity of the applications hosted on a given domain. The list will be automatically updated. Feel free to use the list
to prioritize your security research on Alphabet's applications.

**Domain sensitivity is inherited from the parent domain** by default. If you don't see a particular subdomain (e.g. "foo.google.com"), check if its parent (e.g. "google.com") is listed; the implicit sensitivity of the subdomain will be the same as the parent's.

Domains that are not included in the list should be considered lower tier, or not tiered at all.