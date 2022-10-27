---
title: iptable enable log and seperate to specific log file
date: 2022-09-24 23:00:59
tags:
---

at the begin of your automation script 

```
IPTLOGLEVEL=4

iptables -A INPUT -j LOG --log-ip-options --log-prefix='[netfilter] INPUT ' --log-level ${IPTLOGLEVEL}
iptables -A INPUT -j LOG --log-tcp-options --log-prefix='[netfilter] INPUT ' --log-level ${IPTLOGLEVEL}
```
seperating to specific log file
add filter config for rsyslog / syslog

#### rsyslog filter config
```
vim /etc/rsyslog/rsyslog.d/01-iptables-specific-filter.log
```

#### syslog filter config
```
vim /etc/syslog/syslog.d/01-iptables-specific-filter.log
```
#### rsyslog and syslog filter option to seperate to specific file 
##### in this option to /var/log/iptables.log
 
```
:msg,contains,"[netfilter] " -/var/log/iptables.log
& stop
```

### restart you log service
```
if [ -f "/etc/init.d/rsyslog" ]; then /etc/init.d/rsyslog restart; fi
if [ -f "/etc/init.d/syslog" ]; then /etc/init.d/syslog restart; fi

```

