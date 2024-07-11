
---
title: "Postfix Queue Commands"
date: 2024-02-25T03:30:04Z
lastmod: 2024-02-25T03:31:13Z
categories: ['postfix', 'snippet']
draft: false
---


# Postfix Queue Commands
## See queue
```
postqueue -p
```

## Flush queue
Set to deliver again
```
postqueue -f
```

## Nuke entire queue
```
postsuper -d ALL
```

## Delete just one message
```
postsuper -d <message id>
```


<!-- #postfix #snippet #public -->

<!-- {BearID:B813D902-4ABA-4073-91A1-FB9B5ED097AF} -->
