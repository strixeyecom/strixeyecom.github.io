# Domains

Agent groups requests according to domains while analysing. So each Agent needs at least one domain.

You can see all Domains on the [Domains](https://dashboard.strixeye.com/domains){:target="_blank"} page.

![agent name and agent domains](../assets/images/domains.png)

## Create Domain
You can create a new domain in [Domain Create page](https://dashboard.strixeye.com/domains/create/){:target="_blank"}

![agent name and agent domains](../assets/images/domains_create.png)

**Ignored Paths** fields allow you to filter requests from that domain. For example, if you don't want to analyze all requests under ``/statics/`` path, you can add ``/statics/`` paths to ``Ignored Paths`` fields. There may be some predefined paths, be careful when creating a domain.

## Domain Details

### Edit Domain

In Domain edit page, you can edit Domain's ``Ignored Paths`` fields but you can not edit the Domain name. If you want to edit Domain, you should delete the Domain and recreate it.

![agent name and agent domains](../assets/images/domain_edit.png)

### Detected Suspicions

At the bottom of the domain edit page, you can see the suspicions detected in the domain.

![agent name and agent domains](../assets/images/domain_suspicions.png)
