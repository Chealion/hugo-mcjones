
---
title: "Using jq to modify files"
date: 2024-11-10T06:22:48Z
lastmod: 2024-11-10T06:52:42Z
categories: ['snippet', 'jq']
draft: false
---


# Using jq to modify files
## Insert/Append

```
echo '{"hello": "world"}' | jq --arg foo bar '. + {foo: $foo}'
OR
echo '{"hello": "world"}' | jq '. + {foo: "bar"}'

{
  "hello": "world",
  "foo": "bar"
}
```

And “directly” in a file:
```
jq '.path += { "claims": "bar" } ' file.json > file1.json && mv file1.json file.json
```
`jq` can not edit in place.

## Replace
```
echo '{"hello": "world"}' | jq '. + {hello: "bar"}'
```

## Delete
```
echo '{"hello": "world", "foo": "bar"}' | jq '. | del(.foo)'
```

<!-- #public #snippet #jq -->

<!-- {BearID:1424BB80-64D2-41D8-BE1F-31CEA8A690BD} -->
