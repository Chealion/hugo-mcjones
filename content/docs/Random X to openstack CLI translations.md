
---
title: "Random X to openstack CLI translations"
date: 2018-02-07 11:46:34
lastmod: 2023-07-19 14:39:49
categories: ['snippet', 'openstack']
draft: false
---


# Random X to openstack CLI translations

Official Doc: https://docs.openstack.org/python-openstackclient/latest/cli/decoder.html

## Cinder

```
cinder reset-state
openstack volume set --state
```
## Keystone

```
keystone token-get
openstack token issue
```

## Nova

```
nova service-disable 
openstack compute service set
```

```
nova boot
openstack server create
```

```
nova hypervisor-stats
openstack hypervisor stats show
```

```
nova instance-action-list
openstack server event list
```

```
nova reset-state
openstack server set --state
```
## Swift

```
swift list
openstack container list
```

```
swift list <container>
openstack object list <container>
```

```
swift upload
openstack object create
```

```
swift download
openstack object save
```

NOTE: tempurl is not in the openstackcli.

<!-- #snippet #openstack #public -->

<!-- {BearID:48A0A732-A8D3-40F9-B69D-F861095B4DAE-840-000408030C93C27D} -->
