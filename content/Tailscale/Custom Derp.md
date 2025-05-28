---
title: Custom Derp
draft: false
tags:
---
Install go.

```
wget https://go.dev/dl/go1.23.4.linux-amd64.tar.gz
rm -rf /usr/local/go && tar -C /usr/local -xzf go1.23.4.linux-amd64.tar.gz
rm go1.23.4.linux-amd64.tar.gz
```

Install DERP.

```
sudo useradd --system --create-home --home-dir /opt/derp --shell /bin/bash derp
echo 'export PATH=$PATH:/usr/local/go/bin' | sudo tee -a /opt/derp/.profile
sudo -u derp -i go install tailscale.com/cmd/derper@main
```


Make sure derp can open ports as a regular user.

```
sudo setcap 'cap_net_bind_service=+ep' /opt/derp/go/bin/derper
```

Create the derp service.

```
sudo tee /etc/systemd/system/derper.service <<'EOF'
[Unit]
Description=DERP Server
After=network.target
 
[Service]
User=derp
Group=derp
Environment=DOMAIN=derp.home.xalnet.cc
Environment=DIRECTORY=/opt/derp
ExecStart=/bin/bash -c "${DIRECTORY}/go/bin/derper -c ${DIRECTORY}/derp.conf --hostname ${DOMAIN} --verify-clients"
Restart=always

[Install]
WantedBy=multi-user.target
EOF
```

Start the service.

```
systemctl enable --now derper
```

```
sudo systemctl status derper
```

Port forward TCP 443 and UDP 3478.