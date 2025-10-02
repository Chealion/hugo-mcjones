
---
title: "Using 1Password SDK with External Secrets Operator"
date: 2025-10-02T01:53:18Z
lastmod: 2025-10-02T02:51:02Z
categories: ['snippet', 'kubernetes', 'external-secrets-operator']
draft: false
---


# Using 1Password SDK with External Secrets Operator
https://external-secrets.io/latest/provider/1password-sdk/

The downside with the upstream docs is it’s a copy and paste from the deprecated Connect Server documentation. It does not cover setting up authenticating to 1Password at all. Do we still need Connect in some way? Service Accounts?

We’ll be following part 1 from the SDK setup tutorial (https://developer.1password.com/docs/sdks/setup-tutorial) and then where part 2 starts using Node, we’ll configure External Secrets Operator.

1. (Optional) Create a vault to use with External Secrets operator. In this example we’ve made one called k8s.
2. Log into your 1Password account online
3. Create a service account for 1Password:
   1. https://my.1password.com/developer-tools/infrastructure-secrets/serviceaccount
   2. Give the account a name (eg. eso)
   3. Grant read only access only to the vault you created. *Service accounts can't be modified after they're created. If you need to make changes, revoke the service account and create a new one.*
   4. Save the token to a different vault in 1Password. We will need to inject this into Kubernetes so ESO can use it. There is a helpful “Save in 1Password” button right there to do it as well.
4. (Optional) Create a secret to test with: `op item create --category login --title "test-login-1" --vault "k8s"  'username=example' 'password=password'`
5. Inject the service account token into your cluster so K8s can connect. You can either use `kubectl apply` to apply a yaml file or do it as a one liner.
```
---
apiVersion: v1
kind: Secret
metadata:
  name: onepassword-eso
type: Opaque
stringData:
  token: |-
BASE_64'd_TOKEN_VALUE_SAVED_IN_STEP_3
```
```
kubectl create secret generic onepassword-eso \
    --from-literal=token='TOKEN_VALUE_SAVED_IN_STEP_3' \
--namespace external-secrets
```
6. Create your secret store and optionally, the example item to confirm it works:
```
---
apiVersion: external-secrets.io/v1
kind: SecretStore
metadata:
  name: 1password-sdk
spec:
  provider:
    onepasswordSDK:
      vault: k8s
      auth:
        serviceAccountSecretRef:
          name: onepassword-eso
          key: token

---
apiVersion: external-secrets.io/v1
kind: ExternalSecret
metadata:
  name: fetch-from-onepassword
spec:
  secretStoreRef:
    kind: SecretStore
    name: 1password-sdk
  target:
    creationPolicy: Owner
  data:
    - secretKey: test-login-1
      remoteRef:
        key: test-login-1/username
```
7. Last let’s check the value:
```
kubectl get secret -n external-secrets fetch-from-onepassword -o jsonpath='{.data.test-login-1}' | base64 --decode
```

<!-- #public #snippet #kubernetes #external-secrets-operator -->

<!-- {BearID:E1C51231-ED25-42BE-A851-EB038B0FBF18} -->
