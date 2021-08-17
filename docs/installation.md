# Getting Started

If you have beta access to StrixEye, you can start with this section.

## Configure Dashboard
You can access dashboard from [dashboard.strixeye.com](https://dashboard.strixeye.com){:target="_blank"}

### Create your Domains

Firstly, you must add your Domains that want to analyze with StrixEye. Select `Domains > Create New Domain` from sidebar and create your Domains.

![sidebar domains button > create new domain button](assets/images/domains_sidebar.png)

Domains are not editable, so if you make a mistake while creating a Domain, you should delete and re-create it.

### Create an Agent

Before the install Agent to server, you must create an Agent from Dashboard. Select `Agent > Create New Agent` from sidebar.

![sidebar agents button > create new agent button](assets/images/agents_sidebar.png)

Give a name and select Domains that you want to analyzing with the new Agent. Each Agent must have minimum one Domain. You can add multiple Domains to an Agent.

![agent name and agent domains](assets/images/agent_create.png)


## Install Agent to your server

To install StrixEye Agent, you need [Docker](https://docs.docker.com/engine/install/){:target="_blank"} and [Docker Compose](https://docs.docker.com/compose/install/){:target="_blank"}.

Download StrixEye CLI from [GitHub](https://github.com/strixeyecom/cli/releases){:target="_blank"} and extract to ``/usr/local/bin``

```bash
sudo tar -xvzf cli_${cli_version}_Linux_amd64.tar.gz -C /usr/local/bin strixeye && sudo chmod +x /usr/local/bin/strixeye
```

<!-- For more information about StrixEye CLI, visit CLI Documentation. -->

```bash
sudo strixeye agent install --interactive
```

You need your user API token and your Agent ID. You can access your API token in [Dashboard > Profile](https://dashboard.strixeye.com/settings/profile){:target="_blank"} page and Agent ID in Agent detail page.

![agent installation](assets/images/agent_install.png)

<!-- If you get an error, visit the CLI troubleshooting page. -->

After Agent installation, reload daemon and start **strixeyed**.

```bash
sudo systemctl daemon-reload && sudo systemctl enable strixeyed && sudo systemctl start strixeyed
```

This may takes several minutes. If everythink is OK, you will see Agent statistics on Agent detail page and dashboard.

![agent statistics](assets/images/agent_stats.png)

## Mirror Requests to StrixEye Agent

StrixEye is outside of the request response cycle. You must mirror all incoming requests to StrixEye. You can do this in your load balancer, WAF or firewall.

![strixeye architecture](assets/images/strixeye_architecture_mirror.png)

For example, you can access Nginx Mirror documentation [here.](https://nginx.org/en/docs/http/ngx_http_mirror_module.html){:target="_blank"}

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


We configured Dashboard, installed Agent and mirrored requests to Agent. Now, Agent starts autamtically detect suspects and suspicions. 

<!-- If you don't know what is suspect and suspicion, you can read Suspect and Suspicion page. -->

