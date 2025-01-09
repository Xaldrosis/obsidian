---
title: SMTP relay to M365
draft: false
tags:
---

This was a test which I could not complete due to Telenet blocking outbound SMTP :/


apt update
apt upgrade -y
apt install -y sudo postfix mailutils curl
sudo dpkg-reconfigure postfix

Internet Site

System mail name:
smtp.home.xalnet.cc

Empty postmaster

Add xalnet.cc in the destination

Select No for synchronous updates

Add subnets to the local networks list that can send e-mail

Keep mailbox size limit 0

Keep default Local address extension character

Select internet protocol all

nano /etc/postfix/main.cf

```
relayhost = xalnet-cc.mail.protection.outlook.com
smtp_sasl_security_options = noanonymous
smtp_sasl_tls_security_options = noanonymous
smtp_tls_security_level = encrypt
smtp_use_tls = yes
smtpd_tls_cert_file = /etc/letsencrypt/live/smtp.home.xalnet.cc/fullchain.pem
smtpd_tls_key_file = /etc/letsencrypt/live/smtp.home.xalnet.cc/privkey.pem
```



curl https://get.acme.sh | sh
sudo mkdir -p /etc/letsencrypt/live/smtp.home.xalnet.cc
export CF_Token="CloudflareToken"
export CF_Email="Email"
cd /root/.acme.sh
./acme.sh --issue --dns dns_cf -d "smtp.home.xalnet.cc" --server letsencrypt \
--key-file /etc/letsencrypt/live/smtp.home.xalnet.cc/privkey.pem \
--fullchain-file /etc/letsencrypt/live/smtp.home.xalnet.cc/fullchain.pem


sudo systemctl restart postfix