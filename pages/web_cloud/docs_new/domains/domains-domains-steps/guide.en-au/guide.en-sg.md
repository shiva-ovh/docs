---
title: Set up a custom domain
slug: guide.en-au
section: Domains-Steps
---

**Last updated 6th November 2023**



## Objective  

**Last updated 6th November 2023**



## Objective  

Once your project is ready for production, replace the automatically generated domain with your own custom domain.
Note that adding a domain disables the automatically generated URL for your Production environment only.


If you are an Enterprise or Elite customer and have a Grid or {{% names/dedicated-gen-3 %}} project, you can [customize the URLs for your non-production environments](/domains/steps/custom-domains-preview-environments).
{{% names/dedicated-gen-2 %}} customers can also customize the domain for their Staging environment.
<--->
You can also [customize the URLs for your preview environments](/domains/steps/custom-domains-preview-environments).
{{% /version/specific %}}

## Before you begin

You need:

- A project that's ready to go live


- A domain with access to its settings with the registrar


- A registrar that allows `CNAME` records or [one of the alternatives](./dns.md) on [apex domains](../../glossary#apex-domain)


- Optional: The [CLI](../../administration/cli/_index.md) installed locally


<!-- There are no development plans on Upsun -->
{{< version/only "1" >}}
- If you are on a development plan, you need to [upgrade your tier to a production plan](#optional-change-your-plan-to-a-production-plan).


{{< /version/only >}}

If you are planning to use several subdomains of the same domain on different projects,
see how to [manage multiple subdomains](subdomains) *before* you add your domain to Web PaaS.

{{< version/only "1" >}}
## 1. Get the target for your project

You want to point your DNS record to the automatically generated URL.
Your domain needs to point to that target for your site to go live.

{{< version/only "1" >}}

For Dedicated plans, get the target for your project from your Web PaaS contact.

{{< /version/only >}}

> [!tabs]      

## 2. Configure your DNS provider

Your DNS provider (usually your registrar) is where you manage your domain.
Most registrars offer similar functionalities regarding DNS configuration but use different terminology or configuration.
For example, some registrars require you to use an `@` to create custom records on the apex domain, while others don't.
Check your registrar's documentation.

Note that depending on your registrar and the time to live (TTL) you set,
it can take anywhere from 15 minutes to 72 hours for DNS changes to be taken into account.

> [!tabs]      

## 3. Set your domain

Add a single domain to your project:

> [!tabs]      

## What's next

* [Use a content delivery network](../cdn/_index.md)
* [Use subdomains across multiple projects](./subdomains.md)
* [Use a custom TLS certificate](./tls.md)
