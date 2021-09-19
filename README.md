![Logo](https://i.imgur.com/PyKLAe7.png)

[![License](https://img.shields.io/badge/license-The_Unlicense-red.svg)](https://unlicense.org/)

About
----

**IPsum** is a threat intelligence feed based on 30+ different publicly available [lists](https://github.com/stamparm/maltrail) of suspicious and/or malicious IP addresses. All lists are automatically retrieved and parsed on a daily (24h) basis and the final result is pushed to this repository. List is made of IP addresses together with a total number of (black)list occurrence (for each). Greater the number, lesser the chance of false positive detection and/or dropping in (inbound) monitored traffic. Also, list is sorted from most (problematic) to least occurent IP addresses.

As an example, to get a fresh and ready-to-deploy auto-ban list of "bad IPs" that appear on at least 3 (black)lists you can run:

```
curl --compressed https://raw.githubusercontent.com/stamparm/ipsum/master/ipsum.txt 2>/dev/null | grep -v "#" | grep -v -E "\s[1-2]$" | cut -f 1
```

If you want to try it with `ipset`, you can do the following:

```
sudo su
apt -qq install iptables ipset
ipset -q flush ipsum
ipset -q create ipsum hash:net
for ip in $(curl --compressed https://raw.githubusercontent.com/stamparm/ipsum/master/ipsum.txt 2>/dev/null | grep -v "#" | grep -v -E "\s[1-2]$" | cut -f 1); do ipset add ipsum $ip; done
iptables -I INPUT -m set --match-set ipsum src -j DROP
```

In directory [levels](levels) you can find preprocessed raw IP lists based on number of blacklist occurrences (e.g. [levels/3.txt](levels/3.txt) holds IP addresses that can be found on 3 or more blacklists).

Wall of Shame (2021-09-19)
----

|IP|DNS lookup|Number of (black)lists|
|---|---|--:|
179.43.141.99|-|9
171.25.193.25|tor-exit5-readme.dfri.se|9
107.189.3.160|eu.mypanelplus.com|8
171.25.193.77|tor-exit1-readme.dfri.se|8
60.8.87.190|-|8
202.29.214.13|-|8
222.187.232.60|-|8
192.160.102.170|ogopogo.relay.coldhak.com|8
91.219.237.21|178911033-dedicated.serverastra.com|8
185.100.87.72|iclnm.worlpeed.net|8
141.98.10.125|-|8
141.98.10.179|er.includeswitche.com|8
167.86.71.45|vmi662507.contaboserver.net|8
176.10.99.200|accessnow.org|8
185.31.175.228|-|7
185.31.175.226|-|7
128.31.0.13|tor-exit.csail.mit.edu|7
80.82.77.33|sky.census.shodan.io|7
5.183.209.217|-|7
89.234.157.254|marylou.nos-oignons.net|7
222.186.30.112|-|7
209.141.57.50|mail10.achdaswirdgehen.me|7
185.107.47.215|tor-exit.r1.darknet.dev|7
205.185.127.100|-|7
199.195.252.247|gre.ligahosting.ro|7
162.247.74.74|wiebe.tor-exit.calyxinstitute.org|7
5.2.69.50|-|7
107.189.8.8|258223.com|7
80.82.77.139|dojo.census.shodan.io|7
221.181.185.94|-|7
185.107.47.171|tor-exit.r2.darknet.dev|7
185.220.100.253|tor-exit-2.zbau.f3netze.de|7
185.220.100.254|tor-exit-3.zbau.f3netze.de|7
141.98.10.121|-|7
45.128.133.242|-|7
198.96.155.3|exit.tor.uwaterloo.ca|7
91.149.225.131|tor-exit-node.miao.pt|7
185.220.102.4|communityexit.torservers.net|7
185.130.44.108|tor-exit-se1.privex.cc|7
199.195.248.37|-|7
77.247.181.163|lumumba.torservers.net|7
60.170.247.162|-|7
209.141.32.151|-|7
222.187.227.122|-|7
93.174.95.106|battery.census.shodan.io|7
185.31.175.235|-|7
221.131.165.33|-|7
178.73.215.171|178-73-215-171-static.glesys.net|7
171.25.193.20|tor-exit0-readme.dfri.se|7
222.187.254.41|-|7
176.10.104.240|tor1e1.digitale-gesellschaft.ch|7
185.191.124.143|-|7
213.202.216.189|h176.helix.dedi.server-hosting.expert|7
80.67.172.162|algrothendieck.nos-oignons.net|7
8.209.91.186|-|7
64.113.32.29|tor.t-3.net|7
222.187.232.39|-|7
222.168.30.19|-|7
199.195.250.77|ny1.exit.tor.alkyl.eu.org|7
222.186.30.76|-|7
209.141.48.211|smtpout104.9ninewest.com|7
205.185.114.54|coopernet.co.nz|7
185.31.175.215|-|7
105.203.195.68|host-105.203.195.68.etisalat.com.eg|7
45.153.160.132|-|7
45.153.160.137|-|7
149.202.238.204|204.238.202.149.fr-sbg.flexcloud.seflow.it|7
185.220.100.241|tor-exit-14.zbau.f3netze.de|7
81.161.63.100|-|7
89.163.252.12|srv1358.dedicated.server-hosting.expert|7
185.31.175.243|-|7
185.31.175.247|-|7
117.248.249.70|-|7
89.163.243.88|ca011.calcit.dedicated.server-hosting.expert|7
107.173.209.244|107-173-209-244-host.colocrossing.com|7
209.141.34.36|-|7
185.100.87.202|-|7
