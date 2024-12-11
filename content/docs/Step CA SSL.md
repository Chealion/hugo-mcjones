
---
title: "Step CA SSL"
date: 2024-10-28T21:33:08Z
lastmod: 2024-11-10T05:30:44Z
categories: ['ssl', 'stepca']
draft: false
---


# Step CA SSL
https://smallstep.com/

Step CA offers to run as a service/server. So you can use it as an ACME endpoint or for other integrations.

https://smallstep.com/blog/everything-pki/ is a great overview.

A big note - Step strongly encourages automation - so the default certificate length is a single day.

## Create your CA
```
step ca init

step-ca $(step path)/config/ca.json
step ca root root_ca.crt
```
## Create a certificate
```
step ca certificate localhost localhost.crt localhost.key
step ca certificate svc.example.com svc.crt svc.key

step ca certificate localhost localhost.crt localhost.key --not-after=5m
step ca certificate localhost localhost.crt localhost.key --not-after=90d
```
## Bundle Certs
```
step certificate bundle localhost.crt root_ca.crt localhost-bundle.crt
```
## Check a certificate
```
step certificate inspect svc.crt --short
```
## Creating a cert in two steps (with CSR)
```
step certificate create --csr foo.example.com foo.csr foo.key
step ca sign foo.csr foo.crt
```
## Export your CA root
```

```

## SSH Certificates
Step will also help deal with SSH certs which allows you to rotate your SSH keys frequently.

1. Bootstrap your CA:
```
step ca bootstrap --ca-url [CA URL] --fingerprint [CA fingerprint]
```
2. Configure SSH:
```
step ssh config --roots > /path/to/ssh_user_key.pub
```
3. Configure SSHD:
```
cat <<EOF >> /etc/ssh/sshd_config
# This is the CA's public key for authenticating user certificates:
TrustedUserCAKeys /path/to/ssh_user_key.pub
EOF

systemctl restart ssh
```

## Create SSH Cert
```
step ssh certificate alice@smallstep.com id_ecdsa
```

<!-- #ssl #stepca #public -->

<!-- {BearID:9E9FBCAD-D253-43F1-8CEA-527A3831C7E7} -->
