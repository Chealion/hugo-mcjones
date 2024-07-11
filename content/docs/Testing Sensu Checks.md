
---
title: "Testing Sensu Checks"
date: 2020-04-01T21:02:59Z
lastmod: 2023-10-03T20:46:51Z
categories: ['sensu']
draft: false
---


# Testing Sensu Checks
## On Machine
```
sudo -u sensu <check command>
```

It is easier to cd into the dynamic asset cache folder first:
`cd /var/cache/sensu/sensu-agent/???` .

If using the Ruby runtime:

```
[ root@sensu-proxy /var/cache/sensu/sensu-agent/ff3ba13e1a20f89eaac7613fc2c072a8a355918dbaf158b8d1565ebf02d066f3382dde872c1d80002ded762d8a3a860ccce20410b8dedb47b69fd7038e918dde/bin ] # ./ruby /var/cache/sensu/sensu-agent/75f212aab3255c5862ea84b83951097bd1ad41963714e0f5bbafd5404556b962091d5c95790b3e5f10ac9a728838887f16d84af33e4956bd2265c77d61fbda54/bin/check-dns.rb -s 199.116.232.2 -d google.ca
```

## Testing Filters/Handlers
```
curl -X POST \
-H 'Content-Type: application/json' \
-d '{
  "check": {
    "metadata": {
      "name": "test-critical-check-0002"
    },
    "status": 2,
    "output": "test-critical-check",
    "handlers": ["email"],
    "subscriptions": ["honolulu", "test"]
  }
}' \
http://127.0.0.1:3031/events 
```

Run this at least 3 times to get past the standard filter

And clear:
```
curl -X POST \
-H 'Content-Type: application/json' \
-d '{
  "check": {
    "metadata": {
      "name": "test-critical-check-0002"
    },
    "status": 0,
    "output": "test-critical-check",
    "handlers": ["email"],
    "subscriptions": ["honolulu", "test"]
  }
}' \
http://127.0.0.1:3031/events 
```

```
Jun 30 19:42:39 dair-hnl-sensu-01 sensu-backend[15708]: {"component":"pipelined","error":"ReferenceError: 'honolulu' is not defined","level":"error","msg":"error executing JS","time":"2020-06-30T19:42:39-06:00"}
```


## Manually Triggering/Testing a Handler

```
cd /var/cache/sensu/sensu-backend
find . -name 'sensu-email-handler'
cd <HASH FROM ABOVE>/bin

sensuctl event info ENTITY CHECK --format json | ./sensu-email-handler -f sensu@dair-atir.canarie.ca -t dair-sysadmins@cybera.ca -s smtp.cybera.ca  -i
```
## Other Resources
https://docs.sensu.io/sensu-go/latest/operations/maintain-sensu/troubleshoot/#manually-execute-a-handler

<!-- #public #sensu -->

<!-- {BearID:1C0AFCA6-28B6-43A8-B5F8-9B143E15A225-1087-000085409E159F25} -->
