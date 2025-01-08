# Load balancer solution using Nginx

* By now you have learned what Load Balancing is used for and have configured an LB solution using Apache, but a DevOps engineer must be a versatile professional and know different alternative solutions for the same problem. That is why, in this project we will configure an Nginx load balancer solution.

* It is also extremely important to ensure that connections to your Web solutions are secure and information is encrypted in transit - we will also cover connection over HTTP (HTTPS protocol), its purpose and what's required to implement it.

* When data is moving between a client (browser) Web Server over the internet - it passes through multiple network devices and if the data is not encrypted , it can be relatively easy intercepted by someone who has access to the intermediate equipment . This kind of information security threat is called Man-in-the-middle-attack

* This treat is real - users who shares sensitive information (bank details, social media access credentials, etc) via non-secured channels , risk their data to be compromised and being used by cybercriminals.

* SSL and it's newer version TSL - is a security protocol that protects connection from MITM attacks by creating an encrypted session between browsers and Web servers . here we will refer this family to cryptographic protocols as SSL/TLS - even though SSL was replaced by TLS . the term is still being widely used .

* SSL/TLS uses digital certificates to identify and validate a website. A browser reads the certificate issued by a certificate Authority (CA) to make sure that the website is registered in the CA so it can be trusted to establish a secure connection .

* There are different types of SSL/TLS certificates - you can learn more about them in the future , you can also watch a tutorial about them .


* In this project we will register our website using LetsEncrypt certificate Authority, to automate certificate issuance we will use a shell client recommended by LetsEncrypt - certbot.

![loadBalancingUsingNginx](https://github.com/user-attachments/assets/8c2cc368-b0e7-4a86-9aa0-60e98d6256c6)
