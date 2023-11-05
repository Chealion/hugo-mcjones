
---
title: "Random X to openstack CLI translations"
date: 2018-02-07 11:46:34
lastmod: 2023-09-14 12:27:32
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

## Neutron
```
neutron l3-agent-list-hosting-router
openstack network agent list --long --router 

neutron dhcp-agent-list-hosting-net
openstack network agent list --long --network

neutron router-list-on-l3-agent
oepnstack router list --long --agents
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
