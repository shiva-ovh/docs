---
title: Use Lando for local development
slug: lando
section: Development-Local
---

**Last updated 6th November 2023**



## Objective  

[Lando](https://docs.lando.dev) is a third-party local development tool for which several stacks are available (LAMP, LEMP, MEAN).
Lando works with most services supported by Web PaaS [except for](https://docs.lando.dev/platformsh/caveats.html#unsupported-things) Vault KMS and network storage.
See a list of [supported services](https://docs.lando.dev/platformsh/config.html#services-yaml).

> [!primary]  
> 
> {{% local-dev/lando-plugin-note %}}
> 
> 

For a complete reference, consult the following resources:

- [Lando Web PaaS plugin documentation](https://docs.lando.dev/platformsh/) and [source code](https://github.com/lando/platformsh)

- [Lando documentation](https://docs.lando.dev/)


## Before you begin

You need :

- Hardware that meets the [requirements](https://docs.lando.dev/getting-started/installation.html#hardware-requirements).

- A PHP project.


Lando doesn't automatically pull and set up environment variables that have been set in the Console.
To use a build hook that requires environment variables, manually [add them](https://docs.lando.dev/platformsh/config.html#environment-variables).

## 1. Install Lando

Follow the [Lando installation instructions](https://docs.lando.dev/getting-started/installation.html).

## 2. Create an access token

To authorize Lando to communicate with Web PaaS, create an [API token](../../administration/cli/api-tokens.md#2-create-an-api-token).
Copy the value.

## 3. Initialize Lando

> [!tabs]      

The `init` command generates the `.lando.yml` file required to start Lando.
It also adds to your account a [public SSH key](../ssh/ssh-keys.md).

## 4. Start Lando

To start your app and services, run `lando start`.

## 5. Access your local app

The last lines of the `lando start` command from the previous step contains URL to the different app and services.
Access your app and services by opening the according URLs in your browser.

## What's next

- [Import data and download files](https://docs.lando.dev/platformsh/sync.html) from your remote Web PaaS site.

- If you make changes in the Web PaaS [configuration files](../../learn-overview/structure) during development, run `lando rebuild` for these to be taken into account in Lando.

- To keep your Lando image up-to-date, see how to [update Lando](https://docs.lando.dev/getting-started/updating.html).


### Access logs

Access the global logs by running `lando logs`.

To access specific logs:

1\. Run `lando list` to get a list of the services you are using.

2\. Choose the one you'd like to inspect.

3\. Run <code>lando logs -s {{% variable "SERVICE_TO_INSPECT" %}}</code>.


For more guidance regarding logs, check the [Lando logs documentation](https://docs.lando.dev/help/logs.html)

### Untrusted SSL certificate

When you access your local Lando sites through HTTPS, you get an error message in your browser.
This is expected behavior.

Find out how to solve it in the [Lando blog](https://lando.dev/blog/2020/03/20/5-things-to-do-after-you-install-lando.html).

### Something still wrong?

[Get in touch with Lando](https://docs.lando.dev/platformsh/support.html).
