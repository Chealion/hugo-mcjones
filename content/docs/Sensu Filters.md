
---
title: "Sensu Filters"
date: 2022-08-10 19:42:09
lastmod: 2022-08-10 20:25:04
categories: ['Passes', '1.', '2.', '3.', 'sensu', 'puppet']
draft: false
---


# Sensu Filters
Our standard filter for events.

```
<!-- #Passes Standard filter if: -->
<!-- #1. Failed 3 checks in a row (will not send a resolution if we only failed once or twice) -->
<!-- #2. OR every hour if we're still in a bad state. -->
<!-- #3. OR if an "instant" label was applied to the check (event.check.labels) -->

  standard:
    ensure: present
    action: allow
    expressions:
      - '(event.check.occurrences == 3 && event.check.occurences_watermark > 2) || ( (event.check.occurrences % (3600 / event.check.interval) == 0) && (event.check.status > 0) ) || ( event.check.labels.  instant == "true" )'
```

<!-- #public #sensu #puppet -->

<!-- {BearID:64518DC9-5600-455F-8FD4-3A4552ADAFBA-51307-000023552418F5C0} -->
