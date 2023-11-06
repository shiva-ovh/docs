---
title: Define routes for your multiple apps
slug: guide.en-us
section: Routes
---

**Last updated 6th November 2023**



## Objective  

**Last updated 6th November 2023**



## Objective  

When you set up a project containing multiple applications,
all of your apps are served by a single [router for the project](../../../define-routes).
Each of your apps must have a `name` that's unique within the project.
To define specific routes for one of your apps, use this `name`.

There are various ways you can define routes for multiple app projects.

{{% version/only "1" %}}
![Diagram of a project containing multiple apps](images/multiple-app.png "0.5")
{{% /version/only %}}

In this project, you have a CMS app, two frontend apps (one using Symfony and another using Gatsby),
and a Mercure Rocks server app, defined as follows:


```yaml {configFile="apps"}
- name: admin


  type: nodejs:16
  source:
    root: admin
  ...
- name: api


  type: php:8.2
  source:
    root: api
  ...
- name: gatsby


  type: nodejs:18
  source:
    root: gatsby
  ...
- name: mercure


  type: golang:1.18
  source:
    root: mercure/.config
  ...
```
<--->
```yaml {configFile="apps"}
applications:
    admin:
        source:
            root: admin
        type: nodejs:{{% latest "nodejs" %}}
    api:
        source:
            root: api
        type: php:{{% latest "php" %}}
    gatsby:
        source:
            root: gatsby
        type: nodejs:{{% latest "nodejs" %}}
    mercure:
        source:
            root: mercure/.config
        type: golang:{{% latest "golang" %}}
```
{{% /version/specific %}}

> [!primary]  
> 
> You don't need to define a route for each app in the repository.
> If an app isn't specified, then it isn't accessible to the web.
> One good example of defining an app with no route is when you [use Git submodules](../project-structure#split-your-code-source-into-multiple-git-submodule-repositories) and want to [use a source operation to update your submodules](../../development-submodules#update-submodules).
> 
> You can also achieve the same thing by defining the app as a [`worker`](../app-reference.md#workers).
> 
> 

Depending on your needs, you could configure the router container
[using subdomains](#define-routes-using-subdomains) or using [subdirectories](#define-routes-using-subdirectories).

### Define routes using subdomains

You could define routes for your apps as follows:


```yaml {configFile="routes"}
"https://mercure.{default}/":
    type: upstream
    upstream: "mercure:http"
"https://{default}/":
    type: upstream
    upstream: "api:http"
```
<--->
```yaml {configFile="routes"}
routes:
    "https://mercure.{default}/":
        type: upstream
        upstream: "mercure:http"
    "https://{default}/":
        type: upstream
        upstream: "api:http"
```
{{% /version/specific %}}

So if your default domain is `example.com`, that means:

- `https://mercure.example.com/` is served by your Mercure Rocks app (`mercure`).


- `https://example.com/` is served by your Symfony frontend app (`api`).



> [!primary]  
> 
> Using a subdomain might [double your network traffic](https://nickolinger.com/blog/2021-08-04-you-dont-need-that-cors-request/),
> so consider using a path like `https://{default}/api` instead.
> 
> 

### Define routes using subdirectories

Alternatively, you could define your routes as follows:


```yaml {configFile="routes"}
"https://{default}/":
    type: upstream
    upstream: "api:http"
"https://{default}/admin":
    type: upstream
    upstream: "admin:http"
```
<--->
```yaml {configFile="routes"}
routes:
    "https://{default}/":
        type: upstream
        upstream: "api:http"
    "https://{default}/admin":
        type: upstream
        upstream: "admin:http"
```
{{% /version/specific %}}


Then you would need to configure each app's `web.locations` property to match these paths:


```yaml {configFile="apps"}
-   name: api


    type: php:8.2
    source:
        root: api
    ...
    web:
        locations:
            "/":
                passthru: "/index.php"
                root: "public"
                index:
                    - index.php
- name: admin


  type: nodejs:16
  source:
    root: admin
  ...
  web:
    locations:
      '/admin':
        passthru: '/admin/index.html'
        root: 'build'
        index:
          - 'index.html'
```
<--->
```yaml {configFile="apps"}
applications:
    admin:
        source:
            root: admin
        type: nodejs:{{% latest "nodejs" %}}
        ...
        web:
            locations:
              '/admin':
                  passthru: '/admin/index.html'
                  root: 'build'
                  index:
                    - 'index.html'
    api:
        source:
            root: api
        type: php:{{% latest "php" %}}
        ...
        web:
            locations:
                "/":
                    passthru: "/index.php"
                    root: "public"
                    index:
                        - index.php

routes:
    "https://{default}/":
        type: upstream
        upstream: "api:http"
    "https://{default}/admin":
        type: upstream
        upstream: "admin:http"
```
{{% /version/specific %}}

So if your default domain is `example.com`, that means:

- `https://example.com/` is served by your Symfony frontend app (`api`).


- `https://example.com/admin` is served by your Admin app (`admin`).



Note that in this example, for the configuration of your `admin` app,
you need to add the URL suffix `/admin` as both an index in the `web.locations` and a value for the `passhtru` setting.

For a complete example, [go to this project on GitHub](https://github.com/platformsh-templates/bigfoot-multiapp/tree/submodules-root-subfolders-applications).
