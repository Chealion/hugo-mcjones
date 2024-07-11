
---
title: "Netbox Snippets"
date: 2023-07-14T19:50:37Z
lastmod: 2023-07-18T06:20:43Z
categories: ['snippet', 'netbox']
draft: false
---


# Netbox Snippets
## REST - basic cURL
```
curl -H "Authorization: Token TOKEN" \
-H "Accept: application/json; indent=4" \
"https://netbox/api/ipam/ip-addresses/?vrf_id=3"
```

https://demo.netbox.dev/static/docs/rest-api/authentication/

Note: This limits to 50 items by default. You can use `&limit` to change.

## GraphQL

A GraphQL UI is available at `/graphql` on Netbox. GraphQL is a bit more work to use with cURL.

The same REST query above in graphQL:

```
query {
  ip_address_list (vrf_id: "3") {
    address
    dns_name
    description
  }
}
```

### cURL
```
curl -g \
-X POST \
-H "Content-Type: application/json" \
-H "Authorization: Token TOKEN" \
-d '{"query":"query { ip_address_list (vrf_id: "3") { address dns_name description } }"}' \
https://netbox.example/graphql
```

## Munging Netbox Data to CSV

```
| jq -r '.results | (map(keys) | add | unique) as $cols | map(. as $row | $cols | map($row[.])) as $rows | $cols, $rows[] | @csv'
```

JQ to CSV conversion one liner from: https://stackoverflow.com/a/32965227

This does NOT work with multiple layers - so this will need tweaking each time to only select fields you want from `.results`. So use `'.results[] | keys` to get the keys you want, and then:
```
| jq -r '.results[] | ( if (.dns_name == "") then .dns_name = .description else . end  ) | { address, dns_name }' | jq -rs '(map(keys) | add | unique) as $cols | map(. as $row | $cols | map($row[.])) as $rows | $cols, $rows[] | @csv'
```

## Merging Two Fields
If you have bad data entry (it wouldn’t be production without it) - how can we “merge” two fields. Eg. dns_name and description - set dns_name to description if dns_name is a blank string

```
.results[] | ( if (.dns_name == "") then .dns_name = .description else . end  ) | { address, dns_name }
```


<!-- #public #snippet #netbox -->

<!-- {BearID:9A3B87F7-F6E8-434E-B951-8D0DBDE91A0E} -->
