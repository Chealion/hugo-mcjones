
---
title: "Kustomize and Resource URLs"
date: 2024-10-29T00:55:16Z
lastmod: 2024-12-11T05:51:31Z
categories: ['snippet', 'kubernetes', 'kustomize']
draft: false
---


# Kustomize and Resource URLs
## Assumptions
You have a .tar.gz file and/or a folder of yaml files that can be downloaded (https) or found in a cloned repository.

In your `kustomization.yaml` you can include the following resource types:

1. Clones the repository and assumes it can build from the yaml files at the root of the repository.
2. Clones the repository and assumes it can build from the yaml files in the `directory` directory at tag `1.0.0`
3. Download a specific file - hence the `https://` at the start.

```
resources:
  - github.com/example/clone
  - github.com/example/directory?ref=1.0.0
  - https://github.com/example/example2/releases/download/tag/abc.yaml
```

<!-- #snippet #kubernetes #kustomize #public -->

<!-- {BearID:987473DF-873E-4784-A0C2-01C709AFEED2} -->
