---
pcx_content_type: example
product: Rules
title: Rewrite blog archive URLs to support a new URL format
---
# Rewrite blog archive URLs to support a new URL format

To rewrite the URLs of a blog archive that follow the URL format `/posts/<YYYY>-<MM>-<DD>-<TITLE>` to the new format `/posts/<YYYY>/<MM>/<DD>/<TITLE>`, create the following rewrite URL rule:

{{<example>}}

Text in **Expression Editor**:

```txt
http.request.uri.path ~ "^/posts/[0-9]+-[0-9]+-[0-9]+-.*"
```

Text after **Path** > **Rewrite to...** > _Dynamic_:

```txt
regex_replace(http.request.uri.path, "^/posts/([0-9]+)-([0-9]+)-([0-9]+)-(.*)$", "/posts/${1}/${2}/${3}/${4}")
```

{{</example>}}

The function `regex_replace()` also allows you to extract parts of the URL using regular expressions' capture groups. Create capture groups by putting part of the regular expression in parentheses. Then, reference a capture group using `${<NUMBER>}` in the replacement string, where `<NUMBER>` is the number of the capture group.