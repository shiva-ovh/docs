---
title: Memcached (Object cache)
slug: add-services-add-services-memcached
section: Add-Services
---

**Last updated 6th November 2023**



## Objective  

**Last updated 6th November 2023**



## Objective  

{{% description %}}

See the [Memcached documentation](https://memcached.org) for more information.

Both Memcached and Redis can be used for application caching. As a general rule, Memcached is simpler and thus more widely supported while Redis is more robust. Web PaaS recommends using Redis if possible but Memcached is fully supported if an application favors that cache service.

{{% frameworks version="1" %}}

- [Drupal](../guides/drupal/memcached.md)



{{% /frameworks %}}

## Supported versions

{{% major-minor-versions-note configMinor="true" %}}


<!-- API Version 1 -->

<table>
    <thead>
        <tr>
            <th>Grid</th>
            <th>Dedicated Gen 3</th>
            <th>Dedicated Gen 2</th>
        </tr>
    </thead>
    <tbody>
        <tr>
            <td>1.6 |  
|  1.5 |  
|  1.4</td>
            <td>- 1.6  
- 1.5  

- 1.4</td>

            <td>- 1.6  
- 1.5  

- 1.4</thd>

        </tr>
    </tbody>
</table>

<--->
<!-- API Version 2 -->

1.6 |  
|  1.5 |  
|  1.4

{{% /version/specific %}}

{{% relationship-ref-intro %}}

{{% service-values-change %}}

```yaml
{
    "service": "memcached16",
    "ip": "169.254.228.111",
    "hostname": "3sdm72jgaxge2b6aunxdlzxyea.memcached16.service._.eu-3.{{< vendor/urlraw "hostname" >}}",
    "cluster": "rjify4yjcwxaa-master-7rqtwti",
    "host": "memcached.internal",
    "rel": "memcached",
    "scheme": "memcached",
    "type": "memcached:{{% latest "memcached" %}}",
    "port": 11211
}
```

## Usage example

{{% endpoint-description type="memcached" php=true python=true /%}}

{{< codetabs v2hide="true" >}}

+++
title=Go
file=static/files/fetch/examples/golang/memcached
highlight=go
+++

<--->

+++
title=Java
file=static/files/fetch/examples/java/memcached
highlight=java
+++

<--->

+++
title=Node.js
file=static/files/fetch/examples/nodejs/memcached
highlight=js
+++

<--->

+++
title=PHP
file=static/files/fetch/examples/php/memcached
highlight=php
+++

<--->

+++
title=Python
file=static/files/fetch/examples/python/memcached
highlight=python
+++

{{< /codetabs >}}

<!-- Version 2: .environment shortcode + context -->
{{% version/only "2" %}}

```yaml {configFile="app"}
{{< snippet name="myapp" config="app" root="myapp" >}}

# Other options...

# Relationships enable an app container's access to a service.
relationships:
    memcachedcache: "cachemc:memcached"
{{< /snippet >}}
{{< snippet name="cachemc" config="service" placeholder="true" >}}
    type: memcached:{{% latest "memcached" %}}
{{< /snippet >}}
```

```json  

```  

```bash {location="myapp/.environment"}
# Decode the built-in credentials object variable.
export RELATIONSHIPS_JSON=$(echo ${{< vendor/prefix >}}_RELATIONSHIPS | base64 --decode)

# Set environment variables for individual credentials.
export CACHE_HOST=$(echo $RELATIONSHIPS_JSON | jq -r ".memcachedcache[0].host")
export CACHE_PORT=$(echo $RELATIONSHIPS_JSON | jq -r ".memcachedcache[0].port")

# Surface a Memcached connection string for use in app.
export CACHE_URL="${CACHE_HOST}:${CACHE_PORT}"
```

{{< /v2connect2app >}}

{{% /version/only %}}


