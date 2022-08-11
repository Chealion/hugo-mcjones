
---
title: "Testing Sensu Checks"
date: 2020-04-01 15:02:59
lastmod: 2022-08-10 19:23:57
categories: ['sensu']
draft: false
---


# Testing Sensu Checks
## On Machine
```
sudo -u sensu <check command>
```

It is easier to cd into the dynamic asset cache folder first:
`cd /var/cache/sensu/sensu-agent/???` - you’ll need 

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

## Other Resources
https://docs.sensu.io/sensu-go/latest/operations/maintain-sensu/troubleshoot/#manually-execute-a-handler

<!-- #public #sensu -->

<!-- {BearID:1C0AFCA6-28B6-43A8-B5F8-9B143E15A225-1087-000085409E159F25} -->
