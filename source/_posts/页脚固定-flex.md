---
title: 页脚固定-flex
date: 2017-11-20 16:04:39
tags: CSS
thumbnail:
---


## The HTML

```
<body class="Site">
  <header>…</header>
  <main class="Site-content">…</main>
  <footer>…</footer>
</body>
```

## The CSS

```
.Site {
  display: flex;
  min-height: 100vh;
  flex-direction: column;
}

.Site-content {
  flex: 1;
}
```

>[参考](https://philipwalton.github.io/solved-by-flexbox/demos/sticky-footer/)