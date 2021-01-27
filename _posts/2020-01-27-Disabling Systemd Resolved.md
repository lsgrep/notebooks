---
title: "Disable Ubuntu Systemd Resolved"
description: "hacking Ubuntu Desktop"
layout: post 
toc: false 
comments: true 
hide: false 
categories: [Ubuntu, Systemd]
---


In Ubuntu, if you want to use custom DNS services which most likely run on port 53
you have to disable `systemd-resolved` first to vacate the port.

* edit `/etc/systemd/resolved.conf`
Add two lines:
   
`DNS=8.8.8.8`
   
`DNSStubListener=no`

```
#  This file is part of systemd.
#
#  systemd is free software; you can redistribute it and/or modify it
#  under the terms of the GNU Lesser General Public License as published by
#  the Free Software Foundation; either version 2.1 of the License, or
#  (at your option) any later version.
#
# Entries in this file show the compile time defaults.
# You can change settings by editing this file.
# Defaults can be restored by simply deleting this file.
#
# See resolved.conf(5) for details

[Resolve]
DNS=8.8.8.8
#FallbackDNS=
#Domains=
#DNSSEC=no
#DNSOverTLS=no
#MulticastDNS=no
#LLMNR=no
#Cache=no-negative
DNSStubListener=no
#ReadEtcHosts=yes
#ResolveUnicastSingleLabel=no
```


* `sudo systemctl restart systemd-resolved`


All set.
