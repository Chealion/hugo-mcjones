
---
title: "Mask Change of a Prefix in Netbox in Python"
date: 2024-07-22T23:27:20Z
lastmod: 2024-07-23T00:14:29Z
categories: ['python', 'snippet', 'netbox']
draft: false
---


# Mask Change of a Prefix in Netbox in Python
```
import pynetbox

def main():
    nb = pynetbox.api('NETBOX_URL', 'NETBOX_TOKEN')

    ip_addresses = nb.ipam.ip_addresses.filter(parent="192.168.0.0/24")
    for ip in ip_addresses:
        if "/32" in str(ip):
            corrected = str(ip)[:-3] + "/24"
            ip.address = corrected
            ip.display = corrected
            ip.save()
            print ip + " -> " + corrected

if __name__ == '__main__':
    main()
```

<!-- #python #snippet #public #netbox -->

<!-- {BearID:67503A4F-7F3A-49ED-9FFF-AD01C96B690E} -->
