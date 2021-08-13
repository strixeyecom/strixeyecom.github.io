# Configure Integration and Trigger Rule

When a Suspect detected, you can get an action manually, but this is useless. For this, we developed Trigger and Integration mechanisms. Basically, Triggers are set of rules. Integrations are actions when a Trigger Rule is triggered. For example, you create an Email Integration, and you create a Trigger Rule. When a Suspect detected and this Trigger Rule triggered, you get an email about this Suspect.

## Create Integration

To create an Integration, go to ``Integrations > Create New Integration``

<img src="/assets/images/integrations_create.png" width="100%">

Then, select an Integration type. **Incident Response** integrations are active Integrations. For example, when a Suspect detected, AWS WAF Integration block this Suspect.

**Notification** Integrations are pasive integrations. For example, when a Suspect detected, Slack Integration sends a message to Slack channel.

<img src="/assets/images/integration_select.png" width="100%">

When an Integration created, you must verify it. Visit the Integration detail page and click the **Integrate** button. 

![integrate button](assets/images/integrate_button.png)

If successfully integrated, you can start using it. 

![test message](assets/images/slack_message.png)

## Create Trigger Rule

To create a Trigger Rule, go to ``Triggers > Create New Trigger``

![sidebar triggers create button > create new trigger button](assets/images/triggers_create.png)

Then, set a trigger rule and select an Integration. 

![trigger rule](assets/images/trigger_rule.png)

Now, when this Trigger Rule is triggered, selected Integration will execute.

## How to Block Attackers?

We need an Incident Response Integration for block attackers. In this section, we will describe Cloudflare Integration. 

First of all, create a custom Cloudflare API token from [Cloudflare Dashboard](https://dash.cloudflare.com/profile/api-tokens) with Zone Firewall Edit permission.

![cloudflare api token set zone firewall edit permission](assets/images/zone_firewall_edit.png)

Secondly, create a Cloudflare Integration with this API token and your Cloudflare Zone ID.

![create cloudflare integration](assets/images/integration_cloudflare_create.png)

Lastly, create a Trigger Rule that using this Cloudflare Integration.

![create a trigger rule](assets/images/cloudflare_trigger_70.png)

That's it! If a Suspect detected with a score higher than 70, Cloudflare Integration will set a firewall rule for this Suspect.

![suspect](assets/images/test_suspect.png)

![cloudflare firewall rule](assets/images/cloudflare_block.png)

If you create a Trigger Rule like above but using Slack Integration, you will receive a Slack message about Suspect.

![sidebar triggers create button > create new trigger button](assets/images/slack_70.png)
