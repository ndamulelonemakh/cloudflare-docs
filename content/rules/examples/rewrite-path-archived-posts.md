---
pcx_content_type: example
summary: You can use the example below for a demo Transform rule where all requests to `/news/2012/...` are rewritten to `/archive/news/2012/...`.
tags:
  - Transform
title: Rewrite path of archived blog posts
---

# Rewrite path of archived blog posts

To rewrite all requests to `/news/2012/...` to `/archive/news/2012/...` you must add a reference to the content of the original URL. Create a new rewrite URL rule and define a dynamic URL path rewrite using an expression:

{{<example>}}

Text in **Expression Editor**:

```txt
starts_with(http.request.uri.path, "/news/2012/")
```

Text after **Path** > **Rewrite to...** > _Dynamic_:

```txt
concat("/archive", http.request.uri.path)
```

{{</example>}}

The filter uses the [`starts_with()`](/ruleset-engine/rules-language/functions/#function-starts_with) function all paths starting with `/news/2012/`. The dynamic path rewrite uses the [`concat()`](/ruleset-engine/rules-language/functions/#function-concat) function to concatenate a prefix to the original URL path of the HTTP request.