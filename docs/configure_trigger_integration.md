# Configure Integration and Trigger Rule

When a Suspect detected, you can get an action manually, but this is useless. For this, we developed Trigger and Integration mechanisms. Basically, Triggers are set of rules. Integrations are actions when a Trigger Rule is triggered. For example, you create an Email Integration, and you create a Trigger Rule. When a Suspect detected and this Trigger Rule triggered, you get an email about this Suspect.

## Create Integration

To create an Integration, go to ``Integrations > Create New Integration``

<img src="/assets/images/integrations_create.png" width="100%">

Then, select an Integration type.

<img src="/assets/images/integration_select.png" width="100%">

### Notification Integrations

**Notification** Integrations are pasive integrations. For example, when a Suspect detected, Slack Integration sends a message to Slack channel.

Select a Notification Integration (e.g. Slack) and create an Integration. After creation, you must verify it. Visit the Integration detail page and click the **Integrate** button. 

![integrate button](assets/images/integrate_button.png)

If successfully integrated, you can start using it. 

![test message](assets/images/slack_message.png)

### Incident Response Integrations

**Incident Response** integrations are active Integrations. For example, when a Suspect detected, Cloudflare Integration block this Suspect.

Select a Incident Response Integration (e.g. Cloudflare) and create an Integration. After creation, you must verify it. Visit the Integration detail page and click the **Integrate** button. 

First of all, create a custom Cloudflare API token from [Cloudflare Dashboard](https://dash.cloudflare.com/profile/api-tokens) with Zone Firewall Edit permission.

![cloudflare api token set zone firewall edit permission](assets/images/zone_firewall_edit.png)

Secondly, create a Cloudflare Integration with this API token and your Cloudflare Zone ID.

![create cloudflare integration](assets/images/integration_cloudflare_create.png)

Lastly, verify the Integration from Integration detail page.

![integrate cloduflare ](assets/images/cloudflare_integrate.png)

## Create Trigger Rule

To create a Trigger Rule, go to ``Triggers > Create New Trigger``

![sidebar triggers create button > create new trigger button](assets/images/triggers_create.png)

Then, set a trigger rule and select an Integration. 

![trigger rule](assets/images/trigger_rule.png)

Now, when this Trigger Rule is triggered, selected Integration will execute.

![create a trigger rule](assets/images/slack_70.png)

Or, if you create a Trigger with an Incident Response Integration, detected suspect will block.

![cloudflare firewall rule](assets/images/cloudflare_block.png)
