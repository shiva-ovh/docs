---
title: Exporting data
slug: exporting
section: Tutorials
order: 9
---

**Last updated 6th November 2023**



## Objective  

As a Web PaaS user, your code and data belong to you.
At any time, you can download your site's data for local development, to back up your data, or to change provider.

## Before you begin

You need:

- [Git](https://git-scm.com/downloads)

- A Web PaaS account

- Code in your project

- Optional: the [Web PaaS CLI](../../administration-cli)


## 1. Download your app's code

Your app's code is maintained through the Git version control system.

To download your entire app's code history:

> [!tabs]      

## 2. Download your files

Some files might not be stored in Git,
such as data your app writes [in mounts](../../create-apps-app-reference#mounts).

You can download your files [using the CLI](../../development-file-transfer#transfer-files-using-the-cli) or [using SSH](../../development-file-transfer#transfer-files-using-an-ssh-client).

## 3. Download data from services

The mechanism for downloading from each service (such as your database) varies.

For services designed to hold non-persistent data, such as [Redis](../../add-services-redis) or [Solr](../../add-services-solr),
it's generally not necessary to download data as it can be rebuilt from the primary data store.

For services designed to hold persistent data, see each service's page for instructions:

- [MySQL](../../add-services-mysql#exporting-data)

- [PostgreSQL](../../add-services-postgresql#exporting-data)

- [MongoDB](../../add-services-mongodb#exporting-data)

- [InfluxDB](../../add-services-influxdb#export-data)


## 4. Get environment variables

Environment variables can contain critical information such as tokens or additional configuration options for your app.

Environment variables can have different prefixes:

- Variables beginning with `env:` are exposed [as Unix environment variables](../../development-variables#top-level-environment-variables).

- Variables beginning with `php:` are interpreted [as `php.ini` directives](../../development-variables#php-specific-variables).


All other variables are [part of `$PLATFORM_VARIABLES`](../../development-variables/use-variables#use-provided-variables).

To back up your environment variables:

> [!tabs]      

## What's next

- Migrate data from elsewhere [into Web PaaS](../migrating).

- Migrate to [another region](../../projects-region-migration).

- To use data from an environment locally, export your data and set up your [local development environment](../../development-local).

