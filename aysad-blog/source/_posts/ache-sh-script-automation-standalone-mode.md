---
title: acme.sh script automation standalone mode
date: 2022-09-24 16:21:08
tags: ache.sh script automation
---

```
ACMEDOMAIN=domainname.tld
/root/.acme.sh/acme.sh --standalone --issue -d www.${ACMEDOMAIN} -d ${ACMEDOMAIN} \
--cert-file /etc/ssl/${ACMEDOMAIN}-cert.pem \
--key-file /etc/ssl/${ACMEDOMAIN}-priv.pem \
--fullchain-file /etc/ssl/${ACMEDOMAIN}-fullchain.pem \
--pre-hook "nginx -s stop; killall nginx" \
--post-hook "nginx"
```

#### check the certificate holder (alternativ to letsencrpyt):
[https://zerossl.com]

#### check to the cli tool for ssl issue handling:
[https://acme.sh]
