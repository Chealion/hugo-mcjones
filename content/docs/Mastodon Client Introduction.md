
---
title: "Mastodon Client Introduction"
date: 2023-02-15 23:49:54
lastmod: 2023-02-15 23:51:56
categories: ['mastodon', 'python', 'golang']
draft: false
---


# Mastodon Client Introduction
## General
* https://docs.joinmastodon.org/api/

## Golang
* https://github.com/mattn/go-mastodon

* RegisterApp is used to register an application
* NewClient is used to make your client
  * Either put your ID, secret, and authtoken into your Mastodon Config object OR
  * Use `Authenticate` if using username/password
  * Use `AuthenticateApp` if using client creds

```
package main

import (
	"context"
	"fmt"
	"log"

	"github.com/mattn/go-mastodon"
)

func main() {
	c := mastodon.NewClient(&mastodon.Config{
		Server: "https://example.com",
		AccessToken: "ACCESS_TOKEN",
	})

	// Print mastodon version
	mastodonVersion, err := c.GetInstance(context.Background())
	if err != nil {
		log.Fatal(err)
	}
	fmt.Println(mastodonVersion.Version)

	//Toot and delete
	information, err := c.PostStatus(context.Background(), &mastodon.Toot{
		Status: "API Test",
	})
	if err != nil {
		log.Fatal(err)
	}
	fmt.Println(information)

	err = c.DeleteStatus(context.Background(), information.ID)
	if err != nil {
		log.Fatal(err)
	}
}
```

## Python
* https://mastodonpy.readthedocs.io/en/stable/
* https://github.com/halcy/Mastodon.py

```
pip install Mastodon.py
```

* `create_app` is used to register an application and save creds
* The credentials file is:
```
client_id/key
client_secret
URL
Name of APP
```
* `log_in` can then be used to get an access token (and save to a file)

If you have an access token (eg. created an app on the web UI) - you can initialize with the access token.

```
from mastodon import Mastodon

mastodon = Mastodon(
    api_base_url = 'https://example.com',
    access_token = 'ACCESS_TOKEN'
)

print ('Mastodon version: ' + mastodon.retrieve_mastodon_version())

information = mastodon.status_post(
    status = "Status via the API",
)

print (information)

mastodon.status_delete(
    id = information['id']
)
```

<!-- #public #mastodon #python #golang -->

<!-- {BearID:F04844D6-8BB1-4F64-9B5B-29E73A8A6EFD-3217-000003D85C8A7AF0} -->
