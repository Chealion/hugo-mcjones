
---
title: "SSL Verification and Derivation Tips"
date: 2023-07-17 10:24:13
lastmod: 2023-07-17 10:37:14
categories: ['snippet', 'ssl', 'tls']
draft: false
---


# SSL Verification and Derivation Tips

## Verify a private key
```
openssl rsa -noout -modulus -in <private-key-file>
```

## Verify the public cert
```
openssl x509 -noout -in <certificate-file> -text
```

## Verifying they match
The modulus of both should match (easiest to verify by hashing)
```
openssl x509 -noout -modulus -in <cert> | openssl md5
openssl rsa -noout -modulus -in <privatekey> | openssl md5
```
## Checking Dates
```
openssl x509 -noout -dates -in <certificate-file>
```

## Derivation Tips
### Apache (2.4+)
Concatenate the cert followed by intermediate cert(s).

Set `SSLCertificateFile` and `SSLCertificateKeyFile` in the virtual host config

### nginx

Concatenate the cert followed by intermediate cert(s)

### haproxy

Concatenate the cert, private key, followed by intermediate certs, and then optionally a dhparam output.

Dhparam output can be created by running: `dhparam -out dhparam.pem 2048`

The entry in haproxy will then look like:
```
bind    :443 ssl crt /path/to/<cert+privkey+intermediate> alpn h2,http/1.1
```

(Check https://ssl-config.mozilla.org/ for the best settings)

<!-- #snippet #ssl #tls #public -->

<!-- {BearID:68506A57-6C1F-423B-B1D4-80613B8BB1F8} -->
