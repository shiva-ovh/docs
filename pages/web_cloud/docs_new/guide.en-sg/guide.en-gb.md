---
title: Introduction
slug: guide.en-sg
section: Guide.En-Sg
hidden: true
---

**Last updated 6th November 2023**



## Objective  

**Last updated 6th November 2023**



## Objective  

{{< home >}}

## How the docs are organized

There are different [kinds](https://documentation.divio.com/) of documentation.
Some docs are useful when you're just starting out, 
while others go into detail that's relevant only after you've deployed many projects on Web PaaS.

This site is roughly split into categories based on where you are in your journey working with Web PaaS, described below.

### Get started

If you're still unfamiliar with Web PaaS and how it works, _but_ you're also looking to quickly start working with the platform, the **Get started** section is the right place to begin.

Learn the basics of how Web PaaS leverages Git to produce reusable build images, identical-to-production environments in staging and development (including production data), as well as the basics of monitoring and troubleshooting your environments. 

Ready to get started? [Let's go!](/get-started/)

### Learn

After going through the **Get started** section, you may want to know more about how Web PaaS works and the logic behind it. The **[Learn](../../../../../../../../learn)** section is a collection of tutorials and conceptual guides to help you understand the ins and outs of Web PaaS.

- [**What is Web PaaS?**](../../../../../../../learn-overview)



    With this guide, find out which problem Web PaaS is trying to solve.
    Learn how Web PaaS's configuration, build and deploy pipelines, and the structure of environments play into the broader philosophy behind reliably deploying applications.

- [**Tutorials**](../../../../../../../learn-tutorials)



    Once you're familiar with Web PaaS, its basic rules and philosophy, you may be curious about how you can replicate common workflows in other tools on our platform. 
    From scheduling dependency updates and backups to exporting data, the [**Tutorials**](../../../../../../../learn-tutorials) provide all the information you need.

- [**Best practices**](../../../../../../../learn-bestpractices)



    Web PaaS makes deploying and managing infrastructure no different than working with Git.
    As your work becomes more experimental, however, you may be interested in optimizing your workflows, and addressing common constraints of the platform. 
    The [**Best practices**](../../../../../../../learn-bestpractices) documentation contains articles that address advanced use cases for caching, microservices, and more.

### Frameworks

Now that you understand the basic rules of Web PaaS, you're likely ready to deploy your own custom code in a chosen framework. 
The **Frameworks** section is a collection of framework-specific how-to guides - from best practices to configuration, local development, and more.

{{< version/specific >}}

| Language              | Frameworks |
| :----------------     | :------  |
| [Python](../../../../../../../languages-python)                |   [Django](../../../../../../../guides-django)  |
| [PHP](../../../../../../../languages-php)                      |   [Drupal](../../../../../../../guides-drupal)<br/>[Ibexa](../../../../../../../guides-ibexa)<br/>[Laravel](../../../../../../../guides-laravel)<br/>[Symfony](../../../../../../../guides-symfony)<br/>[TYPO3](../../../../../../../guides-typo3)<br/>[WordPress](../../../../../../../guides-wordpress)   |
| [Javascript/Node.js](../../../../../../../languages-nodejs)     |  [Gatsby](../../../../../../../guides-gatsby)<br/>[Next.js](../../../../../../../guides-nextjs)<br/>[Strapi](../../../../../../../guides-strapi)  |
| [Java](../../../../../../../languages-java)                  |  [Hibernate](../../../../../../../guides-hibernate)<br/>[Jakarta](../../../../../../../guides-jakarta)<br/>[Micronaut](../../../../../../../guides-micronaut)<br/>[Quarkus](../../../../../../../guides-quarkus)<br/>[Spring](../../../../../../../guides-spring)  |

<--->

| Language              | Frameworks |
| :----------------     | :------  |
| [Python](../../../../../../../languages-python)                |   [Django](../../../../../../../get-started-django)<br/>[Flask](../../../../../../../get-started-flask)  |
| [PHP](../../../../../../../languages-php)                      |   [Laravel](../../../../../../../get-started-laravel)   |
| [Javascript/Node.js](../../../../../../../languages-nodejs)     |  [Express](../../../../../../../get-started-express)<br/>[Next.js](../../../../../../../get-started-nextjs)<br/>[Strapi](../../../../../../../get-started-strapi)  |

{{< /version/specific >}}

### Reference

The **Reference documentation** section is the largest and most comprehensive. 
It includes details of configuration, environment variables, activities, and much more material you can use in your day-to-day work.

{{< home/table "services" >}}
{{< home/table "languages" >}}
{{< home/table "configuration" >}}
{{< home/table "topics" >}}

### API documentation

Find out more about Web PaaS's GIT implementation and REST API, and how you can leverage them to manage every aspect of your projects, through Web PaaS's [API documentation](https://api.platform.sh/docs/).

{{< version/specific >}}

<!-- For now, most of these links are only relevant to Web PaaS -->
### More docs, found elsewhere

There are many resources available outside of the documentation that will help you work with Web PaaS, including demos, talks, and podcasts. 

[Check them out here](../../../../../../../learn-resources).

To stay informed of all the latest Web PaaS news, join our newsletter.

<div style="margin-top: 3rem; text-align: center;">
    <a class="start-cta font-semibold text-sm xl:text-base px-4 py-2 bg-skye rounded text-white hover:bg-skye-dark focus:bg-skye-dark"
    href="https://platform.sh/preferences/" rel="noopener">Sign up for the newsletter</a>
</div>

<--->

<!-- TBD: white-label version when available -->

{{< /version/specific >}}


## Connect with us

{{< version/specific >}}
### Join the community

The Web PaaS community meets on both a [Community forum](https://community.platform.sh) and [Slack](https://chat.platform.sh) for questions and discussion.

Have an experiment you'd like to share?
Looking for a way to contribute?

<div style="margin-top: 3rem; text-align: center;">
    <a class="start-cta font-semibold text-sm xl:text-base px-4 py-2 bg-skye rounded text-white hover:bg-skye-dark focus:bg-skye-dark"
    href="https://chat.platform.sh" rel="noopener">Join us on Slack</a>
</div>

### Contribute
Feel free to open an issue or pull request for any of the repositories below, or let us know on [Slack](https://chat.platform.sh) if you find a problem we can help with:

{{< home/links-github >}}

<--->
{{</version/specific >}}

### Get support

If you're experiencing issues with your projects, don't hesitate to open a [support ticket](/learn/overview/get-support).
