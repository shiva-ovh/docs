---
title: Authenticated Composer repositories
slug: composer-auth
section: Php
---

**Last updated 9th November 2023**



## Objective  

[Packagist](https://packagist.org/) is the primary Composer repository for public PHP packages.
But you can also have Composer download PHP packages from a private, third-party Composer repository.
To make sure Composer has the necessary credentials to do so,
follow the instructions on this page.

## Before you begin

You need:
- A Web PaaS project using [PHP](../languages/languages-php) and Composer

- Credentials to access a private third-party Composer repository

- The [Web PaaS CLI](../../administration/administration-cli)


## 1. Declare a private Composer repository

To allow Composer to download packages from a private third-party repository,
declare the repository in your Composer setup.

```json {location="composer.json"}
{
    "repositories": [
        {
            "type": "composer",
            "url": "https://{{< variable "PRIVATE_REPOSITORY_URL" >}}"
        }
    ]
}
```

## 2. Set up Composer authentication using a variable

To allow Composer to successfully authenticate when accessing the declared private repository,
set an [`env:COMPOSER_AUTH` variable](../../development/development-variables) for your project.

To do so, run the following command:

```bash
{{% vendor/cli %}} variable:create --level project --name env:COMPOSER_AUTH \
  --json true --visible-runtime false --sensitive true --visible-build true \
  --value '{"http-basic": {"{{< variable "PRIVATE_REPOSITORY_URL" >}}": {"username": "{{< variable "USERNAME" >}}", "password": "{{< variable "PASSWORD" >}}"}}}'
```

The [`env:` prefix](../../development/variables/_index.md#top-level-environment-variables) means that the variable is exposed
as its own Unix environment variable.
The `--visible-runtime false` and `--visible-build true` flags mean the variable is available to Composer only during the build.

## 3. Clear your project's build cache

For security reasons, make sure that the authentication credentials aren't cached in your project's build container.
To do so, run the following command:

```bash
{{% vendor/cli %}} project:clear-build-cache
```

## Access dependencies downloaded from a private repository

When you download a dependency from a private third-party Composer repository,
that dependency is usually hosted in a [private Git repository](../../development/development-private-repository).
Access to private Git repositories is restricted through the use of SSH keys.
But most private Composer tools mirror tagged releases of dependencies
and serve them directly without hitting the Git repository.
To avoid having to authenticate against a remote Git repository,
make sure your dependencies specify tagged releases.
