+++
title = 'First'
description = "This is the first page (a test page) for my blog."
date = 2024-09-07T20:11:34+05:30
# author = "prabhpreet singh"
draft = false

weight = 1
aliases = ["/first"]
tags = ["first", "test"]
showToc = true
TocOpen = false
hidemeta = false
comments = false
canonicalURL = "https://canonical.url/to/page"
disableHLJS = true # to disable highlightjs
disableShare = false
hideSummary = false
searchHidden = true
ShowReadingTime = true
ShowBreadCrumbs = true
ShowPostNavLinks = true
ShowWordCount = true
ShowRssButtonInSectionTermList = true
UseHugoToc = true
+++
<!-- [[cover]]
    image = "<image path/url>" # image path/url
    alt = "<alt text>" # alt text
    caption = "<text>" # display caption under cover
    relative = false # when using page bundles set this to true
    hidden = true # only hide on current single page -->



# Heading
## sub heading

some text

1. point 1
2. point 2

<!-- ,hl_lines=[2,"5-7"],linenostart=199 -->
```python  {linenos=table}
print("hello")
print("hello")
print("hello")
for i in range(100):
    print("world")
print("hello")
@dataclass
class Data:
    pass
print("hello")
print("hello")
print("hello")
```

#### another heading
- some more point
- and another

{{< highlight python  >}}
print("hello")
print("hello")
print("hello")
print("hello")
print("hello")
print("hello")
print("hello")
{{< / highlight >}}

<script src="https://gist.github.com/rahularity/86da20fe3858e6b311de068201d279e3.js"></script>