
---
title: "Curtin Notes"
date: 2023-07-16T03:58:42Z
lastmod: 2023-07-16T05:32:37Z
categories: ['snippet', 'curtin']
draft: false
---


# Curtin Notes
## Inheritance/multiple files

Choose a file to include:
```
{{inhert "file"}}
```

However the file being included will REPLACE your previous file’s contents without:
```
{{self.body}}
```
At the top of the file, and this needs to be repeated for each inherited file.

## MAAS required commands
If you’re using Curtin with MAAS remember to ensure you have the following late command:
```
99-maas: [wget, '--no-proxy', {{node_disable_pxe_url|escape.json}}, '--post-data', {{node_disable_pxe_data|escape.json}}, '-O', '/dev/null']
```

As well as the following:
```
debconf_selections:
 maas: |
  {{for line in str(curtin_preseed).splitlines()}}
  {{line}}
  {{endfor}}
```

## Using `echo`

Unlike wget or other commands, commands running in the shell’s environment need to have a shell process spun up in the target to get the correct path.

You will need to use `sh -c` in the command:

```
  18-deny-module-ipmi: ['curtin', 'in-target', '--', 'sh', '-c', "echo blacklist ipmi_si >> /etc/modprobe.d/blacklist.conf"]
  18-deny-module-nouveau: ['curtin', 'in-target', '--', 'sh', '-c', "echo blacklist nouveau >> /etc/modprobe.d/blacklist.conf"]
```


<!-- #snippet #curtin #public -->

<!-- {BearID:C3E804FB-8707-423F-92E1-6F390410D5D6} -->
