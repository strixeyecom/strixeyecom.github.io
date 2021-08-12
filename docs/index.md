# Welcome

StrixEye is a behaviour analyzing tool for your web applications that can detect attackers before they intend to. It receives request without blocking request-response cycle and detect attackers. In this way, it does not cause performance loss. 

![strixeye architecture](assets/images/strixeye_architecture.png)

Our profiling algorithm searches for all requests and identify each request owner. Then we analyze all profiles and assign scores to profiles based on their behavior.

If a profile is detected as an attacker, a warning is generated and admins can get actions for this user. If you want, you use automated ban rules for your WAF or Load Balancer.

Detected attackers are recorded in our database. In this way, an attacker detected in another customer is blocked before they can reach your systems.