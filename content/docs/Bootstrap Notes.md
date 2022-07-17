
---
title: Bootstrap Notes
date: 2022-07-14 23:11:36
lastmod: 2022-07-17 10:14:05
categories: ['bootstrap', 'webdev']
draft: false
---


# Bootstrap Notes
Sometimes it makes sense to just accept standards and roll with it instead of failing miserably at rewriting and relearning CSS you learned a decade ago.

## Usage
Bootstrap has a CSS component and an optional JS component that is required if you want to use some of the more interactive components: https://getbootstrap.com/docs/5.2/getting-started/introduction/#js-components

The easiest to include via CDN, but it helps to have a copy locally as well.
```
<link href="https://cdn.jsdelivr.net/npm/bootstrap@5.2.0-beta1/dist/css/bootstrap.min.css" rel="stylesheet"
integrity="sha384-0evHe/X+R7YkIZDRvuzKMRqM+OrBnVFBL6DOitfPri4tjfHxaWutUpFmBp4vmVor" crossorigin="anonymous">
```

## Docs
https://getbootstrap.com/docs/5.2

## Cheatsheet
https://getbootstrap.com/docs/5.2/examples/cheatsheet/

## Spacing
Most pertinent notes from:
https://getbootstrap.com/docs/4.0/utilities/spacing/

m = margin
p = padding

t, b, l, r = top, bottom, left, right
x, y = Both left and right, or both top and bottom

0 = eliminate / 0
1 = spacer * 0.25
2 = spacer * 0.5
3 = spacer
4 = spacer * 1.5
5 = spacer * 3
Auto

Eg.

```
.ml-1 {
  margin-left: ($spacer * .25) !important;
}

.px-2 {
  padding-left: ($spacer * .5) !important;
  padding-right: ($spacer * .5) !important;
}
```

<!-- #public #bootstrap #webdev -->

<!-- {BearID:BBFF02BA-42CF-4229-8DBF-75C9C565AC6C-68161-00000A793BAA2811} -->
