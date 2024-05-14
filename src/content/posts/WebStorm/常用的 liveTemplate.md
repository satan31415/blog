---
title: 常用的 liveTemplate
published: 2024-05-14
description: "常用的 liveTemplate"
tags: ["WebStorm"]
category: WebStorm
draft: false
---

### 1. 打印(log)
![](https://api.onedrive.com/v1.0/shares/s!AmRYeUQXQNkEqX_6awEMDrV3-94n/root/content)
```ts
console.log('%c 文件路径 ---> $FILEPATH$','background: #4285f4; font-size: 16px')
console.log('%c 行号 ---> $LINE$','background: #4285f4; font-size: 16px')
console.log(
    '%c heh ---> ',
    'background: #4285f4; font-size: 16px',
    $START$
)
```

### 2. 可折叠代码块 + 注释
```ts
/* region ====== $DESC$ start */
/* endregion === $DESC$ end */
```
```html
<!-- region ====== $DESC$ start -->
<!-- endregion === $DESC$ end -->
```

