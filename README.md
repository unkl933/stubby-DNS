<h1 align="center">Stubby Ubuntu</h1>

## Overview

Stubby is an open-source application that acts as a local DNS Privacy stub resolver using DNS over TLS (DoT). Stubby encrypts DNS queries sent from a client device (desktop or laptop) to a DNS Privacy resolver increasing end user privacy.

## Instructions

0. Open the Terminal.

1. Ensure the "Universe" repository is enabled and ensure the repositories are up to date:
```bash
sudo add-apt-repository universe && sudo apt update
```

2. Install Stubby
```bash
sudo apt install stubby
```
3. This will install stubby and the getdns library. Once installed, stubby runs in the background. You you check its status with:
```bash
systemctl status stubby
```
4. Back up and replace the default stubby.yml file with the stubby.yml file attached to this support article.
```bash
sudo mv /etc/stubby/stubby.yml /etc/stubby/stubby.backup.yml && sudo wget -O /etc/stubby/stubby.yml https://raw.githubusercontent.com/unkl933/stubby-DNS/main/stubby.yml
```
5. Restart Stubby to recognize the new configuration.
```bash
sudo service stubby restart
```
6. Set your network connection's IPv4 DNS server to 127.0.0.1 - If using IPv6, also set your connection's IPv6 DNS server to ::1
Follow the instructions here, substituting 9.9.9.9 for 127.0.0.1
7. Then restart NetworkManager for the changes to take effect.
```bash
sudo systemctl restart NetworkManager
```
8. Confirm that DNS resolution is working in general by visiting a website, and confirm you're using Quad9 by going to https://www.dnsleaktest.com/
