# Getting Started

If you have beta access to StrixEye, you can start with this section.

## Configure Dashboard
You can access dashboard from [dashboard.strixeye.com](https://dashboard.strixeye.com)

### Create your Domains

Firstly, you must add your Domains that want to analyze with StrixEye. Select `Domains > Create New Domain` from sidebar and create your Domains.

![sidebar domains button > create new domain button](assets/images/domains_sidebar.png)

Domains are not editable, so if you make a mistake while creating a Domain, you should delete and re-create it.

### Create an Agent

Before the install Agent to server, you must create an Agent from Dashboard. Select `Agent > Create New Agent` from sidebar.

![sidebar agents button > create new agent button](assets/images/agents_sidebar.png)

Give a name and select Domains that you want to analyzing with the new Agent. Each Agent must have minimum one Domain. You can add multiple Domains to a Agent.

![agent name and agent domains](assets/images/agent_create.png)


## Install Agent to your server

To install StrixEye Agent, you need docker and docker-compose.

Download StrixEye Cli from [GitHub](https://github.com/strixeyecom/cli/releases) and extract to ``/usr/local/bin``

```bash
sudo tar -xvzf cli_0.0.1_Linux_amd64.tar.gz -C /usr/local/bin strixeye && sudo chmod +x /usr/local/bin/strixeye
```

For more information about StrixEye Cli, visit Cli Documentation.

```bash
sudo strixeye agent install --interactive
```

You need your user API token and your Agent ID. You can access your API token in [Dashboard > Profile](https://dashboard.usestrix.com/settings/profile) page and Agent ID in Agent detail page.

![agent installation](assets/images/agent_install.png)

If you get an error, visit the CLI troubleshooting page.

After Agent installation, reload daemon and start **strixeyed**.

```bash
sudo systemctl daemon-reload && sudo systemctl enable strixeyed && sudo systemctl start strixeyed
```

This may takes several minutes. If everythink is okay, you will see Agent statistics on Agent detail page and dashboard.

![agent statistics](assets/images/agent_stats.png)

## Mirror Requests

StrixEye is outside of the request response cycle. You must mirror all requests to your application to StrixEye. You can do this in your load balancer, WAF or firewall.

![strixeye architecture](assets/images/strixeye_architecture.png)

For example, you can access Nginx Mirror documentation [here.](https://nginx.org/en/docs/http/ngx_http_mirror_module.html) 

!!! Warning "Mirror Request Headers"
    You need to add two headers to mirrored requests.

    * X-FORWARDED-FOR
    * X-FORWARDED-PORT

    For Nginx, you can add like this
    ```conf
        proxy_set_header X-Forwarded-For  $proxy_add_x_forwarded_for;;
	    proxy_set_header X-Forwarded-Port  $server_port;
    ```

If everything is OK, you can see Agent statistics on Agent detail page or dashboard.

![Agent statistics with requests](assets/images/agent_success.png)


We configured Dashboard, installed Agent and mirrored requests to Agent. Now, Agent starts autamtically detect suspects and suspicions. If you don't know what is suspect and suspicion, you can read Suspect and Suspicion page.

## Configure Trigger and Integration

When a suspect detected, you can get an action manually, but this is useless. For this, we developed Trigger and Integration mechanisms. Basically, triggers are set of rules. Integrations are actions when a trigger is triggered. For example, you create an Email Integration, and you create a Trigger Rule. When a Suspect detected and this Trigger triggered, you get an email about this suspect.

### Create Integration

To create an Integration, go to ``Integrations > Create New Integration``

![sidebar integrations button > create new integration button](assets/images/integrations_create.png)

Then, select an Integration type. **Incident Response** integrations are active Integrations. For example, when a suspect detected, AWS WAF Integration can automatically ban this suspect.

**Notification** Integrations are pasive integrations. For example, when a suspect detected, Email Integration sends an email.

![select inregration type](assets/images/integration_select.png)

When an Integration created, you must verify it. Visit the Integration detail page and click the **Integrate** button. 

![integrate button](assets/images/integrate_button.png)

If successfully integrated, you can start using it. 

![integrated](assets/images/integrated.png)

### Trigger

To create a trigger, go to ``Triggers > Create New Trigger``

![sidebar triggers create button > create new trigger button](assets/images/triggers_create.png)

Then, set a trigger rule and select an Integration. 

![trigger rule](assets/images/trigger_rule.png)
