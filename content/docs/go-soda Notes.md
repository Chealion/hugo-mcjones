
---
title: "go-soda Notes"
date: 2023-02-16 22:44:32
lastmod: 2023-02-16 23:43:20
categories: ['go-soda', 'golang']
draft: false
---


# go-soda Notes
https://github.com/SebastiaanKlippert/go-soda

## Basic
Get a resource URL and just check it’s fields and last modified date
```
package main

import (
	"encoding/json"
	"fmt"
	"log"

	"github.com/SebastiaanKlippert/go-soda"
)

func main() {
  sodareq := soda.NewGetRequest("https://data.calgary.ca/resource/35ra-9556", "")

	modified, err := sodareq.Modified()
	if err != nil {
		log.Fatal(err)
	}
	fields, err := sodareq.Fields()
	if err != nil {
		log.Fatal(err)
	}
	fmt.Println("Modified: ", modified)
	fmt.Println("Fields: ", fields)
}
```

## SoSQL and Filtering
The SODA API also has a more featurful query syntax: http://dev.socrata.com/docs/queries.html / https://github.com/SebastiaanKlippert/go-soda/blob/master/soda.go#L203

In main above you can add the following at the bottom:

```
  // Specify format (json, csv, etc.) - https://dev.socrata.com/docs/formats/
	sodareq.Format = "json"

  // SimpleFilters - https://dev.socrata.com/docs/filtering.html
	sodareq.Filters["description"] = "Stalled"

  // SoQL - https://dev.socrata.com/docs/queries/
  // Query is the SoSQL struct at https://github.com/SebastiaanKlippert/go-soda/blob/master/soda.go#L203
	// Only grab fields we want
  sodareq.Query.Select = []string{"incident_info", "description", "start_dt", "modified_dt", "longitude", "latitude", "id"}
  // Search for pedestrian
	sodareq.Query.Q = "pedestrian"
	// Sort by a column - easier to use AddOrder
  sodareq.AddOrder("start_dt", true)
  // Only the last 5
	sodareq.Query.Limit = 5

```

<!-- #public #go-soda #golang -->

<!-- {BearID:1851277C-FC7A-419D-BA1A-873DC224F7FD-3217-000005A543494DC1} -->
