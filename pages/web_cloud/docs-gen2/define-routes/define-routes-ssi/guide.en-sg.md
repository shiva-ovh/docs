---
title: Server Side Includes (SSI)
slug: define-routes-ssi
section: Define-Routes
---

**Last updated 14th November 2023**



## Objective  

{{% description %}}

At its most basic, you can include files within other ones so as not to repeat yourself.

Start by enabling SSI:

{{< version/specific >}}
<!-- Web PaaS configuration-->
```yaml {configFile="routes"}
"https://{default}/":
    type: upstream
    upstream: "app:http"
    ssi:
        enabled: true
```

